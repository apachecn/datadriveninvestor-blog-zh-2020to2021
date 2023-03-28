# 向决策者解释技术概念|第 1 部分

> 原文：<https://medium.datadriveninvestor.com/tech-concepts-explained-to-decision-makers-part-1-cbf38392115?source=collection_archive---------5----------------------->

在这一部分中:

*   后台/前台和后台/前台的区别。
*   了解 *Git* 及其平台 *Github* 和 *Gitlab。*
*   SaaS 的含义及其如此受欢迎的原因。

![](img/24f387b62a2cfcea5947da6cea73c2ea.png)

“Young me” teaching “Tech Slang” to my previous marketing team

# 后台/前台与后台/前台

***后台*** :一般由您网站上的一个连接部分组成，您可以在其中编辑内容并执行将对*前台*产生影响的操作。在 WordPress 博客上，*后台*包含了发布博客文章的所有工具。在 Shopify 这样的解决方案上，你的*后台*将包含监控你的销售和财务的仪表盘。

***前台*** :与*后台*相对，这是你网站向公众展示的部分。内容可以存储在数据库中，并在用户访问页面时检索，这是大多数网站的标准情况。也可以是*静态* *内容*意思是内容在代码内部，所以不需要数据库。

[](https://www.datadriveninvestor.com/2020/05/24/do-i-need-a-technical-cofounder-a-guide-for-startups/) [## 我需要一个技术合伙人吗？创业指南|数据驱动的投资者

### 如果你在问这个问题，那么你从根本上问的是你正在建立的公司的类型…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/05/24/do-i-need-a-technical-cofounder-a-guide-for-startups/) 

***后端:*** 经常与*后台*混淆，术语*后端*用于架构和编码概念。任何一种网站、app、平台都有*后端*技术。在 web 行业，目前主要的*后端*技术有 *PHP* 、 *Node.js、*和 *Python* 。简单来说:*后端*负责检索内容并对数据执行操作。后端工程师将构建数据库，并设计访问和操作数据的方法。例如:作为 Medium 的内容创建者，我点击了“新故事”按钮。*后端*负责在中型数据库中创建条目，负责定期自动保存和许多其他功能。

***前端* :** 直到现代*前端*技术的到来，术语*前端*才被用来定义样式定制(也称为 CSS)、实际的页面组装(HTML)，以及一点点用户效果(Javascript)。如今，随着 Angular、React 或 Vue 等 Javascript 搭建技术的出现， *Frontend* 有了广泛的应用。仍然包含设计和搭建，现在*前端*可以与*后端*异步对话，并为最终用户提供无缝体验。以我们之前的例子为例:作为 Medium 的内容创建者，我点击了“新故事”按钮。*前端*负责显示内容创建页面，当您点击“+”时显示工具栏，当您想要从 Unsplash 添加图像时询问*后端*。

![](img/812a1dfbecbbbd494ee4170d44f58647.png)

Photo by [Yancy Min](https://unsplash.com/@yancymin?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# Git VS Github/Gitlab

***代码版本控制*** :开发团队使用的一个概念，用于跟踪他们代码的不同更新，并高效地一起工作。使用代码版本控制对于任何现代项目都是强制性的，全球范围内，对于任何团队都是如此。如果你是一个人的团队，你可以在没有代码版本控制的情况下生存，但是建立代码版本控制总是会提供附加值。

***Git*** :可能是世界上最著名的版本控制解决方案。它曾经与来自阿帕奇的 SVN 针锋相对，但是现在已经没有竞争了，因为 Git 赢得了开源竞赛。 *Git* 是一个引擎，有它的语言。是**不是**一个平台，是**不是**一个网站。Git 是一个可以安装在本地环境和服务器上的模块。您将在命令行中使用它的语言来执行版本控制操作。需要理解的有用表达:使用 *Git* 的项目被称为 ***库*** 。 *Git* 使用 ***分支*** 来分隔不同版本的代码。 ***主*** 分支一般是项目的现场版。为了与团队的其他成员分享他们的代码，开发人员将 ***提交*** 他们的代码，然后 ***推送*** 他们正在工作的分支。当你不是程序员的时候，我会写一整篇文章来讲述如何理解 *Git* 及其好处。

Github :这是最流行的 *Git* 库平台。 *Github* 是一个 SaaS 解决方案，处理 *Git* 库的托管。您可以将您的存储库设置为 ***Public*** ，主要由开源项目或学生使用。或者可以建立一个 ***私有的*** 资源库，一般用于专业项目。最需要理解的是 ***Github* 并不托管你的项目， *Github* 托管你的代码及其版本。**使用 Github 的费用取决于你需要的私人项目的数量和规模

Gitlab :与 *Github 非常相似，Gitlab* 也是一个用于 *Git* 仓库的平台。两个平台的主要区别在于 Gitlab 有 SaaS 版本和内部版本。它允许团队托管自己的 *Gitlab* 环境，并对其拥有完全的控制权。这可能被视为节省预算的有效方法，但重要的是要明白你需要一个人来维护它。不是全职的，而是为了维护的目的。如果你经营一个多项目机构，你需要考虑 SaaS 版本。如果你的本地 *Gitlab* 平台宕机 2 小时，你可以让几个团队随时待命。

# SaaS VS 内部部署

***SaaS*** :软件即服务。任何种类的服务、工具或平台都可以被构建成 *SaaS* 。这意味着您不必托管、维护或开发解决方案，您可以订阅一个 *SaaS* ，并且只关心如何以最佳方式使用它。通常，SaaS 平台是以每月订阅为基础进行营销的，并根据资源使用情况进行演进定价。流行的 SaaS 平台:用于代码版本控制的 Github，用于项目管理和票务的吉拉，以及用于几乎任何事情的 AWS。

*:这个术语指的是需要自己安装、配置和维护的解决方案。这些解决方案的主要优势是您可以自由使用该解决方案。你可以有 10 或 1000 个用户，每个月的账单不会有巨大的差距。缺点是需要知道如何配置和维护解决方案。*

*一般来说，**与内部解决方案相比，大公司更喜欢 SaaS。如果你想了解更多关于**为什么**你可以看看**我关于这个话题的文章**。***

*[](https://medium.com/swlh/why-major-companies-prefer-saas-over-in-house-solutions-85ce58fedc23) [## 为什么大公司更喜欢 SaaS 而不是内部解决方案

### 是财务方便吗？他们如何创造附加值？如何建立自己的 SaaS 业务？

medium.com](https://medium.com/swlh/why-major-companies-prefer-saas-over-in-house-solutions-85ce58fedc23) 

# 在接下来的部分

先睹为快，看看下一部分的主题:

*   语言 VS 框架
*   Cookies 与会话
*   微服务与整体服务

[](https://medium.com/datadriveninvestor/tech-concepts-explained-to-decision-makers-part-2-a42f77aaf505) [## 向决策者解释技术概念|第 2 部分

### 我们一起继续探索技术俚语和技术概念，帮助您做出更好的决策。

medium.com](https://medium.com/datadriveninvestor/tech-concepts-explained-to-decision-makers-part-2-a42f77aaf505) 

如果你对某个特定的主题感兴趣，请使用评论区，我会与你联系。

谢谢你读我的台词。

**进入专家视角—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)*