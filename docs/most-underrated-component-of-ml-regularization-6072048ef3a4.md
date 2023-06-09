# 最被低估的 ML 组成部分:正规化

> 原文：<https://medium.datadriveninvestor.com/most-underrated-component-of-ml-regularization-6072048ef3a4?source=collection_archive---------4----------------------->

## 用正则化及其类型的数学知识强化你的机器学习模型

![](img/3ad5a7012409e354bd962d452a39db6a.png)

Photo by [ThisisEngineering RAEng](https://unsplash.com/@thisisengineering?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/mathematics?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

大家好，这个博客包含了你需要知道的关于正规化的所有信息。这个博客是关于正则化背后的数学直觉及其在 python 中的实现。这个博客是专门为那些发现正规化难以消化的新手准备的。对于任何机器学习爱好者来说，理解数学直觉和后台工作比仅仅实现模型更重要。

> 我看到很多博客都在回答为什么需要正规化，正规化有什么作用，但是没有回答如何正规化？

# 目录

1.  [什么是过度拟合？](https://medium.com/p/6072048ef3a4#464e)
2.  [正规化](https://medium.com/p/6072048ef3a4#4043)
3.  [实现](https://medium.com/p/6072048ef3a4#a79d)
4.  [正则化率怎么用？](https://medium.com/p/6072048ef3a4#f4a8)
5.  [结束注释](https://medium.com/p/6072048ef3a4#ec20)

# **什么是过度拟合？**

每个数据集都包含一定量的噪声。当你的模型试图拟合你的数据时，你就会陷入过度拟合。过度拟合试图达到每个噪声数据，从而增加了复杂性。过度拟合的后果是模型的训练精度太高，而测试精度太低。这意味着您的模型将无法预测新的/实时数据。

![](img/9b7068464539a1ef3f74267fd70f5615.png)

Image by owner

**避免过度拟合的一种方法是惩罚权重/系数，这正是正则化所做的。**

# **正规化**

这是一种回归形式，将估计的系数约束或缩小到零。换句话说，*这种技术不鼓励学习更复杂或更灵活的模型，以避免过度拟合的风险。*

*主要有两种正规化:*

## ***1。*岭回归**

我将通过岭回归来解释广义数学直觉，除了正则项之外，岭回归对于其他类型也是一样的。假设你正在进行简单的线性回归。

因此，假设的公式是:

![](img/7a1bcaf1cec3aba0f2489ce71589be98.png)

损失函数为:

![](img/51360e0e27c7d6c6d630982d01733d66.png)

这里，J(theta)/Loss 是模型的损失函数。它不同于普通的损失函数，因为它加入了一个正则项来惩罚最终的系数。λ是正则化率。

这里，正则项是λ乘以系数平方的总和。因此，添加正则化项，与正常成本函数相比增加了成本函数

*注意:正常成本函数与上图所示相同，但没有正则项，所以不要混淆。*

*在计算成本后的每个模型中，我们使用任何优化算法来提高我们的权重。在这种情况下，我们将使用梯度下降进行优化。*

梯度下降是寻找最优权重/系数的过程，该最优权重/系数又用于预测新的样本/数据。

![](img/18904466792e7251f007e96ffb6adc90.png)

在梯度下降中，当学习率(α)乘以成本函数的导数(微分)并从旧的权重中扣除时，获得新的权重。对于权重被同时优化的多次迭代，该过程发生。

正如我们之前看到的，添加正则化项增加了成本函数，因此当成本函数的导数从梯度下降中的权重中扣除时，新的权重将比我们使用正常成本函数(没有正则化)获得的权重小得多。

> 简而言之，如果没有正则化的成本函数被称为 X，而有正则化的成本函数被称为 Y，则显然添加了 Y>X 作为正则化项。此外，使用带有正则化的成本函数计算的新权重是 W1，使用不带正则化的成本函数计算的新权重是 W2，而 W2>W1。

回到岭回归，岭回归器的缺点是它可以将系数/权重降低到最小阈值，但不能将其降低到零。出现多重共线性时，使用岭回归。多重共线性意味着要素相互依赖。

## **2。拉索回归(L1 回归)**

![](img/7eac51392501e7bf09fbc5e05c4d10cd.png)

Lasso 遵循与上述岭回归中相同的数学直觉。唯一的区别是正则项。正则项是正则化速率乘以权重模数的总和。套索回归克服了岭回归的缺点，它不仅惩罚系数，而且如果与因变量不相关，还将系数设置为零。

因此，Lasso 回归也可以用作特征选择，它属于特征选择的嵌入式方法。

# **实施**

```
from sklearn.linear_model import Lasso
model = Lasso(alpha=0.6)
model.fit(Xtrain, ytrain)
ypred = model.predict(Xtest, ytest)
```

同样，sklearn 库为 Ridge 提供了功能。它还扩展到 RidgeCV 和 LassoCV。

# **正则化率怎么用？**

如果您面临以下情况，请实施这些回归技术:

(1)过拟合→尽量提高正则化率。

(2)欠拟合→尽量降低正则化率。

# **结束注释**

在本文中，我们对正则化有了一个大致的了解。实际上，这个概念要比这深刻得多。

你觉得这篇文章有用吗？请在下面的评论框中告诉我们你对这篇文章的想法。

乡亲们，祝你们有美好的一天:)