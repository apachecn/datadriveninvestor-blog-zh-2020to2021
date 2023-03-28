# COVID 期间的市场

> 原文：<https://medium.datadriveninvestor.com/the-market-during-covid-ad9ace2f8f9b?source=collection_archive---------8----------------------->

> 注意:回购中提供了所有代码:
> 
> [https://github.com/sankhaMukherjee/theMarketDuringCOVID](https://github.com/sankhaMukherjee/theMarketDuringCOVID)

在[早先的一篇文章](https://medium.com/@sankha.mukherjee_007/a-phd-in-a-stem-file-left-me-financially-underprepared-84b9589a765e)中，我们讨论了根据标准普尔 500 指数的比例，个人财富应该投资多少。PE 值越高，我们就越不应该投资市场，因为在某个时候，市场会自我修正。市盈率的一套简单规则可以概括为:

1.  小数值→😍
2.  大值→😨

在谷歌上搜索这一数量，会显示如下图所示的网站表单 [multpl](https://www.multpl.com/s-p-500-pe-ratio) :

![](img/f3f08a4914710a3406aa37cd7356746c.png)

(Chart available at: [https://www.multpl.com/s-p-500-pe-ratio](https://www.multpl.com/s-p-500-pe-ratio))

如果你深入挖掘，你会发现上一次被低估的市盈率是在 2020 年 1 月 1 日。COVID 开始于同年 2 月。当然，在这一点上必须有一个更好的市盈率估计？

![](img/81dd3ac05d27f25a492cbb0c1d36bae0.png)

(Table available at: [https://www.multpl.com/s-p-500-pe-ratio](https://www.multpl.com/s-p-500-pe-ratio))

你能相信这个值吗？今天的体育配给比一月份的体育配给高 4 分，这是真的吗？请记住，与 8 月份相比，SNP&500 指数在 1 月份的交易价格几乎相同。然而，在 1 月份，这些公司实际上正在盈利，而在 8 月份，许多公司都在亏损。

当然，在这段时间里，我们需要做得比预计的更好。在本文中，我们将解决这个问题。

# 1.疫情期间的市盈率特征

在这段时间里，许多企业都在挣扎，许多企业都在亏损。此外，任何股票的股价都不可能是负数(当然，除非我们讨论的是石油价格)。当一家公司开始亏损时，市盈率会是怎样的？

假设公司的股票价格( *p* )保持不变(=1)。并且每股收益( *e* )随时间变化。有时收益为正，而在其他时候(例如在 COVID 疫情期间)收益为负。

![](img/05b3dbd46e28d008f693f93cb441959c.png)

同样的股价，公司盈利高的时候，市盈率就低。然而，随着价格下降，并接近 0，达到一个拐点，其中 P/E 比率向∞显著增加，然后当公司开始第一次亏损时，P/E 比率向-∞显著下降，然后当公司亏损严重时，P/E 比率开始向较小的负值下降。

现在，在这个非常时期，我们需要增加一些简单的规则。

1.  小+ve 值→😍
2.  大+ve 值→😨
3.  大 ve 值→😱
4.  小 ve 值→💥

现在，让我们来计算一家公司的市盈率。

# 2.下载所需的数据

首先，需要获得股票价格和每股收益(EPS)的值。很多地方都允许你下载数据，我们主要感兴趣的是从 [MarketWatch](https://www.marketwatch.com/) 下载金融数据，从 [Yahoo！财务](https://sg.finance.yahoo.com/)。你还需要一份标准普尔 500 指数成份股公司的名单。这个列表可以在维基百科[上找到。](https://en.wikipedia.org/wiki/List_of_S%26P_500_companies)

您不需要编写从这两个地方下载数据的代码。我已经在这里给你写好代码[。欢迎你使用。需要注意的是，大部分基本面数据每个季度才更新一次。每次运行程序时下载它是没有意义的。请尽可能缓存信息。理想情况下，您会希望建立一个数据库来缓存所有可用的数据。对于这个简单的例子，我们将只在 JSON 文件中缓存数据。这里，我有意保持代码简单。](https://github.com/sankhaMukherjee/financeMacroFactors)

要下载并保存标准普尔 500 列表中的公司，只需执行以下操作:

![](img/11741b05f60dbc007abd76c54b7e5973.png)

同样，你可以下载基本面和股票数据并缓存。查看**附录 A** & **B** 中的一些基本示例代码。我们假设股票数据缓存在文件夹`stockData`的 JSON 文件中，基本面数据在`fundData`中。标准普尔 500 指数成份股公司的名单可以在 T2 找到。让我们看看一个示例公司——微软的每股收益数据和股票数据是什么样的:

微软的股票价格看起来像:

![](img/eba969de2ba3386fbfea48a37218cd59.png)

微软的 EPS 看起来如下:

![](img/f11fc5132bc27f438378b33a02257f94.png)

这里我们假设季度每股收益( *e_Q* )大约是年度每股收益( *e_Y* )的四分之一，因此，为了将它们绘制在同一张图上，季度收益被乘以 4。这并不完全准确，因为这个数量有季节性波动。如果我们有更多的数据(例如来自 Quandl 的付费数据)，我们本可以做得更好。

## 2.1.插值每股收益

请注意，每季度每股收益每 3 个月才公布一次。此外，每个公司在不同的月份报告他们的季度业绩。例如:

![](img/ae4aba4365118d3aabff53912c91d07e.png)

在这种情况下，对每个月的每股收益进行插值(如果需要，还可以进行外推)是非常有用的。下面是一个例子，其中( *e* )是季度和年度平均每股收益，( *e_{Int}* )是每股收益值，也是微软的。最基本的代码如**附录 C** 所示。

![](img/39d6868dd26fef644793ca46ee3ca3e7.png)

当然，随着总库存的减少，同样的事情也会发生。微软稀释后的流通股看起来是这样的。这些数字以十亿计。

![](img/0abd3a5c664fc880250e6891f396b79a.png)

请注意微软在过去几个月里进行的股票回购，这提高了它的每股收益。在此期间，大约有一亿股股票被回购。

# 3.计算公司的市盈率

一旦我们有了插值后的每股收益( *e_{Int}* )和相应的月平均股价( *p* )，你就可以很容易地一个接一个地得到一家公司的市盈率。**附录 D** 中显示的简单函数`getPEandVolume()`将允许您获得每月的 PE 值(以及相应的量)。利用这一点，人们可以一次画出几家公司的市盈率。

让我们来看看一些科技公司:

![](img/1366e873a21ec379bbd7aedb0e097c95.png)

我们观察到了什么？市盈率偏高，但不是天文数字。几乎所有的公司都没有受到市场的严重影响。它们的价格持续上涨，甚至在疫情期间也是如此，在疫情期间略有下降。总的来说，从投资的角度来看，随着时间的推移，市盈率并没有明显的变化。

现在航空公司的情况如何？

![](img/2fa65882e50b7330da11c4149529039b.png)

我们看到了完全不同的画面！我们不仅看到了拐点，还看到了整个行业的收益减少。我们从😍到😨到😱到💥。

# 4.那么市场是什么样的呢？

市场只是所有公司的加权总和。市场的市盈率只是所有公司市盈率的加权和。执行此操作的基本代码如**附录 E** 所示。首先，让我们看看标准普尔 500 指数中所有公司的市盈率:

![](img/723cd2b546d7b60b9d39103f741f0fd0.png)

如你所见，所有行业的综合效应都在推高市盈率。观察不同行业的市盈率是很有趣的。SNP 500 被分成多个不同的 GIS 扇区。绘制不同地理信息系统部门的市盈率，我们立即看到不同部门的问题:

![](img/dba02ae846b8549a005caca361a381aa.png)![](img/cb240d6b9ce8fbbffaf23ff1a37b85bc.png)![](img/f352e3a7063e238c6cb7762e324e5da8.png)![](img/e96e0526aa887d5fc9bf0705acea435b.png)![](img/59cac062e5e64d690cddc396199ab54a.png)![](img/b5f4c2fc325818c18be36a2dd36d2fec.png)![](img/30a55240c76cb95e4b69fb869c11877c.png)![](img/cd2145610327dc1a9e4272764352a213.png)![](img/4ca40540824b10274ff1fc0fa62c39bc.png)![](img/aeccc4c885abfcb33d1277a99edcdfb6.png)![](img/99369e7db4d276ac63e2cf759aaf03aa.png)![](img/fb501f644be7506b04bf3b941e5e4c18.png)

我将让你们思考和评论每个部门的情况。从根本上说，你可以写一本大部头的书来描述每个行业的状况，这可能是另一个话题的讨论。然而，如果你正在考虑使用本文开头所示的图表来为你的投资决策提供信息，我建议你三思。

# 5.结论

在像现在这样动荡的时期，根据 10 年的平均水平来判断市场状况可能是不谨慎的。我们正处于黑天鹅事件中。我们已经研究了在更精细的层面上计算市场市盈率的方法。

我将创建一个 Github 库，我将把所有用于上述计算的代码放在里面，并在这里更新链接。

# 附录

此处显示了代码示例。

## 附录 A

保存 SNP500 公司基本数据的基本代码

![](img/4e137d63d5944cea10de189d40b8e35b.png)

## 附录 B

保存 SNP 500 公司月度平均股票数据的基本代码。有时雅虎可能会限制下载带宽，在这种情况下，对那些下载数据不足的公司重复这个过程。你也可以考虑装一个睡眠计时器来缓解这个问题。

![](img/0c585e8fc36060d83a2c459ebf053945.png)

## 附录 C

计算一家公司的内插每股收益和内插流通股。

![](img/a048d77d3d8c51239fbf07db34107ebc.png)

## 附录 D

计算一个公司的市盈率和成交量

![](img/a65b6b6d6d6cb736d2cd1efa61918e95.png)

## 附录 E

一次画出几家公司的市盈率

![](img/22ec214fff1aa0b7ee4e2eff96890b56.png)

# 参考

1.  早期的一篇文章描述了基于市场条件的投资比例。[ [链接](https://medium.com/@sankha.mukherjee_007/a-phd-in-a-stem-file-left-me-financially-underprepared-84b9589a765e)
2.  S&P 市盈率。【[链接](https://www.multpl.com/s-p-500-pe-ratio)
3.  下载财务信息的市场观察[ [链接](https://www.marketwatch.com/) ]。
4.  雅虎！金融下载股票行情[ [链接](https://sg.finance.yahoo.com/) ]。
5.  从互联网上获取公司财务信息的 GitHub 存储库:*github.com/sankhaMukherjee/financeMacroFactors*。[ [链接](https://github.com/sankhaMukherjee/financeMacroFactors)
6.  本文中所有代码的 GitHub 库:*github.com/sankhaMukherjee/theMarketDuringCOVID*[[链接](https://github.com/sankhaMukherjee/theMarketDuringCOVID)