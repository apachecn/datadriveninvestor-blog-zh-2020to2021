# Jr React 开发人员技术面试问题

> 原文：<https://medium.datadriveninvestor.com/jr-react-developer-technical-interview-questions-eed9058a8b29?source=collection_archive---------0----------------------->

![](img/bc689b601d63a9fb3b43a7f25511e671.png)

Photo by [Siora Photography](https://unsplash.com/@siora18?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

大家好，

如果你是一名 javascript 和 react 开发人员，像我一样打算申请一个入门级/初级职位，这里有一些我发现自己值得研究的常见问题！所以还是挺过去吧！

# 1.React 的主要优势是什么？

*   使用组件，UI 测试变得更加容易
*   提高应用程序的性能
*   JSX 可读性
*   服务器端渲染

# 2.什么是 React 组件？

*   组件是 React 的建筑材料
*   组件将用户界面分解成可重用的部分

# 3.React 中为什么要用箭头函数？

*   您不必使用箭头函数，但是当我们在 React 的函数中使用“this”关键字时，“this”需要访问函数外部的**类**，使用箭头函数允许“this”关键字访问该类。

# 4.道具和状态的区别？

*   “Props”和“State”都是 React 中的数据值，但“Props”是不可变的值，而“State”是可变的，这意味着它可以随时间而改变。

# 5.Redux 是什么？

*   Redux 是一个 React 库和一个可预测的状态容器
*   Redux 帮助开发人员构建性能一致且易于测试的 web 应用程序

# 6.Redux 中真理的单一来源是什么？

*   Redux 拥有整个应用程序的**全局存储库**

# 7.什么是反应事件？

*   事件是由特定用户操作触发的反应
*   例如 onClick、onChange、onFocus、onMouseMove…

# 8.“类组件”与“功能组件”

*   类组件有“render”方法，管理**状态**或使用组件**生命周期方法**
*   功能组件接受**道具**作为参数。这只是象征性的。

# 9.什么是 JSX？

*   JSX 是 Javascript 中一种类似 HTML 的语法，并将它们放在 **DOM** 中

# 10.虚拟 DOM？

*   它是实际 DOM(文档对象模型)的副本
*   React 使用这个副本来确定实际 DOM 中需要根据用户动作进行更改的特定部分
*   它最终会显著提高性能

# 11.为什么是 HOC？

*   我们使用 HOC 是为了在组件之间共享公共功能
*   在这种模式下，函数将一个组件作为参数，并返回一个新的组件
*   ex)const new component = higherOrderComponet(original component)

这就对了。关于 React 还有很多更难的问题，但我相信这会让你为初级/入门级技术面试做好准备！希望这对你有所帮助，祝大家好运！

[](https://www.datadriveninvestor.com/2019/01/23/which-is-more-promising-data-science-or-software-engineering/) [## 数据科学和软件工程哪个更有前途？数据驱动的投资者

### 大约一个月前，当我坐在咖啡馆里为一个客户开发网站时，我发现了这个女人…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/23/which-is-more-promising-data-science-or-software-engineering/)