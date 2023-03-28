# Redis 数据结构

> 原文：<https://medium.datadriveninvestor.com/redis-data-structures-495baef3d486?source=collection_archive---------4----------------------->

## Redis 第六集

## Redis 中数据结构的解释和使用

大家好，今天我们将讨论 Redis 内存数据存储可用的数据结构。在深入主题之前，我们首先讨论一些子概念。这将使文章的流动很好。

![](img/8f2c4a4fc83380c72f96495a76dd0112.png)

Photo by [jesse orrico](https://unsplash.com/@jessedo81?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 雷迪斯

edis 是一个用 C 语言编写的开源( [BSD 许可](https://en.wikipedia.org/wiki/BSD_licenses#:~:text=BSD%20licenses%20are%20a%20family,and%20distribution%20of%20covered%20software.&text=The%20original%20BSD%20license%20was,a%20Unix%2Dlike%20operating%20system.))内存数据结构存储，主要支持 Linux 及相关操作系统。Redis 可以用作 NoSQL 数据库和高速缓存存储。它是一个键值数据存储，不同于以表格格式存储数据的关系数据库。内存中的[让 Redis 变得难以置信的快和高性能。这是许多开发者对 Redis 感兴趣的主要原因。Redis 允许持久化，即使它在内存中，高可伸缩性和简单性。Redis 处理像 Twitter 的 timeline 这样的超级大数据集的速度非常快。它是在 Redis 中实现的。除了堆栈溢出之外，Github 还在实现中使用 Redis 作为缓存存储。你可以在这里找到我的 Redis 介绍文章](https://en.wikipedia.org/wiki/In-memory_database)。

# 数据结构

当我们的东西在工作场所、卧室甚至是工作桌上都没有摆放整齐时，我们可能会觉得很困难。任何类型的工作场所都需要被很好地组织起来，以便于进入，快速地在那里放入新的东西或者从那里移走一些东西，而不会打扰到那里的其他人。编程中的这种概念叫做数据结构。

![](img/4235a180e5df00dc87747dec11db1cb8.png)

Photo by [Brett Jordan](https://unsplash.com/@brett_jordan?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

数据结构是用于组织、处理、检索和存储数据的专用格式。有许多数据结构的例子，如列表、集合、哈希表、树、堆栈、队列、链表等。所有的数据结构都被设计来安排数据以适应特定的目的。一种数据结构对于一个用例可能非常有用，而对于另一个用例可能毫无用处。

# Redis 数据结构

尽管 Redis 是一个键值对存储，但它直接支持几种数据结构。它们是列表、集合、散列、排序集合、位图和超级日志。下面更多细节一个一个来看。

# 列表

![](img/dcb167cfae46a2f52777f90f4204f078.png)

Photo by [Martin Sanchez](https://unsplash.com/@martinsanchez?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

列表是许多编程语言中常见的数据结构之一。从一个非常普通的角度来看，列表仅仅意味着有序元素的序列。列表可以使用一些不同的数据结构来实现，如数组或链表等。根据实现类型的不同，列表的功能可能会有所不同。通过数组实现的列表的属性与通过链表实现的列表的属性非常不同。

Redis 列表是通过链表实现的。这意味着即使你在一个列表中有数百万个元素，在列表的头部或尾部添加一个新元素的操作也是在常量*时间*中执行的。将一个新元素添加到只有五个元素的列表的开头所花费的时间与将一个元素添加到有五百万个元素的列表的开头所花费的时间相同。如果 Redis 列表是使用数组数据结构实现的，那么通过索引访问时间将是常数。

## 列表的一些重要命令

1.  `LPUSH`和`RPUSH`分别是将元素推到列表右侧和左侧的命令。
2.  弹出元素是同时从列表中检索元素和从列表中删除元素的操作。我们可以使用`LPOP`和`RPOP`从左侧和右侧弹出元素，类似于我们如何在列表的两侧推送元素。

3.`LRANGE` 从 Redis 的列表中提取元素范围。

4.命令`LTRIM`类似于`LRANGE`，但是它不是显示指定范围的元素，而是将这个范围设置为新的列表值。移除给定范围之外的所有元素。

# 设置

Redis 集是唯一字符串的无序集合。唯一均值集不允许关键字中的数据重复。还可以对集合进行一些操作，比如向集合追加一个值，检查给定元素是否已经存在，产生多个集合之间的交集、并集或差集，等等。无论集合中包含多少个元素，集合添加、移除和测试成员的存在都将在一个固定的时间内发生。

## 器械包的一些重要命令

1.  命令`SADD` 向集合中添加新元素。
2.  命令`SDIFF`用于减去多组
3.  为了相交多个集合，我们使用`SINTER`。
4.  为了确定一个给定值是否是一个集合的成员，我们可以使用`SISMEMBER`命令。

还有许多其他的集合命令。你可以在这里找到它们。

# 散列表

HashMap 与 HashTable 相同，但是它是不同步的。它也允许放置空键，但是应该只有一个空键对象，并且可以有任意数量的空值。HashMap 允许我们存储键和值对，其中键应该是惟一的。值可以是特定键的任何类型的对象。如果您尝试插入复制键，它将替换相应键的元素。

![](img/4b637390cc5c09a4c48f2493c4f4e1d0.png)

Photo by [Elena Mozhvilo](https://unsplash.com/@miracleday?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

## Redis 散列

Redis 散列是字符串字段和字符串值之间的映射。它们是表示对象的绝对数据类型。你可以在这里找到如何在 Redis [中存储对象。密钥是唯一的。二进制键和值可以通过编程语言客户端存储在 Redis 中。例如 Jedis。BinaryJedis 在这里](https://sthenusan.medium.com/redis-as-object-storage-e6a084b46f8b)[可用](https://github.com/redis/jedis)。

## Redis hash 的一些重要命令

1.  `HSET`用于设置哈希字段的字符串值。
2.  `HGET`用于获取存储在指定键的散列字段的值。
3.  `HGETALL`将给所有的字段和值存储在一个 hash 中的特定键上。
4.  `HEXISTS`将允许我们检查一个关键字段的存在。

Redis Hash 还有更多可用的命令。你可以在这里找到它们。

# 排序集合

![](img/a3983521216c37d41351599e42549eaa.png)

Photo by [Paul Bergmeir](https://unsplash.com/@paulbrgmr?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

有序集合是一种数据类型，类似于集合和散列的混合。排序集由唯一的且不重复的字符串元素组成。有序集合中的每个元素都与一个称为分数的浮点值相关联。这就是为什么排序集被称为类似于哈希，因为每个元素都映射到一个名为 score 的值。有序集合中的元素按顺序排列。它们在已排序的集合中没有排序。顺序是用于描述有序集合的数据结构的特征。它们根据以下规则排序:

*   如果 A 和 B 是两个得分不同的元素，那么 A > B，如果 A . score > B . score。
*   如果 A 和 B 的得分完全相同，那么 A > B，如果 A 字符串在字典上大于 B 字符串。a 和 B 字符串不能相等，因为排序后的集合只有唯一的元素。

让我们从一个简单的例子开始。添加一些选定的板球运动员的名字作为排序的集合元素，以他们在最后一场比赛中得分作为分数。

```
> zadd wcwinners 0 "Virender Sehwag"
(integer) 1
> zadd wcwinners 18 "Sachin Tendulkar"
(integer) 1
> zadd wcwinners 97 "Gautam Gambhir"
(integer) 1
> zadd wcwinners 35 "Virat Kholi"
(integer) 1
> zadd wcwinners 91 "MS Dhoni"
(integer) 1
> zadd wcwinners 21 "Yuvraj Singh"
(integer) 1
```

*   `zadd`更可能是普通集合中的`sadd`，用于在有序集合中添加元素。
*   排序集是通过包含一个跳过列表和一个哈希表的双端口数据结构来执行的，所以每次我们添加一个元素 Redis 都会执行一个 O(log(N))操作。这很好，但是当我们请求排序的元素时，Redis 根本不需要做任何工作，它已经处于排序状态了。
*   当我们从 0 到-1 调用`zrange`时，它将列表中的所有元素按顺序排序。我们可以调用`zrevrange`从排序后的列表中获取反向排序的元素。

```
> zrange wcwinners 0 -1
1) "Gautam Gambhir"
2) "MS Dhoni"
3) "Virat Kholi"
4) "Yuvraj Singh"
5) "Sachin Tendulkar"
6) "Virender Sehwag"
```

*   我们可以通过`zrangebyscore`命令得到一个范围内的排序元素。
*   我们还可以通过`zrank`命令以有序的方式获得特定元素的等级。

```
> zrank wcwinners "MS Dhoni"
(integer) 2
```

此处有更多适用于可用排序集合的命令[。](https://redis.io/commands)

# 位图

位图不是实际的数据类型。Redis 中没有专门的位图数据结构。相反，位级操作是在主要 Redis 数据结构字符串上进行的。

按位运算主要分为两组

1.  操作单比特:像设置一个比特，获得它的值
2.  在位组上的操作:计算给定位范围内设置位的数量

位图最有影响力的好处之一是，在存储信息时，它们通常能最大限度地节省空间。

*例如，在一个通过递增的用户 id 来描述不同用户的系统中，仅使用 512 MB 的内存就可以记住 40 亿用户的一位信息(例如，知道一名员工是否想要免费午餐)。

使用位图中的`setbit`和`getbit`命令设置和检索位。

```
> setbit lunch 11 1
(integer) 1
> getbit lunch 11
(integer) 1
```

`setbit`命令接受位数作为其第一个参数，接受将该位设置为 1 或 0 的值作为其第二个参数。`getbit`只返回指定索引处的位的值。超出范围的位会被判断为零。

*   `bitpos`-获取具有指定值 0 或 1 的第一位。
*   `bitop`-在不同字符串之间执行逐位逻辑运算。
*   `bitcount`-执行群体计数，报告设置为 1 的位数

你可以在这里找到位图[的附加命令。](https://redis.io/commands)

# 超对数

超对数是一种用于计算唯一值的概率数据结构。在数学中，我们可以用计算一个集合的基数来匹配它。通常计数单个项目需要使用与您需要计数的项目数量成比例的内存量。

这个算法的神奇之处在于，我们不需要使用与计算的项目数量成比例的内存量，而是可以使用固定的内存量。在最坏的情况下，它使用 12k 字节。Redis 中的 HLL 编码为 Redis 字符串，因此您可以调用 get 来序列化 HLL，并设置将其反序列化回服务器。超级日志中使用了`pfadd`、`pfcount`和`pfmerge`命令。这些命令在超对数算法的发明者 Philippe Flajolet 的内存中以 pf 为前缀。

下面给出了上述命令的用法示例。

```
> pfadd teachers raj kamal vimal
(integer) 1
> pfcount teachers
(integer) 3
> pfadd students kholi dhoni
(integer) 1
> pfmerge members teachers students
OK
> pfcount members
(integer) 5
```

我相信你已经理解了我们今天讨论的话题。如果您有任何问题或任何澄清，不要犹豫，通过回复部分与我联系。感谢您花费宝贵的时间阅读本文。

干杯…

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)

# 参考

[](https://redislabs.com/) [## Redis 实验室|最佳 Redis 体验

### 如果简单的缓存是你使用 Redis 的全部目的，那你就错过了。利用实时数据库 Redis Enterprise

redislabs.com](https://redislabs.com/) [](https://redis.io/) [## 雷迪斯

### Redis 是一个开源的(BSD 许可的)、内存中的数据结构存储，用作数据库、缓存和消息代理…

redis.io](https://redis.io/)