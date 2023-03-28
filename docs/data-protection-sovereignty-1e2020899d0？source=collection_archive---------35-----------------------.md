# 数据隐私保护和主权

> 原文：<https://medium.datadriveninvestor.com/data-protection-sovereignty-1e2020899d0?source=collection_archive---------35----------------------->

## 数据隐私事关人类尊严

![](img/be26d13a40ff5d0ebdd4064aa2879a5f.png)

Photo by [Jason Dent](https://unsplash.com/@jdent?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 介绍

我们的生活越来越被数字世界扭曲。使用数字工具对我们来说已经变得很自然了。然而，数字隐私的概念却没有。我们从物理意义上理解隐私。我们关上门。我们拉上房间的窗帘。但是我们中的许多人不阅读隐私政策。我们只是同意他们的观点。我们让公司访问我们的隐私数据，如地理位置数据，IP 地址等。

[Times Opinion 的数据隐私项目](https://www.nytimes.com/interactive/2019/12/19/opinion/location-tracking-cell-phone.html)收集了 1200 万美国人的地理位置数据，并表明我们的身份可以仅从我们的地理位置数据中推断出来。每次您打开 GPS 拍摄优步时，都会共享您的位置。两个人共用一个家和工作场所的可能性有多大？这个问题因称为隐私政策的复杂用户条款而加剧。如果我们盲目同意隐私政策，我们就不知道我们在分享什么数据，也不知道公司如何使用我们的数据。你是否曾经谷歌过一些东西，然后奇怪地出现了一个相关的脸书广告？广告现在是如此有针对性，针对每个人量身定做。

因此，我们把这个问题作为项目的想法，并计划创建一个移动应用程序来显示不同的常见移动应用程序的数据隐私政策。我们在应用程序中添加了更多的功能，同时试图将核心理念开发成一个移动应用程序。

我们通过 Google sheets 进行了一项调查，以了解普通用户对数据隐私政策的了解。根据我们调查的[结果](https://docs.google.com/forms/d/1pB2GnFzgYKwaX_xrw-x-QsvRpDKbDNRqzqhCdnaHDew/edit?ts=5e556371#responses)，应用程序的普通用户发现应用程序的隐私政策通常很复杂，并且充满了他们不理解的冗长的法律术语。阅读和理解它们需要很多时间。结果鼓励我们走向应用的必要性。

我们的项目主要关注移动应用程序以及这些应用程序如何收集和使用数据。这个项目的目标是提高移动应用程序用户在使用这些应用程序时对其数据隐私的认识和教育。新闻、隐私提示、不同国家的隐私法规将让消费者了解正在发生的事情以及他们对自己数据的权利。仪表板显示了一个类别内的移动应用程序的比较，以便消费者可以衡量特定类别内应用程序之间的相对侵入性。“筛选数据隐私应用程序”是一个移动应用程序，它指示流行的移动应用程序正在收集多少隐私数据，包括隐私官和用户之间的通信以及其他功能。我们还为管理员开发了一个 web 应用程序，它将显示管理仪表板，并允许他们在隐私策略更新后对其进行编辑。该应用程序是一个重要的开端，旨在让个人能够通过了解他们的数字存在来采取行动保护他们的数据隐私。

# 使用的技术

由于我们为 Android 和 IOS 创建了一个移动应用程序，我们被迫选择跨平台技术来开发应用程序。反应和颤动是我们考虑的首要问题。基于队友的预先了解，我们选择了 Flutter 作为我们移动应用的开发技术。我们更喜欢 NodeJs 作为我们的后端开发语言。由于我们的应用程序不需要任何实时进程，我们被说服使用 MariaDB 作为数据库工具。我们使用 NodeJS 和 eJS 进行网站开发。我们使用 Adobe XD 进行前期界面设计工作。我们使用吉拉作为项目管理工具来管理我们的任务和计划。

# 履行

![](img/affc0d7a6df9464376a170d3c1a4c9bf.png)

Photo by [Glenn Carstens-Peters](https://unsplash.com/@glenncarstenspeters?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

我们将 flutter 的[干净架构](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)用于移动应用，将 [MVC 架构](https://www.guru99.com/mvc-tutorial.html#:~:text=The%20Model%2DView%2DController%20(,Model%2C%20View%2C%20and%20Controller.&text=MVC%20separates%20the%20business%20logic,graphical%20user%20interfaces%20(GUIs).)用于管理员的 web 应用。

作为实施的第一步，设计了 UX 样机。你可以在这里找到 UX 模型。这个模型用于收集用户反馈，并在全球范围内随机进行可用性测试。根据他们的反馈，我们根据用户关注的问题修改了界面设计。这个原型制作步骤帮助我们在使用 Flutter 实现设计决策之前完成它们。下一步，我们使用 MariaDB 实现了数据库。在前端(在移动应用程序和管理仪表板中)和后端检查数据验证，以保持数据库的一致性。

然后，移动应用程序、管理仪表板和后端的开发同时开始。在编码达到稳定状态后，首先构建系统并诊断错误。之后，在模拟器(测试移动应用程序)和 web 浏览器(测试管理仪表板)上对系统进行了测试。代码分析通常使用同行评审来检测缺陷、错误，并保持代码的质量。

最后，后端和数据库被上传到外部服务器。在第一阶段，我们上传到 Heroku 服务器，因为有一个免费版本，但后来我们计划迁移到数字海洋，在那里我们可以做更多的 API 调用和执行。你可以在这里找到移动应用开发代码[，在这里](https://github.com/sthenusan/Sieve-1)找到 web 应用开发代码[。](https://github.com/sthenusan/Sieve_Backend)

# 移动应用程序的界面

![](img/78786e0c059a6599005bedd6e84db1dd.png)

Photo by [Charles Deluvio](https://unsplash.com/@charlesdeluvio?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

*   主页:这个页面将在用户打开应用程序后出现。在这里，用户获得登录或注册选项。用户也可以通过谷歌和脸书注册。
*   登录页面:这里用户可以使用电子邮件和密码登录。用户也可以用他们的谷歌或脸书账户登录。也可以选择注册。
*   注册页面:在这里，用户可以使用电子邮件和密码注册系统。这里还有一个登录选项。
*   类别页面:用户可以查看应用程序数据隐私政策的简化版本。用户可以向下滚动以联系隐私官，讨论特定应用程序的隐私政策。还有一个刷新页面的选项。
*   隐私法页面:用户可以在这里查看该国关于数据隐私的简化法律。用户可以点击查看详细视图。
*   隐私提示页面:用户可以在这里查看为用户提供的关于数据隐私问题的简化提示。用户可以点击查看详细视图。
*   仪表板页面:这个页面上有应用程序，它们是分类的。不同颜色的火焰图标将在那里显示。火焰的数量和颜色取决于这些应用程序收集的数据类型。
*   Newsfeed 页面:世界上所有关于数据隐私的有趣新闻都在这里显示。用户可以通过点击新闻查看详细视图。
*   建议页面:该页面用于由应用程序的用户向开发者发送关于应用程序的建议。

[](https://www.datadriveninvestor.com/2020/09/18/turn-data-privacy-to-your-advantage-and-rebuild-consumers-trust-the-next-investment-frontier/) [## 将数据隐私转化为你的优势，重建消费者的信任:下一个投资前沿

### 抖音的使用在疫情期间激增，全球大约有 8 亿用户使用该平台…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/09/18/turn-data-privacy-to-your-advantage-and-rebuild-consumers-trust-the-next-investment-frontier/) 

# web 应用程序的接口

![](img/1c3fdca397e4e12db2898bcadcf2f933.png)

Photo by [Campaign Creators](https://unsplash.com/@campaign_creators?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

*   登录页面:这里管理员可以使用电子邮件和密码登录。这里也有一个注册的选项。
*   注册页面:这里管理员可以使用电子邮件和密码注册系统。有一个登录到管理仪表板的选项。
*   添加新的应用程序:这里管理员可以添加一个新的应用程序的细节。管理员必须在表格中填写新申请的所有细节。
*   应用程序的表格视图页面:管理员添加应用程序后，此页面将被定向。管理员可以在此以表格形式查看所有应用程序的详细信息。这里有一个选项可以编辑某个应用程序的详细信息。
*   应用程序的详细视图页面:如果管理员在表格视图页面中单击一个应用程序，将显示此页面。在这里，管理员可以查看所选应用程序的所有详细信息。
*   类别添加页面:管理员可以在这里为应用程序添加类别。
*   新闻添加页面:管理员可以通过这个页面添加关于数据隐私的新闻。

移动应用程序和 web 应用程序的所有接口 PNG 文件都可以在[这里](https://drive.google.com/drive/folders/1YiwybhuWS7ZyArMMq42kyAiOFqobuywk?usp=sharing)获得。

# 未来的工作

在未来的升级中，我们打算将隐私得分计算改为加权系统，其中每个收集的数据类型都将根据该数据类型对特定应用程序的重要性进行加权。例如，出租车应用程序收集的 GPS 位置的权重较低，但同一应用程序收集的可用电池数据的权重较高，因为这些数据对应用程序的正常运行并不重要。此外，我们计划将部署的服务器迁移到 DigitalOcean，在那里可以进行更多的 API 调用和执行。在系统的当前版本中，数据隐私的简化是手动完成的，但在未来版本中，我们计划使用自然语言处理(NLP)提取和分类来自动化这一过程。

![](img/1288a7f71c637e57462510e69f18736f.png)

Photo by [Markus Spiske](https://unsplash.com/@markusspiske?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 结论

本文描述了一个基于 Android 和 iOS 的在线移动应用程序的设计和实现，该应用程序声明了移动应用程序的数据隐私策略。这个应用程序解决了移动应用程序无法管理数据隐私策略的问题。Sieve 数据隐私应用程序为用户提供了许多功能。这些功能包括检查不同应用程序的数据隐私政策、阅读世界各地关于数据隐私的新闻、查看不同国家/地区的数据[隐私法律](https://www.privacypolicies.com/blog/privacy-law-by-country/)、以隐私方式建议以安全方式管理用户数据的技巧，以及以隐私方式与官员讨论不同应用程序和用户的数据隐私政策。对于管理员来说，有一个独特的单独的 web 应用程序。这个 web 应用程序主要用于系统管理员向数据库添加数据。由管理员管理的移动应用和管理网站都是在考虑用户体验、可扩展性、可用性、屏幕兼容性、设备兼容性和信息准确性的情况下开发的。

# 我们是谁？

“筛选数据隐私移动应用”是由来自[莫拉图瓦](https://uom.lk/)大学计算机科学与工程系的四名成员完成的一个团队项目。我们该项目的导师是[加提卡·拉特纳亚卡](https://medium.com/u/9fdaa0f25732?source=post_page-----1e2020899d0--------------------------------)和[韦杰](https://medium.com/u/fc157833a431?source=post_page-----1e2020899d0--------------------------------)。其他团队成员有 [Achintha Isuru](https://medium.com/u/422210d4d36d?source=post_page-----1e2020899d0--------------------------------) 、 [Thuvarahan Sivaneswaran](https://www.linkedin.com/in/thuvarahan/) 和 [Tharmeekan Sivarasan](https://www.linkedin.com/in/tharmeekansivarasan/) 。

我相信你理解了今天讨论的项目。如果您有任何问题或任何澄清，不要犹豫，通过回复部分与我联系。感谢您花费宝贵的时间阅读本文。

干杯…

# 参考

[](https://www.lifelock.com/learn-identity-theft-resources-what-is-data-privacy-and-why-is-it-important.html) [## 什么是数据隐私，为什么它很重要？

### 数据隐私一直很重要。这就是为什么人们在文件柜上加锁，并在…

www.lifelock.com](https://www.lifelock.com/learn-identity-theft-resources-what-is-data-privacy-and-why-is-it-important.html) [](https://privacy.google.com/?hl=en#) [## 谷歌安全中心-保持在线安全

### 为每个人制造技术意味着保护每个使用它的人。探索 Google 如何帮助您保持安全…

privacy.google.com](https://privacy.google.com/?hl=en#)  [## 隐私法案

### 1988 年隐私法(隐私法)的出台是为了促进和保护个人隐私，并规范如何…

www.oaic.gov.au](https://www.oaic.gov.au/privacy/the-privacy-act/) ![](img/c459fcb70ca72f5562caf9f19d1893ac.png)

Photo by [Courtney Hedger](https://unsplash.com/@cmhedger?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

**进入专家视角—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)