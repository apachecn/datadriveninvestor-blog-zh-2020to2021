# 面试问 Java 开发者什么？

> 原文：<https://medium.datadriveninvestor.com/what-to-ask-java-developer-in-interview-fbdc12152064?source=collection_archive---------13----------------------->

![](img/ee330b29e4599cf75a5b0e8d58bc4ef6.png)

我们继续我们的采访问题。今天我们将讨论你应该向 Java 开发人员询问什么。按照传统，我们会考虑基础问题并给出答案，然后针对高级开发者讨论问题。

# 介绍

在本文中，我们将讨论 Java 8 版本。首先，会涉及一些基本问题，然后我们会切换到更高级的问题。让我们从头开始，从基础开始。

## 问题 Java 是什么？

这似乎是一个非常简单的问题，对吗？好吧，那么你应该得到一个清晰明确的答案。这里有一个选择。

Java 是一种面向对象的、安全的高级编程语言。它是由一个叫詹姆斯·高斯林的人在 1991 年创造和开发的。Java 语言是在“WORA”的口号下开发的——“一次编写，随处运行”(一次编写，随处运行)。它以灵活高效著称。

![](img/f69d50771daaa978926cabeee70b31f5.png)

## **问题 Java 是完全面向对象的语言吗？**

这是一个很好的 Java 面试问题，而且不，*它并不完全面向对象。Java 使用一些不是对象的数据类型(char，byte，float)。*

## 问题 Java 有哪些好处？

对于新手程序员和开发者来说，最重要的特点就是简单。人们认为 Java 函数相当容易学习，尤其是与其他编程语言相比。

与其他编程语言相比，Java 编程语言也被认为是非常安全的。这是通过一个叫做 JVM 的解释器来实现的——这个解释器是随 Java 一起安装的，它不断地从互联网上为你的计算机提供最新的安全更新。

