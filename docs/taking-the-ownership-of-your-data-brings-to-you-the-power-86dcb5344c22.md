# 掌控您的数据，为您带来强大的力量！

> 原文：<https://medium.datadriveninvestor.com/taking-the-ownership-of-your-data-brings-to-you-the-power-86dcb5344c22?source=collection_archive---------13----------------------->

![](img/830b75f5ab6c1d92746b25c6c15d9966.png)

Taking the ownership of your data,brings to you the power !

A 获得数据所有权的第一步是对数据本身的类型进行分类。在您能够理解哪种算法最适合您的明确定义的 ML 问题之前，您需要理解您所拥有的数据的性质和类型。

两大类数据，定性和定量:

*   *定性数据*，分类为**标称**如果类别之间没有自然顺序(如眼睛颜色)。以及 ***序数*** 如果存在排序(如考试成绩或班级排名)。
*   定量数据，分类为**离散**，如果测量值为整数(如城市或国家的人口)。以及**连续**，如果测量值可以取任何值，通常在某个范围内(如一个人的身高或体重)。

值得一提的是，JSON(JavaScript Object Notation)格式是 ML 解决方案的重要组成部分。JSON 的优势之一是几乎每个开发平台都有库。它是真正的跨平台。

[](https://www.datadriveninvestor.com/2018/10/16/on-the-entrepreneurial-trek-embrace-the-learning/) [## 在创业之旅中，拥抱学习|数据驱动的投资者

### 好像建立一个数百万美元的公司还不够困难，企业家必须额外照顾他们的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2018/10/16/on-the-entrepreneurial-trek-embrace-the-learning/) 

你可能会问，既然我们已经有了 CSV 和 ARFF，完全能够为 ML(机器学习)表示数据，为什么我们还需要 JSON 来处理数据文件。您可能想考虑使用 JSON 有两个原因:

1- JSON 是网络数据交换的理想选择。如果您需要将数据发送到联网设备，使用 JSON 和 HTTP 是一项简单的任务，但是使用 CSV 和 ARFF 就不那么简单了。此外，如果您使用 JSON 作为数据格式，您需要在创建后验证您的 JSON。有许多在线工具可以执行 JSON 验证。它们中的许多都是开源的或者是用脚本语言创建的，所以如果您愿意，您可以在本地运行验证。

2-许多 NoSQL 数据库使用 JSON 文件作为数据的对象存储。这种数据库架构解决了大量数据带来的可伸缩性问题。

说到数据预处理，我认为这里的 t *不能代替了解你的数据。这是一项耗时的手工练习。提前投入时间分析数据以提高数据的质量和完整性，在 ML 项目的后期总是有回报的。*

缺失值和重复值是数据预处理的一个重要方面。缺少的值可以采用空白、破折号或 NaN 的形式。缺失值并不难找到。困难在于当你发现他们时你应该采取什么行动。缺失值通常分为两类:

MCAR(完全随机失踪)

*   系统性缺失:值缺失是有充分理由的，只是因为值缺失并不能告诉您值缺失的原因。

当您发现缺少值时，您必须仔细考虑解决方案。处理缺失值时，您可以考虑多种方法:

*   不要采取行动。保留丢失的值。
*   将该值替换为“未测试”或“不适用”指示器。
*   如果标签包含缺少的值，您应该考虑删除整个实例，因为它不会为您定型的模型增加值。
*   有时，您有一个范围内的规范化值，分配一个最小值或最大值可以使算法更有效。
*   为缺失值估算一个值。估算是指在研究其他属性的基础上用新值替换该值。

我将在另一篇文章中介绍 Weka ML 环境，因为它是一个知识分析工具。Weka 使用其基于 Java 的工具具有许多预处理数据的能力。但是，您也可以使用 OpenOffice Calc 的宏处理功能来预处理您的数据。

此外，为了创建您自己的数据，我列出了私有数据和合成数据作为潜在的数据源。我们生成这两类数据。**合成**数据表示由计算机创建的数据。我们都携带着有史以来最伟大的数据收集设备: ***智能手机*** 。

需要记住的另一个关键点是，能够可视化您的数据非常重要。可视化使您能够轻松洞察数据。数据可视化是最好的工具之一，您可以将它添加到您的工具包中，以便对自己的数据提出更高的要求。

最重要的是，当您遵循这些最佳实践时，您就踏上了成为数据科学家的道路:

*   要开发 ML 应用程序，您必须采用数据驱动的方法。
*   要开发成功的 ML 应用程序，您必须对自己的数据有更高的要求。
*   你的大部分代码都是关于数据的争论。80/20 法则适用于:对于你承担的任何给定项目，你 80%的时间将用于处理数据。
*   对于一个明确定义的问题，高质量的相关数据是起点。
*   了解你有什么类型的数据。
*   定义您的数据类型，并考虑将它们保存在数据字典中。
*   有许多来源可以用于您的 ML 应用程序数据:公共的、私有的、政府的、合成的等等。
*   您可以生成自己的数据。
*   您可以使用许多工具来操作数据，包括 Open Office Calc 电子表格程序。您将探索 ML 环境中可用的其他数据过滤工具。
*   JSON、CSV 和 ARFF 格式是 ML 的流行数据格式。对它们都感到舒适。
*   大多数实体没有足够的高质量数据用于 DL(深度学习)，而 CML(经典机器学习)应用只需要合理的数据量就可以成功。
*   智能手机是有史以来发明的最好的数据收集设备。
*   可视化是 ML 和理解数据的一个关键方面。
*   为了帮助您可视化您的数据，您可以利用第三方包，使在浏览器和 android 设备上可视化数据变得容易。

起源于[blog.selcote.com](http://blog.selcote.com/2020/01/10/taking-the-ownership-of-your-databrings-to-you-the-power/)