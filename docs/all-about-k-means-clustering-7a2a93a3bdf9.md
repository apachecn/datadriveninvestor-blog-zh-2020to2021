# 关于“K 均值”聚类的所有内容

> 原文：<https://medium.datadriveninvestor.com/all-about-k-means-clustering-7a2a93a3bdf9?source=collection_archive---------7----------------------->

![](img/7cee768f2ab0fd7587c1e495543be5c8.png)

在这篇文章中，我们将讨论**K-均值聚类**！！！

我们将学习如何对可以放在一条线上的样本进行分组。在 X-Y 图上，甚至在热图上，最后，我们还将讨论**如何为 k 选择最佳值**

想象一下，你有一些数据，你可以画在一条线上，你知道你需要把它分成 3 组。也许它们是对 3 种不同类型的肿瘤或其他细胞类型的测量。

![](img/fe4198dc67483ed0c7ae099fddf9902e.png)

在这种情况下，数据形成三个相对明显的集群。但是，**与其依靠我们的眼睛，不如让我们看看能否让计算机识别出**相同的 3 个星团。

![](img/7682543a05d350d0c9ab4cbeb4043752.png)

为此，我们将使用 K 均值聚类。

我们将从尚未聚类的原始数据开始。

**步骤 1:** 选择您想要在数据中识别的聚类数。这就是“K-means 聚类”中的“K”。

![](img/5bbb058fb96c412e566dc2321c36af1a.png)

在这种情况下，我们将选择 K=3。也就是说，我们要识别 3 个集群。

有一种更好的方法来选择“K”的值，但是我们将在后面讨论。

