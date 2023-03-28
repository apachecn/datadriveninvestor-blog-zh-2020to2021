# 分离分类超平面

> 原文：<https://medium.datadriveninvestor.com/separating-hyperplanes-for-classification-52de4a1c5321?source=collection_archive---------14----------------------->

![](img/47d908eb78489db2ccee4e47e6e2d73f.png)

Photo by [Mihály Köles](https://unsplash.com/@mihaly_koles?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

## 机器学习理论

## 深度学习和支持向量机的起源

分离超平面过程构造线性决策边界，该边界显式地尝试尽可能将数据分成不同的类。有了它们，我们将定义支持向量分类器。

有时，在上一篇文章中解释的 LDA 和逻辑回归[会产生可避免的错误，这可以使用以下方法解决。](https://medium.com/datadriveninvestor/the-basic-methods-for-classification-9c10a961b0ee)

# 罗森布拉特感知机

该算法是现代深度学习进展的前身，它试图通过最小化误分类点到决策边界的距离来寻找一个分离超平面。目标是最小化以下功能:

![](img/835491b4625cad551516bcf3bc2ec7f5.png)

Function to minimize, self-generated.

其中 ***M*** 索引误分类点的集合。该数量是非负的，并且与错误分类的点到由 ***β^T x + β0 = 0 定义的决策边界之间的距离成比例。*** 如果我们假设 M 是固定的，则梯度由下式给出:

![](img/ac31b9c417be2462825c16dcb859c64c.png)

Gradient functions, self-generated.

该算法使用随机梯度下降来最小化分段线性准则。这意味着我们在每个输入值之后在负梯度方向上计算一步，而不是在处理所有数据之后计算。因此，错误分类的数据值以某种顺序被访问，并且 ***β*** 被更新为:

![](img/787e9b212981079ee7da708c7a4d2967.png)

Beta update function, self-generated.

其中 p 是学习率，必须根据数据来选择。如果存在可分离的超平面解，则该算法收敛于它，但是它有一些问题:

*   当数据是可分的时，有许多解，找到的解取决于起始值。
*   寻找解决方案的有限步骤可能是巨大的。班级之间的差距越小，找到它的时间就越长。
*   当数据不可分时，算法将不会收敛，并开始在可能的最优值中循环。

通过创建基函数和增加原始空间，我们可以解决第二点，通过向数据添加约束，我们可以解决第一点。

# 最优分离超平面，支持向量分类器

最优分离超平面将两个类分开，并最大化每个类到闭合点的距离。有了这些，我们可以通过最大化两个类之间的差额来实现唯一的解决方案。

优化问题是:

![](img/b34b75dc8ba60276b7ba970000e703d9.png)

SVC optimization problem, self-generated.

在这些条件下，我们确保所有点距离决策边界的距离至少为 M。我们可以用 as 条件去掉**|*| |β| | = 1***约束:

![](img/51f7bef34957d78231458dde7fab97bf.png)

Constraint conditions, self-generated.

由于对于任何满足这些不等式的***【β】***和***【β0】***，任何正比例倍数也满足这些不等式，所以，我们可以设 ***||β||= 1/M.***

![](img/a5e4640a0e81d58492ac25c69ab3c5a1.png)

Optimization problem simplified, self-generated.

然后，我们利用拉格朗日函数来解决最小化问题:

![](img/2eb9f67fc6ec288713eb42966905e626.png)

LaGrange function of the minimization problem, self-generated.

将导数设置为 0:

![](img/b8d44421d11c58c75db96c5a53380a8a.png)

LeGrange derivatives, self-generated.

将它们减去 Lp，我们得到 Wolfe 对偶:

![](img/ccc529d5ac7012a94a9acd3220a3104a.png)

Wolfe dual, self-generated.

通过最大化 ***L_D*** ，我们找到了解，并且必须满足卡鲁什-昆-塔克条件。

![](img/40b169a28ff9c134a8497c07151234a1.png)

Karush-Khun-Tucker conditions last condition, self-generated.

现在我们可以说

![](img/91952d74f9c8996b89d48a499da9333e.png)

解决方案向量仅使用决策实验室中的值来定义，这些值被定义为支持点。

# 结论

仅使用决策实验室值，该解决方案对模型错误设定更具鲁棒性。与之前解释的模型相比，当数据不是高斯型时更好。如果是高斯分布，LDA 会更快，性能更好。

当数据不可分时，没有可行的模型，您可以尝试使用基变换来扩大空间，但这会导致过拟合问题。

这是我的第 38 篇文章，我将在 GitHub、Twitter 和 Medium ( [Adrià Serra](https://medium.com/u/48c8d3ce491d?source=post_page-----7053db93ba6----------------------) )上发布这个挑战的进展。

[https://twitter.com/CrunchyML](https://twitter.com/CrunchyML)