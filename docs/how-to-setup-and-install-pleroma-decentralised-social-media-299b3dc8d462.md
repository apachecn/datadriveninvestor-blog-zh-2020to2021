# 如何设置和安装 Pleroma(分散式社交媒体)

> 原文：<https://medium.datadriveninvestor.com/how-to-setup-and-install-pleroma-decentralised-social-media-299b3dc8d462?source=collection_archive---------6----------------------->

一个开源和分散的社交媒体平台，你可以自己主持

![](img/51bef93576d955beca24c04ce59451d8.png)

Photo by [Prateek Katyal](https://unsplash.com/@prateekkatyal?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

Video showing the steps to setting up the instance

特朗普被踢出 Twitter，帕勒被踢出 AWS，已经过去一周了。去平台化已经成为一个热门话题，这使得一些人质疑社交媒体的未来。对大多数人来说，这不是一个大问题，因为他们不会讨论有争议的话题，但就像生活中的其他方面一样，寻找不会让你更加依赖大公司的替代方案是件好事。社交媒体大部分问题的答案是你可以托管自己的联合/分散平台。你可以决定谁可以和你交流，你也不用担心审查。在之前的一篇文章中，我谈到了乳齿象，但是在这篇文章中，我将向你展示如何设置一个 Pleroma 实例。我相信 Pleroma 是一个更好的平台，无论是在性能方面还是在社区方面。

# 细节

Pleroma 和其他联合平台是不同于其他任何社交媒体网站。Pleroma 是一个开源软件项目，任何人都可以使用它来创建自己的定制实例，而不是访问一个运行在某个大型科技公司数据中心的网站。每个 Pleroma 实例可以相互通信，站点所有者决定在它们的实例上可以做什么和不可以做什么。

# 技术细节

通常运行这些应用程序时，你的服务器需要 Debian 或 Ubuntu。然而，如果你真的讨厌坚持称之为“gnu-linux”的人，Pleroma 甚至有 Gentoo、FreeBSD 或 Alpine 的指南。所以你的服务器不太可能运行不支持 Pleroma 的操作系统。

在你开始安装之前，你需要加固你的 SSH 并设置 fail2ban 以保证安全。我之前写过一篇关于[如何做到这一点的文章，可以在这里找到](https://biasedriot.co/fail2ban.html)。

接下来，您需要为您的域名设置 DNS 记录。如果你用 GoDaddy 或任何其他域名注册中心购买了你的域名，那么只需将你的记录指向你的服务器 IP 地址。

这里有一个由 Pleroma 提供的关于如何使用 OTP 版本设置一切的[文档。](https://docs-develop.pleroma.social/backend/installation/otp_en/)上面的视频显示了各个步骤，结合文档中的步骤，在您的服务器上安装它应该没有任何问题。我建议您按照视频运行命令，因为其中一些命令需要一些文档中没有提到的额外步骤。

Pleroma 在后台使用的服务是 Nginx、post gress for DB 和 certbot，以获得您的域的 SSL 证书。基本上就是这样，从各方面考虑，这是一个相当轻量级的应用程序，我已经能够在我的 VPS 上运行的所有电子邮件和云服务上运行一个实例。

与典型的社交媒体网站不同，你将能够有一个更紧密的体验，你将完全控制你的数据和谁使用你的实例。如果你卡住了，在上面的视频中有一些额外的解释。

保持快乐，保持隐私。

**我的网站:**【https://biasedriot.co 

**Youtube:**[https://www.youtube.com/channel/UCehh50T6qtDpt_kEUF33GJw/](https://www.youtube.com/channel/UCehh50T6qtDpt_kEUF33GJw/)

**Monero:**84 y4 fzitble r5 q 1c 1 fbrbhb 1 yq 5 agktedoixq 2 w 1 ysxjv 486 mibcz 3c zgt 15 bquexdpdlonyf 93 nxy 3 bck 6g 8 mrdmnkoars

**比特币:**1 DMN 9 jetwahdlk 1 hhwkuvnedda abcwnajm