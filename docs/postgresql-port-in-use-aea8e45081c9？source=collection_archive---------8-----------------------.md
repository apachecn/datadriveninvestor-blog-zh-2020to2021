# PostgreSQL:端口正在使用中

> 原文：<https://medium.datadriveninvestor.com/postgresql-port-in-use-aea8e45081c9?source=collection_archive---------8----------------------->

![](img/f609dae0b3febfb9a54c806cd84c3ec6.png)

没有什么比点击可爱的小象图标来启动你的 PostgreSQL 数据库更令人恼火的了，*哦，太可怕了。* **港口在使用。**

大量的谷歌搜索如何关闭一个端口，一个完整的计算机重启，以及太多的`kill -9 <PID>`命令之后，你被卡住了。现在怎么办？为什么 PostgreSQL 端口不会被释放？

事实证明，如果你通过自制软件安装了 Postgres，释放端口的正确方法是运行`brew services stop postgresql`,如果你仔细想想，这很有意义。Brew 告诉 postgreSQL，如果您碰巧手动关闭了端口，就重新启动端口，因此这是一场无休止的、令人沮丧的斗争。

运行该命令后，您将需要重新启动 PostgreSQL，您应该看到您的服务器已经启动并运行，就像新的一样。你可能会想，“这太简单了！”诚然，这是一个非常简单的修复，但这些是我最喜欢的类型。

❤让我们在 LinkedIn 上[连接](https://www.linkedin.com/in/alexandria-pugia/)！