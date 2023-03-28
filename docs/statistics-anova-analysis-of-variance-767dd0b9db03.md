# 统计学:ANOVA(方差分析)

> 原文：<https://medium.datadriveninvestor.com/statistics-anova-analysis-of-variance-767dd0b9db03?source=collection_archive---------4----------------------->

![](img/52d9fd1c2d9b651327bd1bf8ead6ff88.png)

image:SRM University

# **概述:**

统计学中的 Anova(此处特指单向 ANOVA)检验用于确定三个或三个以上独立(不相关)组的平均值之间是否存在任何统计学上的显著差异，并基于任何检验得出结论。

一个 **ANOVA** 测试是一种发现调查或实验结果是否有意义的方法。

让我们通过设置零假设和替代假设来理解方差分析

![](img/9a36437e6a0466cc524765d86455b34c.png)

## **计算方差分析的步骤:**

假设我们想知道每组有三个学生时，每组阅读的书籍数量是否相同。

![](img/3070b70339eeb6422908a53236a917b9.png)

**第一步:求大平均值**

其两步过程:

**一个**。求每组的总和除以每组中值的总数。

![](img/4179e555146ba97f24adcfb11b340eaa.png)![](img/6eb9b2afe7bb2bd3a4c6436949c8e4f6.png)![](img/a9f53d95c826c31f42a265dad1bff733.png)

**B** 。将所有组相加，然后除以组数，得到总平均值。

![](img/40f0cb611de65c06f9ca508c868ac4fc.png)

**第二步:计算组间和组内的 DOF(自由度)。**

**自由度(之间)**:K-1 = 3–1 = 2

其中 K 是组的数量

**自由度(以内):N-K = 9–3 = 6**

其中 N 是考虑所有组的值的总数

**第三步:找到要比较的 F(临界)值。检查下面的 F-分布表**

![](img/a1950e5be9e619aed0baeebe718cb19a.png)

这里考虑的显著性水平是 0.05

**F(临界)** =F(DOF(间)，DOF(内))= **5.14**

**第四步:求平方和(** SStotal **)**

![](img/0af45d62e462f58af434bb0f45549dba.png)![](img/a58a504d8fd0964eafafc7bd059275d1.png)

**第五步:求(SSw)组内的平方和**

![](img/ede011d05bc8f248b6021ecfa119106f.png)![](img/ec41104116e98a39fc18baa1ff0a005b.png)

**第 6 步** : **求(SSb)组之间的平方和**

![](img/f086bac9a79a994f8f6010b1177ce262.png)![](img/4d3ad4de91d64498156d418d49d0b83c.png)

**步骤 7:组间均方/方差&组内均方/方差**

![](img/e130ee16c37f994d44be41070c513f3c.png)![](img/922057d33853c05b6901166e49e03be1.png)

**步骤 8:找到 F 统计值**

![](img/6a859405c6011243f4faa903d9ef6215.png)![](img/28eaad31d6360f7de078befc9a111fb2.png)

在**步骤 2 中计算的 f(临界)为 5.14**

## **F-统计< F(临界)= 0.058 < 5.14**

如果 F-Statistics 小于 F(临界),这里就是这种情况，**我们无法拒绝零假设。这意味着所有手段都是一样的。(每组读相同数量的书)**

**H0 : μ1=μ2 =μ3=⋯=μc**

**结论**:方差分析是统计学中非常重要的概念，在数据科学领域经常被用来验证测试/实验的方法。

[](https://www.datadriveninvestor.com/2020/02/19/five-data-science-and-machine-learning-trends-that-will-define-job-prospects-in-2020/) [## 将定义 2020 年就业前景的五大数据科学和机器学习趋势|数据驱动…

### 数据科学和 ML 是 2019 年最受关注的趋势之一，毫无疑问，它们将继续发展…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/19/five-data-science-and-machine-learning-trends-that-will-define-job-prospects-in-2020/) 

希望你喜欢我的文章。请鼓掌👏(50 次)激励我继续写下去。

想要连接:

链接进来:[https://www.linkedin.com/in/anjani-kumar-9b969a39/](https://www.linkedin.com/in/anjani-kumar-9b969a39/)

如果你喜欢我在 Medium 上的帖子，并希望我继续做这项工作，请考虑在[](https://www.patreon.com/anjanikumar)**上支持我**