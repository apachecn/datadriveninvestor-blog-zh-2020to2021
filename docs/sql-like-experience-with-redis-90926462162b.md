# 类似 SQL 的 Redis 体验

> 原文：<https://medium.datadriveninvestor.com/sql-like-experience-with-redis-90926462162b?source=collection_archive---------6----------------------->

## Redis 事件

## 讲解如何在 Redis 中获得类似 SQL 的体验

大家好，

随着时间的推移，技术在不断变化。当我们设计一个软件系统时，我们可能会考虑我们将使用什么技术来实现这个系统。技术不是一个固定的东西。它可能会随着时间的推移，随着用途或用途的改变，甚至随着客户的要求等而改变。我们的系统必须具有适应新技术的能力，而不需要在实现层面上做太多的改变。程序员可能出于各种目的喜欢一种旧技术。他们总是在寻找新技术与旧技术相比有哪些相似的能力。他们的思维总是沿着旧的思路去和新的一起工作。这是一件普通的事情，而不是一件奇怪的事情。

![](img/79ae8f4466e25bad67ec4bf71210ee0c.png)

Photo by [Ross Findon](https://unsplash.com/@rossf?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

今天我们将讨论如何在 Redis 中获得类似 SQL 的体验。开发人员熟悉 SQL 相关数据库的时间比熟悉 NoSQL 相关数据库的时间长。突然从使用 SQL 转向 NoSQL 将会更加困难。大多数较老的软件系统通常也希望 Redis 具有 SQL 类型的经验。尽管两者具有相同的功能，但它们的质量属性、应用程序和交互可能不同。Redis 是一个高级的键值数据存储。您可能会从我以前的文章中对 Redis 有更好的了解，如[Redis 简介](https://medium.com/nerd-for-tech/introduction-to-redis-3e6c3a0083a7)、[Redis 数据持久性](https://sthenusan.medium.com/data-persistence-with-redis-52b7d7cdfc53)、[Redis 可用性](https://blog.usejournal.com/availability-with-redis-66611f5a5e2b)、[Redis 比较博客、Infinispan 和 Memcached](https://sthenusan.medium.com/redis-vs-infinispan-vs-memcached-7f7cf3b26522) 、 [Redis 作为对象存储](https://medium.com/nerd-for-tech/redis-as-object-storage-e6a084b46f8b)和 [Redis 数据结构](https://medium.com/datadriveninvestor/redis-data-structures-495baef3d486)。作为 Redis 的一个组织良好的教程集，这些文章可能对新手有所帮助。

![](img/706aa1adb79f0351e2402c687261e3f2.png)

Photo by [Patrick Tomasso](https://unsplash.com/@impatrickt?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

从一种技术转移到另一种技术的最佳方式是在两种技术之间映射可用的资源和用途。SQL 有存储数据的表，但是 Redis 是一个键值存储。Redis 中没有可用的表，但是 Redis 数据结构可以替代表。因此，转换中最重要的一步是将表重新建模为 Redis 数据结构。使用这个选项，我们通常需要对系统代码进行修改，以使用 Redis 命令来代替 SQL 查询。

在本文中，我计划展示如何将从 SQL 插入和检索数据映射到 Redis。例如，在此之前，我们假设要将基于产品的工厂软件系统从关系数据库更改为 Redis 数据库，而不更改系统的逻辑。

# 1.插入数据

```
SQL:insert into basic_info (product_id, name, category, price)
values (1001, “Anchor”,“MilkPowder”, 400);
```

在 SQL 中，我们使用示例性数据将数据插入到 basic_info 表中。我们必须将表改造成 Redis 数据结构，但是我们不能盲目地这样做。考虑到数据的使用，我们需要这样做。产品细节必须能够查询其属性，特别是价格和产品 id。因此，我们将产品细节存储在 Redis 散列表中，将产品 id 和价格存储在 Redis 排序集中。

```
Redis:MULTI
HMSET product:1001 name Anchor category “MilkPowder” price 400
ZADD product_list 1001 product:1001
ZADD product_price 400 product:1001
EXEC
```

# 2.按价格查询

```
SQL:select * from basic_info where price < 250
```

SQL 为我们提供了一种使用不等式查询条件表的简便方法。这里我们想得到价格低于 250 英镑的产品的数据。如果没有适当的数据结构模型，我们就不能在 Redis 中做到这一点。由于我们将价格数据存储在已排序的集合中，因此根据所需的价格范围获取已排序的产品 id 非常方便。

```
Redis:

ZRANGEBYSCORE product_price 0 250
```

# 3.按产品 id 查询

```
SQL:select * from basic_info where id = 1001
```

在 SQL 端，我们只是从 basic_info 表中查询数据。这是一项非常直截了当的工作。因为我们使用“product:id”模式作为 Redis 散列表中的键，所以我们也能够简单地从 Redis 端获得数据。

```
Redis:HGETALL product:10200
```

对于需要使用 Redis 数据库的程序员来说，还有更重要的几点。

*   Redis 中没有关系数据库中的主键特性。无论如何，Redis 键需要是唯一的。因此，明智地为每个记录设计唯一的键，而不违反任何数据完整性或一致性。
*   Redis 中有一个称为“Redis expires”的特殊功能，用于从数据存储中删除数据。我们可以为数据库中的任何密钥设置到期时间。在该特定时间后，键和值都将被删除。
*   尽可能使用 Redis 散列，因为 Redis 散列的设计采用了内存优化，而不是简单的键值对。
*   永远不要通过文本格式在 Redis 中存储对象。我们需要将对象序列化为字节数组或流，通过 Redis 的二进制函数将它们存储在 Redis 数据存储中。这篇[文章](https://medium.com/nerd-for-tech/redis-as-object-storage-e6a084b46f8b)有助于深入理解。

这些要点肯定会帮助你与 Redis 合作。

我相信你理解了今天讨论的项目。如果您有任何问题或任何澄清，不要犹豫，通过回复部分与我联系。感谢您花费宝贵的时间阅读本文。

干杯…

# 参考

[](https://redislabs.com/) [## Redis 实验室|最佳 Redis 体验

### 如果简单的缓存是你使用 Redis 的全部目的，那你就错过了。利用实时数据库 Redis Enterprise

redislabs.com](https://redislabs.com/) [](https://redis.io/) [## 雷迪斯

### Redis 是一个开源的(BSD 许可的)、内存中的数据结构存储，用作数据库、缓存和消息代理…

redis.io](https://redis.io/) ![](img/2c096acaf026581e9362ed505d96beb4.png)

Photo by [Morvanic Lee](https://unsplash.com/@morvanic?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)