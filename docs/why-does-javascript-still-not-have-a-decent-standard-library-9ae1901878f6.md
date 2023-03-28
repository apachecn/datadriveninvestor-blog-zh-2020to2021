# 为什么 JavaScript 仍然没有一个像样的标准库？

> 原文：<https://medium.datadriveninvestor.com/why-does-javascript-still-not-have-a-decent-standard-library-9ae1901878f6?source=collection_archive---------8----------------------->

![](img/118a670c7e9266148479d7a79fe58a9f.png)

We need a decent standard library for JavaScript

现在是 2020 年。根据 Stack Overflow 2019 年的开发者调查，JavaScript 是迄今为止全球最受欢迎的技术，使用率高达 67.8%(1)。

如果是这样的话，为什么我们仍然没有一个标准的库来提供像 Python、Java 和 C++那样的工具呢？缺少这样的库极大地阻碍了编写 JavaScript 应用程序的效率，并阻止了它用于各种应用程序。

如果没有一个像样的标准库，许多常见的实用程序必须从头实现，这是一个灾难。能够有效处理大量输入的数据结构很难正确有效地实现。在这方面，操作数据的算法是相似的。当然，你不希望细微的错误在你的程序中肆虐吧？

此外，缺乏像样的标准库不可避免地会降低生产率。当涉及到快速迭代时，生产率，即花费的时间，是一个主要的关注点。推出自己的实现需要很多时间。当然，您可以选择在 npm (2)上找到符合您需求的库。然而，从许多低质量的库中筛选出维护良好、正确且高效的库是非常耗时的。无论你选择哪个选项，你最终都会浪费时间。

[](https://www.datadriveninvestor.com/2020/03/29/microsoft-having-an-edge-over-chrome/) [## 数据驱动的投资者|微软比 Chrome 有“优势”

### 简史我从来不是浏览器的粉丝，确切地说，我只是一个浏览器的粉丝，Chrome。这是我的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/03/29/microsoft-having-an-edge-over-chrome/) 

除此之外，JavaScript 开发人员的算法知识也因为缺乏一个标准的库来正确实现算法和数据结构而受到影响。近年来，大量的 JavaScript 开发人员并不具备数据结构和算法的正式知识。除了数组、哈希表和排序，他们可能不知道太多其他的东西。他们可能不知道计算系统所需值的有效技术。他们也可能不知道在他们的程序中操纵数据所涉及的成本。

低效算法的例子包括从数组的头部弹出，不使用哈希表，以及对数组进行冒泡排序。

注意，前面提到的例子都是非常简单的错误。实际上，应用程序处理的数据要复杂得多。在这种情况下，对数据结构和算法的深入理解是必要的。

JavaScript 开发人员对数据结构和算法缺乏理解的问题可以通过一个维护良好、正确且高效的标准库得到很大程度的缓解。这种实现的可用性让开发人员知道了比他们已经知道的技术更好的技术。JavaScript 开发人员算法知识的下限增加了。最终，开发者会写出更高效的程序。

在编写 JavaScript 应用程序时，我发现需要数据结构和算法，比如队列、二分搜索法和选择算法。我也不时需要简单的数字函数。没有像样的标准库，我不得不从头开始编写这些函数的实现。每次我使用这些函数的实现时，我都会提醒自己，“*为什么 JavaScript 仍然没有一个像样的标准库？*”。

[1]:数据来源于[栈溢出开发者调查 2019 —最流行技术](https://insights.stackoverflow.com/survey/2019#most-popular-technologies)。

[2]:这样的库有很多: [Moment.js](https://momentjs.com/) 、 [Lodash](https://lodash.com/) 等等。然而，搜索这样的库来满足你的需要就像大海捞针一样。