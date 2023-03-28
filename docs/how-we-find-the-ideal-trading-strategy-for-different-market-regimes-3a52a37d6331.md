# 我们如何为不同的市场体系找到理想的交易策略

> 原文：<https://medium.datadriveninvestor.com/how-we-find-the-ideal-trading-strategy-for-different-market-regimes-3a52a37d6331?source=collection_archive---------2----------------------->

知道如何在不同的市场体制下交易，和交易什么一样重要，如果不是更重要的话。那么什么是市场机制呢？

市场机制是一种组织不同交易环境特征的量化方法。我们有五个:

*   公牛易挥发
*   公牛安静
*   中立的
*   保持安静
*   忍受不稳定

每一种机制都是对标的资产运行方向的衡量，看涨、看跌或中性。

并进一步按易变或静来组织。

这是用一种叫做系统质量指数(SQN)的工具来衡量的。你可以在这里观看视频。SQN 测量前 100 天收盘时的平均百分比变化，然后用平方根计算。这就是我们如何量化看涨或看跌，如果在过去的 100 个交易日中变化平均为正，那就是看涨，如果为负，同样也是看跌。然后，随着百分比变化的增加，它变得更加不稳定，并减少不太稳定。一个很好的量化方法来衡量。

这种方法是跟踪的，所以 SQN 是一个跟踪指标，这一点很重要。SQN 不是一个圣杯超级分类高度脆弱的高胜率指标，它会告诉你什么时候买入下一个 24%的上涨或做空市场崩溃。

相反，它更像一个日历。如果你知道现在是一月，而你在蒙大拿，你很可能需要一件厚外套、靴子、帽子、手套，而且你几乎可以保证你不需要背心和人字拖。

[](https://www.datadriveninvestor.com/2020/03/12/three-simple-questions-and-one-difficult-one-to-ask-before-investing-in-a-blockchain/) [## 投资区块链前要问的三个简单问题(也是一个困难的问题)|数据…

### 现在是了解区块链的最佳时机。不同货币之间的增长率，比如…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/03/12/three-simple-questions-and-one-difficult-one-to-ask-before-investing-in-a-blockchain/) 

SQN 是相似的，因为现在我们可以定量地识别我们所处的“季节”。就像日历显示现在是冬天，而你知道你在蒙大拿州，SQN 说我们正处于熊市动荡时期，所以让我们准备好合适的工具(在这个类比中是服装)。

让我们开始本周的行动吧。

![](img/c96fdf3c03a65b111f2d5138e591a152.png)

SQN Indicator on daily S&P500 Chart

看看 2020 年 4 月 6 日的标准普尔 500 指数，本周的市场走势是熊市波动和熊市平静之间的过渡特征。当我们从地狱的深渊回到现在的位置时，乐观情绪开始出现，这就变得棘手了。

空头很紧张，正在补仓或等待补仓，上个月被刺中喉咙并在第一次反弹时卖出的多头开始怀疑他们是否做对了，开始买入。这是推动熊市反弹的原因，也是所有反弹中最猛烈的一次。

正如你所知，我们不是在这里呼吁底部或顶部，我们让市场机制引导我们。在牛市平静状态下有效的方法在很多其他状态下无效，在熊市波动中有效的方法在熊市平静状态下无效，反之亦然。

作为我目前正在运行的导师计划的一部分，也就是交易 Thunderdome，我们正在做大量的工作，寻找不同市场体制的特征以及在不同体制下执行的相应策略。

为了加入交易 Thunderdome 计划，您需要完成[系统构建/回溯测试大师课程](http://bit.ly/2UcGbYo)，以确保您拥有适当的工具和技能，从课程中受益。

*我们将很快发布正式计划……*

我们将在全年开展这些项目，所以如果你想成为一名成功的交易者，参加这个课程。现在是 1/2 折！

Grant 目前在这个项目中，他在寻找一个在熊市波动中表现良好的系统方面做了很多工作。他在 60 分钟图上使用 Vol 突破做空策略，确定了 ES(标准普尔 500·埃米尼),但是更低的时间框架也一样好。

格兰特将向你展示他的发现…

嗨，交易员们，

格兰特又来了，过几天我们会做一个更正式的介绍。然而，现在我们将讨论在 2008-2009 年金融危机期间，波动突破在小时图上的表现。我们将努力完善这个系统，以便你们所有人都能理解如何测试系统或想法。

那么，我们开始吧。

什么是波动突破或简称 VBO？这是一个布林线位于凯尔特纳通道内的设置，表明波动性较低。我们的一个信念是，波动性在低波动性和高波动性之间循环往复。因此，我们希望看到价格突破高于或低于布林通道和凯尔特人通道。当该柱收盘时，我们在突破柱的上方或下方设置买入或卖出止损。这是一种趋势跟踪策略，因此我们预计 FVBO 系统的胜率较低。然而，在某些制度下，我们看到 VBO 战略的光芒。具体来说，熊市动荡不安。

回溯测试注释

1) 12/13/2007–3/6/2009

2)我们只进行了短期 VBO 交易

3)所有止损都基于棒线收盘

4) 20 天均线追踪止损

5)所有交易都是在美国东部时间上午 7 点到下午 4 点之间进行的

既然你已经掌握了策略的要点，让我们来看看原始数据。我还在 Google Sheets 中提供了我的回溯测试的链接，你可以拿着这个电子表格，复制一份，它就是你的了！

[2007 年至 2009 年的回测空头仅在此承受波动的 VBO](https://docs.google.com/spreadsheets/d/1DsAaF3AtxPW-2KF7D22y0WvG6vKGt-3obTsciL0nGlE/edit?usp=sharing)

首先要注意的是，这种策略提供了相当多的机会。这很重要，因为我们希望大数定律对我们有利。我们看到的机会越多，我们满足回溯测试数据预期的机会就越大。

接下来我想引起注意的是胜率；61.5%!！！对于趋势跟踪系统来说，这是闻所未闻的。好的趋势跟踪系统只有 40%的胜算。这应该在每个人的头脑中敲响巨大的教堂钟声…市场机制对战略选择至关重要。

![](img/aa4b0f5532aa976de31f74e02b3c572f.png)

最后，该系统具有正偏斜。这意味着我们在赚钱的交易中赚的钱比在赔钱的交易中赔的钱多。这为 VBO 战略提供了稳健性，也是其盈利能力的重要因素。

![](img/aedbe5c95167caf4c8cc3e301de63546.png)

谢谢格兰特。

他正在做伟大的工作。

最后，现在我们已经对 2007-2009 年的“训练数据集”熊市波动机制进行了回溯测试，我使用了 2020 年 3 月熊市波动机制的“测试数据”,今天早上在 YouTube 上做了一个“仓促的回溯测试”

结果对我来说非常相似，虽然只是几周的交易。

今天就到这里，祝你好运。