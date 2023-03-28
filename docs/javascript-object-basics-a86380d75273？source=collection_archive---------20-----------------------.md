# JavaScript 对象基础

> 原文：<https://medium.datadriveninvestor.com/javascript-object-basics-a86380d75273?source=collection_archive---------20----------------------->

## 学习 web 开发

![](img/c86fe77efb6936f8d60716f4b25b2b72.png)

Photo by [🇨🇭 Claudio Schwarz | @purzlbaum](https://unsplash.com/@purzlbaum?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

大多数开发人员将 OOP 与通常在学校教授的语言联系在一起，如 Java、ObjectC++和 C#。他们熟悉类，当他们开始学习 JavaScript 时，他们会感到困惑，因为 JavaScript 没有对类的正式支持。JavaScript 中的对象是可变的键控集合，比如数组、函数、正则表达式等等。

> 记住，在 JavaScript 中，**数组**是**对象**，**函数**是**对象**，**正则表达式**是**对象**，对象是对象。

在本帖中，我们将讨论以下主题。

*   定义和添加对象
*   向对象添加属性
*   访问属性
*   检测属性
*   防止对象修改
*   删除属性
*   删除对象

# 如何在 JavaScript 中定义一个对象？

在 JavaScript 中创建对象有多种方法，但有 3 种最简单的方法。

## 使用对象文字

在 JavaScript 中定义对象最简单的方法是使用对象文字。

*   首先，我们从一个空白对象开始

```
var circle = {
}console.log(circle)
**<< {}**
```

*   然后我们给这个对象添加一个属性

```
circle.radius = 10console.log(circle)
**<< { radius: 10 }**
```

*   最后，我们向它添加一个方法

```
circle.grow =  function () {
    this.radius++
}
```

看看它是如何工作的？

```
console.log(circle)
**<< { radius: 10, grow: [Function] }**circle.grow()
console.log(circle)
**<< { radius: 11, grow: [Function] }**
```

在上面的例子中，我们从一个空对象开始，然后向它添加一个属性和一个方法(函数)。我们创建的对象总是可以修改的，除非我们另外指定。

> 请记住，JavaScript 中的对象是动态的，这意味着它们可以在代码执行过程中的任何时候发生变化。

## 使用内置构造函数

另一种方法是，我们可以使用内置的构造函数——Object()，但它是反模式的。现在已经不鼓励了。

```
// add an empty object
var circle = new Object()

// add a property
circle.radius = 10

// add a method
circle.grow =  function () {
    this.radius++
}

console.log(circle)
**<< { radius: 10, grow: [Function] }**circle.grow()

console.log(circle)
**{ radius: 11, grow: [Function] }**
```

## 使用自己的自定义构造函数

除了前面的方法，我们还可以使用自己的自定义构造函数创建对象，如下例所示。

```
var Circle = function(radius) {

    this.radius = radius
    this.grow = function () {
        this.radius ++
    }
}
```

看看它是如何工作的？

```
firstCircle = new Circle(10)
console.log(firstCircle)
**<< Circle { radius: 10, grow: [Function] }**secondCircle = new Circle(12)
console.log(secondCircle)
**<< Circle { radius: 12, grow: [Function] }**secondCircle.grow()
console.log(secondCircle)
**<< Circle { radius: 13, grow: [Function] }**
```

这里有一个低效的地方，如果我们在任何时候调用一个新的 Circle(…)，就会在内存中创建一个新的 grow()函数。我们可以使用 prototype 关键字来更好地改进代码。

```
Circle.**prototype**.grow = function () {
        this.radius ++
}
```

# **查找对象的属性**

我们可以使用操作符中的*来测试一个属性的存在。*操作符中的*在特定对象中查找具有给定名称的属性，如果找到则返回 true。*

> *记住，in 操作符检查自己的属性和原型属性。*

例如，当它用于检查 circle 对象中的某些属性时，会发生以下情况。

```
console.log(“radius” in circle)
**<< true**
```

因为方法只是引用函数的属性，所以你可以用同样的方法。

```
console.log(“grow” in circle)
**<< true**
```

> 请记住，方法只是属性。

为了确保只返回对象自己的属性，可以预先实现一个快速检查。

```
var key = "radius"
if (circle.hasOwnProperty(key)) {
    console.log(key + “: “ + circle[key])
}
**<< radius: 10**
```

通过 toString()方法，是所有对象上都存在的原型属性。

```
console.log(circle.hasOwnProperty("toString"))
**<< false**
```

# 更新属性

我们可以在任何时候使用赋值来改变属性的值。例如，我们可以像这样改变*半径*属性的值。

```
circle.radius = 15
console.log(circle)
**<< Circle { radius: 15, grow: [Function] }**
```

# **移除属性**

使用`delete`操作符可以从对象中删除任何属性。例如，如果我们想从 *circle* 对象中删除 *grow* 函数，我们将输入以下内容。

```
delete circle.grow
**<< true**console.log(circle)
**<< Circle { radius: 10 }**
```

# 如何防止对象修改？

像属性一样，对象也有控制其行为的内部属性。其中一个属性是[[Extensible]]，它是一个布尔值，表示对象本身是否可以修改。默认情况下为 true，这意味着可以随时向对象添加新属性。

您可以使用 Object.isExtensible()来检查[[Extensible]]的值。

```
Object.isExtensible(circle)
**<< true**
```

创建不可扩展对象的一种方法是使用 Object.preventExtensions()。

```
Object.preventExtensions(circle)
Object.isExtensible(circle)
**<< false**
```

一旦你在一个对象上使用了这个方法，你就再也不能添加任何新的属性了。

```
// add a method
circle.shrink = function() {
    circle.radius--
}// cannot add new methods
console.log(circle)
**<< Circle { radius: 10, grow: [Function] }**
```

# 删除对象

在 JavaScript 中，你不能自己销毁一个对象，但是你可以把它标记为删除。`delete`操作符只删除一个引用，而不是对象本身。

> 请记住，你不能自己摧毁一个物体。使用`**delete**`关键字将删除对该属性的引用。

要做到这一点，您需要理解当一个对象上的所有引用被移除时，该对象将被自动删除。

很简单，对吧？希望我已经涵盖了一切。

[](https://www.datadriveninvestor.com/2020/03/29/microsoft-having-an-edge-over-chrome/) [## 数据驱动的投资者|微软比 Chrome 有“优势”

### 简史我从来不是浏览器的粉丝，确切地说，我只是一个浏览器的粉丝，Chrome。这是我的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/03/29/microsoft-having-an-edge-over-chrome/) 

感谢阅读😘，再见👋，别忘了👏最多 50 次并跟随！