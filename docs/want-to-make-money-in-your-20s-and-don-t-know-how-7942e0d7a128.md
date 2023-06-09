# 想在 20 多岁的时候赚钱却不知道怎么赚？

> 原文：<https://medium.datadriveninvestor.com/want-to-make-money-in-your-20s-and-don-t-know-how-7942e0d7a128?source=collection_archive---------4----------------------->

## 如何使用 python 和 ML 每年赚 100k+的完整蓝图

![](img/f0f832334433751950ef8705f5971ba6.png)

> “简明扼要，精确，并以最简单的方式解释复杂的主题。”

随着全球金融市场暴跌，下一次大萧条似乎即将来临，千禧一代必须明白，尽管这个世界很快就会陷入火海(如果它可能变得比现在更糟)，但他们有能力让这种情况为自己服务。虽然许多悲剧已经并将继续从这些事件中产生，但更有商业头脑的人可能已经找到了获利的方法，而不是闲着没事干，抱怨。

虽然本文中提到的技术**可以被任何人应用**，千禧一代被选为目标受众，因为这种商业策略可以成为数十万美元的来源，并且需要 0 美元作为启动资金。换句话说，**可以被所有人追随**，它只是**适合千禧一代，**因为**大多数人没有一分钱**。**(不，这不是在 Airbnb 上展示你的房产的宣传)**

**注意！** *会有编程涉及。我将代码附在文件的末尾，因为不是每个人都有兴趣重新创建它。对于那些人来说，我以这样一种方式构建代码，即使* ***你一生中从未接触过计算机，*** *你也将* ***能够跟随*** *并在需要时简单地复制粘贴。*

一直读到最后，你会得到一个独家的惊喜！

# 目录

