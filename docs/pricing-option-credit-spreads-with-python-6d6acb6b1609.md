# 用 Python 定价期权信用利差

> 原文：<https://medium.datadriveninvestor.com/pricing-option-credit-spreads-with-python-6d6acb6b1609?source=collection_archive---------2----------------------->

![](img/235e00620899ef24caa3303daec5e7a8.png)

Photo by [Chris Liverani](https://unsplash.com/@chrisliverani?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

在之前的一篇文章中，我提到我在玩期权交易策略。现在我又有了一些进步。第一，快速 TL；以前工作的博士。计划是卖出看涨期权，然后以更高的价格买入，将差价作为利润。为了对冲这一头寸，我将买入相关股票。

现在我想展示一下我是如何在市场数据中寻找机会的。有许多相互竞争的因素，所以我必须权衡它们。我想要:

*   最高预付保费
*   净接近零的买入/卖出比率δ和γ具有大的正θ
*   股票购买和期权保证金的最低现金要求
*   中低股票波动
*   充足的股票和期权流动性

为了简化搜索并最小化风险，我将把重点放在两次直接执行之间的期权差价上。这也将保持我们的利润成本下降，虽然也有更少的溢价差异。为了限制时间范围，我打算在期权到期前一周集中买入价差，希望它们到期时一文不值。接下来的计划是寻找下一组期权，在接下来的一周进行交易。

***免责声明:*** *再次声明，我不是理财顾问，这不是理财建议。期权和股票交易有风险，其中一些我会在这里讨论。在投资股票或期权市场之前，你应该做自己的研究。我一直把这个策略写在纸上作为学术练习，因为我觉得这很有趣。您可以出于自己的目的和研究目的自由使用下面的代码，但它的提供没有任何明示或暗示的保证。你想要你的钱，但是你已经被警告了。*

# 收集必要的数据

我之前提到过我没有很好的市场数据来源，但是我找到了一些可行的方法。雅虎财经有免费的市场数据，并且有许多 Python 库支持访问这些数据。我选定的是 [yahoo_fin](http://theautomatic.net/yahoo_fin-documentation/) 。虽然雅虎确实提供了期权的隐含波动率，但我并不觉得它们特别好。也就是说，当我用隐含波动率为期权定价来计算δ，γ和θ时，我的价格与市场价格相差甚远。所以我选择的方法是取最后一个期权价格，自己计算隐含波动率。然后取隐含波动率，我会再次给期权定价(这应该会给我最后的价格)来得到希腊价值。对于期权定价，我使用 Python 绑定 [QuantLib](https://quantlib-python-docs.readthedocs.io/en/latest/) 。虽然他们的文档不是很好，但对我来说足够做我需要做的事情了。

```
# Standard library imports
import datetime
import re# Third-party library requirements
import pandas as pd
import QuantLib as ql
from yahoo_fin.options import get_calls
from yahoo_fin.stock_info import get_quote_table# Hard-coded ticker and expiration for example purposes
ticker = "AAPL"
expiration = datetime.date(2021, 2, 12)# Get the current stock price and dividend rate
info = get_quote_table(ticker)
current_price = info["Quote Price"]
yield_re = re.compile(r"\((?P<value>(\d+\.\d+))%\)")
try:
    dividend_yield = float(
        yield_re.search(info["Forward Dividend & Yield"])["value"]
    )
except (KeyError, ValueError, TypeError):
    dividend_yield = 0.0# Fetch call option chain prices
calls = get_calls(ticker, expiration.strftime("%B %d, %Y"))# Setup instruments for Black-Scholes pricing
today = ql.Date.todaysDate()
underlying = ql.SimpleQuote(current_price)
exercise = ql.AmericanExercise(
    today,
    ql.Date(expiration.day, expiration.month, expiration.year)
)
dividendYield = ql.FlatForward(
    today, dividend_yield, ql.Actual360()
)
riskFreeRate = ql.FlatForward(today, 0.0008913, ql.Actual360())def create_option(row):
    volatility = ql.BlackConstantVol(
        today,
        ql.UnitedStates(),
        row["volatility"],
        ql.Business252()
    )
    option = ql.VanillaOption(
        ql.PlainVanillaPayoff(ql.Option.Call, row["Strike"]),
        exercise
    )
    process = ql.BlackScholesMertonProcess(
        ql.QuoteHandle(underlying),
        ql.YieldTermStructureHandle(dividendYield),
        ql.YieldTermStructureHandle(riskFreeRate),
        ql.BlackVolTermStructureHandle(volatility),
    )
    # Don't use the quoted implied vol
    # Calculate it out from the last price
    imp_vol = option.impliedVolatility(row["Last Price"], process)
    implied_volatility = ql.BlackConstantVol(
        today,
        ql.UnitedStates(),
        imp_vol,
        ql.Business252()
    )
    process = ql.BlackScholesMertonProcess(
        ql.QuoteHandle(underlying),
        ql.YieldTermStructureHandle(dividendYield),
        ql.YieldTermStructureHandle(riskFreeRate),
        ql.BlackVolTermStructureHandle(implied_volatility),
    )
    option.setPricingEngine(
        ql.FdBlackScholesVanillaEngine(process, 1000, 1000)
    )
    return {
        "Name": row["Contract Name"],
        "Strike": row["Strike"],
        "Last": row["Last Price"],
        "Bid": row["Bid"],
        "Ask": row["Ask"],
        "NPV": option.NPV(),
        "Delta": option.delta(),
        "Gamma": option.gamma(),
        "Theta": option.theta() / 365,
        "Volatility": imp_vol * 100,
    }# Filter down to only OTM strikes
calls = calls[calls["Strike"] >= current_price * 1.025]
calls = calls[calls["Strike"] <= current_price * 1.10]
# Parse out implied volatility
calls = calls.assign(
    volatility=lambda x: x["Implied Volatility"].str.rstrip("%").astype("float") / 100,
)
# Price options and calculate greeks
options = calls.apply(create_option, axis=1, result_type="expand")
```

与 yahoo_fin 和 QuantLib 一起，它利用[熊猫](https://pandas.pydata.org/pandas-docs/stable/index.html)进行一些数据操作和过滤。这将获取给定股票代码和到期日的股票和期权的当前市场价格。它只过滤出 2.5%到 10%的价格(OTM)，并计算布莱克-斯科尔斯价格。

我需要的一个市场数据是无风险利率。因为我关注的是一周后的期权，所以我决定使用上面代码中显示的 [1 周 LIBOR 利率](https://www.global-rates.com/en/interest-rates/libor/american-dollar/usd-libor-interest-rate-1-week.aspx)。这不是自动抓取的，必须每周更新。

# 最小化风险和最大化利润

有了市场数据，现在又有了每个期权的希腊价值，我开始为每个期权对定价，试图找到一个最有价值的。同样，我将此限制为仅在链中彼此相邻的罢工，但这可以扩展到搜索更广泛的传播。

```
# This code is a continuation of the same file from above
# Pair up options with the next available option
pairs = pd.concat(
    [
        options.add_suffix("_1"),
        options.shift(-1).add_suffix("_2")
    ],
    axis=1
)
pairs = pairs[pairs["Name_2"].notna()]def maximize_theta(row):
    bid, ask = row["Bid_1"], row["Ask_2"] strike_1, strike_2 = row["Strike_1"], row["Strike_2"]
    delta_1, delta_2 = row["Delta_1"], row["Delta_2"]
    gamma_1, gamma_2 = row["Gamma_1"], row["Gamma_2"]
    theta_1, theta_2 = row["Theta_1"], row["Theta_2"] def calculate_values(sell): buy = round(gamma_1 * sell / gamma_2)
        credit = (bid * sell * 100) - (ask * buy * 100) - ((sell + buy) * 0.65)
        shares = -1 * round(delta_2 * buy * 100 - delta_1 * sell * 100)
        delta = delta_2 * buy * 100 - delta_1 * sell * 100 + shares
        gamma = gamma_2 * buy * 100 - gamma_1 * sell * 100
        theta = theta_2 * buy * 100 - theta_1 * sell * 100
        share_cost = shares * current_price
        margin = strike_2 * buy * 100 - strike_1 * sell * 100
        return {
            "Sell Contract": f"{row['Strike_1']} @ {bid}",
            "Sell Amount": sell,
            "Buy Contract": f"{row['Strike_2']} @ {ask}",
            "Buy Amount": buy,
            "Shares": shares,
            "Share Cost": share_cost,
            "Margin": margin,
            "Credit": credit,
            "Cost Ratio": credit / (share_cost + margin),
            "Net Delta": delta,
            "Net Gamma": gamma,
            "Net Theta": theta,
            "Risk Ratio": theta / (delta ** 2 + gamma ** 2) ** 0.5,
        } trades = []
    sell = 1
    values = calculate_values(sell)
    while (abs(values["Share Cost"]) + abs(values["Margin"])) < 2500:
        if values["Shares"] > 0 and values["Credit"] > 0:
            trades.append(values)
        sell += 1
        values = calculate_values(sell)

    if trades:
        results = pd.DataFrame.from_records(trades)
        results.sort_values(
            by=["Risk Ratio", "Cost Ratio"],
            ascending=False,
            inplace=True
        )
        return results.iloc[0]
    return Noneresults = pairs.apply(maximize_theta, axis=1, result_type="expand")
results = results[results["Shares"].notna()]
print(results)
```

这是暴力搜索。它不断增加我要卖出的合约数量，直到我们的总股票成本和利润超出上限。在这里，我将其设置为 2500 美元。这可能比实际情况更聪明，所以我可能会错过一些机会，但它现在是有效的，并且很容易理解它是如何工作的。

对于每一对，我会根据我得出的两个比率选择最高的交易。首先，我按风险比率排序。我把它定义为:

```
Risk Ratio = (Net Θ) / √(Net Δ^2 + Net Γ^2)
```

这在期权定价中没有任何意义，但它做了我想做的事。特别是，它奖励与接近零的δ和γ配对的高正θ交易，不管它们是正还是负。这是另一个值得尝试的领域，但是我喜欢在早期迭代中使用。

我关心的下一个比率是成本比率，它被定义为:

```
Cost Ratio = (Net Credit) / (Share Cost + Margin Required)
```

与持有交易所需的资金总额相比，这种奖励交易为我们提供了较高的预付溢价。把我们的钱投入到一个交易中意味着它不能投入到其他可能出现的机会中。如果我能在一个利差上获得 2%的净信贷，在另一个利差上获得 1.5%的净信贷，风险大致相等，那么我会选择 2%。我没有运行这个来扫描每一个可用的股票，但一些抽查和运行对一打左右，1-2%似乎是一个坚实的百分比。这是一个查看 2/12 AAPL 呼叫的输出示例。

![](img/4dfc652fc8e48c1c86ca92919a258994.png)

Best AAPL option spreads for the 2/12/2021 expiration

在这里，最好的差价是以 53 美元的价格卖出一个 141 看涨期权，以 40 美元的价格买入一个 142 看涨期权，11.70 美元的价格为 13 美元减去 1.30 美元的手续费。为了对冲头寸，需要购买 4 股。这个例子是在 2 月 7 日周日定价的，现在我们可以看到这个交易是如何进行的。如果你在 2 月 8 日周一以 136.03 美元买入，你将花费 544.12 美元，以 0.13 美元的差价卖出 141/142 的差价，扣除费用后你将净得 11.70 美元，但要求你保留 100 美元的保证金。2 月 12 日，AAPL 股票收于 135.37 美元，这使得这两种期权都到期了。如果你在收盘时卖出，那么你在股票头寸上总共损失了 2.64 美元，这一周的净利润为 9.06 美元，所需的 644.12 美元资本回报率为 1.4%。

# 一个集合在一起的策略

虽然没有完全自动化，但这对于继续测试这一策略非常有帮助。我们的想法是在每周五或周末使用这个脚本来寻找下周五到期的期权的价差机会。也就是说，每周一开始新的交易，周五平仓。如果某周没有好的机会，那么资本就会闲置。我不确定这将如何扩展。至少目前我搜索的是相当小的职位。虽然每周从 1000-2000 美元中获得 1-3%的回报似乎是可行的，但如果你希望投资$10K 或更高，是否能找到足够多的好机会来真正扩大这一回报就不太清楚了。这并不限制它作为一项实验的乐趣，但目前来看，赚钱的潜力似乎是有限的，因为如果你不能再投资，你就不能真正复合你的收益。

从最初的一系列要点来看，还没有解决的是股票的波动性和流动性。在测试这一策略时，这应该是下一个关注和研究的领域。在短期内，它可能会表现为一组用于每周扫描的股票。

我还没有放弃我的日常工作，我会继续在纸上测试这个，记下这个规定的交易和最终的结果。如果我能找到一个好的(免费的)历史期权定价来源，那么我可以做一些更大规模的回溯测试。我希望你觉得这是有帮助的和有趣的，如果你有关于如何改进这项工作的想法，请留下回应。交易愉快！