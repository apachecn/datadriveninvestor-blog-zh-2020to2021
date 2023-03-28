# 有用的 JavaScript 技巧——时间和数字

> 原文：<https://medium.datadriveninvestor.com/useful-javascript-tips-time-and-numbers-f3050d299cbd?source=collection_archive---------15----------------------->

![](img/981464fffd21d75602f1b17c2628921a.png)

Photo by [Brooke Lark](https://unsplash.com/@brookelark?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

像任何类型的应用程序一样，JavaScript 应用程序也必须写得很好。

否则，我们以后会遇到各种各样的问题。

在本文中，我们将了解一些应该遵循的技巧，以便更快更好地编写 JavaScript 代码。

[](https://www.datadriveninvestor.com/2020/06/26/understanding-software-project-management/) [## 关于成为软件项目经理|数据驱动投资者的思考

### 我做程序员已经 3 年了，我想是时候领导我自己的团队了。作为项目经理，我现在可以…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/06/26/understanding-software-project-management/) 

# 获取当前时间戳

有几种方法可以从`Date`实例获得 UNIX 时间戳。

时间戳是从 UTC 时间 1970 年 1 月 1 日上午 12 点开始的毫秒数。

我们可以使用`Date.now()`方法来获取时间戳。

然后我们得到类似于 1589399748029 的结果。

我们也可以使用`new Date().getTime()`方法。

`new Date().valueOf()`做同样的事情。

为了用秒来表示时间戳，我们只需将它除以 1000。

所以我们可以写:

```
Math.floor(Date.now() / 1000)
```

# 这个的价值

`this`根据使用场合的不同，可以取不同的值。

在一个对象之外，`this`在严格模式下总是`undefined`，

否则，它就是全局对象。

`this`将绑定到方法顶层的对象。

例如，如果我们有:

```
const person = {
  name: 'james',
  greet() {
    console.log(`hi ${this.name}`)
  }
}
```

然后当我们调用`person.greet()`时，我们已经记录了`'hi james'`。

`this`不绑定到箭头函数。它只是在外面取`this`的值。

我们也可以显式设置`this`的值。

为此，我们可以使用`bind`方法来完成。

例如，我们可以写:

```
const joe = person.greet.bind({ name: 'joe' });
```

然后当我们调用`joe`时，我们得到`'hi joe'`。

`bind`返回函数。

我们可以改变`this`的值，用`call`和`apply`调用新`this`的函数。

例如，我们可以写:

```
person.greet.call({ name: 'joe' });
```

或者:

```
person.greet.apply({ name: 'joe' });
```

两者的区别在于他们如何对待论点。

例如，如果我们有:

```
const person = {
  name: 'james',
  greet(greeting) {
    console.log(`${greeting} ${this.name}`)
  }
}
```

那么我们可以通过书写来称呼`person.greet`:

```
person.greet.call({ name: 'joe' }, 'hello');
```

然后我们得到`'hello james'`，因为我们把`'hello'`作为第一个参数传入。

为了调用`apply`，我们将参数作为数组传递。

例如，我们写道:

```
person.greet.call({ name: 'joe' }, ['hello']);
```

然后我们得到同样的结果。

在 HTML 事件元素处理程序中，`this`被绑定到元素。

例如，如果我们有:

```
document.querySelector('button').addEventListener('click', function(e) {
  console.log(this) 
}
```

那么`this`的值就是按钮。

# 将字符串转换为数字

有许多方法可以将字符串转换成数字。

## 数字

我们可以用`Number`函数将一个字符串转换成一个数字。

例如，我们可以写:

```
const count = Number('123');
```

那么`count`就是`'123'`。

## parseInt

要将字符串解析成整数，我们可以使用`parseInt`。

例如，我们可以写:

```
const count = parseInt('123', 10)
```

第一个参数是要转换的字符串，第二个参数是基数。

然后我们将字符串转换成十进制。

只要数字以数字开头，它就会转换数字部分。

如果我们有:

```
const count = parseInt('123 bottles', 10)
```

然后我们得到 123。

## parseFloat

为了将一个字符串解析成一个浮点数，我们可以使用`parseFloat`。

例如，我们可以写:

```
parseFloat('1.20')
```

然后我们得到 1.2。

## 一元+

同样，我们可以使用`+`操作符来做与`parseFloat`相同的事情。

例如，我们可以写:

```
+'1.20'
```

得到同样的东西。

## 数学.地板

同样，我们可以使用`Math.floor`将一个字符串舍入到它的底部。

我们可以直接将一个字符串传递给这个方法，它会为我们进行转换。

例如，如果我们写:

```
Math.floor('9.81')
```

我们得到 9。

## 使用`* 1`

我们可以将一个字符串乘以 1，转换成一个数字。

例如，我们可以写:

```
'9.20' * 1
```

我们得到 9.2 分。

# 将数字格式化为货币值

JavaScript 有一个`Intl.NumberFormat`构造函数将数字转换成货币值。

例如，我们可以写:

```
const formatter = new Intl.NumberFormat('en-US', {
  style: 'currency',
  currency: 'USD',
  minimumFractionDigits: 2
})

const price = formatter.format(888);
```

然后我们得到`“$888.00”`作为`price`的值。

`style`是格式样式，我们将其设置为`'currency'`以将其转换为货币字符串。

`currency`是我们要将字符串格式化的货币。

`minimumFractionDigits`是小数位数的最小值。

![](img/83b2a41066f4a32d179752ef904093ab.png)

Photo by [Mike Benna](https://unsplash.com/@mbenna?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 结论

我们可以用数字做很多事情。

我们可以将它们格式化为货币字符串。

此外，有许多方法可以将字符串转换为数字。

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)