*   [*项目介绍*](https://medium.com/datadriveninvestor/millennials-this-is-the-unconventional-money-making-technique-you-were-looking-for-3b47c7384c60#d744)
*   [*项目蓝图*](https://medium.com/datadriveninvestor/millennials-this-is-the-unconventional-money-making-technique-you-were-looking-for-3b47c7384c60#d61a)
*   [*分析/结果*](https://medium.com/datadriveninvestor/millennials-this-is-the-unconventional-money-making-technique-you-were-looking-for-3b47c7384c60#9d8a)
*   [*结束语(* ***必读！*** *)*](https://medium.com/datadriveninvestor/millennials-this-is-the-unconventional-money-making-technique-you-were-looking-for-3b47c7384c60#a645)

# 项目介绍

现在很明显，这个项目旨在展示一个人如何利用 Python 和机器学习来赚足够的钱，而不需要任何初始资本。

房地产行业是积累资本的最佳方式之一。想想吧！哪种人工制造的商品在当今社会最根深蒂固？答案很简单:**房屋**。不管你怎么看，庇护所是必不可少的。这是一个本质上永远不会完全饱和的市场。

近几十年来，房地产行业经历了翻天覆地的变化。**20 世纪**是房地产所有权的**时代，一个男人的房子是他最大的骄傲。另一方面，21 世纪已经改变了方向。拥有财产现在已成为过去。西方的新规范是租赁房产。**

2008 年标志着一个新时代的开始。Airbnb 诞生了。房主现在可以通过在有限的时间内出租他们的房产来赚钱。

[](https://www.datadriveninvestor.com/2020/07/07/5-principles-for-business-value-and-artificial-intelligence/) [## 商业价值和人工智能的 5 个原则|数据驱动的投资者

### 提取商业价值很难。我是说真的很难...说到高级分析，这一过程甚至…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/07/07/5-principles-for-business-value-and-artificial-intelligence/) 

目前，由于新冠肺炎病毒，世界正处于灾难性的状态。目前旅游受到限制，旅游业遭受了毁灭性的打击。然而，这种情况不会永远持续下去，众所周知，比起酒店，游客们更喜欢住在 Airbnb。

Airbnb 是一种很棒的赚钱方式。不幸的是，对于那些在**名下没有任何住宅房产的**千禧一代**来说，他们没有办法出租房屋！**还是他们呢？****

# 宣言/项目蓝图

考虑到上述情况，我想:“*我如何利用我的数据和计算机科学技能在 Airbnb 上赚钱？”*

*   *无自有或租赁房产*
*   ****不要求初始投资金额****
*   ****未进入饱和市场****
*   ****利用机器学习最大化结果****
*   ****想出一个别人能够轻易复制的方法****

*经过深思熟虑，我得出的结论是，该企业的基础业务模型应该类似于直运业务的结构。当然，为了让它工作，它应该被修改… **很多。***

***我的商业计划包括以下内容:**我将分析过去几年我能找到的所有雅典的 Airbnb 房源。在分析数据以获得更多洞察力后，我将使用**机器学习**来确定**对价格影响最大的变量是什么**。一旦我找到了这些特征并对它们进行了分类，我将联系那些最有可能成为我的客户的 Airbnb 房源所有者(由模型指示的**)，我将为他们管理 Airbnb 上的房产，收取**20%的佣金**。所有与买家的初始沟通都将由我将要建立的一个由人工智能驱动的信息平台进行。***

*本质上，这个模型会告诉我应该接触哪些客户，然后如何让他们的房源飙升，并从我带来的租户那里赚钱。*

# *分析/结果*

*(所有代码都可以在本节末尾找到！)*

*首先，我需要一个数据集。经过大量研究，我能找到的关于雅典的最佳数据集是这个。致力于提供数据的小组(insideairbnb)不断更新和废弃来自世界各地城市的 airbnb 房源信息。*

*我导入了数据库并创建了一个[熊猫数据框架](https://www.geeksforgeeks.org/python-pandas-dataframe/) *，以便恰当地使用数据。数据框架包含 11541 个具有各种特征的列表*。*

*不幸的是，它包含许多 NaN 值*(缺失数据)，并且有许多我并不真正需要的特性。在清理集合并移除不需要的输入后，我绘制了数字和布尔类别的分布:*

*![](img/e6e20b2abe1d8b6333748ffdee2f02dc.png)*

*在他们的核心，这些是模型的关键信息，包括房产的平方英尺，卧室的数量等数据*

*为了探索数据，我将查看该地区提供的**不同类型的房地产**:*

*![](img/eff631f5401cd7c5abfebd78e61fc2a8.png)*

*似乎大部分是公寓和房屋。没有我们没有预料到的。实际上…我收回那句话。似乎有人列出了…一个洞穴？。*

*我将假装我没有看到这一点，并继续创建一个其重要性将由模型评估的功能列表(我个人从列表中删除了一些功能，如“厕所”，因为所有住宿都很可能包括此类“奢侈品”)。*

*这些“**合意的设施**是:*

```
*‘Cable TV’,
 ‘Ceiling fan’,
 ‘Central air conditioning’,
 ‘Coffee maker’,
 ‘Cooking basics’,
 ‘Dishes and silverware’,
 ‘Dishwasher’,
 ‘Dog(s)’,
 ‘Dryer’,
 ‘Elevator’,
 ‘Essentials’,
 ‘Extra pillows and blankets’,
 ‘Extra space around bed’,
 ‘Family/kid friendly’,
 ‘First aid kit’,
 ‘Free parking on premises’,
 ‘Free street parking’,
 ‘Freezer’,
 ‘Full kitchen’,
 ‘Game console’,
 ‘Garden or backyard’,
 ‘Gym’,
 ‘Hair dryer’,
 ‘Heating’,
 ‘High-resolution computer monitor’,
 ‘Host greets you’,
 ‘Hot water’,
 ‘Indoor fireplace’,
 ‘Internet’,
 ‘Iron’,
 ‘Kitchen’,
 ‘Long term stays allowed’,
 ‘Microwave’,
 ‘Mini fridge’,
 ‘Mountain view’,
 ‘Netflix’,
 ‘Other pet(s)’,
 ‘Outdoor parking’,
 ‘Oven’,
 ‘Pets allowed’,
 ‘Pool’,
 ‘Private bathroom’,
 ‘Private entrance’,
 ‘Private living room’,
 ‘Private pool’,
 ‘Satellite TV’,
 ‘Refrigerator’,
 ‘Shared gym’,
 ‘Shared pool’,
 ‘Smart TV’,
 ‘Smoking allowed’,
 ‘Suitable for events’,
 ‘TV’,
 ‘Table corner guards’,
 ‘Washer/Dryer’,
 ‘Wifi’,
 ‘Window guards’*
```

*当人们评估来自世界各地城市的数据集时，很明显这个列表将**显著变化**，取决于**文化**、**宗教**、**等***

*现在已经有了一个令人满意的便利设施的列表，并且数据已经被适当地清理了，我们可以继续… **实际上不是**。*

> *数据科学家 80%的宝贵时间都花在查找、清理和组织数据上，只有 20%的时间用于实际执行分析…*
> 
> *~ IBM 数据分析~*

*向上帝祈祷不要再做进一步的调整，我现在将可视化清单上第一次**审查**、**到数据被抓取**之间的时间跨度。*

*![](img/0b16f24b01dc5b3517ed8cae13517318.png)*

***数据中可能观察到不一致**，因为形状在 0 之前开始。没有理由惊慌，，因为我知道错误的原因(实际时间和检索信息的日期之间的差异)。*

*尽管很有趣，但迄今为止分析的数据并没有多大帮助。为了改变这一点，我将在雅典 Airbnb 房源的**夜间价格**中绘制出每年的**变化**。*

*![](img/9400f397333551583122560ad6aed77d.png)*

*结果相当有趣。我将通过列出雅典 Airbnb 房源的年平均价格来补充上述发现，并对 Airbnb 在该地区的流量有更多的了解。*

*![](img/57db220a65b008c138b2a6c67c34a580.png)*

*很明显，Airbnb 在雅典的第一年**是价格最低的时候。通过使用逻辑和理性可以推断，造成这种现象的主要原因是人们还不熟悉 Airbnb，大多数卖家可能不知道价格应该是多少。还可以观察到，价格峰值在 2013 年**达到**。***

*如“描述”数据帧所示，夜间广告价格范围从:*

*![](img/d6da57733f590a9256b0080ccbafeaa7.png)*

*另一个有用的数字是**中值**和**平均值**每个主机的**列表数量。通过这种方式，我们将能够了解 Airbnb 住宿在雅典的市场份额，即我们是否正在与一个“**卡特尔**”打交道。***

*![](img/057b77f069999c0563aeb121b34b24cb.png)*

*似乎存在明显的市场集中度。目前尚不清楚这些人对商业提议的反应程度和方式。从现实的角度来说，要让这些人考虑成为我的客户，两个**中的一个必须是真的**:*

*   **我可以展示并证明我的成果* ***优于业主的*** *，他/她只会从成为我的客户* *中获益* ***。****
*   **所有者* ***未能*** *达到* ***期望的客户量*** *，并且正在寻找一种方法来提高参与度和未来的销售。**

*在这一点上，我无法证明我可以成功地满足第一个，所以**梯子似乎是最佳的行动方案**。*

*我们肯定是在正确的轨道上！让我们对数据集的一些我们感兴趣的特性获得一些**的额外见解**。*

*![](img/f0231b0122a0684890e69141982f5337.png)*

*从第一个数字可以明显看出，一处房产能够容纳的人数与其价格直接相关。这是意料之中的事，因为它能容纳的人越多，房子就越大。*

*![](img/c31c44b55f427da5cd3d886f7cf8f617.png)*

*整体上市评级对我们来说是一个至关重要的数据点。很明显**大多数列表**都在**95–100%**正反馈范围内。*

***超级主机**是**例外**的主机。这些人给顾客免费赠品，总是在那里提供帮助，并且总是在*

*![](img/2e972cfed013ccad67f2bac8c2980cde.png)*

*他们的服务。*

*所有这些信息很快就会变得有用。没有被考虑到的，也是至关重要的，是**位置**。**与其他行业**不同，房地产**依赖于位置**。换句话说，位置会对资产价格产生巨大影响。*

*这就是为什么，我将绘制雅典每个地区的 Airbnb 房源数量，以及每个地区的中值价格。*

*所有这些信息很快就会变得有用。没有被考虑到的，也是至关重要的，是**位置**。**与其他行业**不同，房地产是**的区位依赖**。换句话说，位置会对资产价格产生巨大影响。*

*这就是为什么，我将绘制雅典每个地区的 Airbnb 房源数量，以及每个地区的中值价格。*

*![](img/5b58d781f3917d26a3fdbb961f9d15fd.png)*

*大多数房源似乎都位于市中心。老实说，我希望更多的房产位于郊区和最靠近度假胜地的地区，一般来说是海边。然而，一个有趣的发现。或许，我应该避免涉足深蓝领域，而去涉足那些市场不太饱和且尚未成熟的领域。*

*![](img/8df263a7823454a6b0d407c1b0c9e40a.png)*

*在大多数列表的**位置**和**中间价格**之间似乎也存在**相关性**。尽管情况可能如此，但这些地区的某些特定区域被视为高端区域，这可能是中位价格较高的原因。*

***现在是**到**运行机器学习模型**的时候了，并决定哪些变量是**最重要的**。*

*![](img/28eac40032fe461d76be2352d40936f3.png)*

*瞧吧！我们现在可以看到所有功能的排名。其中一些似乎是由地理位置决定的，正如我之前说过的，有些地区被认为是更“高端”的，价格也更高。其他功能包括提供**免费停车场**，一台**电视**，评论分数在 80-94%之间的**，等等。***

*包含代码的笔记本可以在下面找到**:***

*[](https://github.com/Filippos101/Airbnb-PART1.git) [## filippos 101/Airbnb-第 1 部分

### 在 GitHub 上创建一个帐户，为 Filippos101/Airbnb-PART1 开发做出贡献。

github.com](https://github.com/Filippos101/Airbnb-PART1.git)* 

# *最后备注(非常重要！)*

*这是两篇系列文章中**的第一篇** **的**结尾**。总结一下我们在这一部分所做的工作，我们*确定问题*并*找到解决方案* , *制定项目蓝图*,*执行所需的分析*以便得出某些*结果和结论。****

*让我们看看**的下一部分是什么:***

*   **利用第一部分的结果，制定出***两条最优作战路径。***
*   ***彻底地* ***分析运行路径*** *并通过使用上述获得的数据* *确定两个* ***中的哪一个最适合每个人口统计。*****
*   **建立一个人工智能驱动的信息平台，根据你选择的路径，向潜在客户群发信息。一旦客户回复机器人，它将被训练相应地回答所有问题，并在不需要我们人工干预的情况下完成交易。**

# **你想了解更多吗？**

**如果你想**提高你的知识**并且对**用机器学习赚钱**感兴趣，我**强烈鼓励你**阅读下面**列出的文章**:**

**[](https://medium.com/datadriveninvestor/sell-anything-to-anyone-using-ai-and-machine-learning-1de5669a844c) [## 向任何使用人工智能和机器学习的人出售任何东西

### 关于如何使用人工智能和 IBM 沃森的个性确保向潜在客户销售产品的 A-Z 指南…

medium.com](https://medium.com/datadriveninvestor/sell-anything-to-anyone-using-ai-and-machine-learning-1de5669a844c) [](https://medium.com/datadriveninvestor/maximize-your-stock-market-earnings-with-machine-learning-87709494b1e3) [## 用机器学习最大化你的股市收益

### 如何利用 ML 最大化股票投资组合的效率？

medium.com](https://medium.com/datadriveninvestor/maximize-your-stock-market-earnings-with-machine-learning-87709494b1e3) [](https://medium.com/datadriveninvestor/machine-learning-shows-you-are-responsible-for-george-floyds-murder-17ab2b1fa0bd) [## 机器学习显示你对乔治·弗洛伊德的谋杀负有责任！

### 实用的大开眼界需要带来彻底的改变

medium.com](https://medium.com/datadriveninvestor/machine-learning-shows-you-are-responsible-for-george-floyds-murder-17ab2b1fa0bd) [](https://medium.com/datadriveninvestor/create-the-ultimate-stock-investing-portfolio-with-machine-learning-1f8034648211) [## 利用机器学习创建终极股票投资组合

### 关于如何使用机器学习和公众情绪分析建立机器学习投资组合的 A-Z 指南

medium.com](https://medium.com/datadriveninvestor/create-the-ultimate-stock-investing-portfolio-with-machine-learning-1f8034648211) 

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)**