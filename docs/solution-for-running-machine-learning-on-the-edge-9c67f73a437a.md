# 在边缘运行机器学习的解决方案

> 原文：<https://medium.datadriveninvestor.com/solution-for-running-machine-learning-on-the-edge-9c67f73a437a?source=collection_archive---------20----------------------->

## 在设备上部署您的模型

![](img/3e2e6d3360a476d12b94fd8db8e1aaac.png)

Photo by [Christopher Rusev](https://unsplash.com/@ralics?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

你的主要目标之一是在边缘应用 ML 解决方案。这要求您生产轻量级的模型，可以部署到便携式设备中，比如移动电话。Java ML(机器学习)环境满足了这些需求。

Java ML 环境选中所有复选框:

*   它们是免费和开源的。
*   你可以很容易地生产出轻量级的模型。
*   如果需要更高的计算资源，可以在桌面或云中运行 Java ML 环境。
*   很容易导出该模型，以便在移动设备或小型计算机(如 Raspberry Pi)中使用。

实际上，Java ML 环境就像 ML 管道中的一个中间件。ML 环境创建的模型将输入数据与用户应用程序连接起来。

[](https://www.datadriveninvestor.com/2019/02/08/machine-learning-in-finance/) [## 金融中的机器学习|数据驱动的投资者

### 在我们讲述一些机器学习金融应用之前，我们先来了解一下什么是机器学习。机器…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/08/machine-learning-in-finance/) 

在选择最佳的 Java ML 环境时，有几个因素需要考虑。

这些因素包括:

**许可和商业条款**:你应该喜欢免费的开源软件包，它允许你创建可用于商业应用的模型。

**算法**的可用性:你应该寻找支持[七种最重要算法](https://medium.com/@zouhaire.elakioui/7-ml-algorithms-will-solve-99-of-the-problems-cba5ef4db0c1)的软件包。

持续支持:你应该寻找一个用户社区或创作者的长期承诺。

**模型的可移植性**:您应该寻找导出模型的能力，这样任何设备上的 Java 客户端都可以使用您创建的模型。这有助于你在边缘实现 ML。

**灵活性** : Java 随着每个主要版本的发布而不断发展。你需要一个基于 Java 的 ML 环境，它可以随着语言的发展而发展。

也许在将来，我们会看到 ML 特性直接包含在 Java 中，就像 JSON 和其他特性现在是包含的候选者一样。

对于使用 Java 语言的最重要的 ML 环境，我们有:

**Weka**

Weka 是怀卡托知识分析环境的缩写。新西兰的怀卡托大学创造了 Weka。有趣的是，Weka 也是新西兰一种不会飞的鸟(Gallirallus Australis)的名字，因此有了这个标志。

ML 环境 Weka 已经存在一段时间了。它于 1997 年移植到 Java，已经成为数据挖掘行业的中流砥柱。2005 年，Weka 在 SIGKDD 会议上获得了 ACM 颁发的数据挖掘和知识发现服务奖。将 Weka 迁移到 Java 的决定让它保持了相关性。

所有重要的 CML(经典机器学习)算法都适用于 Weka。Weka 有一个友好的许可证，GNU 通用公共许可证(GPL)。因此，有可能研究算法如何工作并修改它们。

Weka GUI 看起来过时了。Weka GUIs 和可视化工具远没有 RapidMiner 那么流畅。然而，在引擎盖下，它什么都不缺。Weka 是一个非常强大的 ML 环境，可以提供您的 ML 应用程序所需的模型。尽管相对于 RapidMiner，它的 GUI 较差，但 Weka 检查了所有的复选框。

**RapidMiner**

RapidMiner 是一个令人难以置信的 ML 环境。RapidMiner 是数据科学平台的领导者。基于 Java 的 RapidMiner 在以下方面表现出色:

RapidMiner 快如闪电。

RapidMiner 有许多工具。

RapidMiner 在准备数据方面表现出色。

RapidMiner 允许您构建预测 ML 模型。

就灵活性而言，Weka 和 RapidMiner 都提供了 jar 文件库，您可以将它们集成到您的 Java 项目中。这允许您在 Java 应用程序中利用预构建的模型。

**克尼姆**

像 RapidMiner 一样，KNIME 也是数据科学平台的领导者。KNIME 的一些关键卖点是:

*   KNIME 是数据科学家的工具箱。
*   KNIME 包含 2000 多个模块。
*   KNIME 是一个开放的平台。
*   KNIME 可以在本地、服务器或云中运行，这正是您所寻求的灵活性。

**埃尔基**

ELKI 是一个擅长集群和离群点检测的 Java 平台。Weka 和 RapidMiner 是通用框架，而 ELKI 只做一件事，而且做得很好:集群。

如果通用框架中包含的基本聚类算法不足以解决您的 ML 聚类问题，ELKI 可能是解决方案。

ELKI 专注于研究和教育。它有助于解决现实世界中的聚类问题，如聚类鲸鱼的位置和重新平衡公共自行车共享计划。

ELKI 的一个独特特性是使用 SVG 进行可伸缩图形输出，使用 Apache Batik 渲染用户界面。如果您需要无损、高质量、可伸缩的图形输出来解决集群问题，ELKI 是一个很好的选择。

起源于[blog.selcote.com](http://blog.selcote.com/2020/02/12/solution-for-running-machine-learning-on-the-edge/)