[](https://www.datadriveninvestor.com/2020/01/16/software-development-process-how-to-pick-the-right-process/) [## 软件开发过程:如何选择正确的过程？数据驱动的投资者

### 软件是任何企业组织成功的生命线。没有软件的帮助，一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/01/16/software-development-process-how-to-pick-the-right-process/) 

*另外，Java 的适应性也很强。多亏了 Java 语言所基于的“WORA”原则，它可以在你需要的任何计算机和操作系统上移植和使用——它是完全灵活和多功能的。*

## 问题 Java 8 的特点是什么？

在 Java 中，开发人员必须像这样清楚地回答比较问题。*这是最大的语言更新之一，所以最好能知道它们是什么。*

*Java 8 引入了对字符串的语言支持，提供了改进的日期/时间 API，并为 JVM 的开发做出了贡献，JVM 是一个负责 Java 中许多事情的系统，包括 Java 的安全功能。总的来说，Java 8 使编程语言变得更容易理解，更类似于现代编程语言。*

## 问题 Java 中的访问说明符是什么？

有四个候选人应该理解的访问说明符。有以下限定符:公共的、私有的、受保护的和标准的。

*公共限定符允许访问任何类或通过任何方法(因此得名)。相反，私有说明符只允许在指定的类本身内访问。受保护的类开放了与类相关的访问——或者来自类内部，或者来自子类，或者只是来自同一个包。最后，default 表示一个标准区域，只允许从一个包中访问。*

## 问题 6:什么是构造函数？

*构造函数是一段初始化特定对象的代码。Java 编程语言有两种类型的构造函数——默认的和修改的。*

## 问题 7:什么是对象？

Java 工作面试中的一个普遍问题。Java 中的对象有状态和行为。对象最常见和最容易理解的定义是它是类的一种类型。

## 问题 Java 中可以有哪些对象引用？

这是一个最简单的问题— *在 Java 中，所有的对象引用都是 null。*

## 问题 9:JDK、JVM 和 JRE 有什么区别？

*JDK (Java 开发包)是一个 Java 开发包。这是用这种语言编译程序的主要 Java 函数工具。这个包有开始使用它的所有必要工具。*

*我们前面已经提到了 JVM (Java 虚拟机)——这是指 Java 虚拟机。这是一台创建 Java 字节码被正确处理的环境的机器。*

*JRE (Java 运行时环境)是一个 Java 运行时环境。这就是 JVM 提供的环境类型——它允许 Java 字节码正常工作。*

既然我们已经讨论了一些基本问题，我们可以继续讨论针对有经验的开发人员和程序员的问题。这些问题将主要与代码相关。

![](img/5b1abc376009b3e0714c48f19a40783e.png)

# 高级问题

## 问题 1:“方法重载”和“方法重写”有什么区别？

这可能是你在 Java 面试中问的第一个问题。*在‘方法重载’的情况下，属于同一个类的方法名称相同，但参数不同。这更适用于方法行为的扩展。相反，“方法覆盖”子类拥有相同名称和参数的方法。这里的目标是改变现有方法的行为。*

## 问题 2:这个 Java 程序的结论是什么？

```
public class Test
{
Test (int x, int y)
{
System.out.println ("x =" + x + "y =" + y);
}
Test (int x, float y)
{
System.out.println ("x =" + x + "y =" + y);
}
public static void main (String args [])
{
byte x = 30;
byte y = 65;
Test test = new Test (x, y);
}
}
```

正确答案看起来是这样的:
*a = 30 b = 65*

## 问题 3:没有' main()方法可以运行程序吗？

一个非常标准的 Java 面试问题*是的，这是可能的。运行这种程序最常见的方法之一是使用静态块。*

## 问题 4:什么是“运行时多态性”？

运行时多态性是一个过程，其中使用特定方法发送的特定调用将在运行时解决，而不是在编译时解决。下面是一个例子:

```
class Tree {
void run ()
{
System.out.println ("tree is standing");
}
}
class Willow extends Tree {
void run ()
{
System.out.prinltn ("willow is standing on a hill");
}
public static void main (String args [])
{
Tree b = new Willow (); // upcasting
b.run ();
}
}
```

## 问题 5:什么是‘继承’？

坦率地说，这个术语只是表面现象。*继承是指一个对象获得另一个对象(另一个类)的属性和参数。上面讨论的覆盖方法使用了这一点。继承的基本思想是你可以在现有的类上创建新的类。有五种不同类型的继承，但是 Java 编程语言只支持四种(不支持多重继承)。为什么不支持多重继承？其实具体原因只有一个——简化程序。*这应该是建议考生记住的重要注意事项。

## 问题 Java 中存在的最大的类(超类)是什么？

*这是最简单的问题之一。Java 中最大的是 object 类。*

## 问题 Java 中的超级前缀是什么意思？

*Java 中的 Super 作为引用指向类的直接父类。您也可以使用命令来叫用类别和建构函式的直接父方法。*

## 问题 8:这个项目的结果会是什么？

```
class Animal
{
public Animal ()
{
System.out.println ("Animal class constructor called");
}
}
public class Zebra extends Animal
{
public Zebra ()
{
System.out.println ("Zebra class constructor called");
}
public static void main (String args [])
{
Zebra e = new Zebra ();
}
}
```

下面是答案:
*动物类构造函数叫
斑马类构造函数叫*

## 问题 Java 中的‘关联’是什么？

这是一个关于 Java 编程的常见问题。乍一看，这似乎很简单。然而，像聚合和组合这样的东西来自于关联，所以开发人员清楚地理解这个术语是很重要的。

*关联是指所有对象都有自己的生命周期，并且不存在特定的所有者。范围可以从“一个”到“多个”。*

## 问题 10:什么是“对象克隆”？

*“对象克隆”命令用于创建一个对象的相同副本。这是使用 object 类中的 clone()方法完成的。*

![](img/f76a01b3faf12ed3e6099c0fcc92777e.png)

## 结论

编程专家总是很吃香。Java 是世界上最流行的编程语言之一(由于它的灵活性、安全性和简单性)。在本文中，我们已经了解了 Java 面试问题，这些问题将帮助您评估候选人的知识。

剩下你要做的就是举行一次面试，为 Java 开发人员的职位选择一个有能力的员工！

*原载于 2020 年 5 月 13 日*[*https://geniusee.com*](https://geniusee.com/single-blog/what-to-ask-java-developer-in-interview)T22。