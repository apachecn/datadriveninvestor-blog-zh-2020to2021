# 为什么是大 O？为什么算法运行时不是大ω或者大θ？

> 原文：<https://medium.datadriveninvestor.com/why-big-o-why-not-big-omega-or-big-theta-with-algorithm-runtime-112792e3283e?source=collection_archive---------5----------------------->

![](img/66aa4426234f74afa9e5bc5d143fe0f1.png)

当我们用任何语言编写程序或算法时，我们经常发现自己在问两个最重要的问题。

1.  运行这个程序需要多长时间？
2.  它需要多少**空间**，这是一个优化的空间吗？

是啊！这个讨论的是大 O &算法的时间复杂度！！

基本上，程序的时间概念取决于各种因素，如

你的机器有多快？你同时在运行其他程序吗？你用的是哪种编程语言？

我们不再分析这些因素，而是直接考虑算法的运行时间是如何随着输入大小的增长而增长的？

我们可以用渐近符号来描述算法的效率，如大 O，大θ(theta)，大ω(Omega)

**大 O(oh)**[Bachmann–Landau 符号](https://en.wikipedia.org/wiki/Big_O_notation) **:** 它描述了运行时间的渐近上界，我们可以说**最坏情况**或算法完成运算所需的最大运行时间。各种类型的大 O 符号也是可用的

*   **O(1)** —常数时间算法。不管 n 的大小，时间是一个常数，这是最快的。
*   **O(log n)**-对数时间算法-它与输入大小的对数成比例增长。
*   **O(n)** —线性时间算法—它随输入大小线性增长。
*   **O(n log n)** — n log n 时间算法—它与输入大小的 N Log N 成比例增长。
*   **O(n^p)** —多项式时间算法——这些算法比 **O(n log n** )算法慢。
*   **O(k^n)** —指数时间算法—它与输入大小的某些因子指数成比例增长。
*   **O(n！)** —阶乘时间算法—它增长到输入大小的阶乘。这是最慢的。

**大ω:**它描述了运行时的渐近下限，并给出了**最佳情况**的复杂度，即算法花费的时间最少。我们很少讨论算法的下界，因为任何算法，特殊情况下一些输入得到ω(1)将是下界。

**大θ:** 它描述了运行时的严格限制(即 O 和ω),并将向您显示算法完成所需的**平均**时间。因此，有一个上限和一个下限，算法执行时间将落在这个范围内。

因此，用大 O 来解释算法的时间复杂度或效率将是比其他算法更好的选择，因为它给出了任何输入所消耗的最大时间。消耗较少代码、时间和空间的程序或代码也将是优化的。

让我们以具有大小为 4 的整数的数组为例，

int arr[] = {5，6，8，15 }；

如果您想要访问数组中的特定元素，那么下限将是**ω(1)**【在数组的第一个索引中查找元素】**，**平均或严格情况将是 **θ(1)** 【在数组的中间索引中查找元素】，最坏情况或上限是 **O(n)** ，即遍历整个数组来访问特定元素。

这篇文章有助于 DS&Algo 初学者理解时间复杂性，并分享你的意见和建议！

***参考文献:***

[1]Gayle Laakmann McDowell 所著的《破解编码采访》一书。

[2][https://www . khanacademy . org/computing/computer-science/algorithms/渐近符号/a/big-o-notation](https://www.khanacademy.org/computing/computer-science/algorithms/asymptotic-notation/a/big-o-notation)

[3][https://dev . to/sherryummen/渐近符号-b-oot-big-o-big-omega-big-theta-49e 7](https://dev.to/sherryummen/asymptotic-notations-b-oot-big-o-big-omega-big-theta-49e7)