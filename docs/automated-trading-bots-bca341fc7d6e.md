# 自动化交易机器人

> 原文：<https://medium.datadriveninvestor.com/automated-trading-bots-bca341fc7d6e?source=collection_archive---------0----------------------->

难以置信的开源软件交易

![](img/8ef87756ad73f758772de411b5795b9f.png)

Photo by [Austin Distel](https://unsplash.com/@austindistel?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/trading?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

过去几年我一直在交易加密货币，作为一名计算机科学家，我一直对自动化交易机器人感兴趣。我看过一些关于这个话题的[故事](https://towardsdatascience.com/how-to-create-a-fully-automated-ai-based-trading-system-with-python-708503c1a907?source=bookmarks---------0----------------------------)和[视频](https://www.youtube.com/watch?v=-MHhA-Y3DSk)。所以我决定试试这个技术。但是首先，给你一点建议，**我不是投资专家**所以要注意交易的风险。不要用你不愿意输的钱去赌博。做完这个小小的介绍后，让我们看看如何从自动化交易开始。

# 不要重新发明轮子

每当我在考虑一个新的软件项目时，我都会查看 Github。有成千上万令人难以置信的开源项目。即使我可能正在尝试学习或编写一些新的东西，看看其他代码和项目总是一个很好的想法来源。

现在，如果我们在 GitHub 中查找加密交易机器人，我们将获得 695 个存储库。

![](img/f44d31f3501def520f4f708c8115861b.png)

crypto trading bot on GitHub

前三个项目似乎非常有趣，但我会选择 freqtrade 来测试汽车交易。我选择 freqtrade 不仅仅是因为星级数量，我喜欢以下几个关键因素:

1.  它是用 Python 开发的，并且正在积极开发中。我个人更喜欢 Python 来编写这样的脚本项目。
2.  可以通过电报机器人轻松控制。
3.  支持像币安和 Bittrex 这样的流行交易所。
4.  支持策略定制。你可以创造自己的策略。

因此，如果你考虑到这一点，你可以创建自己的学习机器人。但是机器人的关键因素是你将要遵循的策略。我更喜欢花一些时间测试和开发策略。

# 安装 freqtrade

运行 freqtrade 最简单的方法是通过 docker-compose。当然，你需要安装 docker，但是使用官方文档 [docker](https://docs.docker.com/engine/install/) 和 [docker-compose](https://docs.docker.com/compose/install/) 很容易完成。

```
mkdir ft_userdata
cd ft_userdata/# Download the docker-compose file [https://raw.githubusercontent.com/freqtrade/freqtrade/stable/docker-compose.yml](https://raw.githubusercontent.com/freqtrade/freqtrade/stable/docker-compose.yml) -o docker-compose.yml# Pull the freqtrade image
docker-compose pull# Create user directory structure
docker-compose run --rm freqtrade create-userdir --userdir user_data
```

也有可能传统上使用 bash 脚本安装 feqtrade，或者手动安装项目的必要依赖项。

```
sudo apt intall python3.7
sudo apt intall python3.7-dev
sudo apt install python3-pip
sudo apt install python3-venvgit clone https://github.com/freqtrade/freqtrade.git  
cd freqtrade  
git checkout stable
./setup.sh -i
```

这个设置将安装我们需要的一切，并将创建一个 Python 虚拟环境。

```
source ./.env/bin/activate
```

## 在哪里运行 freqtrade？

理论上，如果一切运行正常，您不会停止 freqtrade。因此，运行交易机器人的最佳选择是虚拟专用服务器(VPS)，以便全天候运行。我自己选择的 [VPS 是数字海洋](https://m.do.co/c/01825577c607)，巨大的支持和价格，但你可以选择任何云提供商。

另一件要考虑的事情是将 freqtrade 运行到 Linux 系统中。如果您想将 freqtrade 安装到 windows 中，推荐的方法是使用 Windows Subsystem for Linux (WSL)。

# 配置频率

为了运行 freqtrade，您需要设置一些配置。这可以使用`new-config`命令轻松完成。

```
# If you are using docker-compose
docker-compose run --rm freqtrade new-config --config user_data/config.json# If you are using a traditional installation
freqtrade new-config --config user_data/config.json
```

`new-config`是一个交互式命令，它将帮助我们回答一些问题来完成配置。

![](img/a2f2bc7b38f071ac472d8f0cfa52253c.png)

在这里，我启用了预演(模拟)，使用 BTC 购买其他加密货币，金额为 0.01 BTC，最多 3 笔未平仓交易。用于决策的时间框架将为 500 万英镑，报告法定货币将为美元。最后，我将操作的交易所将是[币安](https://accounts.binance.com/en/register?ref=19719887)。

## 启用电报机器人

如前所述，freqtrade 的一个很酷很有用的功能是使用电报机器人。这个机器人将允许我们控制交易，获得警报并检查交易的状态。使用`new-config`选择交易后，我们将被要求输入电报令牌和聊天 id。

![](img/cdadb7bab4b959f9c6cc8878adc8e8e5.png)![](img/907ffa5311e8b9851aefa87f88364bf0.png)

与电报内的[父亲](https://t.me/botfather)对话并输入`/newbot`即可获得电报令牌。我们需要命名它，然后将提供一个令牌。

![](img/d8eb5b64f5a8a20a8b40404254850c60.png)

除了这个令牌，我们还需要提供一个聊天 id。此聊天 id 是我们在 Telegram 中的帐户 id。与 userinfobot 对话会给我们 id。

![](img/495d93b2cc530af1c5015c20b85c9096.png)

完成这个过程后，将在 user_data 下生成一个 config.json。

## 配置. json

有了这个配置，我们就可以开始在安全模式下玩机器人了。所有这些都是模拟的。但是如果我们想开始赌博，我们需要改变 config.json 中的一些东西。

![](img/bf960aa29a5555ccbe79007cec5cc3a0.png)

首先，我们需要禁用 dry_run 模式，然后添加必要的 API 键。需要在您的 exchange 帐户中创建这些 API 密钥。但是请注意**这些 API 密匙将拥有交易权限**。

![](img/e81e3bd134b93706fa231532e1c008ea.png)

您的 VPS 和 config.json 必须得到适当的保护。这些 API 密钥是非常敏感的数据。你的 VPS 服务器应该被适当地加固，也许在将来，我会写一个关于这个的指南。

# 外贸战略

交易机器人之间的主要核心和差异是使用的策略。freqtrade 策略需要放在/user_data/strategies 下，可以为 freqtrade bot 创建自己的策略。

如果你不了解市场策略，在 [GitHub](https://github.com/freqtrade/freqtrade-strategies) 上有一些开源策略。我们可以下载这些策略并将其移动到我们的/user_data/strategies 文件夹中。

```
git clone [https://github.com/freqtrade/freqtrade-strategies](https://github.com/freqtrade/freqtrade-strategies)
mv freqtrade-strategies/user_data/strategies/berlinguyinca/* /user_data/strategies/
```

这里有一些非常有趣的策略，基于布林线，MACD，RSI 和其他交易指标。但问题是，他们中的哪一个会产生利润？

# 回溯测试

市场未来将如何运作还很不确定，但我们可以用历史数据来检验这些策略。

我们需要做的第一件事是下载历史数据:

```
# Data download for "1m" and "5m" timeframes
freqtrade download-data# Data download for "1h" timeframe
freqtrade download-data -t 1h
```

之后，我们可以根据这些数据测试我们的策略:

```
freqtrade backtesting  --strategy-list ADXMomentum ClucMay72018 MACDStrategy_crossed Simple AdxSmas CMCWinner MACDStrategy ASDTSRockwellTrading CofiBitStrategy SmoothScalp AverageStrategy CombinedBinHAndCluc DoesNothingStrategy Quickie BbandRsi EMASkipPump ReinforcedQuickie  --ticker-interval=5m
```

这个回溯测试将生成几个指标。检查总利润百分比，我们可以看到一些策略是如何亏损的，比如 ASDTSRockwellTrading。但其他像 EMASkipPump 或 ReinforcedQuickie 似乎很有前途。同样**我们无法百分之百确定市场未来将如何运作**。但是，如果市场运行与我们的数据相似，我们将通过这些策略获得收益。

![](img/ca53161bfc30dd020e691ade9d1ac5a0.png)

Backtesting with 5m ticker interval

# 运行机器人

最后要做的事情是用选择的策略运行我们的机器人。

```
# Create user directory structure
freqtrade trade --strategy BbandRsi
```

![](img/fc8cb520c3ec21a4b025647300eced16.png)

另外，请记住，如果您使用 docker-compose，您将需要使用`docker-compose run --rm`来指定命令

```
# Create user directory structure
docker-compose run --rm freqtrade trade --strategy BbandRsi
```

# 控制交易机器人

如前所述，控制交易机器人最简单的方法是通过电报。启动 freqtrade 后，我们可以使用我们的 TelegramBot 开始获取信息。

![](img/dcb3ba22b4f088882e6febd02e631611.png)

每次机器人购买或出售加密货币时，我们都会收到警告:

![](img/3e37bd66a80e98be688f03262491952b.png)

而且你还可以通过电报控制停止或者检查交易机器人的状态。

![](img/c03958e0ff964c77579a069943b9ce25.png)

# 结论

作为一名计算机科学家，我可以创建自己的交易机器人，但我并不喜欢重复发明轮子。在我看来，交易机器人的附加值就是实施的策略。我个人正在用 freqtrade 作为投资来测试一些交易策略。请不要用你不会输的钱去赌博。

非常感谢你阅读我，希望你喜欢这篇文章；).如果你有什么惊人的策略，请告诉我！！