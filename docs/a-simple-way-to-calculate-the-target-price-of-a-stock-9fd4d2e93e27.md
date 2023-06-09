# 计算股票目标价的简单方法

> 原文：<https://medium.datadriveninvestor.com/a-simple-way-to-calculate-the-target-price-of-a-stock-9fd4d2e93e27?source=collection_archive---------0----------------------->

## 对股票的未来价格做出更清晰的预测

![](img/782dea9282f3bfb23d82b6c9fa663510.png)

Photo by [Silvan Arnet](https://unsplash.com/@silvanarnet?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

目标价是对股票未来价格的估计。你可能已经看到各种分析师给出了苹果公司、T2 公司、微软公司和 T4 亚马逊公司的目标价。分析师将使用许多不同的模型来产生目标价格，其中[贴现现金流](https://www.investopedia.com/terms/d/dcf.asp)是更受欢迎的模型之一。问题是贴现现金流会变得有点复杂。找到一个目标价格并不复杂，这就是为什么我会向你展示一个简单的方法来找到一只股票的目标价格。

当谈到产生一个目标价格时，你应该首先做你的基本面分析和技术分析。一旦你了解了一只股票的经营方式和它的价格趋势，你就可以设定一个目标价格。

重要的是要知道，计算目标价并不是股票价格走向的最终解决方案。它有局限性，但在生成目标价的过程中，它为你长期持有的股票增加了更多深度。计算目标价的简单方法是市盈率法。

*注意:我仅出于教育目的分享此信息。记住，在投资之前，一定要做好调查和尽职调查。*

[](https://www.datadriveninvestor.com/2020/07/07/introduction-to-time-series-forecasting-of-stock-prices-with-python/) [## 用 Python |数据驱动投资者进行股票价格时间序列预测简介

### 在这个简单的教程中，我们将看看如何将时间序列模型应用于股票价格。更具体地说，一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/07/07/introduction-to-time-series-forecasting-of-stock-prices-with-python/) 

市盈率是衡量公司股价相对于净收入的指标。市盈率的计算公式是公司在特定时间点的股价除以特定时期的每股收益(EPS)。每股收益是公司一定时期内的净利润除以发行在外的普通股数量。那么，如何才能用 PE 来计算目标价呢？最好举个例子来解释一下。

让我们以脸书为例。在雅虎财经上，导航到它的[财务](https://finance.yahoo.com/quote/FB/financials?p=FB)页面，确保你看到的是它的年度损益表。向下滚动找到其 2016 年至 2019 年的基本 EPS。由于这些值是以千为单位的，所以每个值都乘以 1000，得到每股的美元值。我们发现脸书 2016 年的每股收益为 3.60 美元，2017 年为 5.50 美元，2018 年为 7.70 美元，2019 年为 6.50 美元。为了得到逐年的每股收益增长率，我们将使用以下公式:( *EPS2 — EPS1) / EPS1* 。2016 年至 2017 年的每股收益增长率为:($5.50 — $3.60) / $3.60 = 0.528 或 52.8%。2017 年到 2018 年，是 0.4 或者 40%。2018 年至 2019 年为-0.156 或-15.6%。

现在我们有了每股收益增长率，我们可以找到平均值，即 0.257 或 25.7%。现在，让我们假设 2020 年、2021 年和 2022 年的每股收益每年增长 25.7%，来计算 2020 年、2021 年和 2022 年的每股收益。公式为*EPS *(1+平均 EPS 增长率)*其中 *EPS* 为上一年的 EPS。例如，2020 年我们会做:6.60 美元*(1+0.257)= 8.17 美元。2021 年是 10.27 美元，2022 年是 12.91 美元。

在雅虎财经上，导航到脸书的[统计](https://finance.yahoo.com/quote/FB/key-statistics?p=FB)页面。在这里，寻找截至 2019 年 12 月 31 日的尾随 PE。一共是 32.89。计算目标价的公式是:(*价格/预计 EPS) =尾随 PE* 其中*价格*是我们求解的变量。例如，脸书 2020 年的目标价是:*价格*/【8.17】美元= 32.89 其中*价格*等于 268.71 美元。脸书 2019 年底为 205.25 美元，2020 年 10 月 9 日收盘时为 264.45 美元。这对于 2020 年的目标价格来说还算不错。2021 年目标价 337.78 美元，2022 年目标价 424.61 美元。

如果你希望目标价更保守，你可以将它们乘以 0.9。那有什么用？它认为这是一次市场调整。市场调整被定义为主要指数下跌 10%或更多的时期，如标准普尔 500 指数。因此，将目标价乘以 0.9，脸书 2020 年的目标价是 241.84 美元。2021 年是 304 美元，2022 年是 382.15 美元。

PE 方法往往更适合成长型股票，因为随着公司盈利能力的提高，每股收益预计会随着时间的推移而增长。PE 方法的一个局限性是，由于一次性费用导致当年的 EPS 较低，特定年份的历史 EPS 值可能会有偏差。另一个限制是，它不能提供一个公司的完整视图，因为它只对股权投资者有用。它没有考虑公司的债务持有人。

在了解确定股票目标价的关键方法的基础上，你正在进一步为自己的长期财务成功做准备。在对一家公司做了基本面和技术面的分析后，得出一个目标价有助于更清晰地描绘出预期的回报。如前所述，求解目标价格并不是一个确定的解决方案。没有人能预测一只股票未来的确切价格，但你可以采取必要的措施来确认一家公司的前景是否乐观。

[查看 Tunji 信，保持联系](https://tunji.substack.com/)。

## 获得专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)