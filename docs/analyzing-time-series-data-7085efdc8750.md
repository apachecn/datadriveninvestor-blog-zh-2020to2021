# 分析时间序列数据

> 原文：<https://medium.datadriveninvestor.com/analyzing-time-series-data-7085efdc8750?source=collection_archive---------5----------------------->

![](img/0ea0d8334311ca8440fcfa8749dde6a7.png)

Photo by [M. B. M.](https://unsplash.com/@m_b_m) on [Unsplash](https://unsplash.com/)

我们都听人说过，某种特定商品的价格会随着时间的推移而上涨或下跌。这种商品可以是任何东西，如黄金，或任何可食用的物品等。还有，你一定听说过银行的房屋贷款利率提高了。教育贷款的利率降低了。所有这些是什么，以及所有这些是如何影响我们的？这些类型的数据是数据的时间序列。

> 时间序列通常是在一段时间内收集并依赖于它的数据。按时间顺序收集的一系列数据点称为时间序列。时间序列的组成部分是:

I)趋势:趋势显示数据在一个长时期内增加或减少的方向或一般趋势。可以分析出，在不同的时期，这种趋势可能会增加、减少或保持稳定。但是总的趋势一定是向上的，向下的，或者稳定的。

ii)季节性:时间序列中任何可预测的变化或模式，只要在特定时期重复，就可以说是季节性的。当时间序列受到任何季节性因素(如一年中的某个时间或一月中的某个星期)的影响时，就会出现季节性模式。

iii)不规则性/残差:是去除趋势周期和季节成分后剩下的残差时间序列。

当值为常量或值为任何函数形式时，不应使用时间序列分析。

时间序列不应该与回归混淆。回归模型的基本假设是观测值独立，但这一假设不适用于数据依赖于时间的时间序列数据。

# 平稳时间序列

一个**平稳时间序列**是一个其性质不依赖于序列被观察的时间的序列。因此，具有趋势或季节性的时间序列不被认为是稳定的，因为趋势和季节性会影响时间序列在不同时间的值。我们使数列平稳，以使变量独立。变量可以在许多方面依赖，但只能在一方面独立。所以他们独立的时候我们会得到更多的信息。将一个系列归类为平稳系列有两个基本标准:

I)时间序列的平均值和方差不应是时间的函数。应该是不变的。

ii)*项和*项的协方差不应是时间的函数。**

## 移动平均数

> 在统计学中，移动平均是一种通过创建完整数据集的不同子集的一系列平均值来分析数据点的计算方法。它也被称为移动平均值或滚动平均值。

移动平均线最常见的用途是确定趋势方向和分析支撑位和阻力位。移动平均线的两种基本类型是简单移动平均线和 T2 指数移动平均线。简单移动平均值的计算方法是将几个时间段的值相加，然后将总和除以 n(时间段数)。简单移动平均线(SMA)是给定时间段的平均价格，每个时间段的价格具有相等的权重，而指数移动平均线(EMA)通过将更多权重应用于最近的值来减少滞后。应用于最近值的权重取决于移动平均值中的周期数。即使简单移动平均线和指数移动平均线有明显的区别，但我们不能说一个一定比另一个好。指数移动平均线具有较小的滞后，因此对最近的值以及值的最近变化更敏感。指数移动平均线会在简单移动平均线之前转向。另一方面，简单移动平均线代表整个时间段的真实平均值

[](https://www.datadriveninvestor.com/2020/07/23/learn-data-science-in-a-flash/) [## 一瞬间学会数据科学！？数据驱动的投资者

### 在我之前的职业生涯中，我是一名训练有素的古典钢琴家。还记得那些声称你可以…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/07/23/learn-data-science-in-a-flash/) 

# 固定支票

这个测试帮助我们确定一个时间序列受趋势影响的程度。我们可以利用 **Dicky-Fuller 测试**来检查时间序列数据的平稳性。本测试的*零假设*是时间序列不是平稳的(具有一些依赖于时间的结构)，而*替代假设*是时间序列是平稳的。测试结果由测试统计数据和不同置信水平的一些临界值组成。如果“检验统计量”小于“临界值”，我们可以拒绝零假设，并得出结论，该序列是平稳的。

# ARIMA 模型

ARIMA 代表“自回归综合移动平均线”。它由三个有序参数(p，d，q)指定。

这里，“p”表示自回归模型的阶(时滞数)，“d”是差异度(数据减去过去值的次数)，“q”告诉我们移动平均模型的阶。

我们可以计算时间序列数据与之前时间步长的观测值的相关性，称为滞后。因为时间序列数据的相关性是用先前时间的相同序列的值计算的，所以自相关。为了找到(p，d，q)的优化值，我们将利用 ACF(自相关函数)和 PACF(部分自相关函数)图。ACF 是时间序列与其自身滞后版本之间相关性的一种度量，而 PACF 是时间序列与其自身滞后版本之间相关性的一种度量，但是是在剔除了已经通过干预比较解释过的变化之后。

下面是参考 jupyter 笔记本，展示了如何在现实世界的时间序列分析中应用上述概念:

Python code file for gold prediction by author

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)