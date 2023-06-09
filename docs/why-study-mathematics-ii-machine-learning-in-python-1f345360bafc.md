# 为什么要学数学？II:Python 中的机器学习

> 原文：<https://medium.datadriveninvestor.com/why-study-mathematics-ii-machine-learning-in-python-1f345360bafc?source=collection_archive---------19----------------------->

在这篇后续博客中，我们将研究机器学习背后的下一个数学概念。

> "有三种类型的谎言——谎言、该死的谎言和统计数据."
> —本杰明·迪斯雷利

![](img/f52b3a72d4433d72a602710144159053.png)

Image Source: [Malte Luk](https://www.pexels.com/@maltelu?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels) from Pexels

我们已经看到线性代数和概率在机器学习的世界中是如何工作和发挥作用的。如果你还没有，先看看之前的博客: [*为什么要学数学？:Python 中的机器学习|作者 Divyansh chaud hary | 2021 年 1 月| Medium*](https://divyansh7c.medium.com/why-study-mathematics-machine-learning-in-python-588974f6ed51) 。我们在处理数据和预测时遇到最多的下一个主题是统计学和微积分。

# 统计数字

统计学是机器学习的重要工具。它帮助你在预测趋势时分析、研究和做出假设。统计学是应用数学的一个领域，涉及数据的收集、分析、解释和表达。机器学习专业人员在对数据集进行假设测试时也使用它们。和往常一样，让我们先来看看统计学的术语:

*   **群体:**个体对象或事件的集合或集合，其属性将被分析。
*   样本:总体中的一个子集或一小部分。一个好的样本具有适当的大小和性质，能够正确地代表总体。

为了制作好的样品，我们可以使用各种各样的取样技术。

## 概率抽样:

*   **随机:**群体中的每个成员都有均等的机会被选中。
*   **系统性:**从总体中选择每第 n 条记录作为样本的一部分。
*   **分层:**一个阶层——拥有至少一个共同特征的人口子集，用于构成一个样本。

## 非概率抽样:

*   **雪球**
*   **配额**
*   **判断**
*   **便利**

> **注意:**本博客关注概率抽样，因为非概率抽样超出了本博客的范围。

## 统计类型:

有两种主要的统计类型:

1.  描述统计学
2.  推断统计学

## **描述性统计**

顾名思义，描述性统计是一种用数据集的样本和度量的简短信息来描述数据特征的方法。在这里，我们通过使用数值计算或图表来展示和组织我们的数据。通过根据数据集的属性绘制和排列数据集，我们可以直观地了解数据的总体趋势。描述性统计用两个类别处理数据:

*   **集中趋势的度量** —均值、中值和众数
*   **可变性测量** —范围、IQR、方差、标准差

## 集中趋势的测量:

*   **均值:** 它是一个样本中所有值的平均值的度量。

```
import statisticsdata = [1,2,3,4,5]
statistics.mean(data)
```

*   **中位数:** 是对样本中心值的度量。

```
import statisticsdata = [1,2,3,4,5]
statistics.median(data)
```

*   **众数:** 是一个样本中出现次数最多的值。

```
import statisticsdata = [1,2,3,4,5,2,2,2,3,5]
statistics.mode(data)
```

## 可变性测量:

*   **范围:** 数据集的最大值和最小值之差。它测量数据传播的距离。

```
data = [1,2,3,4,5]
# Range
max(data) - min(data)
```

*   **IQR:** 四分位间距是通过将数据集划分为四分位而收集的可变性的度量。IQR 计算为 Q3-Q1。Q1 代表最小值和中值之间的中间数的值，而 Q3 代表分布中值和最高值之间的点。
    IQR 也可以通过绘制数据集的箱线图来绘制。

```
from scipy import statsdata = [32, 36, 46, 47, 56, 69, 75, 79, 79, 88, 89, 91, 92, 93, 96, 97, 101, 105, 112, 116]#IQR
stats.iqr(data,interpolation = 'midpoint')
```

*   **方差:** 方差是数据集与其均值的离差平方和除以条目总数-1。
    较大的方差意味着数据集高度分散。

```
import statisticsdata = [32, 36, 46, 47, 56, 69, 75, 79, 79, 88, 89, 91, 92, 93, 96, 97, 101, 105, 112, 116]
statistics.variance(data)
```

*   **标准差:** 可以直接通过对一个数据集的方差求平方根来计算。平均值=1 且标准差=1 的正态分布遵循 68/95/99 规则。

```
import statisticsdata = [32, 36, 46, 47, 56, 69, 75, 79, 79, 88, 89, 91, 92, 93, 96, 97, 101, 105, 112, 116]
statistics.stdev(data)#orimport mathmath.sqrt(statistics.variance(data))
```

## 推断统计学

推断统计根据从同一总体中获取的数据样本对整个总体进行推断和预测。推断统计中关键因素的泛化。它不仅能决定什么会发生，还能决定程序中什么会发生。推理统计有助于确定样本间的关系强度。

最常用的推断统计类型有:

*   卡方/列联表
*   方差分析/ T 检验
*   双变量回归
*   多元回归
*   单一样本假设检验

其他:

*   皮尔逊相关
*   置信区间

## 双变量回归；

双变量回归是一个简单的线性回归方程，描述了解释变量和结果变量之间的关系，特别是假设解释变量影响结果变量，而不是相反。典型使用的图是散点图和箱线图。

> 更多关于图表的信息——点击[这里](https://medium.com/swlh/data-visualization-ii-machine-learning-in-python-1d478bd0e305)。

## 多变量回归；

多变量回归是一种测量预测值(自变量)和对这些预测值(因变量)的响应线性相关程度的方法。

## 单一样本假设检验:

假设检验是统计学中的一项重要实践。这是检验实验结果的一种方式，以此来看我们的结果是否有意义。该测试用于评估统计显著性，并允许做出定量决策，以确定当面对差异的数字或图形建议时，是否存在任何*【真实】*差异。
假设检验的基本过程是:

*   弄清楚你的*无效假设*。
*   陈述你的无效假设。
*   选择您需要执行的测试类型。
*   要么支持要么拒绝零假设。

**零假设** 简单来说，零假设就是我们所比较的事物之间没有差异的预期，它是关于事物的公认事实。

**替代假设** 这是关于我们正在比较的事物之间的预期差异的陈述。如果我们在测试过程中达到一定的置信水平，这种说法是可以接受的。

**α水平** 这是置信水平或显著性水平——当零假设为真时做出错误决策的概率。

**Z-Score** 在假设检验中，我们经常会借助 Z-Score。它是根据数据平均值和标准偏差得出的特定条目的分数。

## t 检验/方差分析:

**ANOVA —** 方差分析是在 3 个或更多总体均值之间进行的比较。它检验三个或更多人口平均数之间是否存在显著差异。它还发现了群体中每个个体因素的贡献，甚至从列表中识别出主导因素。

**T 检验—** 它的工作原理与方差分析完全相同。唯一显著的区别是 T 检验用于比较两个群体的平均值。

## 卡方检验/列联表:

独立性卡方检验用于比较*列联表*中的两个变量。这个测试用来看我们的两个变量实际上有多少关联。非常小的检验统计量意味着观察数据与预期数据非常吻合。
非常大的检验统计量意味着数据不太符合数据。

列联表很难制作。也称为交叉表或双向表，用于汇总数据的几个分类元组之间的关系。

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)