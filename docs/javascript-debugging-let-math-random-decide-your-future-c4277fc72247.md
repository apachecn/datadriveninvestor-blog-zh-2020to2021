# JavaScript 调试:让数学。Random()决定你的未来

> 原文：<https://medium.datadriveninvestor.com/javascript-debugging-let-math-random-decide-your-future-c4277fc72247?source=collection_archive---------4----------------------->

![](img/5fb49bd59835b56b289079c8ce7f76b1.png)

Photo by [George Pagan III](https://unsplash.com/@gpthree?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

![](img/0277555cbe2a86ece3beafb9ffca44e7.png)

今天我们要调试一个程序，这个程序有很多与语法相关的错误。在我们上一篇 [JavaScript 调试文章](https://levelup.gitconnected.com/javascript-debugging-function-syntax-364d4d90a4c7)中，我们的函数有一些语法错误。我们经历了如何调试预写代码的过程，同时学习了简单的函数语法。

有一个名为`yourFutureCareer`的函数将根据`Math.Random()`方法的输出输出`FrontEnd Developer`、`BackEnd Developer`或`Full-Stack Developer`。让我们看看代码:

```
function {
 var : Math.random()
  if (career <= 0.32) {
   return = FrontEnd Developer
   else if (career <= 0.65) 
   return : BackEnd Developer,
  } else {
   return 'Full-Stack Developer'
  }yourFutureCareer();
```

我们已经看到有许多语法问题，但首先让我们从最上面开始，一步步往下。

在第一行，我们看到我们声明了一个函数，但是只提到了关键字`function`。该函数没有名称。如果我们看代码中调用`yourFutureCareer()`的最后一行，那是函数的名字。

```
function yourFutureCareer(){
 var : Math.random()
  if (career <= 0.32) {
   return = FrontEnd Developer
   else if (career <= 0.65) 
   return : BackEnd Developer,
  } else {
   return 'Full-Stack Developer'
  }yourFutureCareer();
```

现在我们来看函数体内的第一行，我们已经有了另一个问题。我们注意到创建变量的方法不正确。我们看到一个`var`，一个冒号和`Math.random()`。变量没有名字，冒号应该是一个等号，因为我们把`Math.random()`赋给了一个变量。另外，语句应该以分号结束。

[](https://www.datadriveninvestor.com/2019/03/25/a-programmers-guide-to-creating-an-eclectic-bookshelf/) [## 创建折衷书架的程序员指南|数据驱动的投资者

### 每个开发者都应该有一个书架。他的内阁中可能的文本集合是无数的，但不是每一个集合…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/03/25/a-programmers-guide-to-creating-an-eclectic-bookshelf/) 

我们的变量名应该是什么？如果我们看看我们的 if…else 语句块，我们根据一个名为`career`的变量的值输出字符串(稍后会详细介绍)。有了这些知识，我们缺少的变量名应该是`career`。以下是我们更新后的代码:

```
function yourFutureCareer(){
 var career = Math.random();
  if (career <= 0.32) {
   return = FrontEnd Developer
   else if (career <= 0.65) 
   return : BackEnd Developer,
  } else {
   return 'Full-Stack Developer'
  }yourFutureCareer();
```

当我们查看 if…else 语句时，我们看到了多个语法问题。第一个是在`FrontEnd Developer`和`BackEnd Developer`的返回语句中。对于第一个 return 语句，我们看到一个等号，就好像我们正在将 FrontEnd Developer 赋值给一个名为`return`的变量。当返回一个语句时，在关键字`return`和值之间不应该有任何东西。另一个问题是前端开发者应该是一个字符串。

如果我们看看我们的第二个返回声明，我们看到同样的问题。我们看到一个冒号，它不应该在 return 关键字和 BackEnd Developer 之间，它也应该是一个字符串。此外，逗号应该删除。

我们清理了退货单，以下是我们的更新:

```
function yourFutureCareer(){
 var career = Math.random();
  if (career <= 0.32) {
   return 'FrontEnd Developer';
   else if (career <= 0.65) 
   return 'BackEnd Developer';
  } else {
   return 'Full-Stack Developer';
  }yourFutureCareer();
```

我们差不多完成了，但是还有一个问题。我们缺少一些左花括号和右花括号。我们浏览我们的函数，看看是否每个开括号都有一个闭括号。

在我们声明函数的地方，我们看到一个左花括号，但是右花括号不见了。在调用函数之前，我们在单独的一行插入一个右花括号。

```
function yourFutureCareer(){
 var career = Math.random();
  if (career <= 0.32) {
   return 'FrontEnd Developer';
   else if (career <= 0.65) 
   return 'BackEnd Developer';
  } else {
   return 'Full-Stack Developer';
  }
}yourFutureCareer();
```

在我们的 if…else 语句中，if 块缺少一个右花括号，else if 块缺少一个左花括号。一旦我们添加了这些，我们的程序应该运行良好。

```
function yourFutureCareer(){
 var career = Math.random();
  if (career <= 0.32) {
   return 'FrontEnd Developer';
  } else if (career <= 0.65) {
   return 'BackEnd Developer';
  } else {
   return 'Full-Stack Developer';
  }
}yourFutureCareer();
```

对于这么小的代码，如果您使用 JavaScript 美化器或任何代码格式纠正工具，有时会更容易在某些地方发现缺少了哪些花括号。但是即使有了这些工具，仔细检查也没有坏处，因为有时即使在格式化的代码中，遗漏的左花括号或右花括号也可能会被忽略。

通过这次调试，我们主要了解了更多关于正确的 JavaScript 语法。有时调试几行长的代码时，很容易卡住。大多数时候，最恼人的错误是由小的语法错误引起的，就像我们所经历的那样。除此之外，我们的调试会话到此结束。

您喜欢这篇代码调试文章吗，请查看我的上一篇 JavaScript 调试文章:

[](https://levelup.gitconnected.com/javascript-debugging-function-syntax-364d4d90a4c7) [## JavaScript 调试:函数语法

### 我们要调试一个有不止一个语法问题的程序。这些问题可能是什么？

levelup.gitconnected.com](https://levelup.gitconnected.com/javascript-debugging-function-syntax-364d4d90a4c7)