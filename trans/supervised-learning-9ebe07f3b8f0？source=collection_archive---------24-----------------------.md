# 机器学习——监督学习

> 原文：<https://medium.datadriveninvestor.com/supervised-learning-9ebe07f3b8f0?source=collection_archive---------24----------------------->

## 分类、回归、损失函数和参数更新

![](img/d26b1146c6f9578f948a49526824c60b.png)

Photo by [Yannis H](https://unsplash.com/@yanphotobook?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/teaching?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

在这篇博文中，我们将讨论监督学习和它所涵盖的一类问题。在进入监督学习之前，我强烈建议浏览一下机器学习术语，比如什么是数据集、目标、预测器、模型等等。来自[之前的博文](https://mayurji.github.io/machine-learning/)。

# 📌监督观察

在机器学习中，如果一个标签或目标可用于观察，那么这样的观察被称为**监督观察**。从技术角度来看，给定一组与一组标签或结果 Y 相关联的数据点 X，我们尝试构建一个模型，该模型学习从 *x.* 预测 *y*

![](img/9190c8bf5d59fe87b1bddbfc0027a11b.png)

# 📌预测类型

考虑观察动物，当我们看到一个动物，在我们给它贴上狗或猫的标签之前，我们用我们的超速度意识，我们检查像腿的数量、眼睛、头、身体、胡须等特征，然后给它贴上动物 A、B、C 等标签。

![](img/6f556cd465edd48be322880dcceb31c2.png)

Figure 1: Supervised Learning — Classification Based Problem

分类动物或识别物体或识别邮件是否是垃圾邮件，所有这些问题被称为基于**分类**的机器学习问题。因此，这里我们将预测值/观测值预测为 N 个有限类别中的一个**。例子-逻辑回归，SVM 等。**

![](img/fe8fbb807632e9d4be50d9c2a563cc2f.png)

Figure 2: Supervised Learning — Regression Based Problem

现在，考虑预测股票价格，我们知道股票价格在本质上是不稳定的，这意味着它每分钟都在变化。价格的下降或上升不是绝对的，比如+5/+10 或-10/-5，而是以小数形式变化的连续值。

像股票价格预测、房价预测等问题都属于一类叫做**回归**的问题。因此，在这里我们把预测因子/观测值看作是**一个无限连续的值。**示例—线性回归、基于决策树的回归等。

# 📌模型类型

![](img/fb0cf402e637834dd4f62da840af1f49.png)

Figure 3: Supervised Learning — Discriminative and Generative Model

一个模型可以学习用两种不同的方法对动物进行分类或预测股票价格。

首先， ***判别*** 模型， ***其中模型学习建立一个决策边界，基于该边界它将预测器分类为目标 A 或 b。***判别建模试图直接预测给定 x 的 y。示例- ***线性回归。***

![](img/15e47ef4f167e9349263946cc277c16b.png)

Discriminative Model

二、 ***生成式*** 模型、 ***其中模型基于给定的 y 从预测器 x 的概率分布中学习然后推导出给定的目标 y x***。**例子-*朴素贝叶斯。***

![](img/fc4eea18ec7a97d97db482c920ba14a7.png)

Generative Model

因此，我们可以基于判别方法或生成方法来执行分类或回归。

# 📌损失函数

损失函数是监督学习的关键组成部分之一。每个机器学习算法都有一个损失函数，帮助学习预测器的模式，然后估计目标 *y* 。损失函数将估计的 y_hat 作为真实数据点的输入，并与真实目标 y 进行比较，找出它们之间的差异。

考虑一个线性回归问题，损失函数的作用是在预测值之间产生最佳拟合线，这样当一个新的看不见的数据点被放入回归线时，它最多尝试识别看不见的数据点的 y 的最佳估计。对于线性回归，广泛使用的损失函数是均方误差。之所以称之为误差，是因为估计值偏离了真实值。

![](img/7fa8a2a6f6ee7ea93b5df518ecf846c2.png)

Figure 4: Loss Function — Mean Squared Error

> **最小二乘法**是一种统计**程序**，通过最小化绘制曲线上各点的偏移量或残差的总和来找到一组数据点的最佳拟合。**最小二乘**回归是**用来**预测因变量的行为。

**常见损失函数**

*   均方误差
*   绝对平均误差
*   物流损失
*   交叉熵损失
*   铰链损耗

# 📌参数更新θ

当模型试图学习或识别数据中的模式时，它会在学习过程中保留一些参考点。每次模型看到新数据时，这些参考点都会更新。从技术上讲，这些参考点被称为学习方程的**系数**。

在线性回归中，模型在训练模型时学习这些参数，并对其进行更新，从而减少损失，并且使估计的 y 接近真实的 y。参数更新是开发概化模型的关键因素。学习率是一个超参数，被调整用于找到合适的更新。

![](img/9df34a80a93303db0fd574bdfe35e1c2.png)

Figure 4: Parameter Update — Gradient Descent — CS229

广泛用于参数更新的算法是**梯度下降**。梯度下降使用偏导数来更新参数 **θ** 。类似地，还有其他方法来查找参数更新，如似然法和牛顿算法。

# 📌估价

在监督学习中，在分类和回归问题中，评估是相当简单的。由于数据集被标记，我们可以从我们的数据集创建一个单独的测试集和验证集，并使用训练好的模型来预测它在测试集上分类的准确性，使用准确度、精确度、召回率、f1 分数等指标。

在回归问题中，我们可以保持模型允许的误差幅度，并用 R 平方、调整 R 平方、MSE 等来度量。我已经在[机器学习概念](https://mayurji.github.io/machine-learning/2020-11-06-machine-learning-III)中谈到过这个话题。

❌ **警告** ❌从不使用训练集来评估模型！

我希望我已经涵盖了理解监督学习所需的所有基础知识。接下来，我们将深入研究无监督学习。

感谢阅读。如果你喜欢阅读我的文章，请查看[数学+计算=人工智能](https://mayurji.github.io/data-structure-algorithms/)获取更多文章。

## 在 [LinkedIn](https://www.linkedin.com/in/mayur-jain-ds) 和 [Twitter](https://twitter.com/mayur__22) 上与我联系🐅 ✋

## **参考**

CS229 机器学习—斯坦福大学