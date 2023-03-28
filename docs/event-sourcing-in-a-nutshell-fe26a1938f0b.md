# 简而言之，活动采购

> 原文：<https://medium.datadriveninvestor.com/event-sourcing-in-a-nutshell-fe26a1938f0b?source=collection_archive---------4----------------------->

## 捕获事件的体系结构产生自然的审计日志，并允许时间旅行。

![](img/1d8b73618b0e005a379fbd7b55e0e8d4.png)

Photo by [John Baker](https://unsplash.com/@jlondonbaker?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

今天，我们来看看一个已经存在了很长时间的软件架构模式，但是由于这样或那样的原因，它并没有被频繁地实现。当微服务架构变得流行时，事件外包确实受到了欢迎，但它从来没有真正成为构建软件的革命性新方法，当时许多人声称。

它没有成为软件架构中的主流有很多原因，在本文中，我们将回顾事件源的一些优点，以及它的一些缺点。

# 什么是事件采购？

事件源是通过重放影响实体的事件来确定实体在给定时刻的状态的实践。我们不仅能够查询一个实体的当前状态，还可以查看它的所有历史，并重建它的当前状态是如何形成的。

在传统的软件架构中，每当一个实体的状态改变时，我们只是在数据库中更新它的值。例如，当您的地址因为搬家而改变时，包含您的联系方式和送货细节的记录会更新以反映您的新地址，下次您订购东西时，它会到达您的新住处。

事件源系统的工作方式完全不同。他们从不更新任何记录；他们只插入记录。那些记录是事件。在上面的例子中，如果您的地址改变了，一个新的记录将被简单地插入到事件存储中，表明您已经搬家了。

[](https://www.datadriveninvestor.com/2019/01/23/which-is-more-promising-data-science-or-software-engineering/) [## 数据科学和软件工程哪个更有前途？数据驱动的投资者

### 大约一个月前，当我坐在咖啡馆里为一个客户开发网站时，我发现了这个女人…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/23/which-is-more-promising-data-science-or-software-engineering/) 

在前一个例子中，我们只知道你现在住的地方。在基于事件的例子中，我们知道你*过去住在哪里*，*现在住在哪里*，以及*什么时候你搬到了*。我们之所以知道这些，是因为这三样东西都存储在事件中。不用说，这是非常有效的。

当然，从事件存储中检索数据并重建对象的状态比简单地运行 SQL 查询并观察结果要复杂得多。您必须收集影响一个实体的事件，并将它们回放到特定的时刻，以观察实体的状态。

本质上，事件源是为您的实体创建一个时间序列数据库。

# 确定实体的状态

在基于事件的系统中确定实体状态的最简单的方法是获取实体的默认状态，获取它的事件，并将它们应用到实体的状态。很明显，为什么这也是一种非常慢的处理方式，尤其是在给定架构中有大量实体是事件源的情况下。

为了让基于事件的应用程序保持高性能，需要某种缓存和优化。因为实体的状态可以完全从其事件中获得，所以以某种方式缓存实体的当前状态通常是个好主意。

这可以通过多种方式实现。一种方法是简单地在内存或磁盘上缓存一个实体的当前状态，假设当前状态是最终用户最想要的。每当应用新事件时，只需使缓存无效并重建实体的状态。这种方法适用于不经常改变的实体。

另一个是捕捉事件旁边的实体*快照*。快照代表实体在特定时刻的状态。这些可以和事件一起存储，但不是必须的。不是每次都应用*所有*事件，而是抓取最近的快照，抓取之后的所有事件，并将它们应用到快照的状态。这种方法适用于经常变化的实体。

可以说，这两种方法都比 SQL 数据库中的简单记录需要更多的簿记和处理能力。

# 利用事件穿越时间

有了上面提到的所有簿记，我们得到了一个非常酷的功能:时间旅行！在我们的领域中，对一个实体的所有更改都在一个事件中被捕获。它们存储在*事件存储库*中，并作为我们领域内的单一真实来源。

因为每一个变化都作为一个事件被捕获，所以任何给定实体的状态都可以在任何给定的时间点被重构。让我们考虑一个银行账户。一个银行账户不仅仅只有一个余额，它通常包含许多交易，这些交易共同构成了它今天的余额。

这是一个非常好的事件源系统的例子。因为随着时间的推移改变账户余额的所有事件都在那里，所以我们可以获取它们的任何子集来确定在两个时间点之间发生的余额变化。

由于其事件，事件源系统会留下自然的审计线索。这使得它非常适合货币体系。想知道去年 2 月 16 日的账户余额吗？只需抓取到该点的事件，并回放它们。

# 什么时候应该使用事件源？

**简短回答:**几乎没有。
**略长的回答:**只有当你绝对需要，并且你能承受与之相关的复杂性的时候。

尽管事件源在概念上非常令人印象深刻，但真实世界的用例数量非常有限。因为确定一个实体的状态变成了重放事件的练习，所以事件源需要大量的簿记和技术技巧才能正常工作和执行。

在某些情况下，审计日志是绝对必要的。以银行为例。法律要求银行拥有高度准确的书面记录，详细记录他们处理过的每一笔交易。如果不这样做，他们将面临巨额罚款的风险。

在这种情况下，实现基于事件的系统可能是有意义的。实际上，我想几乎每家银行都在他们的系统中使用过类似的方法。

事件源是非常有趣的实验。如果您想起草一份实施方案，这里有一些很好的资源可供参考:

*   [https://martinfowler.com/eaaDev/EventSourcing.html](https://martinfowler.com/eaaDev/EventSourcing.html)
*   https://microservices.io/patterns/data/event-sourcing.html

当选择是否要将事件源引入软件产品的时候，一定要问自己这样一个问题:这真的值得争论吗？