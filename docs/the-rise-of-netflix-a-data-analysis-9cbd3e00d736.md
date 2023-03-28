# 网飞的崛起:数据分析

> 原文：<https://medium.datadriveninvestor.com/the-rise-of-netflix-a-data-analysis-9cbd3e00d736?source=collection_archive---------1----------------------->

![](img/97fea2d0224719f69ab543c036919e31.png)

网飞始于 1997 年，当时是一家通过邮件出租 DVD 的服务公司，采用的是先租后付的模式。用户(我也是其中之一)会在他们的网站上浏览和订购他们想要的电影，下订单，网飞会把它们送到你的门口。租借者看完 DVD 后，他们会简单地把它们寄回去。2020 年 7 月 10 日，网飞成为市值最大的娱乐公司。该公司已经从一家 DVD 邮购公司成长为原创内容之王。随着新冠肺炎对电影院运营的影响，以及越来越多的人不得不呆在室内，网飞可能很快就会成为可行的替代选择。该数据集由截至 2019 年网飞上可用的电视节目和电影组成。

这是用 Python 进行[数据分析的顶点项目:从零到熊猫](https://jovian.ml/outlink?url=zerotopandas.com)，由[jovian.ml]和[freecodecamp.org]举办的为期八周的课程，涵盖以下主题:Python 基础知识、用 Numpy 进行数值计算、Numpy 数组操作、用 Pandas 分析表格数据、用 Matplotlib 和 Seaborn 进行数据可视化。

带源代码的 Python 工作簿链接在这里:【https://jovian.ml/kelroydbjames/netflix-worldwide-analysis 

数据从卡格尔图书馆 h[ttps://www . ka ggle . com/Shiva MB/网飞-shows](https://jovian.ml/outlink?url=https%3A%2F%2Fwww.kaggle.com%2Fshivamb%2Fnetflix-shows) 下载。Kaggle 是数据科学家用来合作或参与数据挑战的数据集的关键存储库。数据集收集自第三方网飞搜索引擎 Flixable。2018 年，他们发布了一份有趣的报告，显示网飞的电视节目数量自 2010 年以来增长了近两倍。自 2010 年以来，流媒体服务的电影数量减少了 2000 多部，而电视节目数量增加了近两倍。探索从相同的数据集中可以获得什么样的其他见解将是有趣的。

首先，网飞的节目类型有很大的不同。

可以看出，网飞的电影数量以 2:1 的比例超过了电视节目。这可能是因为网飞并不生产自己的大部分内容，而是依赖于竞争对手的产品，而这些竞争对手都在开发自己的流媒体平台。

网飞的平台上有各种不同类型的电影和电视节目。我们将看看哪些流派最受欢迎。

数据显示，纪录片是迄今为止最大的电影类别。这可能是因为纪录片可能从电影制片厂收取较低的许可费，并且将是更便宜的内容来源，

我们现在将通过一个条形图来看看哪些类型的电视节目在网飞占据了最大的份额。

儿童电视节目的大量出现也可能是因为这种类型的内容比电视喜剧更便宜，后者是最低的。大多数电视喜剧都是由主要的网络和电影工作室制作的，他们会要求额外的许可，或者目前将它们保留在自己的平台上。

我们现在来看看过去十年的发布频率。

如图所示，2018 年是该年发布节目数量最多的高水位线。从 2019 年开始的急剧下降可能是因为竞争对手开始推出自己的流媒体服务。例如，漫威的四部剧集都没有和网飞继续合作，版权回到了漫威/迪斯尼手中。

按收视率划分的节目类型

收视率为 80%的节目明显占大多数.其次是 TV-14。

区分电影和电视节目的收视率显示，两个类别的比例相当于 2:1。

通过 seaborn，我们将了解数据的其他一些有趣方面，例如:

1.  演出的发行
2.  内容最多的国家
3.  演出时长

Q1:在过去的十年里，发布的频率是多少

从 2011 年到 2018 年，内容有了大幅增加，其中电影占了大多数。网飞现在也开始制作他们自己的原创电影，其中一些也在奥斯卡金像奖上挑战主要工作室的荣誉。

Q2:哪些国家生产的内容最多？

我们可以使用 value_counts 方法确定内容创建量最高的国家。

网飞上创建的内容大部分来自美国，有近 1600 个标题。印度是第二大，也许是由于宝莱坞制作的流行。

问题 3:国家制作的内容类型是什么？

要回答这个问题，我们需要使用 groupby 数据框方法来聚合每个国家的行。然后将使用 seaborn 应用柱状图。

美国制作的电影构成了该国的大部分内容。应该指出的是，由于宝莱坞市场的受欢迎程度和规模，印度电影也是一个主要组成部分。

Q4:内容的整体类型构成。

总体而言，纪录片和单口喜剧节目构成了网飞的大部分内容。

问题 5:电视节目和电影的时长是多少？

大多数电视节目只有一季。这可能是由于多种因素造成的，如许可证费用、缺乏知名度和生产成本。

# 推论和结论

从最初的邮购目录，到现在世界上最大的流媒体提供商，网飞的发展是惊人的。它现在正与大多数原创内容提供商竞争，这些提供商现在都在创建自己的流媒体服务。

随着美国国内的节目和电影转移到其他平台，它对这些节目和电影的依赖可能会减少。虽然他们现在已经开始创作自己的内容，但大多数节目仍然是纪录片、喜剧或单季电视节目。

随着 2011 年至 2018 年的增长，由于竞争以及新冠肺炎导致的停产，新内容出现了放缓。虽然这导致内容减少，但网飞的订阅数量随着股票价值上升，因为人们必须在全球范围内接受隔离。

# 未来的工作

此数据的未来分析可包括:

1.  分析不同国家的可用内容。
2.  使用网络分析识别基于导演、演员和女演员的洞察力。
3.  电视节目和电影的流行洞察分析。

# 参考

https://interesting engineering . com/网飞的迷人历史

[](https://knowtechie.com/coronavirus-pandemic-leads-to-massive-spike-in-new-netflix-subscribers/) [## 疫情冠状病毒导致新网飞用户激增

### 网飞昨日发布了第一季度收益报告，

https://know techie . com/coronavirus-疫情-导致新网飞订户大规模激增/里面有一些关于 earnings…knowtechie.com 的无聊内容](https://knowtechie.com/coronavirus-pandemic-leads-to-massive-spike-in-new-netflix-subscribers/) 

熊猫用户指南:【https://pandas.pydata.org/docs/user_guide/index.html】T2Matplotlib 用户指南:【https://matplotlib.org/3.3.1/users/index.html】T4Seaborn 用户指南&教程:[https://seaborn.pydata.org/tutorial.html](https://jovian.ml/outlink?url=https%3A%2F%2Fseaborn.pydata.org%2Ftutorial.html)开放数据集 Python 库:[https://github.com/JovianML/opendatasets](https://jovian.ml/outlink?url=https%3A%2F%2Fgithub.com%2FJovianML%2Fopendatasets)

[www.jovian.com](http://www.jovian.com)

点击此处订阅 DIntel [。](https://ddintel.datadriveninvestor.com/)

请访问我们的网站:[https://www.datadriveninvestor.com](https://www.datadriveninvestor.com/)

在这里加入我们的网络:[https://datadriveninvestor.com/collaborate](https://datadriveninvestor.com/collaborate)