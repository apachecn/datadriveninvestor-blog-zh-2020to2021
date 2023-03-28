# 使用文章与 Python 和 Robinhood 进行简单交易

> 原文：<https://medium.datadriveninvestor.com/using-news-to-make-some-trades-with-python-and-robinhood-aa5da2aa4b36?source=collection_archive---------8----------------------->

![](img/6f0a75c32ea3ec16af8e4492b5289d14.png)

Photo by [CDC](https://unsplash.com/@cdc?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

冠状病毒，CEO 下台，还有特朗普。多篇文章中的主要关键词。让我们用它们来做一些交易。

## 我们需要什么

*   罗宾汉帐户
*   计算机编程语言
*   我们想捕捉新闻的股票

## 设置

1.  连接到 Robinhood。
2.  选择一只股票
3.  选择关键字
4.  根据关键字的存在，创建买卖股票的代码

## 编写代码

对于这个例子，我将使用微软，主要是因为它是一个高性能的股票，冠状病毒正在影响许多公司，尤其是技术。我将使用 Python 连接到 Robinhood，并使用 Robinhood 的新闻功能。

如果文章包含我设置的关键字，那么我希望我的代码可以买入或卖出股票。在我看来，如果我已经持有这只股票，我会想卖掉它。如果我不拥有它，我想买(买蘸，以防它回去了)。

[](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) [## 2019 年最值得学习的编码语言|数据驱动的投资者

### 在我读大学的那几年，我跳过了很多次夜游去学习 Java，希望有一天它能帮助我在…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) 

首先，我们需要一个 Robinhood 帐户和一种使用 Python 连接到它的方法。我已经写了一篇这样的文章，请随意浏览。我们将使用一个模块连接到罗宾汉。他们有不同的请求方法。Robinhood 最初是一款手机交易应用，但它慢慢建立起了自己的在线平台。`robin_stocks`通过发送请求和从它的在线端点获取数据来工作。如果你对 web 开发了解的多一点，也会更容易理解一点。

[](https://towardsdatascience.com/using-python-to-get-robinhood-data-2c95c6e4edc8) [## 使用 Python 获取罗宾汉数据

### 让我们自动化一些股票，可以用来建造一个交易机器人。

towardsdatascience.com](https://towardsdatascience.com/using-python-to-get-robinhood-data-2c95c6e4edc8) 

我们可以使用电子邮件和密码连接到 Robinhood。如果您启用了双因素身份验证，您应该会收到一条带有发送到您号码的代码的文本。连接后，我们可以创建一个想要在文章中查找的关键字列表。我将使用新闻文章的标题来节省我们的时间。我想到的关键词只是一个简单的单词列表，我认为这些单词会对股票产生负面影响。我将它们存储为字符串，然后放在一个列表中，这样我就可以遍历它们了。

```
word_list = ['coronavirus','virus','Trump','CEO']
```

既然我们已经设置了关键字，现在我们可以使用 Python 从 Robinhood 获取新闻文章。它有一个方法，我们可以通过给出符号来提取数据。如果我们不将变量 info 设置为任何值，这将返回多个值，包括 URL、描述、视图等等。我只想要文章的标题，所以我们设定了`info=’title’`。

```
data = r.stocks.get_news(symbol, info='title')
```

这将根据我们启动代码的时间返回不同数量的标题。我现在想搜索这些文章的标题。如果它们包含我设置的关键字，那么我希望它返回一个真值。如果文章确实包含关键字，我们现在可以向 Robinhood 发送一个命令，要求卖出股票。

```
for word in word_list:
    if any(word in s for s in data):
        result = True
```

根据你的策略，我们可以卖掉我们所有的微软股票，也可以只卖一部分。对于这个代码，我会卖掉我所有的股票。卖掉我所有的股票会给我带来最大的利润。此外，如果需要，我们可以随时回购。

为了做到这一点，我将撤出我所有的股票投资组合。然后，我将把数据放入数据帧中；这让我更容易看到数据的结构。由于 ticker 被设置为索引，因此我为 ticker 创建了自己的列。

我现在将创建只过滤微软信息的代码。因为数据帧基本上就像一个 excel 文件。我将只抓取包含有`MSFT`的股票代码的特定行。既然我们现在已经有了所有的信息，基本上就是把正确的变量代入等式，我将在下面演示。

```
df_new = df.loc[df['ticker'] == symbol]
r.orders.order(symbol, df_new['quantity'], orderType='market', trigger='immediate', side='sell', limitPrice=None, stopPrice=None, timeInForce='gtc', extendedHours=False)
```

一切都准备好了！如果我们希望重新运行代码，我们现在需要改变的唯一变量是股票代码和我们的关键字。这是一种非常简单的阅读文章和购买的方式。我们甚至可以应用一些自然语言处理，进一步让代码区分什么是好的，什么是坏的。

链接到完整的代码[这里](https://www.patreon.com/posts/34368531)。

我在这里也有家教和职业指导[！](https://square.site/book/8M6SR06V2RQRB/mentor-melv)

如果你们有任何问题、评论或担忧，请不要忘记通过 LinkedIn 与我联系！