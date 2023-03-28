# 什么是 Java 代码块以及如何使用它们

> 原文：<https://medium.datadriveninvestor.com/what-are-java-code-blocks-and-how-to-use-them-f0df15873fb6?source=collection_archive---------0----------------------->

![](img/078d7d72f55193b669280f3978faf905.png)

代码只不过是文本和空白。任何人都可以把代码输入计算机。但是让它可读完全是另一回事。让我们回顾一下 Java 代码块的一些关键部分，以及如何将其放入可读的程序中。代码块类似于 Java [包](https://myitcareercoach.com/ship-your-java-in-a-package/)，但是有不同的用途。

# Java 代码块

Java 喜欢把事情放在行间，不要用花括号({})。这就是我们如何在 Java 中开始和停止代码块。大括号让编译器知道我们要从哪里开始({)和结束(})。

在我们的第一个例子中，我们有两个而不是一个代码块。首先，对于第 3 行带有左大括号的 JavaCodeBlock 类。接下来的 online 4，我们用另一个大括号打开 main 方法。然后我们在第 6 行为 main 方法关闭它，在第 7 行为类关闭它。一个专业提示，当你把光标放在大括号旁边时，大多数 ide 会高亮显示右大括号，反之亦然。

在这个例子中，我们有一个 if-else，每个都有自己的代码块。我们没有必要这样做，但这有助于提高可读性。稍后，我们还有一个随机代码块。如果你是开发新手，这看起来应该是错误的，但这是完全合法的。

[](https://www.datadriveninvestor.com/2019/01/23/which-is-more-promising-data-science-or-software-engineering/) [## 数据科学和软件工程哪个更有前途？数据驱动的投资者

### 大约一个月前，当我坐在咖啡馆里为一个客户开发网站时，我发现了这个女人…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/23/which-is-more-promising-data-science-or-software-engineering/) 

# 匿名的

匿名代码块非常突出。它们也被称为*实例初始化块*。它们在调用构造函数之前运行。

正如你在这个例子中看到的，我们可以把匿名代码块放到类中，它将在构造函数之前被调用。如果运行这个示例，输出将是。

```
Anonymous Code Blocks
Constructor
```

这些有用吗？这是有人在 StackOverflow.com 的[上问的一个很棒的问题。剧透警报！不完全是…](https://stackoverflow.com/questions/1563030/anonymous-code-blocks-in-java)

# 命名代码块

我们也可以创建代码块并给它们命名。不像你的宠物石头，这些可以是有用的。

这里我们看到如何使用命名代码块跳出 if 语句。同样的事情也可以在循环之外完成。许多开发人员认为这类似于使用 goto 语句。因此你可能要避免使用这个。

# 静态

Java 有另一个代码块，叫做静态代码块，因为我们对它们使用了 static 关键字。

在本例中，您可以看到静态代码块，然后是普通的构造函数。当我们运行它时，我们会看到有趣的部分变得生动起来。

```
static block called 
StaticCodeBlockTest Constructor called
```

奇怪的是，静态块在构造函数运行之前被调用。静态代码块只被调用一次。

总之，Java 有很多方法来使用和定义代码块。一些比另一些更有用。您可能会在遗留代码中遇到这些问题。在我多年的 Java 开发生涯中，我偶然发现了其中的大部分。

你使用过这些 Java 代码块吗？