# Web 开发框架和 Node.js 的重要性

> 原文：<https://medium.datadriveninvestor.com/web-development-frameworks-and-why-node-js-matters-dc5850fa93df?source=collection_archive---------23----------------------->

## 对什么是框架以及 Node.js 通过 Express.js 框架和 MEAN 堆栈带来了什么的基本回顾

## 什么是 web 开发框架？

现在有很多 web 开发框架:Rails、Django 和 Laravel 等等。在很高的层面上，框架是一种编程语言和一组使用该语言的代码库和工具的组合，允许我们构建 web 应用程序的结构和功能。这种结构包括浏览器理解的前端(客户端)语言和后端(服务器端)语言，后者编写附加应用程序逻辑并与任意数量的 [SQL 或 NoSQL 数据库](https://www.mongodb.com/nosql-explained/nosql-vs-sql)通信。前端浏览器、后端服务器和数据库统称为“栈”，而一个[全栈](https://www.w3schools.com/whatis/whatis_fullstack.asp)开发者是能够用各种语言和工具的组合对这三者进行编程的人。前端包括:

*   **HTML:** 一种基本的结构化语言，创建了页面的框架，如文本、标题、段落和图像。
*   CSS: 一种样式语言，它将视觉元素添加到 HTML 中，比如颜色和边框。它“皮肤”一个页面，给它一个特殊的外观和感觉。
*   **JavaScript:** 一种向页面添加逻辑并使其具有交互性的脚本语言，允许静态页面通过基于用户动作、多媒体控件等更新内容而变得动态。

这三种语言合起来就是浏览器所能理解的全部。有像 React 这样的前端框架，本质上也是一个健壮的 JavaScript 库，它简化了网页结构和功能的构建。像 Ruby on Rails 和 Django 这样的框架适合不同的开发设计模式，将前端和后端结合成一个单一的 MVC 或 MVT 模型。Rails 也可以严格地用作后端 API，将它从 MVC 模式中分离出来，并允许您使用独立的前端框架，如 React。这就是说，有许多不同的设计模式可供选择，每种模式都有其用例以及优缺点，但在 [Node.js](https://nodejs.org/) 运行时环境出现之前，它们都有一个共同点:它们都没有在整个堆栈中完全用 JavaScript 实现。他们使用了 Python，Ruby，PHP，C#，以及其他语言。

## 那又怎样？

在浏览器和服务器上运行 JavaScript 有很多好处，尤其是允许开发人员做以前不可能或很难实现的事情。让我们深入一些细节。

几十年来，开发人员一直使用 web 的无状态请求-响应范式。它是无状态的，因为当客户端向服务器发送请求时，服务器发送响应，并立即忘记客户端。一般来说，连接是单向的，因为客户端必须总是发起连接。这些年来已经有了变通方法，包括 Flash 和 Java 小程序，它们都是安全噩梦，并且已经在网上被弃用。还有 [WebSocket API](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API) ，它今天仍然广泛用于客户端和服务器之间的有状态通信，但是这是另一个独立于 HTTP 的协议，需要实现。

进入 Node.js，这是一个 JavaScript 运行时环境，它在 web 浏览器之外执行 JavaScript 代码，允许您在服务器上使用它，并在整个堆栈中围绕单一编程语言统一 web 开发。托米斯拉夫·卡潘[写下了这些好处](https://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js):

> Node.js 在通过 websockets 使用推送技术的实时 web 应用程序中大放异彩。这有什么革命性的？在经历了 20 多年基于无状态请求-响应范式的无状态 web 之后，我们终于有了具有实时双向连接的 web 应用程序，其中客户端和服务器都可以发起通信，允许它们自由地交换数据。这与典型的 web 响应范例形成了鲜明的对比，在典型的 web 响应范例中，客户端总是发起通信。此外，它完全基于运行在标准端口 80 上的开放 web 堆栈(HTML、CSS 和 JS)。

![](img/7ac00ae084e41c6b7febc6566bd2bf5e.png)

由于 Node.js 能够以高吞吐量处理许多并发连接，这也使得它具有高度的可伸缩性，因此在连接性方面有所提高。Node.js 的一个主要禁忌是 CPU 密集型、繁重的计算任务，因此另一个解决方案可能更合适。

在整个栈中使用 JavaScript 的平均栈中使用像[这样的统一语言有很多重要的优势。对于开发人员来说，软件性能和生产率都有所提高。一种语言和一种完全基于该语言的数据交换格式(](https://www.mongodb.com/blog/post/the-mean-stack-mongodb-expressjs-angularjs-and) [JSON](https://www.json.org/) — JavaScript 对象符号)！到目前为止，[最流行的](https://medium.com/javascript-in-plain-english/top-10-node-js-frameworks-for-web-app-development-in-2020-21-38e3ea2a57e5) Node.js 框架是 [Express](https://expressjs.com/) ，以其轻量级、灵活、可伸缩和完全可定制的设计而闻名。让我们概括一个 JavaScript 无处不在的范例堆栈(MEAN stack)的例子:

*   前端(浏览器)的 JavaScript 带有 [AngularJS](https://angularjs.org/) ，它扩展了 HTML 属性以获得更多功能
*   后端快速(服务器)
*   MongoDB 作为 NoSQL 数据库，以类似 JSON 的格式存储文档

来自 MongoDB 博客:

> 通过全程使用 JavaScript 编码，我们能够在软件本身和开发人员的生产力方面实现性能提升。使用 MongoDB，我们可以以类似 JSON 的格式存储文档，在基于 ExpressJS 和 NodeJS 的服务器上编写 JSON 查询，并将 JSON 文档无缝地传递给 AngularJS 前端。当存储在数据库中的对象与客户端 JavaScript 看到的对象基本相同时，调试和数据库管理就变得容易多了。更好的是，在客户端工作的人可以很容易地理解服务器端代码和数据库查询；全程使用相同的语法和对象使您不必考虑多种语言最佳实践，并降低了理解代码库的门槛。

## 结论

Node.js 可能不是每个应用程序的正确解决方案，但它通过将堆栈统一在一种语言下提供了非常独特的东西，因此提高了开发人员的生产率，同时降低了入门门槛，并在许多用例中提高了性能和可伸缩性。

## 参考资料和其他资源

*   [NoSQL vs SQL 数据库](https://www.mongodb.com/nosql-explained/nosql-vs-sql)
*   [什么是全栈？](https://www.w3schools.com/whatis/whatis_fullstack.asp)
*   [MVC 和 MVT 设计模式](https://www.geeksforgeeks.org/difference-between-mvc-and-mvt-design-patterns/)
*   [Node.js](https://nodejs.org/)
*   [Flash 和 Java 小程序的死亡](https://www.i-programmer.info/news/86-browsers/8783-death-of-flash-and-java.html)
*   [WebSocket API](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)
*   [为什么要用 Node.js？案例教程](https://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js)
*   [平均栈:MongoDB、ExpressJS、AngularJS 和 Node.js](https://www.mongodb.com/blog/post/the-mean-stack-mongodb-expressjs-angularjs-and)
*   [JavaScript 对象符号](https://www.json.org/)
*   [2020–21 年 Web App 开发十大 Node.js 框架](https://medium.com/javascript-in-plain-english/top-10-node-js-frameworks-for-web-app-development-in-2020-21-38e3ea2a57e5)
*   [快递框架](https://expressjs.com/)
*   [棱角](https://angularjs.org/)