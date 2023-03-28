# Java 常量的方式

> 原文：<https://medium.datadriveninvestor.com/the-way-of-the-java-constant-8b25eac06bc1?source=collection_archive---------19----------------------->

![](img/1478478e77f4036f98e136aa209e3d97.png)

Java 常量可以帮助您创建可读性更强的代码。我们可以创建一个名为 SALES_TAX 的常量[变量](https://myitcareercoach.com/java-variables/),而不是在你的代码中加入 5%。换句话说，当它上升时，你可以在一个地方改变 Java 常量！

# Java 常量

当你创建新的应用程序时，你会碰到一些不应该改变的东西。就像前面提到的 SALES_TAX，你不希望有人不经意间把它改了。Java 有一个关键字 final，它确保了 Francis 在 Stripes 中所说的“没人能碰我的东西！”

这个例子给你一个 Java 常量的例子。注意，在 Java 中，我们通常将常量声明为 static 和 final。但是，这确保了类只有一个副本，而不是每个实例都有一个。大写也是典型的代码约定。这有助于它从其他变量中脱颖而出。

# 易读的

常量有助于使代码对我们人类来说更具可读性。编译器和计算机并不在乎。和前面的例子一样，我们可以用一个常数来表示销售税。此外，下一个查看代码的开发人员可以知道发生了什么。同样，给常数取个好名字也很重要。

[](https://www.datadriveninvestor.com/2020/01/16/software-development-process-how-to-pick-the-right-process/) [## 软件开发过程:如何选择正确的过程？数据驱动的投资者

### 软件是任何企业组织成功的生命线。没有软件的帮助，一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/01/16/software-development-process-how-to-pick-the-right-process/) 

# 接近

总的来说，大多数常量应该被广泛使用，并且可以用于所有的类。但是，在极少数情况下，一个类需要一个常量。在这种情况下，您可以使用 private 修饰符。对于所有其他情况，您可以使用 public 修饰符。

# Java 的持续优势

使用 Java 常量有几个重要的好处。第一个我们已经提到的是可读性。在这之后，下一个就是改变的难易程度。改变一个常量可以很快地在代码中查找所有出现 5%的情况。名称一致性是使用常数的另一个好处。

# 数学常数

Java API 提供了一些常量供您使用。让我们来看看其中的一些。

这里我们使用了 [java.lang.Math](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html) 包中的两个常量。圆周率和 E 可以用在你需要的任何计算中。

总之，如果使用正确，Java 常量会很有帮助。从提高可读性到帮助控制访问，在代码中使用它们是一个不错的选择。

**你在哪里见过 Java 常量被误用？**

为此鼓掌并在[MyITCareerCoach.com](https://myitcareercoach.com/)订阅