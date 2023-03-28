# 以有效的方式优化、管理和部署 ML 模型

> 原文：<https://medium.datadriveninvestor.com/optimize-manage-and-deploy-the-ml-model-in-an-effective-way-3a1133c8ab14?source=collection_archive---------11----------------------->

![](img/a0f2178dc42f8b765e453e0e59142338.png)

Photo by [Daria Nepriakhina](https://unsplash.com/@epicantus?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

导出训练数据最终会降低准确性。找到正确的平衡点是一个权衡决策，您可以使用灵敏度分析来帮助您选择曲线上最有效的点。

**敏感性分析**是一种财务模型，它根据称为输入变量的其他变量的变化来确定目标变量如何受到影响。

> *优化设备的模型尺寸包括对所选算法的关键参数进行灵敏度分析。创建模型以观察它们的大小，然后沿着灵敏度曲线选择切点以进行最佳权衡。*像 [Weka](http://blog.selcote.com/2020/02/14/introduction-to-machine-learning-with-weka/) 这样的机器学习(ML)环境使得[试验参数来优化你的模型](http://blog.selcote.com/2020/02/19/weka-explorer-how-powerful-it-is/)变得很容易。

深度学习(DL)算法的一个巨大优势是，通常情况下，它们的大小不会随着数据集的大小而线性扩展，随机森林算法就是这种情况。诸如 CNN 和 RNN 算法之类的 DL 算法使用隐藏层。随着数据集的增大，隐藏图层的数量不会增加。DL 型号变得更智能，但尺寸不会成比例增长。

# 模型版本控制

一旦创建，您应该将您的 ML 模型视为有价值的资产。尽管您没有在创建过程中编写代码，但是在管理它们时，您应该将它们视为代码等价物。这意味着 ML 模型被置于版本控制之下，就像您的应用程序源代码一样。

您是否存储实际的模型(在 Weka 的模型导出的情况下是一个序列化的 Java 对象),取决于模型是否可以确定地再现。理想情况下，您应该能够从输入组件中重现您的任何模型，包括:

*   资料组
*   输入配置，包括过滤器或预处理
*   算法选择
*   算法参数

对于可重现的确定性模型，没有必要存储模型本身。相反，您可以选择存储输入组件。当创建时间很长时，例如使用 KNN 算法处理大型数据集时，存储模型本身以及输入组件是有意义的。

以下工具是免费和开源的，承诺允许您以可伸缩、可靠和成本优化的方式无缝地部署和管理模型:

[](https://dataversioncontrol.com) [## 数据版本控制 DVC

### 下载(pip，conda，brew)$ DVC run-d images-o model . p CNN . py $ DVC remote add-d my repo S3://my bucket DVC 曲目…

dataversioncontrol.com](https://dataversioncontrol.com)  [## Datmo -数据科学和人工智能的生产力

### Datmo 工具有助于增强您现有的模型工作流。数据科学家为数据科学家建立的新标准。

datmo.com](https://datmo.com) 

这些工具支持与 AWS 和 GCP 等云提供商的集成。它们通过保证所有基于模型的资产的可再现性来解决版本控制问题。

# 更新模型

当您开始部署您的 ML 应用程序时，要考虑的一个关键方面是您将来如何更新模型。其中一个解决方案是在应用程序启动时直接从项目的资产目录中加载 ML 模型。

当开始 ML 应用程序开发时，这是最简单的方法，但是在将来升级应用程序-模型组合时，这是最不灵活的方法。

更灵活的架构是从应用程序中抽象出模型。这为将来更新模型提供了机会，而无需重新构建应用程序。

结论:

为[设备上](http://blog.selcote.com/2020/02/12/solution-for-running-machine-learning-on-the-edge/) ML 应用创建和处理预构建模型的最佳实践:

*   最佳模型大小取决于输入数据集大小、属性复杂性和目标设备硬件能力。
*   准备模型灵敏度分析，绘制模型精度与模型尺寸的关系图。