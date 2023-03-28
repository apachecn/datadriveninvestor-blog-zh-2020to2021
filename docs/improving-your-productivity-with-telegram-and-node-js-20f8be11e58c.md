# 利用 Telegram 和 Node.js 提高您的工作效率

> 原文：<https://medium.datadriveninvestor.com/improving-your-productivity-with-telegram-and-node-js-20f8be11e58c?source=collection_archive---------6----------------------->

![](img/c601183d13b829fd72f89c3712785c37.png)

[https://unsplash.com/photos/efzwcMRM6j4](https://unsplash.com/photos/efzwcMRM6j4)

不久前，我寻找了一种在移动设备和 Node.js webserver 之间建立通信通道的简单方法。我的目标是通过这个频道交换信息，并接收有关天气、公共交通等信息。

例如，我发送消息`/train`并收到一个响应，其中包含关于预配置路线的列车出发时间的实时详细信息。因此 Node.js 服务器接收传入的消息，对其进行处理，并向客户端发回响应。

[](https://www.datadriveninvestor.com/2019/03/25/a-programmers-guide-to-creating-an-eclectic-bookshelf/) [## 创建折衷书架的程序员指南|数据驱动的投资者

### 每个开发者都应该有一个书架。他的内阁中可能的文本集合是无数的，但不是每一个集合…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/03/25/a-programmers-guide-to-creating-an-eclectic-bookshelf/) 

在做了一些研究后，我终于想出了电报机器人，因为它们很容易安装，完全符合我的需要。除了发送文本消息，您还可以共享图像或音频记录等数据。

首先，电报机器人到底是什么？([来源](https://core.telegram.org/bots))

> 机器人是运行在 Telegram 内部的第三方应用程序。用户可以通过向机器人发送消息、命令和内嵌请求来与它们进行交互。你控制你的机器人使用 HTTPS 请求我们的机器人 API。

因此，你只需通过 Telegram 从手机发送一条信息，你的网络服务器就会通过 Telegram 的 API 接收到它。

只是列举一些你可以用你自己的机器人做的事情。无论是为你还是为你的朋友:

*   收集天气信息
*   获取公共交通的到达/离开时间
*   接收推文、新闻、状态更新
*   发送自动消息
*   物联网

还有更多。

电报机器人的一个很大的好处是，你不需要一个可以从网络外部通过 IP 地址访问的公共服务器。在我的例子中，我使用 Raspberry Pi 来运行节点应用程序。

因为通信是通过 Telegram API 进行的，所以只需要一个互联网连接。

为了与它交互，你可以使用 Node.js 之类的运行时环境，就像我在下面的示例应用程序中所做的那样，或者任何其他编程语言。

[在这里](https://core.telegram.org/bots/api)你可以找到关于如何与 API 交互的介绍。

正如我上面提到的，我最近基于 Node.js 为 Telegram bot 服务器创建了一个示例应用程序。请随意将它用于您自己的 bot，并根据您的愿望进行定制或为其做出贡献。

让我知道你用你的机器人做什么，并分享你的经验！

[](https://github.com/larswaechter/telegram-bot-server) [## 拉斯瓦切特/电报机器人服务器

### 用于与电报机器人 API 通信的可扩展网络服务器。telegram-bot-server 是一个 Node.js 驱动的 web 服务器…

github.com](https://github.com/larswaechter/telegram-bot-server)