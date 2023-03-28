# 华尔街交易员使用的 5 种定量策略

> 原文：<https://medium.datadriveninvestor.com/5-strategies-in-quant-trading-algorithms-f4f782d152e2?source=collection_archive---------0----------------------->

## 算法不需要复杂

大学一毕业，我就在华尔街的一家电子对冲基金开始了我的交易生涯。几个朋友对我说，交易是 r/wall street betts 的一个更有纪律的版本，实际上是赚钱的。在经历了几次失败的初次面试后，我很幸运地在一家顶级公司找到了一份工作，比如 Jane Street、Optiver 和 IMC。

第一天，我立刻就迷上了。

![](img/8bf9bc69ca0284f23b00643973474d87.png)

Photo by [Chris Li](https://unsplash.com/@chrisli) on [Unsplash](https://unsplash.com/photos/6Y6OnwBKk-o)

我在那里的主要角色是做市商。为了解释这一点，假设您是一名商人。假设您想购买一种商品，比如苹果。你需要找到一个苹果卖家，并商定一个公平的价格。做市商是中间人，他们总是愿意以给定的价格买入或卖出，从而切断了这种互动。

用金融术语来说，这叫做向金融交易所提供流动性。在任何给定的时刻，你都应该有信心变现你的头寸。从规模上来说，这些公司每年要处理数十万亿美元。

我的时间交易是我一生中最具变革性的时期之一。它不仅教会了我许多技术知识，还塑造了我成为一个积极主动、独立思考和努力工作的人。我强烈建议任何喜欢解决问题的人尝试一下交易。你不需要数学或金融背景就能进入。

交易文化类似于职业运动。这是一个零和游戏，有明确的赢家和输家——要么赚钱，要么赔钱。这意味着您的薪酬和工作保障都高度依赖于您的表现。对于那些好奇的人来说，根据业绩粗略分配交易者的报酬是 NBA 年薪的十分之一。

由于对复杂的定量模型的抽象，大众媒体交易有一种神秘性。我将阐明一些根植于所有交易策略的基本原则，以及它们如何适用于你。

## **套利**

交易者赚钱的一种方式是通过套利或无风险交易。假设你可以用 1 美元从萨姆那里买一个苹果，然后以 3 美元卖给梅根。一个理性的人会协调这两笔交易，以无风险获得 2 美元。

套利不仅存在于金融市场。流行的电子商务策略“直运”是一种套利形式。假设你发现一个三脚架在全球速卖通卖 10 美元。你可以在亚马逊上以 20 美元的价格列出同样的三脚架。如果有人从你这里购买，那么你只需要从全球速卖通购买三脚架，就可以获得 10 美元的利润。

这同样适用于车库销售。如果你在易趣上找到一张 2 美元的棒球卡，最近一次的售价是 100 美元，你有可能赚到 98 美元。当然，这不是一个完美的套利，因为您面临着找到买家的风险，但好处是值得的。

## **正期望值赌注**

交易者赚钱的另一种方式类似于赌场增加对他们有利的赔率。想象你抛一枚公平的硬币。如果它正面着地，你赢 3 美元，如果它反面着地，你输 1 美元。如果你只抛一次硬币，你可能会不走运，失去美元。然而，从长远来看，你有望每掷一次硬币获得 1 美元的正利润。这被称为正期望值下注。在数以百万计的交易中，你几乎可以保证盈利。

这就是为什么你永远不应该在赌场游戏中赌博，如轮盘赌。这些游戏都是负期望值赌注，这保证了你长期亏损。当然也有例外，比如扑克或者二十一点中的算牌。

下一次你走进一家赌场，做一个心理记录，观察它的设计方式，让你尽可能长时间地呆在那里。请注意没有窗户和迷宫一样的配置。甚至免费的饮料和便宜的住宿都是让你留在那里的一场闹剧。

## **相对定价**

当两种产品有明确的因果关系时，相对定价是一个很好的策略。让我们考虑一个苹果和一盒苹果汁。假设有一个因果关系，纸箱总是比苹果贵 9 美元。苹果和纸箱目前的交易价格分别为 1 美元和 10 美元。

如果苹果的价格涨到 2 美元，价格不会立即反映在纸箱上。总会有时间差。同样重要的是要注意，我们没有办法确定苹果的交易价格是合理还是过高。那么我们如何利用这种情况呢？

如果我们以 10 美元的价格买下纸盒，以 2 美元的价格卖出苹果，我们实际上以 8 美元的价格买下了“差价”。由于因果关系，差价的合理价值为 9 美元，这意味着我们赚了 1 美元。高频交易公司如此关注纳秒级延迟的原因是为了成为第一个发现这些相对错误定价的人。

这是三角洲一号战略的支柱。相互交易的常见配对包括 ETF 及其反向交易对手、包含该股票的 ETF 的特定股票或合成期权结构。

## **相关性**

相关性是两个事物之间的相互联系。当它们的趋势相同时，我们说它们正相关，反之亦然，负相关。一个流行的正相关的例子是鲨鱼袭击的数量与冰淇淋销售的数量。值得注意的是，鲨鱼袭击不会导致冰淇淋销售。

通常情况下，某些相关性没有直观的原因，但它们仍然有效。传奇的文艺复兴技术公司从数十亿字节的历史数据中筛选出有利可图的信号。例如，一个城市早晨的好天气往往预示着其股票市场的上涨。理论上，人们可以在开盘时买入股票，然后在中午卖出获利。

一条重要的建议是，不要理会任何向你推销课程的散户，他们声称自己有一套系统。这些都是骗局。在最好的情况下，这些都是在扣除交易成本后几乎无利可图的底线信号。你自己也不太可能有系统延迟、交易经验或研究能力来做这件事。这是可能的，但非常困难。

## **意味着逆转**

交易者依赖的另一个常见策略是均值回归趋势。在期权领域，主要关注的是购买相对于历史价值便宜的波动性，反之亦然。购买期权本质上等同于购买波动性。当然，事情没有这么简单，所以不要用这种策略把你的积蓄押在罗宾汉身上。

对大多数人来说，最适用的均值回归趋势是利率。这往往会上下波动，取决于央行是否想刺激储蓄或支出。由于全球利率接近于零或负值，为你的抵押贷款锁定这个低利率可能是个好主意。同样，在你做任何事情之前，先咨询一下财务顾问。

# [加入 1000 多名读者，了解更多关于金融和决策的信息](https://investinglessons.substack.com/)

*在过去的生活中，我是华尔街一家大型自营交易公司的衍生品交易员。每个星期天，我都会发表一些我在那里学到的关于投资、交易和决策的东西。本文原载于我的*[](https://christopherjgan.com/)**。* ***跟我上*** [***这里推特***](https://twitter.com/christopherjgan) ***。****

# *热门帖子*

*   *你是在交易还是在赌博？ — 40K+浏览量*
*   *华尔街量化分析师使用的 5 种量化策略*
*   *[做市初学者指南](https://investinglessons.substack.com/p/beginners-guide-to-market-making) — 5K+观点*

*对于那些对**开始交易生涯**感兴趣的人，我写了一本[新手指南来应对交易面试](https://gumroad.com/l/eSQCE)。这是我用来帮助十几个客户的土地交易工作。*