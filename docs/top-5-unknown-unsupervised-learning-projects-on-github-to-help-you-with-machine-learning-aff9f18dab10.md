# Github 上帮助你完成机器学习任务的 5 大未知无监督学习项目(包括链接)

> 原文：<https://medium.datadriveninvestor.com/top-5-unknown-unsupervised-learning-projects-on-github-to-help-you-with-machine-learning-aff9f18dab10?source=collection_archive---------4----------------------->

## 无监督学习是一种从未标记数据中学习模式的算法。希望机器通过模仿被迫建立一个其世界的紧凑的内部表示。[维基百科](https://en.wikipedia.org/wiki/Unsupervised_learning)

> **无监督分类**运行起来相当快速简单。不需要对该领域有广泛的先验知识，但是你必须能够在**分类**之后识别和标记类别。
> 
> 无监督学习的主要应用包括聚类、可视化、降维、发现关联规则和异常检测。
> 
> **聚类**。
> 
> 可视化。
> 
> 降维。
> 
> 寻找关联规则。
> 
> 异常检测。
> 
> 更多关于**无监督学习**。

## 在今天的文章中，我们将谈论 Github 上的五个 6 无监督学习项目/资源库，以帮助您通过您的 ML 旅程来增强您在数据科学和 AI 领域的技能。

> **注意** : **在本文中，我们将讨论一些非常好的开源无监督学习项目/资源库，您可以在您的项目中使用它们。要阅读更多关于它们的内容，我推荐你点击项目中给出的链接。**

![](img/a88a4cefa4bbcead5237326ba51a8d0e.png)

