# 多平台 SaaS 应用的 2020 年发展选择|数据驱动的投资者

> 原文：<https://medium.datadriveninvestor.com/2020-development-choices-for-multi-platform-saas-application-data-driven-investor-fa27ffb2645a?source=collection_archive---------15----------------------->

![](img/bf925ca6eea91915aa02791f17314773.png)

我目前正在为公司做一个新项目。该项目包括一个由服务器支持的移动应用程序；一个非常标准的 SaaS 项目设置。

在本文中，我想讨论实现这个项目的不同开发选项。我知道这些项目在今天有多受欢迎，所以我希望这个总结研究可以帮助你快速做出正确的选择。

这个评估过程应该在开始一个新项目之前完成。过程的深度(以及它消耗了你多少时间)应该与项目的规模和预期寿命相关。

选择正确的工具可以在开发的初始阶段给你所需要的推动力，并为进一步的扩展铺平道路。

我会和你一起完成我正在做的项目。我的项目的需求可能与你的不同，所以你应该相应地调整过程以适应你的需求。

[](https://www.datadriveninvestor.com/2020/06/03/the-modern-day-solo-medical-practice-needs-more-than-just-a-technology/) [## 现代个体医疗实践需要的不仅仅是一项技术。数据驱动的投资者

### 围绕医疗保健的官僚主义和不断增加的行政负担对任何医学专家来说都不陌生…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/06/03/the-modern-day-solo-medical-practice-needs-more-than-just-a-technology/) 

为了使这一过程成功，您需要客观地看待非技术/业务方面。你可能更喜欢某些技术。你可能会对你知道的解决方案感到更舒服。技术战偶尔会像病毒一样传播，可能会影响到你。所有这些都要考虑进去，才能让它达到应有的客观。

评估流程由以下步骤组成:

1.  列出您的所有需求—技术、业务…
2.  找到三个最好和最受欢迎的解决方案——简单的网络搜索
3.  选择两个最合适的选项——更深入的网络搜索
4.  两个选项的详细比较
5.  如果难以区分，则实施 POC
6.  更新比较
7.  以一个解决方案结束，同时考虑未来的变化

人们经常把这样的项目分为前端和后端。为了简单起见，我将[分别处理](https://www.datadriveninvestor.com/glossary/address/)，但是你应该总是考虑它们之间的联系和一致性。我将在另一篇文章中讨论这种联系。

大部分的比较都是依靠网络上的相关资源来完成的。当搜索这样的来源时，应该仔细寻找可靠的和最新的来源。

可靠性可以通过以下方式验证:

1.  检查网站的声誉——知名度、软件开发的专业性和非品牌相关；我们无法在[节点](https://www.datadriveninvestor.com/glossary/node/)的官方网站上查看 NodeJS 是否良好
2.  作者的客观性——我们不能依赖作者的想法和偏好
3.  文章的形式——正式语言的使用，文章元数据的可用性

最后一个主题将给我们关于文章写作时间的信息，从而帮助我们找到最新的信息(技术发展很快，尤其是在它们的初始阶段)。此外，我们可以使用搜索引擎的工具过滤掉旧的结果。

注意:当没有足够的信息时，我们可以通过与其他文章进行比较来验证文章的可靠性。

# 前端

我们的主要要求是前端需要运行在 Android、iOS 和 Web 平台上。为了提高业务效率，**最佳解决方案需要基于跨平台开发框架**(因为开发两个独立的原生应用非常昂贵)。

这些框架在过去的几年里已经足够成熟，今天它们已经可以用于企业应用程序中(像 Skype、脸书/Instagram 和 Google Ads 这样的应用程序已经使用这些框架开发出来)。

这一领域的领先框架是 React Native、Flutter 和 Xaramin。

React Native 和 Flutter 比 Xaramin 更新，更受欢迎，性能也更好(更多细节见这篇[文章](https://blog.logrocket.com/flutter-vs-react-native-vs-xamarin/))。

真正的竞争是在 React Native 和 Flutter 之间。

# 反应自然 vs 颤动

我的项目要求是:

*   对 Web、Android 和 iOS 的本机支持
*   移动硬件的使用—例如位置、文件系统、摄像头…
*   支持地图——首选是谷歌地图，但也应考虑其他地图提供商
*   良好的统一用户界面定制(适用于所有平台)——例如日历支持
*   接近自然的表现
*   所有平台之间的共享代码

这篇[文章](https://dev.to/fyresite/react-native-vs-flutter-for-cross-platform-development-in-2020-3nak)做了一个很好的对比。

**两个框架几乎是平局**。**需要执行 POC，以得出更适合我们使用情形的结论。**

我做了一个简单的概念验证来验证我的要求。POC 包含一个欢迎屏幕和一个地图视图屏幕。在欢迎屏幕中，我添加了一个带有日历的表单。在地图屏幕上，我显示了设备的位置和一个固定地点的自定义标记。这足以让我对以后要处理的事情有所了解。

# 考虑使用情形时的主要差异

**UI: (** ReactNative)内置 UI 不好看(纯 HTML UI)但是可以极度定制。有很多 UI 库(一个完整的 UI 设计系统)看起来很棒，并且支持所有平台。您也可以创建自己的元素。
(颤动)内置 UI 在所有平台上看起来都没问题。您可以创建自己的 UI 元素。UI 库更多的是特定的小部件/元素，而不是一个完整的设计系统(就像在 RN 中一样)。

**赢家** - Flutter(只因为不需要外部库就能获得良好的基本 UI)

**与后端代码共享**(查看后端部分):(ReactNative)如果后端是用 JS 写的，可以有代码共享。
(Flutter)后端可以用 Dart 编程，但不是我们后端的选择之一。transpile 后可以共享为 JS 代码。

**获胜者** -反应型

**学习曲线:** (ReactNative) JS 语言简单易学。React 原生框架更难学，官方文档也不错，但还不够。从反应到 RN——非常简单。
(扑)镖语简单易学。从官方文档中学习 Flutter 框架有些容易。

**获胜者** -颤振

**社区支持:**就反应而言，它是一流的。在颤动中，它不见了。

**胜利者** —反应者

**最容易雇佣:** (ReactNative)几乎每个开发者都知道 JS。有许多开发人员在为 web 开发 React。
(Flutter) Dart 对这个行业来说是新的，因此几乎每个开发人员都需要学习这种语言。

**胜利者** -反应者

**平台支持:** ReactNative 完全支持，而 Flutter 对 web 的支持处于测试阶段。

**胜利者** -反应者

**环境设置:**(都)因为跨平台支持，对新人来说比较难。

**地图支持:** (ReactNative) 有 Google、Apple、Mapbox 地图的库。需要修改以支持 web 地图。只有谷歌地图库，而且是测试版。

**胜利者** -反应者

**硬件支持:**(两者)几乎相同

*注*:这是一个更大的对照表的汇总版。更大的版本包括了额外的方面，这些方面由于其不显著的差异或重要性而从该表中省略，并且用加权 1-5 分对每个方面进行评级(权重代表与用例相关的某个方面的重要性)。

# 结论

如前所述，这些框架几乎完全相同。但是当您考虑到业务需求和技术要求时，我们可以说此时 **React Native 是更好的选择** (Flutter 将在几年内缩小这一差距)。

# 后端

目前业界对此类用例最流行的选择是。NET Core(核心)、NodeJS(节点)、以及 [Python](https://www.datadriveninvestor.com/glossary/python/) 。

请注意，虽然 Core 是一个完整的一体化框架，但 Node 和 Python 不是。Node 更像是 web 框架所基于的运行时环境。Python 是一种通用的编程语言，它有许多用于 web 开发的[框架](https://www.hackernoon.com/top-python-web-development-frameworks-to-learn-in-2019-21c646a09a9a)。

将要考虑的框架是用于 Python 的 Django 和用于 Node 的 ExpressJS，因为它们是最流行的框架。

我们需要尝试和判断这些技术，而不需要参考特定的实现(框架)，但是由于异构比较，我们可能需要依赖社区驱动的实现标准(流行的框架)。这并不意味着我们局限于使用最流行的框架进行开发。

Django 是一个非常大的框架，非常适合开发企业应用程序。然而，它会减缓初始开发(更加臃肿)并且性能较差，为此它会输给核心和节点。查看这篇[文章](https://dottutorials.net/top-5-backend-frameworks-to-learn-in-2020/)了解更多信息。

。NET Core 是新的跨平台框架，它将取代。NET 框架。[这些](https://docs.microsoft.com/en-us/dotnet/standard/choosing-core-framework-server)就是两者的区别。

# NodeJS 与. NET 核心

# 一般比较

Node 基于 JavaScript (JS)编程语言，这种语言的名声不好，因为:

*   [回调地狱](http://callbackhell.com/)
*   问题排除—复杂代码中的堆栈跟踪很难理解
*   硬调试—有几个原因:
*   JS 作为异步的本质
*   回调地狱
*   动态打字
*   代码重用和模块化问题——在 JS 中解耦代码变得更加困难(不太自然)
*   类型安全/动态类型——是 JS 中许多问题的原因。一开始可能会很有趣，但是当编写大量代码时，建议我们利用静态类型。

然而，核心(C#)开发人员并不关心这些问题。

这些问题在过去是真实存在的，但是自从 JS 引入了新的改进之后:

*   异步/等待机制(自节点 v7.6 22/02/2017 起)—基于 JS 的生成器函数。这篇[文章](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9)解释了为什么回调地狱、故障排除和调试不再是一个问题。
*   [ES6+](https://webapplog.com/es6/) 修复了 JS 的多种语法问题。
*   [Typescript](https://en.wikipedia.org/wiki/TypeScript) 是 JS 的超集，它使用静态类型并将“关键的”OOP 概念引入 JS。这里解释了 ES6 和 Typescript 的区别[。](https://www.javatpoint.com/typescript-vs-es6)
*   模块化问题在 [ES6](https://www.cuelogic.com/blog/advantages-of-javascript-es6-over-es5) 中解决，ES6 是[内置节点](https://nodejs.org/en/docs/es6/)。

这篇[文章](https://www.samarpaninfotech.com/blog/net-core-vs-nodejs-for-enterprise-web-development/)总结了核心和节点的区别(最新)。

# 考虑使用情形时的主要差异

*   节点被认为比核心更小(占用空间更小)。
*   [前端选择](https://docs.google.com/document/d/1fkQnQMqlxJ8Vk7yOLVAUO7hzmKsEQ7_nAAoy4sCr4vA/edit#heading=h.db7c2eine893) (React Native)，给节点一些优于核心的优势；由于两者都基于 JS，代码可以在前端和后端之间共享。
*   Node 更容易启动中小型应用程序，而 Core 更适合大中型应用程序。
*   Npm，Node 的包管理器，是一个非常强大的工具，被认为是优于其他框架(如 NuGet)的一大优势，它有一个巨大的库。
*   。NET Core 更适合在 Windows 上开发——Nuget 是一个在 Linux/Mac 上开发所缺少的工具的例子。
*   核心性能更好——更适合 CPU 密集型任务(尽管我没有找到最近版本的详细基准)。
*   Node 更适合[客户端](https://www.datadriveninvestor.com/glossary/client/)交互——在开发时更有效，例如 Node 中的直接路由机制。
*   框架的并行性和伸缩性——稍后见。

这篇[文章](https://medium.com/@guillaumejacquart/experience-on-working-with-asp-net-core-and-nodejs-5e6c6351fc1f)详细阐述了不同之处(写于 2017 年— CI/CD 今天对于 Core 来说要成熟得多)。

# 可扩展性和性能

几乎相同；核心使用多线程(单进程)进行扩展，而节点使用多进程(单线程)进行扩展。

性能几乎相同(如果部署正确)。

这两种扩展概念之间的主要区别可能是优势/劣势:

*   更容易在单线程上开发。
*   多线程具有共享内存，这对于开发来说更加直观，但也使得解耦和利用微服务概念变得更加困难。

# 平行

节点本质上是异步的(JS ),核心被认为是同步的；Node 中的所有代码都是异步运行的，无论何时需要同步，都必须声明它并使用语言/框架提供的机制之一。相比之下，核心中的所有代码都是同步的，当需要异步时，您需要针对特定的操作使用多线程开发。异步主要与 IO 阻塞操作相关。

另一个相关的区别是，Node 是事件驱动的，而 Core 不是(在选择代码的架构方面有更大的灵活性，但是作为事件驱动来使用会更加臃肿)。

优点/缺点:

*   对于 OOP 开发者来说——开发同步代码更加直观。
*   异步开发更适合 IO 密集型和实时应用程序(如聊天)。

# 结论

没有一个好的选择，正如我们前面看到的，Node(更准确地说是 JS)解决了它所面临的所有问题(尽管需要几年时间来纠正这种声誉)，可以被认为与企业应用程序的 Core 一样重要。这个决定仅仅是基于偏好和未来的需要。

有许多项目同时使用核心和节点的例子。

为了更快的开发，最好的计划是从节点开始(因为 MVP 通常具有不复杂的功能)，之后我们可以为 CPU 密集型功能和复杂的业务逻辑集成核心。使用这两种框架，架构将是微服务兼容的。

# 临终遗言

对我来说是对的，对你来说可能是错的。总是检查我的基本假设是否适用于你。

然而，希望这能让你看到一条更容易管理和更有思想的道路。

*原载于 2020 年 7 月 13 日*[*【https://www.datadriveninvestor.com】*](https://www.datadriveninvestor.com/2020/07/13/2020-development-choices-for-multi-platform-saas-application/)*。*

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)