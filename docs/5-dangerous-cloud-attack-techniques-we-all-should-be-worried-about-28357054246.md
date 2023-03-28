# 我们都应该担心的 5 种危险的云攻击技术

> 原文：<https://medium.datadriveninvestor.com/5-dangerous-cloud-attack-techniques-we-all-should-be-worried-about-28357054246?source=collection_archive---------6----------------------->

## 最臭名昭著的云攻击技术

![](img/d8ebca169d79dba2819c0bfccebcfc1b.png)

Photo by [Kaitlyn Baker](https://unsplash.com/@kaitlynbaker?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

这里我将列出黑客和破解者用来获取信息的最危险的云攻击技术。

**凭证填充攻击或凭证暴露**

![](img/7d69c784360c442ce0dabb2727554d11.png)

Photo by [Austin Distel](https://unsplash.com/@austindistel?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

**凭证填充**这是一种基于云的网络攻击其中 API 凭证的暴露导致帐户劫持，很有可能攻击云中的杀伤链。这种特殊的攻击是网络罪犯最常用的攻击方式之一。凭证通常由帐户用户名和密码组成，可以作为访问密钥。

当攻击者获得这些凭证或访问密钥中的一个时，他们将从他们控制的一组或平台中使用它，并执行 API 关注的恶意操作或权限提升。密钥经常通过 GitHub、BitBucket、共享图像、快照暴露出来——“到处都是，”他继续说道。攻击者反编译谷歌 Play 商店应用程序，提取静态凭据，然后使用这些凭据。有人可以进入开发人员的笔记本电脑或实例，并在其命令历史或配置文件中寻找和访问允许他们进入云环境的密钥。

# 错误配置事故

![](img/96c7e5703e5fdb70f1c454b103095b53.png)

Photo by [Markus Spiske](https://unsplash.com/@markusspiske?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

**错误配置**在很大程度上，或者至少在某种程度上是 IT 阴影的重塑。任何人都可以得到一个亚马逊 S3 桶，并用它做任何他们想做的事情。与错误配置相关的攻击仍然会发生，因为组织经常无法保护他们在公共云中的信息。

在这些场景中，敏感数据被放入对象存储中，并受到不适当的保护。访问控制也可以设置为公开或匿名；存储桶策略或网络也可能过于宽松，或者普通公共 CDN 即将访问私有数据。攻击者扫描并发现一个打开的数据存储，然后提取他们需要的信息。

[](https://www.datadriveninvestor.com/2019/03/20/azbit-aims-to-connect-traditional-finance-and-cryptocurrency/) [## Azbit 旨在连接传统金融和加密货币|数据驱动的投资者

### Azbit 是下一个提供交易平台的加密项目，该平台提供保证金和算法交易。一样多…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/03/20/azbit-aims-to-connect-traditional-finance-and-cryptocurrency/) 

云提供商提供了减少这种情况的工具，但这对于组织来说仍然是一个难题。一些科学家建议持续评估并特别注意对象级权限:在您更改存储桶级权限后，并不总是更改对象级权限。

# 秘密采矿

![](img/6169d42330b9c7d260befb364cf9b99c.png)

Photo by [Clifford Photography](https://unsplash.com/@cliffordgatewood?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

当他们进入云时，许多入侵者仍然从事加密挖掘:这是大多数企业面临的低严重性、高可能性的攻击。

攻击者可以通过 RunInstance、虚拟机或容器获取凭据，运行超大的实例或虚拟机，运行并注入加密挖掘程序，连接网络，然后泄漏结果。或者，他们可能会破坏一个暴露的实例、虚拟机或容器，并在那里注入 crypto miner。

服务器仍然是最有效的加密挖掘平台，但拥有访问权限的攻击者正在采取措施隐藏他们的活动。许多人习惯于“抓取系统中的所有东西”，受害者会注意到这一点。现在，他们正在限制自己的活动，以避开企业的注意。

# 服务器端请求伪造

![](img/03f66f6b9026012a12af8d1f8b429d45.png)

Photo by [Florian Krumm](https://unsplash.com/@floriankrumm?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

**服务器端请求伪造(SSRF)** 可能是一种危险的攻击方法，也是云环境中一个日益严重的问题。由于元数据 API 的使用，SSRF 可能是一个威胁，它允许应用程序访问底层云基础架构中的配置、日志、凭据和其他信息。元数据 API 只能在本地访问；但是，一个 SSRF 漏洞使得它可以从 web 访问。如果被利用，它可以让攻击者横向移动并进行网络侦察。

攻击者首先确定一个可能存在 SSRF 漏洞的实例或容器，利用它通过元数据服务提取凭据，并在攻击者的环境中建立一个具有凭据的会话。从那里，攻击者可以执行 API 调用来提升权限或采取其他恶意操作。

SSRF 要想成功，必须做几件事:某些东西必须暴露在网络中，它必须包含 SSRF 漏洞，它必须拥有身份和访问管理(IAM)权限，允许它在其他地方出现。现在，它甚至必须在每个元数据服务中都有版本 1。

# 强力和访问即服务

![](img/4b5c1a09fe9f7949c066290e66567e07.png)

Photo by [Markus Spiske](https://unsplash.com/@markusspiske?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

暴力攻击是攻击者的首选，他们需要开始制作带有恶意页面链接的钓鱼电子邮件，这些恶意页面与云基础架构和帐户相关联。弹出窗口可能会提示受害者在 Office 365 和其他云应用程序的虚假登录页面中输入用户名和密码。

使用的来源:

【https://www.darkreading.com 号

查看我的其他故事:

[](https://medium.com/datadriveninvestor/coronavirus-leads-to-a-new-wave-of-phishing-and-malware-799060938f41) [## 冠状病毒导致新一波网络钓鱼和恶意软件

### 随着世界对全球健康问题因为新冠肺炎或更好地称为冠状病毒的传播，与…

medium.com](https://medium.com/datadriveninvestor/coronavirus-leads-to-a-new-wave-of-phishing-and-malware-799060938f41) [](https://medium.com/datadriveninvestor/cyber-threat-intelligence-b6ceb6d9e6f5) [## 网络威胁情报

### 什么是…？

medium.com](https://medium.com/datadriveninvestor/cyber-threat-intelligence-b6ceb6d9e6f5) [](https://medium.com/datadriveninvestor/r-a-t-remote-access-trojan-how-it-affects-to-major-enterprises-822ef3c15a35) [## 远程访问木马|它如何影响大型企业

### 即将到来的 2020 年新年是鼠年。在中国，他们带着喜悦和幸福庆祝农历新年，但是…

medium.com](https://medium.com/datadriveninvestor/r-a-t-remote-access-trojan-how-it-affects-to-major-enterprises-822ef3c15a35)