[](https://www.datadriveninvestor.com/2020/02/19/cognitive-computing-a-skill-set-widely-considered-to-be-the-most-vital-manifestation-of-artificial-intelligence/) [## 认知计算——一套被广泛认为是……

### 作为它的用户，我们已经习惯了科技。这些天几乎没有什么是司空见惯的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/19/cognitive-computing-a-skill-set-widely-considered-to-be-the-most-vital-manifestation-of-artificial-intelligence/) 

**第二步:**随机选择 3 个不同的数据点。这些是最初的集群。

![](img/d39abf68fdbcc20cd3ed498b42c00f44.png)

**步骤 3:** 测量第一个点和三个初始聚类之间的距离。

![](img/943ab8fc9572dc6bb8b13e69c9a35817.png)

**步骤 4:** 将第一个点分配给最近的聚类。在这种情况下，最近的星团是蓝色星团。

![](img/dad7a311cd26f0747274336b36740de9.png)

现在对下一点做同样的事情。

我们测量距离…将该点分配给最近的集群。

![](img/a8b46eb90f5878cc604a077183b57e66.png)![](img/c242913d2be0fa7404c0e65632b16275.png)

现在我们弄清楚第三个点属于哪个集群。

我们测量距离…并将该点分配给最近的群集。

![](img/192fd6960430ef32fa8574ea6a534908.png)

其余的这些点离橙色集群最近，所以它们也将进入那个集群。

![](img/0a99d9e8c82e14448d0c42e41c32e3e6.png)

现在所有的点都在集群中，我们继续…

**第五步**:计算每个聚类的**均值**。

![](img/d13a2a4f6dc99ccad6ab959045374528.png)

然后，我们使用平均值重复我们刚刚做的事情(测量和聚类)**。**

![](img/76c6551e860674181a46d599c648b1e8.png)![](img/295d07cc871c23f8148716544707c0a5.png)![](img/cf1d851cfb7da1444f8e824a211d0735.png)![](img/5556e070e8600280471ee177bcd5e1f7.png)![](img/8868944e6ef987cbc4091c241bc9c559.png)

***由于聚类在最后一次迭代中没有任何变化，我们完成了…***

与我们目测的结果相比，K-means 聚类非常糟糕。

我们可以通过累加每个聚类内的变化来评估聚类的质量。

![](img/e3c1589ed44367f9ddf32ae3f52d30b9.png)

这是星团内的总变化量。

![](img/b28fb612e2ae5d6eeb9158d6cefef8c4.png)

由于 K-means 聚类不能“看到”最佳聚类，它唯一的选择是跟踪这些聚类，以及它们的**总方差**，并以不同的起点重新做整个事情。

所以，我们又回到了起点。

![](img/93fb05e506e0ea52190f1636da888285.png)![](img/32b4e2417ee2fa80ea391124f480c2d3.png)

k 均值聚类**挑选** 3 个初始聚类…然后**聚类**所有剩余的点，计算每个聚类的**均值**，然后**基于**新均值**重新聚类**。它**重复**直到簇不再改变。

![](img/a8d83a9d971a0bc4609f83473c18899b.png)![](img/57a5d3e14c7d22d3c7eb697764fcfcca.png)![](img/bc2c299ef2766c620a3d058ed95a2254.png)![](img/49cc104740561b9d50d800ccce4507c9.png)

既然数据已经聚类，我们就要对每个聚类内的变化进行求和。

![](img/80f2fd276b3f1e0bd6cc46e1693aa910.png)

然后再做一遍…

![](img/48c3d98aae6c3f47bd324113e055e443.png)

此时，K-means 聚类知道第二次聚类是迄今为止最好的聚类。但是它不知道它是否是整体上最好的，所以它会再做几个集群(你让它做多少它就做多少)，然后如果它仍然是最好的，就返回那个集群。

![](img/ece7c471ce6acc1acdc741bbdf7585cd.png)

**问题:**怎么算出“K”用什么值？

有了这个数据，很明显我们应该把 K 设为 3，但其他时候就不那么清楚了。

![](img/6c2ec55764047bdd8354ab84e358c1de.png)

决定的一个方法是尝试不同的 k 值。

从 K = 1 开始。

K = 1 是最坏的情况。我们可以用总变差来量化它的“坏”。

![](img/eb6acd1a6413a4c4edc00f8a8ffa1465.png)

现在试试 K = 2。

K = 2 更好，我们可以通过比较 2 个集群内的总变化与 K = 1 来量化好多少。

![](img/68e59827aaa77c0e5c788278c6c52b7a.png)![](img/7617e24385fbc4d6784219db9519e24e.png)

现在试试 K = 3。

K = 3 就更好了！我们可以通过将 3 个聚类内的总变化与 K = 2 进行比较来量化好多少。

![](img/05b1a9fed466b263ff81e07a05fa7785.png)![](img/11e7be1d2a89330860db403f5d7e5556.png)![](img/a4399c3302071518a7b881acb0c08210.png)

现在试试 K = 4。

![](img/30c759e27083c7bc78b024bad85b76b1.png)

每个聚类内的总变化小于 K = 3 时的总变化。

![](img/1c41efe41f43eecc48a324cd247a93cb.png)

每次我们添加一个新的聚类，每个聚类内的总变化都比以前小。而当每个聚类只有一个点时，变差= 0。

然而，如果我们画出每 K 值的方差减少量，那么当 K = 3 时，方差会大幅减少，但在此之后，方差不会很快下降。

![](img/9607210ba222318b877c43869a12863b.png)

这叫做一个**“肘图”**，在图中找到“肘”就可以挑选**“K”**。

**问题:****K-means**聚类和**层次聚类**有什么不同？

***K-means 聚类专门尝试将数据放入你告诉它的聚类数中。***

***层次聚类只是告诉你，两两之间，哪两个东西最相似。***

![](img/e51904f5a6925d074402d327c842895e.png)![](img/f6e5a0134bf91dd2bd128d7ceb349469.png)

**问题**:如果我们的数据没有绘制在数字线上会怎么样？

就像以前一样，你随机选择三个点…

我们用欧几里德距离。在二维空间中，欧几里得距离与勾股定理是一回事。

![](img/3e61f24d24b4553cc3b4e555af1bd0d6.png)![](img/8eb01b7ee986115b5b4c4c1dd90e303b.png)

然后，就像之前一样，我们将该点分配给最近的簇。

和以前一样，我们计算每个聚类的中心，然后重新聚类…

虽然这看起来不错，但计算机直到进行几次聚类后才知道。

![](img/8d1a2ed4c55a43adca7be80321219474.png)![](img/892b48a1c4517f6b98d140bc3227d5cb.png)![](img/c31f6857e1e64dfcf61d52e058c3212d.png)![](img/d348cfdc7533efb88564ee58a0903bb5.png)

问:如果我的数据是热图，该怎么办？

好吧，如果我们只有两个样本，我们可以把它们重命名为“X”和“Y”。然后将数据绘制成 X/Y 图。然后我们就可以像以前一样聚在一起了！

注意:我们实际上不需要绘制数据来进行聚类。我们只需要计算事物之间的距离。

即使我们有 2 个样本，或 2 个轴，欧几里德距离是:sqrt(x2 + y2)。

当我们有 3 个样本或 3 个轴时，欧几里德距离是:sqrt(x2 + y2 + z2)。

当我们有 4 个样本或 4 个轴时，欧几里德距离是:sqrt(x2 + y2 + z2 + p2)。

等等。等等。等等。

![](img/280186fd0a0223e83887d001ebaa4595.png)

> [嘿！我们已经到了激动人心的博客文章的结尾。如果你喜欢这篇博文，并想了解更多，请在这个平台上**关注我**。](https://medium.com/@praveen.pareek)

**好吧！请在另一个时间收听另一篇激动人心的博文。**