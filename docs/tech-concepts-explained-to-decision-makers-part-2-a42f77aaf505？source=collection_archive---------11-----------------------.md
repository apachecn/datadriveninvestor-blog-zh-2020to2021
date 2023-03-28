# 向决策者解释技术概念|第 2 部分

> 原文：<https://medium.datadriveninvestor.com/tech-concepts-explained-to-decision-makers-part-2-a42f77aaf505?source=collection_archive---------11----------------------->

在这一部分中:

*   什么是 *CDN* ？
*   理解*微服务*的概念。
*   什么是*框架*以及它与*语言*的区别？

![](img/24f387b62a2cfcea5947da6cea73c2ea.png)

“Young me” teaching “Tech Slang” to my previous marketing team

# 什么是 CDN？

***CDN*** :一个*内容交付网络*是多台服务器的服务，通常分布在全球各地**以更快地传递信息**。这个想法是，这些服务器并不托管实际的数据，而是托管数据的映像。真正的数据托管在 *origin* 服务器上，你会在专门的段落中了解到更多。

图像作为一个 TTL(生存时间),一般来说，一旦这个 TTL 通过，你网站的第一个访问者将**无缝触发从*源*服务器检索数据**。因此，对于这个特定的访问者，响应时间可能有点长。但是对于来自世界任何地方的所有其他访问者来说，响应时间将被优化。

截至目前，大多数高流量网站都在使用某种 CDN 服务。如果你的目标受众是整个世界，甚至只是一个大洲，你应该考虑投资 CDN 服务。最知名的服务是 **Akamai** 和 **Cloudflare** 。如果你用的是 AWS 生态系统，也可以用 AWS Cloudfront。

[](https://www.datadriveninvestor.com/2020/08/12/how-congress-blindly-sees-the-future-of-tech-companies/) [## 国会如何盲目地看待科技公司的未来

### 美国国会召集 4 家大型科技公司的首席执行官在全国电视上表演马戏…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/08/12/how-congress-blindly-sees-the-future-of-tech-companies/) 

一个 *CDN* 也是一个**主要的安全提升**，因为你不是直接攻击你的*源*服务器，而是通过一个由服务器连接而成的网络，这些服务器拥有专门过滤和分类请求的技术。我将在另一篇文章中详细解释 CDN 的所有安全优势。

***起源* :** 如果你使用 *CDN* 服务，你可能会经常听到*起源*服务器*这个术语。*非常简单，它设计了真正数据所在的**服务器**。一般来说，服务器位于世界的某个特定地区，例如法国，如果你的市场之一是印度，你将尝试为你在印度的访问者签订一个 *CDN* 服务合同，以获得与你在法国的用户相同的体验。

重要的一点是，这个系统的性能提升对于静态或者普通页面来说是实实在在的。比如你的**登陆页面**。但是，如果你有一个经过认证的后台和定制互动的 UX，你将不会受益于 CDN 的性能提升。在这种情况下，**可以考虑为不同的市场建立专门的网站**。

![](img/5103e431783853dc940c82d9a2e43cd6.png)

Photo by [Anastasia Dulgier](https://unsplash.com/@dulgier?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 微服务与整体服务

***Monolith*** :我自愿从这个定义开始，通过对立来帮助你理解*微服务*的概念。在这里，我们讨论的是**架构概念**。自从软件工程开始以来，每个人都在使用 Monolith 架构。

简单来说，这意味着你的项目的每个技术方面都在同一个地方(或者几乎在同一个地方)。你通常有一个服务器来存放你的代码和数据库。有时候是在两个不同的服务器上可以通信。但是**所有的特性都打包在同一个地方**。在同一块*巨石*上。这意味着应用程序的每个特性都使用相同的公共资源。不管是什么类型的行动。

***微服务*** :这几年最流行的名词之一。关键的概念是，不是有一个巨大的地方来存放你所有的代码和特性，而是把它分成几个更小的服务，做同样的工作，但是作为一个组。最简单的例子是发送事务性电子邮件。

假设你有一个组织活动的网站。当活动即将开始时，您希望向所有订阅者发送电子邮件通知。与其让你的 *Monolith* 处理邮件发送，这会导致整个网站运行缓慢，不如创建一个*微服务*负责发送这些邮件。一旦到了你的网站联系人的时候，你把请求发送到这个服务，服务会处理邮件发送，而网站本身保持正常运行。

比如**亚马逊**，在其首页**有上百个*微服务*** 同时工作。这种架构可能是最佳解决方案，但如果您从头开始，它可能会变得昂贵。它最适合技术改造。因为你可以在现有的 *Monolith* 的基础上创建新的*微服务*，而不必关闭你的站点。如果您的期限很紧或者预算有限，可以考虑从更标准的架构开始。

![](img/90c0361d74ca5bdd0bbdd5c418cd5f85.png)

Photo by [Max Duzij](https://unsplash.com/@max_duz?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 语言 VS 框架

***语言* :** 要建立一个网站或软件，你必须写出其特性的代码。并不是所有的*语言*都适合所有的情况，你可能需要将其中一些结合起来。例如，HTML 和 PHP 几乎总是一起使用。它们都是网络语言，但执行的任务不同。使用 HTML，您将构建您的页面来呈现它们，同时您将使用 PHP 函数检索当前时间来显示时间和日期。

以前有 web 项目专用的*语言*和软件专用的*语言*。如今，这种区别趋于模糊。随着软件越来越多地变成 SaaS 解决方案，一切都是网络的，一切都是移动的。以下是你可能听说过的主要语言:HTML、PHP、Javascript、Java、Python、SQL、C、C++、Scala、Kotlin 等等

[](https://md17.medium.com/how-to-properly-manage-multiple-ssh-keys-for-git-on-your-local-environment-14b9d89307e9) [## 如何在本地环境中正确管理 Git 的多个 SSH 密钥

### 基本用例:为单个存储库部署密钥。高级用例:多个存储库的多个部署密钥

md17.medium.com](https://md17.medium.com/how-to-properly-manage-multiple-ssh-keys-for-git-on-your-local-environment-14b9d89307e9) 

***框架* :** 你可能听说过一些 PHP 最流行的*框架*，比如 **Symfony** 或者 **Laravel** 。常见的错误是认为这些是语言。Symfony 或者 Laravel 都是用 PHP 写的。所以当有人在用这些*框架*构建项目的时候，是用 PHP 构建的。

一个*框架*就是一个**架构工具包**。它的目标是帮助你**构建**你的项目**更快**和**避免**重大**安全** **漏洞**。它包含预构建的功能和技术工具，可以帮助您只关注功能，而不是体系结构。在开源项目社区的帮助下，或者在开发团队提供的授权*框架*的发展下，你的工具包在不断发展。

# 在下一部分

先睹为快，看看下一部分的主题:

*   UX VS UI
*   架构与基础设施
*   持续集成与持续部署

如果你对某个特定的主题感兴趣，请使用评论部分，我将在下一部分中介绍它。

谢谢你读我的台词。

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)