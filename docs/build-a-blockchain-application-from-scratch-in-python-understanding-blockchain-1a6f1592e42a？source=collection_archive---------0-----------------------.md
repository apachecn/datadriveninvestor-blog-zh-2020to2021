# 用 Python 从头开始构建区块链应用程序:理解区块链

> 原文：<https://medium.datadriveninvestor.com/build-a-blockchain-application-from-scratch-in-python-understanding-blockchain-1a6f1592e42a?source=collection_archive---------0----------------------->

我不是区块链专家。我只研究了区块链一个学期。但是我知道最有效的学习方法是从头开始。我将有机会处理建设过程中的问题。我很高兴分享我对构建一个全功能应用程序的过程的看法:一个简单的基于区块链的投票系统([视频演示](https://www.youtube.com/watch?v=CqNoDjuf6EE))。开源可用[这里](https://github.com/ngocjr7/voting-blockchain)。

[](https://github.com/ngocjr7/voting-blockchain) [## 非政府组织委员会 7/投票-区块链

### 一个简单的基于区块链的投票系统应用程序，由 Python 从头开始构建。它可以和…一起跑步

github.com](https://github.com/ngocjr7/voting-blockchain) 

本文由两部分组成:
第一部分:了解区块链。
第二部分:一个简单的基于区块链的投票系统(现在还没准备好)。

![](img/c01ad07093a9abfef817ca2870735f6f.png)

Blockchain formation. The main chain (black) consists of the longest series of blocks from the genesis block (green) to the current block. Orphan blocks (purple) exist outside of the main chain. ( source: wiki )

# 什么是“区块链”？

我们可以简单的理解区块链是一种类型的[****数据库****](https://steemit.com/blockchain/@abdulganiy/understanding-decentralised-and-distributed-databases) **用来存储数据，任何类型的数据。关键区别在于数据是以块的形式存储的，块链使用哈希函数。对于比特币，数据可以是交易(比特币从一个账户转移到另一个账户的日志)。块链通过散列来链接，其中当前块的散列包括前一个块的散列。**

**![](img/3759bb58a635510b0d8b2a480ab6ca47.png)**

**A Simple Blockchain Architecture**

**区块链具有以下特征:**

*   ****去中心化:**这意味着存储在区块链的任何信息都作为整个网络的一个单元。没有中央集权；相反，所有信息都在节点间共享。**
*   ****不变性:**区块链的数据仅*追加。*没有删除。您必须添加新的带注释的数据来修复过去的某些东西。这使得区块链上的数据可以追踪。**
*   ****分布式账本:**区块链可以是公有的，也可以是私有的。但它永远属于一个群体，不属于任何人。它通常由[对等](https://en.wikipedia.org/wiki/Peer-to-peer)网络管理，共同遵守[协议](https://en.wikipedia.org/wiki/Protocol_(communication))用于节点间通信和验证新块。**

## **区块链背后的核心理念**

**回顾一下历史，在 2008 年，为了实现一个不需要可信方就不能篡改文档时间戳的系统，Nakamoto 改进了 Merkle 树的设计，使用了一种类似于 T2 Hashcash 的方法来标记块的时间戳。Hashcash 是一个工作证明系统，最初用于限制垃圾邮件和拒绝服务攻击。Hashcash 算法要求发件人在邮件头中添加 hashcash 戳记编码。报头需要收件人的邮件地址、消息日期、计数器和重要条件，报头的 160 位[SHA-1](https://en.wikipedia.org/wiki/SHA-1)哈希的前 20 位都是零。发送方必须找到合适的计数器来满足上述条件。唯一已知的方法是[暴力](https://en.wikipedia.org/wiki/Brute_force_attack)。收件人可以很容易地检查电子邮件的情况。如果它满足，收件人就知道发件人在发送一封电子邮件时丢失了一定的计算量，所以他们可以相信发件人不能将这封邮件发送给所有人。**

**[](https://www.datadriveninvestor.com/2019/02/13/5-real-world-blockchain-applications/) [## 5 行业转型区块链应用|数据驱动投资者

### 除非你一直生活在岩石下，否则我相信你现在已经听说过区块链了。而区块链…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/13/5-real-world-blockchain-applications/) 

区块链类似 Hashcash 的方法使用相同的机制。数据是仅附加的，并被组织为块。一个块由数据、以前的散列和随机数组成。在电子邮件示例中，随机数充当计数器，当前散列充当 hashcash。

```
current_hash = hash(previous_hash + data + nonce)
```

当前哈希中第一个零的数量称为难度参数。难度越大，找到合适随机数的可能性越低。为了追加一些数据，您必须创建一个新的块，并找到一个 nonce，使当前的哈希表示具有足够多的第一个零。这意味着你必须牺牲一定的计算能力来增加一个新的模块。这个算法叫做 ***工作证明*** ，这个过程叫做 ***挖掘*** 。

由于一个块的散列将在下一个块的头中，如果你想改变过去的数据，你必须重新计算随后的块。这也意味着可能有许多不同的分支和许多不同的数据版本。在这种情况下，区块链维护一个协议，保证最长的链将被视为主链。这个协议叫做**。**

*现在，有许多类型的区块链，具有不同的一致性算法。我们不会在这里讨论它们。*

## *为什么是“hashcash”、“chain”和“最长链”？*

*为了理解，我们考虑一个称为 51%攻击的场景，这是在比特币诞生时提出的。让我们想象一下，你加入比特币，用比特币买车。比特币无可信方。它必须自己验证你的交易(检查你的账户中是否有足够的钱，这个过程将由比特币网络中的其他人进行验证)。假设你是一个黑客，你想欺骗交易。比特币不会储存你的余额(比特币会追踪你过去的所有交易来获取你的余额)。你唯一能做的就是让之前的交易从比特币数据库中消失。怎么会？*

*您可以将区块链克隆到您的计算机上，删除您的事务，并继续在网络中共享和验证其他事务。你会有自己的分店。在这个分支，你没钱也有车。*

*![](img/317759f72d2432646addf0d1824e2a5b.png)*

*问题是区块链网络中的其他人只接受最长的链。你想让别人相信你的链子是真的。因此，你必须让你的链条比别人长。但是当你开采你的区块时，其他人也在主链中开采。因此，您必须拥有一台计算能力超过所有其他计算机总和的计算机。换句话说，你的计算能力至少要达到整个网络计算能力的 51%才能赶上主链。有了比特币这样的公网，有可能认为是不可能的。*

# *Python 中的区块链*

*在这一节中，我们用 Python 从头开始实现了一个简单的区块链。这篇文章是对[精彩文章](https://developer.ibm.com/technologies/blockchain/tutorials/develop-a-blockchain-application-from-scratch-in-python/)的总结。这篇文章旨在帮助你更容易地理解源代码，你应该自己运行它，并打印所有你混淆的东西。如果您已经知道它是什么，请查看第 2 部分，构建一个功能完整的基于区块链的投票系统。*

*首先，您需要一个类来表示一个块:*

*和一个代表区块链的类:*

**事务*是以 JSON 格式存储的数据。例如，在比特币中，它看起来像:*

```
*{ 
  "index": "an unique id", 
  "sender": "private key of sender",
  "receiver": "public key of receiver",
  "amount": 100,
  "timestamp": "The time at which the transaction was created"
}*
```

**unconfimed_transactions* 是一个存储未验证事务的池。Miner 将从池中挑选交易进行验证。*

*区块链中的第一块总是用 *previous_hash 为 0* 来构造。为了向区块链添加一个新的块，您必须实现*工作证明*算法，该算法将通过强力查找适当的 nonce 和 *mine* 函数，该函数将获取*unconfirmed _ transactions*并尝试验证这些事务，运行 *proof_of_work* 并向链中添加一个新的块。*

**add_block* 应该很容易追加一个新块。但问题发生在多人同时挖矿的时候。他们可能会在我们之前得到一个新的区块，然后我们使用的链条不再是最长的链条。所以我们必须在添加之前检查我们的链的有效性。*

*我们几乎有了一个可以在一台电脑上运行的区块链。接下来我们应该做的是使用这个区块链创建一个应用程序。我们利用 [Flask](https://flask.palletsprojects.com/en/1.1.x/api/) 框架来构建一个与我们的区块链数据库交互的 RESTful 应用程序。*

*最后，要加入区块链网络，你必须遵守用于节点间通信的[协议](https://en.wikipedia.org/wiki/Protocol_(communication))，这是共识算法。*

*至此，我们已经了解了什么是区块链，以及如何实现一个简单的。在下一篇文章中，我想和你分享如何用不同的架构实现一个全功能的基于区块链的应用程序。我还想在区块链介绍一个新概念，智能合同，以及如何处理它。*

# *参考资料:*

1.  *[https://developer . IBM . com/technologies/区块链/tutorials/develop-a-区块链-从零开始应用 python/](https://developer.ibm.com/technologies/blockchain/tutorials/develop-a-blockchain-application-from-scratch-in-python/)*
2.  *[https://en.wikipedia.org/wiki/Blockchain](https://en.wikipedia.org/wiki/Blockchain)*
3.  *[https://en.wikipedia.org/wiki/Hashcash](https://en.wikipedia.org/wiki/Hashcash)*
4.  *[https://www . coin desk . com/Moscow-区块链-投票-系统-完全-不安全-说-研究员](https://www.coindesk.com/moscow-blockchain-voting-system-completely-insecure-says-researcher)*
5.  *[https://steemit . com/区块链/@阿卜杜勒加尼/understanding-去中心化和分布式数据库](https://steemit.com/blockchain/@abdulganiy/understanding-decentralised-and-distributed-databases)*
6.  *[https://blog . good audience . com/what-a-a-51-attack-or-double-spend-attack-aa 108 db 63474](https://blog.goodaudience.com/what-is-a-51-attack-or-double-spend-attack-aa108db63474)***