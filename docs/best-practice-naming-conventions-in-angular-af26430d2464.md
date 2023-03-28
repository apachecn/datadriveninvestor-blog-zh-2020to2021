# Angular 中的最佳实践命名约定

> 原文：<https://medium.datadriveninvestor.com/best-practice-naming-conventions-in-angular-af26430d2464?source=collection_archive---------0----------------------->

## 角度命名指南

![](img/24a5f72725c0899ac474564f19862dd2.png)

Photo by [Patrick Perkins](https://unsplash.com/@stay_in_touch?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 介绍

在这篇文章中，我将与你分享 Angular 团队提倡的好的命名惯例。命名是我们作为软件开发人员做得最多的事情之一，因此，我们把它做好是很重要的。

良好的命名实践在软件中非常重要，因为它们有助于:

*   代码可读性
*   代码的可维护性
*   新开发人员加入团队。

Angular 本质上是一个非常固执己见的框架，这是有充分理由的。它有助于确保我们的编码模式是可预测的，因此易于维护。

# 命名的黄金法则

命名的黄金法则应该成为你命名模式的基础。无论如何，它们必须得到应用或遵循。

## **1。一致性**

在 Angular 代码中命名工件时，一致性是关键。一致性的原则是遵循一个好的模式并坚持下去。

保持一致有助于快速找到内容。此外，它还为新开发人员提供了如何命名事物的指导。这里引用了官方 Angular 文档中关于命名一致性的一段话。

> “项目内部的一致性至关重要。与团队保持一致很重要。整个公司的一致性提供了巨大的效率”

## 2.给有意义的名字

项目中的所有工件；文件夹、文件、类等应该被命名以传达意义。这些名称应该提供一个关于一个工件做什么的提示。

*   使用传达意图的名称
*   使用可搜索的名称
*   对类、文件夹和文件名使用名词
*   对方法或功能使用动词或动词短语
*   避免使用缩写和符号，因为它们会引起混淆

# 棱角分明的表壳款式

除了上面讨论的一般命名原则，Angular 主要使用三种 case 样式来命名工件。骆驼案，帕斯卡案，烤肉串案。知道何时何地使用这些案例风格是很重要的。在下一节中，我将介绍每种案例风格以及在哪里使用它们。

[](https://www.datadriveninvestor.com/2020/10/12/4-key-habits-i-learned-as-a-software-engineer/) [## 我作为软件工程师学会的 4 个关键习惯|数据驱动的投资者

### 我从事软件工程已经快 3 年了。老实说，我不认为我擅长这个(我不知道我会不会…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/10/12/4-key-habits-i-learned-as-a-software-engineer/) 

# **1。烤肉串盒(kebab-case)**

kebab-case 是一种命名风格，其中**名称中的所有字母都是小写** **和** **它使用破折号来分隔名称中的单词**。此外，在 Angular 中，用一个点来分隔文件名的名称、类型和扩展名。

通过在文件名中包含该类型，可以很容易地使用文本编辑器或 IDE 找到特定的文件类型。此外，它们还为自动化任务提供模式匹配。

kebab-case 用于命名文件夹、组件选择器、文件和 Angular 应用程序本身。Angular 项目中的典型文件包括组件文件、服务文件、模板文件、模块文件等。

## 示例:

跟踪汽车列表的组件可以命名为***car-list . component . ts .***相应的服务可以是***car-list . service . ts .***

日期的管道文件是 ***date.pipe.ts.***

在表中显示汽车的选择器可以命名为下面的粗体。

```
@[Component](https://angular.io/api/core/Component)({ selector: ‘**car-list-table**’, templateUrl: ‘./car-list-button.component.html’ })
```

测试文件有点特殊。除了类型和扩展名，它们还应该有后缀 ***spec*** 用于单元测试文件，以及 ***e2e-spec*** 用于端到端测试文件。

一个日期管道单元测试文件可以被命名为

*汽车列表组件端到端测试文件可以命名为**car-list . component . e2e-spec . ts***

# ***2。帕斯卡格(PascalCase)***

*PascalCase 是一种名称中所有单词的首字母都大写的风格。*

*Pascal case 主要用于 Angular 项目中的类命名。*

## *示例:*

*car-list 组件的类名可以命名如下。*

```
*Export class **CarListCompoent** **{}***
```

*转换日期的管道类可以命名如下*

```
*Export class **DatePipe {}***
```

*类名必须跟在 PascalCase 后面，不管它们是否属于模块、服务、组件等。*

# ***3。骆驼案(camelCase)***

*camelCase 命名风格有点类似于 PascalCase，除了名称中的第一个字母应该总是小写。名称中所有其他后续单词的首字母都将大写。*

***注:**单个单词名称的茶色和烤肉串色类似。*

*camelCase 用于命名方法或函数、属性、字段、指令选择器和管道选择器，如下所述。*

***例子:***

*指令选择器使用驼峰大小写*

```
*@[Directive](https://angular.io/api/core/Directive)({ selector: ‘[**carValidate**]’ }) export class CarValidateDirective {}*
```

*管道名称选择器也使用骆驼大小写*

```
*@[Pipe](https://angular.io/api/core/Pipe)({ name: ‘**initCaps**’ }) export class InitCapsPipe implements [PipeTransform](https://angular.io/api/core/PipeTransform) { }*
```

*在 Angular 中，方法或函数名也使用骆驼大小写。例如，获取汽车列表的方法可以命名如下。*

```
*public **getCars**();*
```

*如果你像我一样有一些基于 C 的编程语言背景，并且习惯于在 PascalCase 中使用函数名。那么也许你可以用同样的角度。只要确保你选择了一种模式并坚持下去(保持一致)。*

# *代码注释*

*无论你如何努力，一些工件的名字可能无法传达意思。在这种情况下，使用注释作为名称的辅助。评论应该简短而准确。*

# *结论*

*在这篇文章中，我们已经了解了 Angular 中的一些命名原则。好的命名对于代码的可读性和可维护性非常重要。*

*当我们给工件命名时，我们当然是为了我们的开发伙伴和我们自己。用好的名字来表达爱。*

## *访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)*