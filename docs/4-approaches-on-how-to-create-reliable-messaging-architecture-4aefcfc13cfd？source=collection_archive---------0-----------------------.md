# 关于如何创建可靠的消息传递架构的 4 种方法

> 原文：<https://medium.datadriveninvestor.com/4-approaches-on-how-to-create-reliable-messaging-architecture-4aefcfc13cfd?source=collection_archive---------0----------------------->

![](img/2043dc35046677a3eee4cf0ba4e7e39e.png)

Photo by [Kate Macate](https://unsplash.com/@katemacate?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

微服务架构现在很流行。它经常通过消息传递基础设施与异步数据处理结合在一起。我所说的异步处理是指在后台执行的数据处理功能。从这个意义上说，我们公司也不例外，我们在应用程序中使用了大量的消息传递。它允许在后台处理耗时的任务。用户不必等到事情处理完毕。应用程序对用户的响应也变得更快。

你有没有想过如何处理容忍各种错误的消息？并且还需要更少的人工来处理这些错误？让我向您介绍消息管道中的消息重试、等幂和发件箱。

在本文中，我将描述如何使用 [RabbitMQ](https://www.rabbitmq.com/) 和 [MassTransit](https://masstransit-project.com/) 库实现错误处理。它将使您的数据处理管道更具弹性和可靠性。

在成功运行本文中使用的示例代码之前，有一些先决条件:

*   在 [Windows](https://www.rabbitmq.com/install-windows.html) 或者 [Linux](https://www.rabbitmq.com/install-debian.html) 上安装 RabbitMQ。
*   安装[。网芯 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)
*   安装 [MongoDB](https://www.mongodb.com/try/download/community)

此外，本文假设您已经掌握了 C#知识以及 RabbitMQ、MassTransit 和 MongoDB 的基础知识。

## 一级重试

想象一下，您集成的服务之一在几分钟内变得不可用。当调用特定服务时，您很可能会得到服务不可用异常。这可能不会立即导致消息处理失败，因为消息将被移动到错误队列中，谁愿意手动处理潜在的大量消息呢？在这种情况下，第一级重试是救命稻草。

[](https://www.datadriveninvestor.com/2018/08/02/making-the-leap-from-speech-to-dialogue-the-challenge-for-human-to-machine-communication/) [## 从语音到对话的飞跃:人机交流的挑战

### 机器人无处不在，几乎无所不在。我们甚至已经开始与他们交谈，在这种情况下…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2018/08/02/making-the-leap-from-speech-to-dialogue-the-challenge-for-human-to-machine-communication/) 

它们主要用于处理暂时性异常，如数据库死锁、短暂连接不可用，以及其他类型的情况，此时问题持续时间很短，应用程序可以快速恢复。

下面是如何配置一级重试的代码示例。

我创建了一个简单的。NET 核心控制台应用程序来显示启用重试所需的配置，并添加了一个普通消息处理程序来测试重试逻辑。请注意，当您运行应用程序时，消息会重试三次。

你可以在[大众运输文档](https://masstransit-project.com/usage/exceptions.html#retry)中了解更多关于一级重试的信息。

## 二级(重新传递)重试

当您与其他系统集成时，这些重试特别有用，这些系统可能会由于各种原因而长期不可用。您的应用程序应该容忍这种情况，而不是立即将消息发送到错误队列。错误队列是消息处理管道中的最后一招。

我通过添加一个支持消息重新传递的配置，对前面的示例做了一些小小的调整。

我选择使用 [RabbitMQ 延迟消息插件](https://github.com/rabbitmq/rabbitmq-delayed-message-exchange/)，因为它是 Quartz 的轻量级替代，不需要 RabbitMQ 之外的任何存储。

您需要完成几个步骤才能进行重新交付。为了让 RabbitMQ 工作，你还需要按照[插件安装指南](https://www.rabbitmq.com/installing-plugins.html)安装`rabbitmq_delayed_message_exchange`插件。安装完插件后，在 RabbitMQ sbin 命令行中运行`rabbitmq-plugins enable rabbitmq_delayed_message_exchange`命令来启用它。

启用它并启动应用程序后，将创建一个新的交换(见下图)来存储需要在一段配置时间后重试的消息，并保证在 RabbitMQ 节点重新启动时消息不会丢失。

![](img/92e5df0ed066f0d92cacf8f4986c9cc7.png)

你可以在[大众运输文档](https://masstransit-project.com/usage/exceptions.html#redelivery)中了解更多关于重新交付的信息。当您运行更新后的应用程序时，您会注意到第一级重试是在开始时执行的，只有到那时，对于在第一级重试期间未成功处理的邮件，才会重新传递。在这个例子中，消息最终会出现在错误队列中，因为异常总是被抛出。在这种情况下，重新交付无济于事。

**不重试某些异常**

在执行第一级或第二级重试的过程中，您可能会遇到应该忽略特定类型的异常的情况。例如，如果消息没有通过某些特定的验证，就不应该重试。幸运的是，MassTransit 提供了这样的功能，它被称为[异常过滤器](https://masstransit-project.com/usage/exceptions.html#exception-filters)。您可以忽略某些异常，或者只重试特定的异常。

与前一个示例相比，我在两个地方添加了这行代码。

`retryConfigurator.Ignore(typeof(NameTooShortException));`

这告诉我们对于第一级和第二级重试都忽略重试`NameTooShortException`。

## 消息幂等性

下面是来自[维基百科](https://en.wikipedia.org/wiki/Idempotence)的幂等性定义:

> **幂等性** ( [英国](https://en.wikipedia.org/wiki/British_English) : [/ˌɪdɛmˈpoʊtəns/](https://en.wikipedia.org/wiki/Help:IPA/English) ，[【1】](https://en.wikipedia.org/wiki/Idempotence#cite_note-1)[美国](https://en.wikipedia.org/wiki/American_English):[/ˌaɪdəm-/](https://en.wikipedia.org/wiki/Help:IPA/English))[【2】](https://en.wikipedia.org/wiki/Idempotence#cite_note-2)是[数学](https://en.wikipedia.org/wiki/Mathematics)和[计算机科学](https://en.wikipedia.org/wiki/Computer_science)中某些[运算](https://en.wikipedia.org/wiki/Operation_(mathematics))的属性，由此它们可以被多次应用而不改变超出初始应用的结果。

你可能会问，这如何适用于信息传递。在消息传递体系结构中，幂等性意味着确保可以无限次处理相同的消息，并且结果总是相同的。这意味着没有重复的数据库记录，没有电子邮件，或其他类型的通知发送多次。这种方法有以下好处:

*   不需要交易。它们在消息传递基础设施中可能相当棘手。通常，消息处理程序调用其他服务，跨多个系统管理事务是相当困难的。
*   允许使用重试，而不用担心使用者第二次处理消息时可能会失败。

如何开始使用？为了避免在数据库中创建重复的记录，您需要添加一个检查。它将在添加新记录之前验证该记录是否存在。如果记录已经存在，您应该返回现有记录或跳过创建新记录。这取决于具体的用例。

为了避免重复发送通知，例如电子邮件或短信，您需要将之前发送的信息保存在某个地方。最明显的选择是数据库。然后添加一个逻辑来验证是否已经发送了相同类型的通知。

在消费者端的所有地方应用这种模式，您将能够无限次地处理相同的消息。

## 邮件发件箱

提高消息传递可靠性的另一种方法是在生产者(发布者)端使用消息发件箱。当你失去和 RabbitMQ 的连接时，信息发件箱是一个很好的处理方法。您希望在不使用户操作失败的情况下将消息发送给消费者。

实现这一点的一种方法是添加一些持久性存储来保存序列化的消息。持久存储的类型无关紧要。这可能取决于您公司使用的数据库技术，也可能是您最了解的数据库。您还需要创建一个基于计时器的后台作业，稍后将重新发送这些失败的消息。这将保证消息不会丢失。当然，数据库也可能不可用。在这种情况下，一种选择是在 GUI 中显示出错的错误消息，用户应该联系支持人员。

让我向您展示创建发件箱的两种可能方式。

MassTransit 提供[内存信息发件箱](https://masstransit-project.com/2020/02/08/in-memory-outbox/)。你可以观看克里斯·帕特森的一个很棒的[视频](https://www.youtube.com/watch?v=P41IsVAc1nI)，在那里他展示了《发件箱》与传奇的实践。你可以在 [GitHub](https://github.com/phatboyg/Trashlantis) 上查看他的源代码。

我将展示如何实现消息发件箱的另一种方法。在我的例子中，消息发件箱驻留在生产者端，它可以处理 RabbitMQ 关闭时的情况。

我使用了以下技术:

*   [RabbitMQ](https://www.rabbitmq.com/)
*   [MassTransit](https://masstransit-project.com/) 库
*   [。网络核心 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
*   [MongoDB](https://www.mongodb.com/)

我已经创建了。NET 核心控制台应用程序，并使用[工人服务](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#worker-service-template)模板来托管三种类型的服务:

*   消息发布者服务
*   信息发件箱处理服务
*   消费者服务

如果发布失败，Message publisher 服务负责将消息保存在 MongoDB 中。

消息发件箱处理服务从 MongoDB 收集所有未处理的消息，并尝试发布它们。

请注意，在进行消息处理时，我使用了 MongoDB 事务。如果失败，消息状态将设置回未处理。使用事务的另一个原因是确保数据库中的记录在事务期间被锁定。下面是启动事务的方法的示例。该类的完整代码可在 [GitHub](https://github.com/viktors-telle/mass-transit-examples/blob/master/src/MessageOutbox/Outbox/MessageOutboxRepository.cs) 上获得。

如果上一步运行正常，消费者服务将会收到这些消息。

## 结论

这里描述的方法在生产环境中经过了实战检验，效果相当好。消息重发、等幂和发件箱减少了支持工程师的手工工作，使我们的服务更加稳定，对各种错误更有弹性。

你可以在 [GitHub](https://github.com/viktors-telle/mass-transit-examples) 上查看完整的例子。

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)