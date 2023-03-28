# 关于 JavaScript 中的析构

> 原文：<https://medium.datadriveninvestor.com/all-about-destructuring-in-javascript-c71d9c23bb44?source=collection_archive---------5----------------------->

## ES6 的一大特色

![](img/8ab6d60340368ca83f669603090eb852.png)

Photo by [Max Duzij](https://unsplash.com/@max_duz?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

例如，在 ES6 之前，使用普通赋值，我们一次提取一条数据。

![](img/bcf1041d2c0574962e1819da36b79cb5.png)

输出。

![](img/2e317ef2a6ad88497fe8721d9c3d5d5d.png)

# 什么是解构作业？

在 JavaScript ES6 中，添加了一种新的语法，用于从数组索引或对象属性创建多个变量，称为[析构](https://eslint.org/docs/rules/prefer-destructuring#further-reading)。此规则强制使用析构，而不是通过成员表达式访问属性。

[](https://www.datadriveninvestor.com/2020/03/29/microsoft-having-an-edge-over-chrome/) [## 数据驱动的投资者|微软比 Chrome 有“优势”

### 简史我从来不是浏览器的粉丝，确切地说，我只是一个浏览器的粉丝，Chrome。这是我的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/03/29/microsoft-having-an-edge-over-chrome/) 

下面是使用值数组的简单析构赋值。

![](img/bcd3cd95721e3024e00bc1b31f14ecd2.png)

这段代码的输出与前面的代码相同，它只提取我们需要的内容。

# **对象破坏**

对象析构让我们通过看起来像对象文字的模式批量提取属性值。

## 基本语法

![](img/9d5c66e08a9659f9e74c969ff7ec3ebc.png)

我们可以把模式想象成放置在数据上的透明片:模式键`‘user_name’`在数据中有一个匹配。因此，我们也可以对原始值进行对象析构。

![](img/226a9a46820df6497dd1533d3e9ad94b.png)

我们也可以像下面这样对数组进行对象析构。

![](img/6e039211d908c31709b74ecee4119921.png)

## 我们可以在没有声明的情况下做作业

变量的赋值和析构可以独立于它的声明。

![](img/a29d606204fbc511305db26780b29d11.png)

## 对象析构时缺少属性

如果对象模式中的一个属性在右边没有匹配，我们得到`undefined`值。

![](img/fa4a1d26063fa12c461d3de805375c4c.png)

如果我们想要使用不同的值，我们需要指定一个默认值。

![](img/0bc79894be3eb5bad9866b66537939c5.png)

## 我们不能析构未定义的空对象

只有当要析构的值是`undefined`或`null`时，析构对象才会失败。

例如使用`undefined`值。

![](img/6c503e6827e2161a61103289f164bb78.png)

输出。

![](img/5a9fdcb5861336c03b9101f476c75762.png)

# **数组析构**

数组析构允许您通过看起来像数组文字的模式批量提取数组元素的值。

![](img/c684c6ee81f901307c665eee012f71ce.png)

我们可以通过提到数组模式中的孔来跳过元素。索引`1`处的数组元素被忽略。

![](img/97c71b62693d46f973e6a289d6f7d176.png)

## 数组析构中缺少元素

如果数组模式中的一个元素在右边没有匹配项，那么就会得到`undefined`值。

![](img/411e1ad88e822c47943bee322ccaf0c2.png)

输出。

![](img/635894b258b06949f41e4417d2410496.png)

我们也可以在数组析构中设置默认值。

![](img/3b0c6d88da76249f61f92141ab4da405.png)

## 我们不能数组解构不可迭代的值

数组析构要求析构的值是可迭代的。因此，我们不能对`undefined`和`null`进行数组解构。但是我们也不能数组解构`non-iterable`对象。

![](img/3273d9e262f6113e0485fdfc48cf7e19.png)

输出。

![](img/bac675c243dbeac5409fdedef352ab87.png)

# 解构的魔力

## 我们可以用析构来交换 JavaScript 中的变量值？

之前。两个变量怎么互换？

![](img/4d1629ab9a6a44b29f49ede431060572.png)

现在，我们可以使用数组析构来交换两个变量的值，而不需要临时变量。

![](img/322e1839cd3847d039199ba34b7f1807.png)

输出。

![](img/206988ce81fca54441c4e8170e739eac.png)

所以，我们可以交换多个变量的值，而不需要任何临时变量。

![](img/f48916b3805104d29ea34e1c1a0f676f.png)

## 返回数组的运算

当操作返回数组时，数组析构很有用。

![](img/34ccfb26ffc6c5cedb94b646eff63829.png)

我们跳过了索引 0 处的元素，因为它匹配整个。

## 编写一个返回多个值的函数

如果函数返回多个值，析构非常有用。

![](img/3d2d3e5270c929a8446da66df6457576.png)

## **参数定义类似于析构**

其实下面两个函数声明是等价的。

![](img/923269e2eff70af54a4e920be47bf7c4.png)

# **嵌套解构**

析构也适用于嵌套对象。

![](img/38b478112ae064ccf48751dd5a4d2e3c.png)

很简单，对吧？

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)