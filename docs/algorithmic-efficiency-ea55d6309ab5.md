# 算法效率|加速您的模型

> 原文：<https://medium.datadriveninvestor.com/algorithmic-efficiency-ea55d6309ab5?source=collection_archive---------25----------------------->

![](img/4a59ec75983782a51a60f15e268f549c.png)

Photo by [Marc Sendra Martorell](https://unsplash.com/@marcsm) on [Unsplash](https://unsplash.com/)

并非所有能够解决问题的算法都是实用的。有些可能太慢，无法在实际项目中实现。一些问题可以通过快速算法来解决，对于一些问题，可能不存在快速算法。

处理算法复杂性比较的计算机科学领域被称为算法的*分析。*大 O 符号用于根据算法的运行时间如何随着输入大小的增长而增长来对算法进行分类。

[](https://www.datadriveninvestor.com/2020/08/27/what-is-a-data-catalog-and-how-does-it-enable-machine-learning-success/) [## 什么是数据目录，它如何使机器学习取得成功？数据驱动的投资者

### 数据目录是机器学习和数据分析的燃料。没有它，你将不得不花费很多…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/08/27/what-is-a-data-catalog-and-how-does-it-enable-machine-learning-success/) 

例如，考虑在大小为 n 的示例集 S 中寻找最大距离的 1-D 示例的问题。我现在能想到的一种算法如下:

在上面的程序中，我们对 S 中的所有值进行循环，在第一次循环的每次迭代中，我们再次对 S 中的所有值进行循环。因此，上面的程序对数字进行了 N 次比较。在每一次迭代中，我们有一次比较，两次 abs 和两次赋值操作，从而使该算法的时间复杂度为 5N。对于上面的算法，使用大 O 记法，我们写出算法的复杂度为 O(N)；常量，如 5，被忽略。

对于同一个问题，我们可能会这样想:

在上面的代码中，我们只对 S 中的所有值循环一次，所以算法的复杂度是 O(N)。在这种情况下，我们说后一种算法比前一种算法更高效。

如果一个算法的复杂度是输入大小的多项式，则称它是有效的。但是，对于非常大的输入，O(N)算法可能会很慢。

> 在这个大数据时代，数据科学家往往会寻找 O(log N)算法。

出于实用的目的，我们应该避免使用循环，只要有可能就应该选择其他算法。如果需要迭代大量元素，可以使用 Python 生成器创建一个函数，一次返回一个元素。除非你确切地知道该做什么，否则最好使用流行的库来编写你自己的科学代码。您可以使用 python 中的 **cProfile 包**来发现代码中的低效之处。

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)