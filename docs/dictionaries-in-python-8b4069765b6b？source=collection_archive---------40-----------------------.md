# Python 中的字典

> 原文：<https://medium.datadriveninvestor.com/dictionaries-in-python-8b4069765b6b?source=collection_archive---------40----------------------->

## 如何在 Python 中使用字典

![](img/70ed877d03746bef829fab6e712a8cc2.png)

Photo by [Aaron Burden](https://unsplash.com/@aaronburden?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

在本教程中，我们将介绍 Python 字典的基本特征，并学习如何访问和管理字典数据。

## 什么是字典？

Dictionary 是无序且可变对象的集合，但是它使用键和值而不是索引。字典类似于列表。它们之间的主要区别是列表元素是通过它们的位置来访问的，通过索引来访问*，而字典元素是通过键*来访问*。在字典中，每个键值对都将键映射到其关联的值。*

[](https://www.datadriveninvestor.com/2020/07/07/introduction-to-time-series-forecasting-of-stock-prices-with-python/) [## 用 Python |数据驱动投资者进行股票价格时间序列预测简介

### 在这个简单的教程中，我们将看看如何将时间序列模型应用于股票价格。更具体地说，一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/07/07/introduction-to-time-series-forecasting-of-stock-prices-with-python/) 

## 定义字典

在 Python 中，定义字典的方法是用大括号({})括起逗号分隔的键值对列表，并用冒号( : )将每个键与其关联的值分隔开。示例:

![](img/aada256db444d7274c17e7b893bbbe13.png)

我们还可以用内置的 *dict()* 函数构造一个字典。dict()的参数应该是一个键值对序列。

![](img/c76beed1801d217d1849df36bd553010.png)

## 访问字典中的项目:

我们可以通过引用在方括号*[]中的关键字名称来访问字典的条目。通过指定相应的键从字典中检索值:*

*![](img/bb1f16fab70df4f265a09f3fbf17a5da.png)*

*使用 *get()* 方法也会得到相同的结果:*

*![](img/8666a8424e6a538b5ce9ccafc05bf434.png)*

## *更改/更新词典中的条目:*

*向现有字典添加条目—意味着分配新的键和值:*

*![](img/66ab06086e455fc0bfa3bde9c1de02d0.png)*

*更新条目—为现有键分配新值:*

*![](img/f0bdb3558fcd1ddcd855d136cf1accdf.png)*

*删除条目—使用 *del* 语句，指定要删除的键:*

*![](img/523d39b5cbd9b73a5f45151f11172ea5.png)*

*另一种方法是使用 *pop()* 方法:*

*![](img/9ae657d5da78158eeb36eb8367110484.png)*

**popitem()* 方法删除最后插入的项目:*

*![](img/3a8bdb6993a3e45ab15269a27a86aa37.png)*

*方法清空字典:*

*![](img/b41ac53341b7052ec34029187da2f4a7.png)*

*复制字典— *copy()* 方法用于复制字典。*

*![](img/0cf99c05300a284ceb93a948affc574f.png)*

## *在字典中循环:*

*我们可以使用*作为*循环来遍历字典。当遍历字典时，返回的值是字典的*键*，但是也有返回*值*的方法。*

*![](img/9e2401c19aa033304cc682c44cdb4b4d.png)*

*我们想要返回字典中的值是什么？*

*![](img/9db4ebbb50095990d29c3bbdae5472b7.png)*

*另一种方法是使用`values()`方法:*

*![](img/c030b245ba8833c278692b61498d79b5.png)*

*返回字典中的键和值:*

*![](img/15e62edeedbb3d962c61a25b92241672.png)*

## *嵌套词典:*

*包含许多字典的字典称为嵌套字典。*

*![](img/ffe6902e0b2e65644402e8fc7cd55c5c.png)*

*如果我们想从不同的字典中创建一个字典，该怎么办:*

*![](img/e9e86854dc125a891f0239c2cae22482.png)*

## *结论*

*在本教程中，我们讲述了 Python 中字典的一些基本属性，并学习了如何访问和操作它的数据。*

*正如所看到的，列表和字典有几个相似之处，但是不同之处在于它们的元素是如何被访问的。列表中的元素通过基于顺序的数字索引来访问，字典元素通过键来访问。*

## *访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)*