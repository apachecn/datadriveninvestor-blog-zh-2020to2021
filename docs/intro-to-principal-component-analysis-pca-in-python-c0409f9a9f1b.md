# Python 中的主成分分析(PCA)简介

> 原文：<https://medium.datadriveninvestor.com/intro-to-principal-component-analysis-pca-in-python-c0409f9a9f1b?source=collection_archive---------10----------------------->

![](img/d0a2167bad247a7baab2a54f4fc2b563.png)

[https://unsplash.com/photos/D9Zow2REm8U](https://unsplash.com/photos/D9Zow2REm8U)

想象你正在处理一个分类问题，你正在对苹果和橘子进行分类。您有一个包含大量要素的数据集，但您知道只有少数要素是重要的。从主观上讲，您可以手动将数据集缩减到您认为会产生良好结果的要素，同时仍然保留大量用于区分苹果和橙子的信息。或者，我们可以使用一个无偏的解决方案，数学，来降低数据集的维度。在这篇文章中，我们将回顾主成分分析(PCA)。PCA 是一种用于降维的算法。

# 什么是 PCA，我们为什么要关心它？

PCA 是一种无监督学习技术，用于减少数据集中的维数。PCA 可以减少数据集中的噪声，并通过减少数据集中的维数来增加数据的解释。现在有一股巨大的推动力去创造更容易被人类理解的模型，而创造更多可解释的模型的一种方法就是从可解释的数据开始。如果有一个包含数百个维度的数据集，很难找到可视化来理解数据，但如果我们可以将维度减少到 5 或 10 个维度，那么绘制趋势图和显示数据的可视化将会非常容易。那么，如何计算 PCA 呢？

# **计算 PCA**

那么，现在我们知道了 PCA 是做什么的，我们如何在数据集上执行 PCA 呢？计算 PCA 有三个步骤。

**第一步:** **将数据标准化，计算训练数据的协方差矩阵**(我们将这个矩阵称为 C)。这产生了一个 dxd 矩阵，其中 d 是维数。

**第二步:求 c 的特征值和特征向量**

**第三步:降低数据的维度。**我们通过取 n 个最大特征值对应的 n 个特征向量来降维。当与数据相乘时，对应于最大特征值的特征向量被称为第一主元。当与数据相乘时，对应于第二大特征值的特征向量被称为第二主元，依此类推。

听起来很简单，但是让我们看一个 PCA 的例子。

# PCA 示例

在这个例子中，我们将使用 MNIST 数据集，一个由 0 到 9 的手写数字组成的数据集(我们将只使用数字 0 和 1)。MNIST 数据集中的每个影像都是 28x 28 的影像，这意味着有 784 个要素。在这个例子中，我将展示我们可以构建一个测试准确率为 99%的分类器，同时在 PCA 算法的步骤中只对 2 个特征进行分类。

## 步骤 1:加载数据并执行数据预处理

数据预处理的一个主要步骤是标准缩放。标准化势在必行，因为 PCA 算法依赖于找到方差最大的特征。如果我们不标准化数据，某些特征可能仅由于特征的权重而具有不成比例的大差异。这可能会导致 PCA 性能不佳。

当使用所有特征对数据进行分类时，我们得到的准确率为 98.6%。让我们看看在对数据集执行降维后，当我们执行分类时会发生什么。

## 第二步:利用主成分分析进行降维

这里，我们将介绍 PCA 算法的步骤。我们首先计算训练数据的协方差矩阵。然后我们找到协方差矩阵的最后两个特征值和特征向量。然后，我们通过乘以训练数据来计算训练数据的第一和第二主成分。测试数据也是如此。在讨论分类算法时，我们将更深入地了解为什么不使用测试数据来计算协方差矩阵、特征值和特征向量。简单的解释是，我们需要一组数据来验证模型的结果。

**PCA 数据可视化:**

![](img/ea0e6987592d4dd86286082effe23c9d.png)

## 第 3 步:使用缩减维度进行分类

对降维后的数据进行分类后，准确率为 99%。与其在 784 个维度上进行分类，我们只能在 2 个维度上进行相当的准确度。我并不是说这种情况会一直发生，但为了同样的准确度，我更愿意对 2 个特征进行分类，而不是 784 个特征。

# 结论

嗯，我希望你学到了很多！我希望您已经了解了 PCA 的重要性以及如何应用它。像往常一样，如果你喜欢这个帖子，一定要打破拍手按钮。如果你喜欢这个帖子，我会鼓励你看看我的其他一些帖子，然后跟着我。下次见！