> 学习不仅仅是为了更好地胜任工作，而且远不止于此。[***data camp***](https://datacamp.pxf.io/x9nmvv)*让我学无止境。*
> 
> [***data camp***](https://datacamp.pxf.io/x9nmvv)*为您提供所需的灵活性，让您可以利用自己的时间参加课程，学习向成功职业过渡所需的基本技能。*
> 
> [***【data camp】***](https://datacamp.pxf.io/x9nmvv)*教会了我快速获取新想法，并将其应用于现实世界的问题。当我还在学习阶段的时候，*[***data camp***](https://datacamp.pxf.io/x9nmvv)*让我对课程中发生的一切都着了迷，从课程内容和助教反馈到 meetups 活动和教授的 Twitter feeds。*
> 
> 这里有一些我最喜欢的课程，我强烈推荐你学习，只要它符合你的时间表和心情。你可以将从这些课程中学到的概念和技能直接应用到工作或大学中令人兴奋的新项目中。

1.  [使用 python 的数据科学家](https://datacamp.pxf.io/LPDqQZ)
2.  [数据科学家与 r](https://datacamp.pxf.io/MXQxrJ)
3.  [机器学习科学家与机器人](https://datacamp.pxf.io/DVLg4j)
4.  [使用 python 的机器学习科学家](https://datacamp.pxf.io/9WePXW)
5.  [面向所有人的机器学习](https://datacamp.pxf.io/kjR3mN)
6.  [人人共享的数据科学](https://datacamp.pxf.io/15bLmd)
7.  [使用 python 的数据工程师](https://datacamp.pxf.io/jW13ve)
8.  [使用 python 的数据分析师](https://datacamp.pxf.io/kjR3mz)
9.  [基于 pyspark 的大数据基础](https://datacamp.pxf.io/e4RM6r)

***回到正题-***

# 1.热电偶

> [*Github*](https://github.com/yzhao062/pyod)
> 
> [*正式文件*](https://pyod.readthedocs.io/en/latest/)

P[***yOD***](https://pyod.readthedocs.io/en/latest/)是一个 Python ***工具箱，用于可扩展的离群点检测(异常检测)。* PyOD** 有多个基于神经网络的模型，例如*自动编码器，在 Keras 中实现。*

***PyOD*** 是一个*综合*和*可扩展的* Python 工具包，用于 ***检测多元数据中的远距离对象*** 。这一激动人心而又富有挑战性的领域通常被称为[](https://en.wikipedia.org/wiki/Anomaly_detection)**或*[***异常检测***](https://en.wikipedia.org/wiki/Anomaly_detection) 。***

*****PyOD*** 包含超过 *30 种检测算法*，从经典的 LOF (SIGMOD 2000)到最新的 COPOD (ICDM 2020)。**

## **PyOD 的特点是:**

*   ****跨各种算法的统一 API、详细文档和交互示例**。**
*   ****高级模型**，包括来自 scikit-learn 的**经典，最新的**深度学习方法**，以及 COPOD** 等**新兴算法。****
*   ****尽可能使用 [numba](https://github.com/numba/numba) 和 [joblib](https://github.com/joblib/joblib) ，通过 JIT 和并行化**优化性能。**
*   ****兼容 Python 2 & 3** 。**

# **2.SfMLearner**

> **[*Github*](https://github.com/tinghuiz/SfMLearner)**
> 
> **[论文](https://people.eecs.berkeley.edu/~tinghuiz/projects/SfMLearner/)**

**S[***FM learner***](https://people.eecs.berkeley.edu/~tinghuiz/projects/SfMLearner/)是一个**无监督学习框架**用于*深度*和*自我* - *单目视频的运动估计*。**这个代码库实现了论文中描述的系统:****

**[***来自视频的深度和自我运动的无监督学习***](https://people.eecs.berkeley.edu/~tinghuiz/projects/SfMLearner/)**

**![](img/99012c3d47df17418523aa6f89997524.png)**

**在这篇论文中，他们提出了一个用于从非结构化视频序列中进行*单目深度*和*相机运动估计的*无监督学习框架。****

**这个代码库是用 ***Tensorflow 1.0、CUDA 8.0 和 Ubuntu 16.04 开发和测试的。*****

# **3.KarateClub**

> **[*Github*](https://github.com/benedekrozemberczki/karateclub)**
> 
> **[论文](https://karateclub.readthedocs.io/en/latest/)**

**K[***arate club***](https://karateclub.readthedocs.io/en/latest/)是一个面向 ***API 的开源 Python 框架*** 用于 ***图上的无监督学习*** 。**

**![](img/f8319e78166c5ad2cebf396b01c9b187.png)**

****空手道俱乐部**是一个 ***无监督机器学习扩展库*** 用于 [*NetworkX*](https://networkx.github.io/) 。它基于其他开源的*线性代数、机器学习和图形信号处理库*，例如[***Numpy***](https://numpy.org/)***、***[***Scipy***](https://www.scipy.org/)***、***[***Gensim*空手道俱乐部** 由*最先进的方法*组成，在图结构数据上做 ***无监督学习。***](https://radimrehurek.com/gensim/)**

**简单来说，就是一把*小规模图挖掘研究的瑞士军刀。***

*   *****首先，提供了节点级和图级的网络嵌入技术。*****
*   *****其次，它包括多种重叠和非重叠的社区检测方法。*****
*   *****空手道俱乐部采用现代社区检测技术相对简单明了(见*** [***此处***](https://karateclub.readthedocs.io/en/latest/notes/introduction.html) ***为附带教程)。*****

# **4.体素形态**

> **[*Github*](https://github.com/voxelmorph/voxelmorph)**

**V[***oxelMorph***](https://github.com/voxelmorph/voxelmorph)是一个用于图像配准的 ***无监督学习项目*** 。 ***Voxelmorph*** 是一个 ***通用库，用于基于学习的工具，用于对齐/配准，更一般地说，用于变形建模。*****

**如果你想训练你的**模型**，你将需要为你的*数据集和数据格式定制数据加载代码。*然而，假设您有一个包含 npz (NumPy)格式的训练数据文件的 ***目录，那么可以运行许多现成的示例脚本。*****

> ****关键词*:机器学习、卷积神经网络、对齐、映射、配准*****

# **5.域转移网络**

> **[*Github*](https://github.com/yunjey/domain-transfer-network)**
> 
> **[论文](https://arxiv.org/abs/1611.02200)**

**D [***域转移网络***](https://github.com/yunjey/domain-transfer-network) 是 ***TensorFlow 实现的*** [***无监督跨域图像生成***](https://arxiv.org/abs/1611.02200) ***。*****

**![](img/76dbe6a068a1949cc64201a7e098e3a5.png)**

**这是一个将一个域中的样本转移到另一个域中的模拟选择的问题。给定两个相关的部分， **S** 和 **T** ，我们想要学习一个生成函数 **G** ，它将来自 **S** 的输入样本映射到域 **T** ，使得接受任一域中的输入的给定函数 **f** 的输出将保持不变。除了函数 **f** 之外，训练数据是无监督的，由每个部分的样本组成。我们提出的域转移网络(**【DTN】**)采用了一个复合损失函数，它包括一个多类****损失**、一个**f-恒定性分量**，以及一个鼓励 ***G 将样本从 T*** 映射到它们自身的正则化特征。****

****他们将方法应用于 ***视觉领域，包括数字和面部图像*** ，并展示他们能够 ***生成以前未见过的实体的引人注目的新颖图片，同时保留它们的身份。*******

## ****从照片到表情符号(在报纸上)****

****![](img/2165c87691cf8bb0e295c7c5d06c7929.png)********![](img/1bbd2c420442ed2844f641508d2e10d0.png)****

# ****6.非监督分类****

> ****[*Github*](https://github.com/wvangansbeke/Unsupervised-Classification)****
> 
> ****[论文](https://arxiv.org/abs/2005.12320)****

****U [***无监督分类***](https://github.com/wvangansbeke/Unsupervised-Classification) 是一个 ***无监督学习项目来扫描:学习对没有标签的图像进行分类(ECCV 2020)。*******

*****这个 repo 包含我们论文的 Pytorch 实现:*****

> ****[***扫描:学习对没有标签的图像进行分类***](https://arxiv.org/pdf/2005.12320.pdf)****

****![](img/139b9ae17eedd8d7a79a8f538d81a104.png)********![](img/3c48faf909f8aad28a10ac2334bc4d36.png)****

****该项目可以在缺乏基本事实注释时，自动将**图像**分组到 ***语义有意义的簇中。*****无监督图像分类**的任务仍然是计算机视觉中一个重大而公开的挑战。本文偏离了最近的工作，提倡一种两步方法，其中 ***特征学习和聚类是解耦的。*******

> ****就分类准确性而言，它们远远超过了最先进的方法，特别是在 CIFAR10 上+26.6%，在 cifar 100–20 上+25.0%，在 STL10 上+21.3%。他们的方法是第一个在 ImageNet (1000 类)上表现良好的方法。****

> ****如果你喜欢读这篇文章，我相信我们有相似的兴趣，并且现在/将来会在相似的行业中。所以让我们通过 [LinkedIn](https://www.linkedin.com/in/mrinal-walia-b0981b158/) 和 [Github](https://github.com/abhiwalia15) 联系一下。请不要犹豫发送联系请求！****