# Java 枚举，多么特殊的类型！

> 原文：<https://medium.datadriveninvestor.com/java-enums-what-a-special-type-276d27423a71?source=collection_archive---------10----------------------->

![](img/97094822f52983d6c119bef54edda535.png)

Java 枚举是一种特殊类型的[变量](https://myitcareercoach.com/java-variables/)，它允许开发者创建自己的常量。换句话说，开发人员必须在编译时为枚举定义所有可能的值。Java 枚举是 Java 版本 5 的一部分。

当我们提前知道所有可能的值时，我们应该使用 Java 枚举。正如 [App Shah](https://crunchify.com/why-and-for-what-should-i-use-enum-java-enum-examples/) 指出的，“当你需要一个预定义的值列表来表示某种数字或文本数据时，你应该使用枚举。例如，在国际象棋游戏中，你可以用一个枚举来表示不同类型的棋子。所以在那些特殊情况下使用枚举！

# Java 枚举

让我们看看如何定义一个简单的 Java 枚举。

这个 Java 枚举单独存在于一个文件中。它有四种类型的自行车轮胎，山地，公路，混合动力，和自行车越野。此外，您可能注意到枚举的 Java 约定是全部大写。枚举被声明为 public static final，因此不能更改。

# 申报

我们也可以在另一个 Java 类中声明 Java Enum。

在这个自行车类，我们有新的枚举自行车管，我们一起使用我们的自行车轮胎枚举。我们使用 enum 来驱动 *replaceTires* 方法中的 switch 语句。请注意，不能在方法内部声明枚举。

[](https://www.datadriveninvestor.com/2020/01/16/software-development-process-how-to-pick-the-right-process/) [## 软件开发过程:如何选择正确的过程？数据驱动的投资者

### 软件是任何企业组织成功的生命线。没有软件的帮助，一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/01/16/software-development-process-how-to-pick-the-right-process/) 

# 方法

默认情况下，枚举有几个方法。 **values()** 方法将返回枚举中的所有值。我们可以使用 **ordinal()** 方法获得一个类似于数组的枚举的索引。还有一个 **valueOf()** 方法返回单独的值。

以下是这三种方法的一些例子。values()方法有助于迭代枚举值的集合。

# 字段和方法

您可以将字段添加到您的枚举中，也可以创建自定义方法。

我们以之前的 GolfClub enum 为例，在其中添加了一个俱乐部编号。该字段在构造函数中设置。还有一个返回俱乐部号码的方法。

# 集合中的 Java 枚举

Java 在集合中使用枚举有一些很好的特性。例如，有一个 EnumSet 和 EnumMap 专门为它们使用这些工作。

这里我们用一个 EnumSet 来存储一些自行车轮胎，我们有一个 EnumMap 用于一些高尔夫俱乐部。因此，如果你在集合中使用枚举，请记住这些，因为它们会更好地为你服务！

总之，我们已经和你分享了一些使用 Java 枚举的方法以及何时可以使用它们。在我的职业生涯中，我很少使用 Java 枚举。但是，我大概已经忽略了他们很多次了。使用它们有助于提高代码的可读性。

还有哪些用例适合 Java 枚举？

为此鼓掌并在 MyITCareerCoach.com[订阅](https://myitcareercoach.com/)