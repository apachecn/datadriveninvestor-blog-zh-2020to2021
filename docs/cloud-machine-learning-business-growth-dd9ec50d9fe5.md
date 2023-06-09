# 云+机器学习=业务增长

> 原文：<https://medium.datadriveninvestor.com/cloud-machine-learning-business-growth-dd9ec50d9fe5?source=collection_archive---------16----------------------->

![](img/6f3367ea3a421612f9ec94ba62b0a23b.png)

Cloud + machine learning = business growth

I aaS(基础设施即服务)解决方案允许您扩展您的计算环境，以满足您在 CPU、内存和存储方面的需求。您只需要为所需的资源付费。还使您能够轻松地跨地理区域分配资源。

这种方法比构建您自己的服务器并在它们变得太慢时升级它们要容易得多，也便宜得多。

[](https://www.datadriveninvestor.com/2018/11/09/a-business-moves-on-its-stomach-how-to-make-allowances-for-gut-feelings/) [## 一个企业在肚子上移动:如何照顾直觉|数据驱动的投资者

### 事实证明，直觉不仅仅是一种感觉。科学很清楚:你的直觉比你知道的更多…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2018/11/09/a-business-moves-on-its-stomach-how-to-make-allowances-for-gut-feelings/) 

与 DL(深度学习)相比，创建 CML(经典机器学习)解决方案的一个优势是它们需要更少的数据和 CPU 资源。这通常使您能够完全在桌面上创建解决方案。然而，你不应该忽视云。云提供商不断改进他们的 ML(机器学习)产品。今天，它们提供了一系列令人惊叹的服务和 API，使得没有 ML 经验的开发人员创建和部署 ML 解决方案比以往任何时候都更容易，这是出于多种考虑:

**本地资源可用性:**

您是否有一台可以处理大型数据集并构建 ML 模型的本地台式机或服务器？本地处理允许您保持对数据的控制，并避免云使用费。

**深度学习:**

深度学习项目往往倾向于基于云的架构，因为它们依赖于更大的数据集和对模型创建的高计算要求。

**地理多样性:**

云提供商可以让你在全球多个国家和地区增加资源。将资源放在离用户尽可能近的地方是有利的。

**数据大小:**

您是否有一个可以在桌面上管理的数据集大小，就像 CML 项目中经常出现的情况一样？

**可扩展性:**

您预计未来您的数据或存储需求会增长吗？云提供商提供了更好的可扩展性。添加云资源比升级或购买更强大的台式机/服务器要容易得多。

**时间限制:**

模型创建时间重要吗？即使对于具有中等规模到大型数据集的 CML 项目，在台式机或服务器单 CPU 上创建模型也可能需要几分钟到几小时。将这些计算密集型操作转移到云上可以大大减少模型创建时间。如果您需要实时或接近实时的创建时间，云是您唯一的选择。

**供货情况:**

您需要高可用性吗？您的项目可以从所有云提供商提供的分布式多节点架构中受益。

**安全注意事项:**

如果你有自己的联网服务器，你就会知道安全是一个多么大的挑战。云提供商简化了安全性，因为您可以利用他们的大规模基础架构。

**隐私考虑:**

您的客户可能不希望他们的数据放在由四大提供商之一管理的公共云网络上。在这种情况下，您可以实施私有云解决方案并收取额外费用。

即使您决定不为您的项目使用云提供商，关注他们的产品也很重要。服务会不断更新，您的决策可能会根据这些更新而改变，

> *由于最大的云提供商之间的激烈竞争，如今跨平台的云资源成本基本相同。四大银行敏锐地意识到他们竞争对手的产品，定价套利机会不再存在。云 ML 服务不是免费的。无论他们使用何种类型的容器或虚拟化技术，在某些时候都需要专用或共享的硬件(CPU、内存、存储)。每个提供商通常都有一个免费的试用版，所以你可以在购买前试用这项服务。*

建立模型的目的是利用它进行预测。AWS ML 允许实时、单次或批量预测。批预测特别有用，它允许您加载许多实例来分类为一个批。AWS ML 通过让您将批量预测加载到 S3 存储桶中来实现这一点，就像您加载原始数据集一样。

然后，您只需指定批量预测的 S3 位置，然后模型将生成结果。进行批量预测确实会增加成本。

AWS SageMaker 是一个完全托管的平台，可帮助您构建 DL 模型。这是最近增加的 AWS 服务之一。SageMaker 背后的主要思想是 ML 对开发人员来说很难，原因如下:

*   收集数据、处理数据、构建模型、测试模型和部署模型的过程给开发人员带来了过多的手动工作。
*   由于重复的手动工作，创建 ML 解决方案非常耗时。
*   创建 ML 解决方案过于复杂，因为所需的数据和分析技能集已经取代了传统的软件开发。

SageMaker 试图解决这些问题。它承诺消除复杂性，克服阻碍开发者的障碍。像所有的 AWS 服务一样，有大量的在线文档帮助你理解服务。SageMaker 开发者指南的链接是*https://docs.aws.amazon.com/sagemaker/latest/dg*。

SageMaker 很有潜力。两个特别重要的特性使它成为在 AWS- notebook 实例上实现 ML 的一种强大方式，以及它对算法的灵活支持。

SageMaker notebook 实例是一个运行 Jupyter Notebook 应用程序的计算实例。Jupyter 是一个开源的 web 应用程序，运行在 Python(因此它的拼写)上，允许你创建和共享包含实时代码和可视化的文档。它在 Python 和 DL 领域非常流行。

SageMaker 的另一个有趣的特性是它的算法灵活性。SageMaker 支持两类算法:内置算法和自带算法。

内置算法列表可在[](https://docs.aws.amazon.com/sagemaker/latest/dg/algos.html)*获得。算法列表非常完整。AWS 声称，由于优化，预装算法的性能是其他提供商的 10 倍。这是一个令人印象深刻的说法。然而，AWS 没有提供他们如何做到这一点的细节，或者它适用于哪些算法。*

*最后，用户可以带来自己的算法或框架。GitHub 上的 SageMaker 示例展示了如何为各种模型和算法实现这一点，包括 XGBoost、k-means、R、scikit、MXNet 和 TensorFlow。*