# Redis 作为对象存储

> 原文：<https://medium.datadriveninvestor.com/redis-as-object-storage-e6a084b46f8b?source=collection_archive---------0----------------------->

## Redis 第 5 集

## 如何使用 Redis 存储对象

正如我们之前讨论的, [Redis](https://sthenusan.medium.com/introduction-to-redis-3e6c3a0083a7) 是一个内存中的数据库，我们可以将数据存储为键值对。Redis 有很多特性，像[数据持久性](https://sthenusan.medium.com/data-persistence-with-redis-52b7d7cdfc53)和[高可用性](https://blog.usejournal.com/availability-with-redis-66611f5a5e2b)。我决定在本文中讨论如何将对象存储在 Redis 数据库中。首先，在深入这个话题之前，我将向你介绍一些新的术语。

![](img/ff9e355dd23b64898b8b1bffd7cec0f2.png)

Photo by [Danny Feng](https://unsplash.com/@hellodannyfeng?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 目标

对象表示抽象数据类型。一个对象可能有不同的属性和方法，甚至可能携带其他对象。在大多数编程语言中，对象被表示为类。对象为编程提供了结构化的途径。

由于 Redis 是一个键值存储，我们不能简单地直接存储复杂的对象。因此，我们需要一种方法来处理存储在 Redis 数据库中的对象。

# 对象序列化

序列化意味着将对象转换成字节流，以便将对象存储在内存中。主要目标是保存对象的状态，以便在需要时能够重新创建它。序列化的反向过程称为反序列化。

# 客户

编程中的客户端是依赖于另一个程序运行的计算机程序。在所有广泛使用的编程语言中，许多技术都有可用的客户端，例如，MySQL 有 JAVA、Python、NodeJS 等的客户端。同样，Redis 也有许多不同编程语言的客户机。当我们使用客户端时，我们不必过多考虑内部连接是如何发生的。Redis 的 JAVA 客户端叫做 Jedis。Jedis 给了我们一个很好的接口，可以通过 JAVA 很容易地使用 Redis。我们可以从[这里](https://jar-download.com/artifacts/redis.clients/jedis)轻松下载 Jedis jar 文件。

# 对象存储过程

在 Redis 中，所有东西都只能以键-值对格式存储。键必须是唯一的，以字符串格式存储对象无论如何都不是一个好的做法。对象通常以二进制数组格式存储在数据库中。这里我们也将使用二进制数组格式来存储对象。Jedis 允许我们使用 BinayJedis()构造函数来处理二进制数组。

Redis Instance Creation

在这个方法中，我们以线程安全的方式创建了一个 BinaryJedis 对象。“jedis”变量被称为 BinaryJedis。方法确保通过调用此方法只创建一个对象。当“jedis”变量为空时，创建新的对象。否则，该方法返回已经创建的对象。主机和端口是 Redis 部署的主机地址和端口号。

我将使用 apache 的序列化库来序列化和反序列化对象。您可以查看 apache 的[文档](https://commons.apache.org/proper/commons-lang/apidocs/org/apache/commons/lang3/SerializationUtils.html)以获得更多关于该库使用的知识。下面显示的两种方法用于序列化和反序列化。

我选择一个简单的对象来演示目的。

在这里，我定义了一个名为 human 的样本类，它有两个属性，比如年龄和姓名。下面的代码是用 Redis 存储和检索样本对象的演示部分。

最初，我们应该通过 getJedisInstance()方法获取 jedis 对象。之后，我使用参数为 12 和“Alias”的 human 类创建了一个名为 h1 的示例对象。现在，对象创建完毕。然后，我们需要使用 BinaryJedis 将对象序列化为字节数组格式，以存储在 Redis 中。我们需要将对象转换为 serializable 接口来序列化对象。由于 BinaryRedis set 方法要求键和值采用字节数组的形式，因此键被转换为字节数组。当程序执行这一行时，对象存储在 Redis 中。

```
jedis.set(“human_1”.getBytes(), h1_obj);
```

我们还需要在从 Redis 中检索对象时使用字节数组格式的键。当我们从 Redis 数据库中检索对象时，对象将是字节数组格式。我们需要反序列化它以获得实际的人类对象。我们必须在反序列化后将其转换为人类对象。

```
object h2_obj = deserialize(jedis.get("human_1".getBytes()));
human h2 = (human)h2_obj;
```

我们需要测试对象 h1 和 h2 是否相同。因此，human 类的 get_age()方法在 h1、h2 之上被调用，并且值可以被比较。12 将在终端中打印两次。

```
System.*out*.println(h1.get_age());
System.*out*.println(h2.get_age());
```

因此，我们可以成功地用 Redis 数据库存储和检索对象。

我相信你已经理解了今天讨论的主题。如果您有任何问题或任何澄清，不要犹豫，通过回复部分与我联系。感谢您花费宝贵的时间阅读这篇文章。

***享受文章？成为*** [***中等会员***](https://sthenusan.medium.com/membership) ***继续无限制学习。如果你使用上面的链接，我会收到你的一部分会员费，不需要你额外付费。***

干杯…

![](img/6a0376a0e0234b5a276191960abe2c04.png)

Photo by [Jon Tyson](https://unsplash.com/@jontyson?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

参考

 [## jedis 3.4.0 javadoc

### 编辑描述

javadoc.io](https://javadoc.io/doc/redis.clients/jedis/latest/index.html) [](https://redis.io/) [## 雷迪斯

### Redis 是一个开源的(BSD 许可的)、内存中的数据结构存储，用作数据库、缓存和消息代理…

redis.io](https://redis.io/)