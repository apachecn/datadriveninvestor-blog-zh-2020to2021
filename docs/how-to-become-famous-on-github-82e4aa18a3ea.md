# 如何在 GitHub 上成名

> 原文：<https://medium.datadriveninvestor.com/how-to-become-famous-on-github-82e4aa18a3ea?source=collection_archive---------6----------------------->

![](img/c4480582d11dcb3788b5d0e230212285.png)

Photo by [Andrew Neel](https://unsplash.com/@andrewtneel?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

GitHub 可能拥有这个星球上最大的开源软件集合。对于开发者和组织来说，这是一个协作、学习和集成的生态系统。你可以写软件，贡献给其他软件，或者在其他项目和产品中使用自由开放软件。这是一个不可思议的工具，它为编程世界提供了动力，促进了访问和协作，为每个人制作开源软件。

作为一名开发者，使用 GitHub 来推进你的事业或者增加你在开源领域的影响力是有点不同的。在 GitHub 上出名并不是一件简单的事情，需要对是什么推动了开源包的使用，以及是什么让最受欢迎的包与众不同有着复杂的理解。我将讨论作为开发者使用 GitHub 的最佳和最差方式，以及如何在网站上创建下一个趋势库或包。不保证，但希望你会受到启发，并被引导到正确的方向。

# 一个生态系统

GitHub 是一个相当开放和无限制的平台。您可以创建存储库，并根据您的需要使用它们。甚至有很多人使用 GitHub 来制定计算机科学课程计划。还有一些应用程序与 GitHub 上的存储库集成，比如 [Git Books](https://www.gitbook.com/) 。GitHub 是一个封装在存储库中的代码生态系统，类似于社交媒体网站是一个包含文本、图片和交互的生态系统。

任何使用 GitHub 的人或人群通常可以分为两类:消费者和生产者。消费者主要使用 GitHub 来使用网站上的软件并将其集成到自己的应用程序中。生产者编写代码是为了让其他人使用他们在网站上发布的回购代码。虽然有些人肯定可以体现这两种类型，但他们通常倾向于一种对他们来说更常见的使用模式。

理解什么样的库和包被频繁使用是很棘手的。该网站包含一些更容易流行的包，以及一些可能永远不会被使用的包。然而，区别并不像你想象的那样。具有罕见用例但产品质量代码和接口的包，比具有普通用例但质量差的代码的包更受欢迎。这将在后面详细讨论。

[](https://www.datadriveninvestor.com/2020/07/13/2020-development-choices-for-multi-platform-saas-application/) [## 多平台 SaaS 应用的 2020 年发展选择|数据驱动的投资者

### 我目前正在为公司做一个新项目。该项目包括一个移动应用程序，由一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/07/13/2020-development-choices-for-multi-platform-saas-application/) 

GitHub 上软件包的另一个重要部分是打包系统。大多数编程语言都有一些用于管理开源或第三方包的构建或安装系统。任何流行的软件包，不管它有多直观或有用，都必须能够很容易地集成到其他项目中。如果有一个很大的学习曲线或障碍，只是为了达到你可以使用一个包的程度，它很可能不会走得很远。

但是，打包并不是使包易于集成的唯一组件。相反，一些软件包关注工具而不是代码束。这种包的一个很好的例子是 [ripgrep](https://github.com/BurntSushi/ripgrep) 。Ripgrep 是一个 CLI 工具，允许您搜索文件和目录中的正则表达式模式。除此之外，它的目标是以极快的速度运行，比你可能已经使用的典型`grep`要快得多。Ripgrep 是用 rust 编写的，rust 是一种跨平台、本机编译的编程语言。通常，发布跨平台的二进制文件有点困难，因为你要么需要下载一个编译器从源代码编译它，要么为每个平台发布一个二进制文件。有了`rust`，有了[的板条箱](https://crates.io/)系统，安装二进制文件就变得更容易了，因为它可以自己管理 CLI 工具的安装。理论上，您可以只使用两个终端命令来安装 ripgrep。

# 需求

需求是在 GitHub 上获得恶名的关键因素。一个项目或软件包通常会因为独特、有趣或“酷”而获得最初的知名度。这既包括完全深奥的项目，也包括功能性但主要用于休闲目的的项目。一个例子是关于[我自己的努力](https://github.com/jweinst1/Oblivion)，一种编译成 SVG 图形的语言。我的主要灵感来自于我对艺术和编程的热爱。它最初获得了一些牵引力和知名度。然而，这种语言只是用来画线和填充线条形状的。对于学习编码的人来说，这可能很有趣，但是缺少 SVG 规范中更复杂的特性，比如转换和动画。因此，它从未在网站上获得过几百颗星。

获得成千上万明星和用户的项目需要一个可应用于生产的目的，或者一个大的开发者社区。前一类包含的项目是功能更全的软件，通常可以独立运行，比如像 [Redis](https://github.com/redis/redis) 这样的数据库，或者像 [Elastic](https://github.com/elastic/elasticsearch) 这样的搜索引擎。这类项目通常作为公司或组织使用的技术堆栈的独立组件，不需要其他包来运行。梯形类别包含不能直接用于生产环境的项目，但是允许创建可以用于生产环境的全功能软件。编程语言、机器学习或数据科学库、质量保证和测试包，每天都有大量的开发者社区在使用他们的项目。许多编程语言甚至举行年度会议，开发者来这里展示他们用这种语言完成的工作的用例。

为了让你或你的项目在 GitHub 上出名，你需要思考是什么解决了一个问题或者提供了一个很多人可以使用的解决方案。

# 现实一点

你还必须对你的项目想法现实一点，比如完成它们需要多长时间，以及你是否有时间完成它们。这是“边”项目的主要问题。人们通常会开始他们永远无法完成的项目。你不太可能有时间或耐心来开发自己的操作系统。如果你选择在 GitHub 上做你自己的项目，先从一个简化了一些任务的库开始，完成后再向上扩展。

# 贡献与创造

在 GitHub 上编码和开发时要考虑的一件事是，你是否应该为现有的项目做贡献，或者创建你自己的项目。很有可能不管你选择哪一个，你都会两者兼而有之。不过，记住以下几条建议很重要，因为你最终会希望以一种对你未来有益的方式明智地利用你的时间:

*   不要为非常小的项目做贡献，除非你相信他们有很大的潜力来获得一个大的社区。由于项目成熟度或设计变更，项目的早期贡献可能会被完全重写或删除。
*   除非项目特别要求，否则不要改进行距或格式。在较大的项目中，这样的贡献可能会被拒绝，因为这样做是试图将你的名字添加到贡献者列表中，而对项目没有任何功能上的贡献。
*   做与代码质量或代码安全相关的贡献。这些类型的更改有助于改进产品的功能，或者使其对严重的错误(如崩溃或内存泄漏)更加不利。
*   对于成熟项目的大型贡献，试着了解你的贡献是否会被接受。对旧项目的设计进行重大修改不太可能被批准或接受。这就是为什么较小的变化和改进通常是首选。

除此之外，仔细考虑你的贡献，明智地使用你的时间，你可能有很好的机会在 GitHub 上获得一些名气。

**进入专家视角—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)