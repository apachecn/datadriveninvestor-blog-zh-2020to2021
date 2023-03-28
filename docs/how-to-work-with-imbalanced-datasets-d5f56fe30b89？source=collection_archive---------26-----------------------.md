# 如何处理不平衡的数据集

> 原文：<https://medium.datadriveninvestor.com/how-to-work-with-imbalanced-datasets-d5f56fe30b89?source=collection_archive---------26----------------------->

![](img/9fd928a8bb7b0d000aa6ce50064d557a.png)

Photo by [Form](https://unsplash.com/@theformfitness?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/balance?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

作为数据科学家，我们的主要工作是检测数据中的趋势。例如，它经常在我们不得不进行预测之前就出现了，并且经常作为异常检测的一项独立任务出现。使用传统的数据科学方法，我们必须在一开始(在数据探索阶段)就决定如何处理非常不平衡的数据集。

对于数据科学家新手来说，不平衡的数据集可能看起来像是“梦想成真”，但实际上这是一个真正的障碍。想象一个分类问题，你的多数类占优势，经常超过 99%。这并不罕见——例如，信用卡欺诈检测经常处理类似比例的欺诈案件，其中欺诈案件不到业务的 1%。或者广义上的任何动物性检测——无论是航班延误分析，还是断电，还是医疗诊断错误。在所有这些现实生活的情况下，我们确实有接近 100%的多数类数据集，或者至少大大超过 80%。

[](https://www.datadriveninvestor.com/2019/02/07/8-skills-you-need-to-become-a-data-scientist/) [## 成为数据科学家所需的 8 项技能|数据驱动型投资者

### 数字吓不倒你？没有什么比一张漂亮的 excel 表更令人满意的了？你会说几种语言…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/07/8-skills-you-need-to-become-a-data-scientist/) 

再说一遍，这似乎不是测试的主要问题。但在你开始做模特之前。作为一个试图在不平衡的集合上建立分类器的人，我可以保证接近 100%的极好的准确性结果。但这意味着什么呢？可能不会，尤其是如果我们比较各种型号的性能。即使是基本的，如逻辑回归，也会以惊人的速度表现出色，精度接近 1.0。但是它能提供多少信息呢？不太多，因为我们应该看一个混淆矩阵(我们应该)，我们的假阳性和假阴性将接近零，真阳性和真阴性接近 1.0。

![](img/e915dd6078eb545ce64574326b8aed86.png)

Photo by [Chris Liverani](https://unsplash.com/@chrisliverani?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/graph?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

但是为什么这是个问题呢？嗯，从一个角度来看，我们的模型是理想的，并且以接近 100%的准确率执行。但是，既然我们几乎所有的样本都属于多数类，我们不是偏向多数类吗？关于误报、漏报和召回，我们能知道什么？我们如何比较逻辑回归分类器和随机森林分类器？还是用神经网络？这并不容易，因为我们将对小数的深度负阶进行运算，以判断哪种分类器性能更好。实际上，我们将如何向客户解释模型的特性，并晃动像 0.999999567 这样的数字，以及它与 0.999999998 之间的差异？

从历史上看，数据科学家试图使用复制少数类(复制它，直到它达到多数类的大小)，或多数类的欠采样(移除其部分样本以降低其大小)。虽然少数类复制本身并不太糟糕，但抽样下的多数类却很糟糕，因为从我们的数据集中丢弃可用数据会危及其完整性，并可能无意中删除有价值的数据，从而危及整个故事。

![](img/82154f658db1d5036d38aba51cc24e2f.png)

Photo by [Tyler Milligan](https://unsplash.com/@tyler_milligan_visuals?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/balance?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

如今数据科学的一个黄金标准是 SMOTE，或称之为**S**synthetic**M**in ority**O**versampling**Te**technique。它是基于一种非常类似于 K-最近邻的算法，在这种算法中，我们创建额外的少数集点，将它们放置在现有集点的附近。它确实工作得很好，并且有助于更好地定义问题。

SMOTE 有几种变体:

*   SMOTE Borderline-1，我们在这里查看新点，并认为它们来自相反的职业。
*   SMOTE Borderline-2 将这些点视为可能属于这两个类中的任何一个。
*   SMOTE Tomek 评估最近邻但来自不同类的点，并且为了澄清类边界，它确实移除了属于多数类的配对点。

![](img/b131a4795588eb4a50fbc717a392babe.png)

Photo by [Alev Takil](https://unsplash.com/@alevtakil?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/neighbor?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

当然，SMOTE 并不是处理不平衡数据的唯一技术。但它只是比简单的简单欠采样/过采样稍微复杂一点，从理论角度来看更有意义。与其他方法相比，它也非常直观和相对简单，因此它非常受欢迎。