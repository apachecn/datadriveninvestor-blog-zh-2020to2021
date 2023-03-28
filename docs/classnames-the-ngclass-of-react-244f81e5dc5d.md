# “类名”反应的 ng 类

> 原文：<https://medium.datadriveninvestor.com/classnames-the-ngclass-of-react-244f81e5dc5d?source=collection_archive---------1----------------------->

![](img/5fb3f47356b31c9404e95afbcb070b44.png)

没有什么比在元素上对类进行良好的条件呈现更好的了。

但作为 React 中不存在的许多东西之一，条件类 render 也是其中之一。我的意思是，对于如何实现要实现的类，有一些变通办法，例如:

让我们在下面的组件中使用数组方法在条件改变时添加/删除类

```
class App extends Component {
state = {flag: false};onClickHandler = () => {this.setState({flag: !this.state.flag});};render() {
const classes = ["btn", this.state.flag ? "btn-green" : "btn-red"].join(" ");return (
 <div className="align-center ">
   <button className={classes} onClick={this.onClickHandler}>
     Click me!
   </button>
 </div>
 );}
}
```

![](img/7707287c5c618ec823d642320ad52aab.png)

Conditional Button Color

这种方法的一个主要问题是，随着需要基于条件的类的元素数量的增加，维护代码变得更加困难。

[](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) [## 2019 年最值得学习的编码语言|数据驱动的投资者

### 在我读大学的那几年，我跳过了很多次夜游去学习 Java，希望有一天它能帮助我在…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) 

处理这个问题的一个最优选的方法是，添加一个名为 [**类名**](https://www.npmjs.com/package/classnames) **的依赖库。**

> 什么是**类名:**

classnames 是一个在 React 中为我们提供条件类选择的库。因为它是直接在 **classNames** 属性中实现的，所以它不会妨碍代码的可维护性，并帮助我们编写更简洁的代码。

> I 安装和导入**类名**:

```
installing -> npm install classnames --saveimporting to js ->import **cn** from 'classnames'
```

这个 **cn** 是一个可以接受 *n* 个参数的函数，每个参数都是一个定义好的 css 类。这个函数完成后返回一个包含所有连接参数的字符串。

```
className={cn("btn","h-100",w-100")}
```

要添加一个条件类，必须在对象符号中定义该类，其中*键*是字符串形式的类名，而*值*返回一个布尔值。

```
className={cn(
  { "btn-green": this.state.flag },
  { "btn-red": !this.state.flag }
 )}
```

让我们使用**类名**更新上面的例子:

```
import React, { Component } from "react";
import cn from "classnames";class App extends Component {
state = {flag: false};onClickHandler = () => {
 this.setState({flag: !this.state.flag});
};render() {
return (
<div className="align-center ">
 <button className={cn("btn",
  { "btn-green": this.state.flag },
  { "btn-red": !this.state.flag }
 )}
 onClick={this.onClickHandler}>
  Click me!</button>
</div>);}
}
export default App;
```

这将产生与上面相同的输出，但这是一个更干净的方法，从长远来看是有帮助的。

我希望这能让你了解如何在 React 中基于一些布尔值来添加/删除类，它不像 ngClass 那么简单，但它能完成工作。