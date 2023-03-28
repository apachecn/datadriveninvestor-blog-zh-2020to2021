# 用 ML 将你的应用货币化

> 原文：<https://medium.datadriveninvestor.com/monetizing-your-application-with-ml-767f97e62943?source=collection_archive---------34----------------------->

![](img/98304967fe32f0034a7f0412d8b21b67.png)

Photo by [Sharon McCutcheon](https://unsplash.com/@sharonmccutcheon?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

令人惊讶的是，现在的应用商店里有这么多可用的应用。事实上，有这么多，它已经变得很难穿过噪音，并建立一个存在。如今，应用商店中有一小部分应用使用机器学习(ML)，但这种情况正在改变。

机器学习是 app 开发的未来。您必须学会将 ML 性能设计到应用程序中，包括考虑模型大小、模型准确性和预测延迟。

[](https://www.datadriveninvestor.com/2019/02/08/machine-learning-in-finance/) [## 金融中的机器学习|数据驱动的投资者

### 在我们讲述一些机器学习金融应用之前，我们先来了解一下什么是机器学习。机器…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/08/machine-learning-in-finance/) 

这最后两个[ML-gate](http://blog.selcote.com/2020/01/04/think-differently-needs-a-new-data-driven-methodology/)(*模型集成/部署*)代表 ML 开发管道的“业务端”。它们代表了管道中的最后步骤，在这些步骤中，您会意识到在处理数据、算法和模型的早期阶段所做的所有艰苦工作的好处。模型集成和部署是最明显的阶段，这些阶段使您能够将应用程序货币化。

# 管理模型

在 ML 应用程序开发中，模型是你的关键资产之一。您必须仔细考虑如何处理模型，包括

*   模型规模考虑因素
*   模型版本控制
*   更新模型

模型可能会变得非常大，您需要首先确保您创建的模型可以物理地驻留在您的目标设备上。

# 设备限制

当您使用来自云提供商的 ML 模型时，您只需依靠网络连接和云提供商 API 来访问模型并做出预测。[在设备上存储预建模型](http://blog.selcote.com/2020/02/12/solution-for-running-machine-learning-on-the-edge/)是一种不同的方法，需要你理解目标设备的局限性。

在 Android 设备上看到大小超过 300 MB 的应用程序是很常见的。这并不意味着您应该创建尺寸相匹配的模型。庞大的模型很难管理。大型模型的主要缺点是加载它们所花费的时间。对于 Android，最好的方法是在后台线程上加载模型，并且您希望加载操作在几秒钟内完成。

本文中[讨论的每种分类算法的模型精度、模型训练和模型测试时间各不相同。还有一个额外的因素，模型大小，这是同样重要的考虑。](http://blog.selcote.com/2020/01/31/7-ml-algorithms-will-solve-95-of-the-problems/)