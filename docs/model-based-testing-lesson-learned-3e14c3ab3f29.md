# 基于模型的测试，一年后(Pt。1)

> 原文：<https://medium.datadriveninvestor.com/model-based-testing-lesson-learned-3e14c3ab3f29?source=collection_archive---------10----------------------->

![](img/70ec28cd06fd754b69d83d849ba5e684.png)

Photo by [Kdwk Leung](https://unsplash.com/@kdwk?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

采用 MBT(基于模型的测试)需要承诺和计划。在这几期文章中，我将分享我在组织中采用 MBT 时学到的东西。

我与 MBT(基于模型的测试)的相遇始于基于属性的测试。从那里，互联网把我和 MBT 联系起来。观看此视频，了解 https://www.youtube.com/watch?v=psOThLDKOFc 的 MBT:

在跳进 MBT 火车车厢之前，一定要检查你能使用的各种工具。此外，最重要的是，选择你要申请 MBT 的级别。在我的情况下，我用它来驱动移动应用程序上的 UI 测试。在这里，我将放下我所学到的。

# 概念证明

我花了大约 2-3 个月的时间建立了一个小型的 PoC 项目。MBT 的工具和文档非常缺乏。也有商业工具和开源软件。当然，商业选项给了你漂亮的 GUI，你可以在那里拖放东西。您可以生成测试用例，并使其与您在 GUI 工具中创建的模型保持一致。促使我远离这些商业产品的一个原因是透明度。工具后面会隐藏很多东西。除非使用该工具，否则无法对其进行编辑。这是我不想做的交易。当然，你的理由可能会有所不同。由于这些商业工具已经相当成熟，总体经验可能会帮助您克服采用 MBT 的最初障碍。

最终，我选择了 [Graphwalker](https://github.com/GraphWalker/graphwalker-project) 。这是(最成熟的)简单的开源 MBT 工具。Graphwalker 提供:

1.  GUI 模型设计器(Graphwalker Studio)。它不如商业产品好，但足以让您开始创建模型并验证您的模型。
2.  CLI 工具。您可以验证模型并离线生成测试。我在 CI 管道中使用模型验证部分来防止签入损坏的模型。
3.  测试库。Graphwalker 提供了 Maven 插件和 Java 库来实现在线测试，也称为测试自动化。

在概念验证中，我从一个正在进行的项目中抽取了一个小特性。这是管理门户网站上键值列表的一个特性(类似于 Firebase 提供的)。一方面，我有常规的方法:列出所有可用的动作和输出、状态列表及其转换、错误消息以及如何触发它们。这是一页很长的表格和文本，用来说明该特性将如何工作。

另一方面，我也尝试基于相同的特征创建模型。当然，我痴迷于捕捉模型内部的全部规格。使用 Graphwalker，您可以创建多个相互连接的模型(参见 Graphwalker 项目中的宠物诊所示例)。将您的功能分解成解决特定问题的模块是非常合理的。然而，虽然这是合乎逻辑的，但实现起来并不那么简单。即使在今天，我还没有使用连接模型。

[](https://www.datadriveninvestor.com/2020/02/27/how-to-use-automation-to-get-more-out-of-your-data/) [## 如何使用自动化从您的数据中获得更多价值？数据驱动的投资者

### 去年的新闻故事不停地谈论机器学习变得多么先进。电脑现在…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/27/how-to-use-automation-to-get-more-out-of-your-data/) 

得到我想要的型号需要一段时间。让模型变得非常优化，就像我们编写代码一样，这是非常诱人的。我的建议是避开这个目标。这只会导致难以创建、读取和维护复杂模型。

从概念验证中，您将了解实施 MBT 需要什么。什么工具适合你的团队。如何合作(模型也需要同行评审)。学习建模需要多大的努力。甚至不知道 MBT 是否适合你的项目。

接下来:[建模](https://medium.com/@neofreko/model-based-testing-one-year-later-part-2-a708eb5e5265)