# 工业中机器学习的三大挑战是什么

> 原文：<https://medium.datadriveninvestor.com/what-are-the-top-3-challenges-for-machine-learning-in-industry-6cf0a9bb1250?source=collection_archive---------17----------------------->

![](img/516fe330980ee4e42278de48f5a5850f.png)

Photo by [Olav Ahrens Røtne](https://unsplash.com/@olav_ahrens?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

今天，机器学习已经彻底改变了许多行业。

它可以帮助我们识别物体，排列事物，甚至理解你在说什么。但它仍处于早期阶段，面临许多挑战。

在这里，我将列出当今机器学习从研究到工业的三个主要挑战，并告诉你我们目前对每个挑战的解决方案。

以下是这些关键挑战:

1.  缺乏训练数据
2.  培训数据和生产数据之间的差异
3.  模型可扩展性

因此，我们将逐一研究这些问题。

最后，我会列出一些资源供您浏览，以便更好地理解这些解决方案。

## 缺乏训练数据

第一个是缺乏训练数据。数据是任何机器学习项目的核心。

然而，获得标记数据通常非常困难和昂贵。如何在没有大量数据的情况下训练一个模型，是当今非常热门的话题。

**迁移学习**就是解决这个问题的方法之一。它使模型能够利用以前学习的任务中的知识，并将它们应用到新的相关任务中。

> 例如，在图像分类任务中，很少有人会从零开始训练一个完整的**卷积神经网络**，这通常需要数百万张标记图像。相反，通常使用预先训练的模型，并在目标域上对它们进行微调。

Transfer Learning Video by Kaggle

自监督表示学习是解决数据缺乏问题的另一种方法。它为更好地利用大量未标记的数据提供了巨大的机会。

这里有一个非常著名的语言建模的例子。如果有一个句子，但是里面有一些缺字。

> 《帕特里夏》是一部法国小说

你如何能填写那些丢失的单词。这个想法是通过学习过去和未来的知识来预测缺失的单词。

语言的表征也是在这个过程中习得的。谷歌使用这种技术比以往任何时候都更好地理解了搜索，这带来了搜索历史上最大的飞跃之一。

## 培训数据和生产数据之间的差异

第二个挑战是，您的培训数据和生产数据之间通常存在一些差异。

有时候，模型在您的原型环境中工作得很好，但是在真实世界的情况中却不能通用化。

让我们来看几个例子:

*   这种模式在一个国家可能行得通，但由于地理差异，在另一个国家可能行不通。
*   由于季节差异，该模型在冬季可能有效，但在夏季可能失效。
*   该模型可能在移动设备上运行良好，但由于用户行为差异，在桌面上可能会失败，因此当您开发您的模型时。

How To Prepare a Dataset: By Siraj Raval

当你收集训练数据时，你需要非常小心。使其尽可能接近您的目标域。一旦你的模型过时了，就要不断更新。

## 模型可扩展性

最后但并非最不重要的挑战是关于模型的可伸缩性。对于工业中的许多项目来说，这是一个大问题。

作为一名机器学习科学家，你需要确保模型能够足够快地运行，并且模型大小足够小，这对于很多任务来说通常是一个很大的挑战。

一种可能的解决方案是使用训练后量化。

> 训练后量化是一种可以减少模型大小的转换技术。

Fundamentals of quantization aware training using TensorFlow/Keras API

同时，它还可以改善 CPU 和硬件加速器延迟，而模型准确性几乎没有下降。

## 资源:

*   [转移学习:吴恩达](https://www.youtube.com/watch?v=yofjFQddwHE)
*   [转移学习:Kaggle](https://www.youtube.com/watch?v=mPFq5KMxKVw)
*   [轻松准备数据集的最佳方式:Siraj Raval](https://www.youtube.com/watch?v=0xVqLJe9_CY)
*   [tensor flow 内部:量化感知训练(通过 TensorFlow)](https://www.youtube.com/watch?v=Q1oBXdizXwI)
*   [tensor flow Lite(TF Lite)中的训练后量化](https://www.youtube.com/watch?v=IuyTC-_otGw)

# 你的下一步是什么？

> 如果你喜欢这篇文章，如果你点击下面的“推荐”会很有帮助！
> 在 [Twitter](https://twitter.com/imPraveenPareek) 、 [LinkedIn](https://www.linkedin.com/in/praveenpareek/) 和 [Medium](https://praveen-pareek.medium.com/) 上关注我
> 
> **在这里阅读我所有的帖子/文章:**[**Praveen Pareek**](https://praveen-pareek.medium.com/)

[](https://medium.com/datadriveninvestor/i-have-learned-syntax-now-what-to-boost-up-a9711c5685dc) [## 我已经学了语法，现在该学些什么？

### 你一定在开始学习计算机编程之后，脑子里也出现过类似的问题。

medium.com](https://medium.com/datadriveninvestor/i-have-learned-syntax-now-what-to-boost-up-a9711c5685dc)