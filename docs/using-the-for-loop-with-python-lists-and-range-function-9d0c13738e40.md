# 面向初学者的 Python For 循环

> 原文：<https://medium.datadriveninvestor.com/using-the-for-loop-with-python-lists-and-range-function-9d0c13738e40?source=collection_archive---------15----------------------->

## *使用 for 循环与 else、break、continue、pass 语句和 python 列表，python 嵌套 for 循环和 range()函数*

![](img/1fdd9118a314742790a9f057f2928ce9.png)

Photo by [AltumCode](https://unsplash.com/@altumcode?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

假设我们有一个蔬菜清单，包含三个项目。如果你想单独访问列表中的每一项，我们可以使用 for 循环。

我们以“的关键字“**开始，并给出单品的名称。在这种情况下，我们可以称之为蔬菜，然后在关键字**中使用**，最后我们循环的列表被命名为**蔬菜**。**

**重要:**无论什么时候看到冒号，缩进确实很重要。因为如果它是有意的，那就意味着它在 for 循环中。

**例 01:求学生身高的平均值**

**例 02:获得最高分**

**让我们看看 for 循环如何用于 range()函数**

range 函数是一个返回一系列数字的内置函数。至少，它需要一个整数参数。

[](https://www.datadriveninvestor.com/2020/10/23/fourier-transform-for-image-processing-in-python-from-scratch/) [## Python 中用于图像处理的傅里叶变换从零开始|数据驱动投资者

### 首先，处理数学问题真的很有趣。对吗？我知道答案可以是是也可以不是…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/10/23/fourier-transform-for-image-processing-in-python-from-scratch/) 

它需要三个参数。这三个参数中有两个是可选的。即 start 和 step 是可选参数。

1.  **start** 参数是序列的起始编号。即下限。默认情况下，如果没有指定，它从 0 开始。
2.  **停止**参数是一个上限。即生成的数字不超过该数字，则 range()在结果中不包括该数字。
3.  第**步**是结果中每个数字之间的差值。如果未指定，步长的默认值为 1。

*   给定一个参数，它返回从到的整数值。例如，range(10)按顺序返回数字到。
*   若要从以外的值开始，请使用两个参数调用 range。例如，range(1，10)返回到之间的数字。

**例 06:添加偶数**

**为循环用*否则*为**

用于循环的**也可以有一个可选的**或**块。如果用于循环的序列中的项目用尽，则执行**否则**部分。break 关键字可用于停止**循环的**。在这种情况下，else 部分被忽略。**

因此，如果没有中断发生，for 循环的 else 部分就会运行。这里有一个例子来说明这一点。

***中断*声明**

python 中的 **break** 语句终止当前循环，并在下一条语句处继续执行

***继续*声明**

使用**继续**语句，我们可以停止循环的当前迭代，并继续下一个:

**python 中嵌套的 for 循环**

当一个 for 循环出现在另一个 for 循环中时，它被称为嵌套 for 循环。我们举一个嵌套 for 循环的例子。

**For 循环用*传递*语句**

Python 中的 **pass** 语句在语法上需要一个语句，但您不希望执行任何命令或代码时使用。

**pass** 语句是一个*空*操作；它执行的时候什么都不会发生。**通道**在你的代码最终要去但还没有被编写的地方也很有用。

如果*字母*的值为‘n’，前面的代码不执行任何语句或代码。当您已经创建了一个代码块，但不再需要它时， *pass* 语句很有用。

然后，您可以删除块内的语句，但让块保留 pass 语句，这样它就不会干扰代码的其他部分。

让我们在下一篇文章中了解 Python 列表内置的函数和方法。注意安全。

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)