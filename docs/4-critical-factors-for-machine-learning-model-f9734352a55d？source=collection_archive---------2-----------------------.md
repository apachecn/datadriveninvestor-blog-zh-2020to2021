# 机器学习模型的 4 个关键因素

> 原文：<https://medium.datadriveninvestor.com/4-critical-factors-for-machine-learning-model-f9734352a55d?source=collection_archive---------2----------------------->

![](img/e9d134f834faa0947a1e8dedf5ade73e.png)

Photo by Andrew Neel on Unsplash

在机器学习应用开发中，模型是你的关键资产之一。您必须仔细考虑如何处理模型，因为它可能会变得非常大，并且您需要首先确保您创建的模型可以物理地驻留在您的目标设备上。

[](https://www.datadriveninvestor.com/2019/02/18/the-challenge-of-forex-trading-for-machine-learning/) [## 机器学习的外汇交易挑战|数据驱动的投资者

### 机器学习是人工智能的一个分支，之前占据了很多头条。人们是…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/18/the-challenge-of-forex-trading-for-machine-learning/) 

在本文中，我将开发四个因素，您必须在模型集成阶段考虑这些因素。这些因素是训练时间，测试时间，准确性和大小。

# 模型训练时间

训练时间很重要。然而，当您在边缘的应用程序中部署静态模型时，优先级较低，因为您总是可以应用更多的资源(甚至可能在云中)来训练模型。

# 模型测试时间

如果算法生成的复杂模型需要相对较长的测试时间，这可能会导致设备在进行预测时出现延迟或性能问题。

# 模型精度

模型精度必须足以产生明确定义的问题所需的结果。

# 模型尺寸

当将预训练的机器学习模型部署到设备上时，模型的大小必须与目标设备的内存和处理资源一致。

为了了解这些因素是如何相互关联的，您可以执行一个**敏感性分析**，这是一个金融模型，它根据称为输入变量的其他变量的变化来确定目标变量如何受到影响。

考虑一下 [**随机森林算法**](http://blog.selcote.com/2020/01/31/7-ml-algorithms-will-solve-95-of-the-problems/) 。你知道迭代的次数，I，是一个关键变量，用来决定算法产生多少树。更多的迭代意味着更多的树，这会导致以下结果:

*   更高的精确度
*   更长的创建时间
*   更大的模型尺寸