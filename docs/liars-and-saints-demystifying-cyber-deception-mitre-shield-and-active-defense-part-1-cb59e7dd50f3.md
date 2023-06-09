# 说谎者和圣徒:揭开网络欺骗、MITRE Shield 和积极防御的神秘面纱(第一部分)

> 原文：<https://medium.datadriveninvestor.com/liars-and-saints-demystifying-cyber-deception-mitre-shield-and-active-defense-part-1-cb59e7dd50f3?source=collection_archive---------6----------------------->

![](img/a6129a0e27ab915436e8356990f8e0f3.png)

【MITRE Shield 如何将网络欺骗技术转化为一项商业要务，以阻止对手进入竞争网络。

# 介绍

就在你开始完全理解米特 ATT&CK 框架的时候，米特出版了一个全新的框架，让你明白它叫做米特盾。

你是否在最近的出版物中看到过 MITRE Shield，或者在供应商的推销中听说过它，但又不好意思问它到底是什么？不明白欺骗技术和它的关系是什么？你并不孤单。由于 Shield 还处于起步阶段，关于这个新的框架和它所建立的*主动防御*的概念，还有很多需要写和理解的地方。

这是我发表的关于 MITRE Shield、主动防御以及网络欺骗技术如何融入这一叙事的系列文章的第 1 部分。

但是首先..

# 谁是米特

MITRE 是一个非营利组织，成立于 1958 年，其使命是通过研究和开发支持美国政府机构。MITRE 是已故 Robert Everrett 的创意，如今已发展到管理位于马萨诸塞州贝德福德和弗吉尼亚州麦克林的联邦资助研发中心(FRDCs)。

简而言之，FRDCs 是公私合作伙伴关系，围绕国家安全、技术和其他挑战的具体问题为美国政府进行研究，这些问题导致了雷达、飞机、计算以及最著名的核武器发展的演变。

2013 年，MITRE 作为网络安全领域的“家喻户晓的名字”而广受欢迎，当时它宣布了新的 MITRE ATT 和 CK 框架，该框架如今已成为网络安全供应商调整其产品的试金石，并让防御者对其网络安全控制措施进行差距分析。如今，ATT&CK 已经成为两家供应商如何定位其网络安全产品的重心，也成为防御者有效防御敌对战术、技术和程序(TTP)的重心。

# 什么是斜盾

MITRE Shield 是一个新的战术、技术和程序矩阵，专为防御方设计，用于指导他们的网络如何实现*主动防御*安全态势。Shield 是 MITRE 十年来对针对他们自己的网络采取的敌对策略进行分析的产物，从基本的网络防御能力到网络欺骗和对手交战。

Shield 背后的前提是用一种新的积极防御概念武装防御者，通过采用有限的进攻行动和反击来阻止他们的网络和资产落入敌手。虽然主动防御的抽象概念在网络安全领域是一个新概念，但在军事行动中并不新鲜。上个世纪，美国国防部和中国军方以及其他国家一直在使用积极防御，并在 M. Taylor Fravel 关于中国军方自 1949 年以来如何将其用作防御战术的书中首次得到推广。

总之，Shield 是防守者战术、技术和程序的矩阵，并且已经与米特 ATT 和 CK 结合，形成了对抗战术和技术与防守者在其映射的机会空间中应用的战术和技术之间的更完整的画面。

[](https://www.datadriveninvestor.com/2020/09/04/the-lowest-cost-most-effective-path-to-better-cybersecurity/) [## 提高网络安全的最低成本和最有效途径|数据驱动型投资者

### 在组织在 2020 年面临的诸多挑战中，网络安全(或缺乏网络安全)已成为新闻报道的焦点…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/09/04/the-lowest-cost-most-effective-path-to-better-cybersecurity/) 

# 盾牌战术

目前盾中定义了 8 种战术。每一个都是服务于战术最终目标的相关技术的有组织的容器。重要的是要注意 Shield 框架中定义的技术的重复，因为 Shield 是技术到战术的多对多映射。一种技术可以与多种战术相关联，正如许多技术可以与一种战术相关联一样，反之亦然。

![](img/85012a9a35fb0885591a65a6d24799b0.png)

1.  渠道:这种战术是一个技术容器，它使用诱饵或欺骗技术创造的其他“面包屑”,引导对手沿着网络中的特定路径横向远离生产系统或网段。欺骗技术使用的面包屑可以被视为诱饵，可以充当合成文件、凭证甚至系统，将对手的注意力从环境中真实的生产系统上转移开。
2.  收集:这种战术定义了用于收集对手信息的技术，特别是学习他们的战术、技术和程序以及他们用来实现目标的工具。一个例子是分析他们用来实现目标的定制恶意软件或以人为中心的间谍软件。
3.  遏制:遏制是利用技术将对手限制在防御者控制的有限空间内，限制防御者创造的合成环境甚至是与生产系统隔离的特定飞地的旋转潜力。
4.  检测:利用网络和端点检测和响应系统，或任何其他安全控制来降低在网络中建立了“滩头阵地”的对手的平均检测时间(MTTD)。
5.  破坏:用来使对手难以完成目标的技术。这通常是通过结合欺骗技术的不同安全控制层来实现的，欺骗技术使真实环境与合成环境难以区分。
6.  促进:与破坏的技术相反，促进用于使对手能够成功地完成他们的部分或全部目标，使用未打补丁的操作系统、应用程序，或在受控环境中完全消除安全控制，例如可以控制和监视活动的诱饵系统。
7.  合法化:这种策略用于增加由欺骗技术创建的合成环境的真实性，例如交互式用户登录的合成活动日志、运行的进程、kerberos 金券、SAM hive 中的凭证等。这些技术试图赋予合成环境以合法性，以便在意识到目标是诱饵之前，增加对手对目标使用的时间和注意力。

# 什么是欺骗技术

欺骗技术是安全控制的相对较新的产品空间，能够创建高保真检测系统，使用面包屑来引诱敌人远离真实的生产系统，以便通过识别他们在环境中的横向移动来降低 MTTD。

直到最近，首席信息安全官(CISOs)还很难有效地理解欺骗技术在他们的预算中的位置——在他们的安全控制框架中的位置——是否有必要拥有或最好拥有。Shield 已经明确表示，欺骗技术现在是一项业务需求，因为当今的现实是高级勒索软件或对手将在“何时”而不是“如果”建立滩头到 2020 年，预防不再是一个现实的目标，这使得 CISOs 们不得不尝试在发生违规时减少检测对手所需的时间。

欺骗技术现在正被用来提高探测和威慑能力，识别对手使用的技术，即旋转/横向移动。

Shield 中定义的许多策略都是使用欺骗技术实现的，包括诱饵账户、诱饵内容、诱饵凭证、诱饵网络、诱饵角色、诱饵流程、诱饵系统和诱饵多样性，这些我将在下一部分中介绍。

# 摘要

在《说谎者与圣徒》系列的第一部分中，我解释了 MITRE Shield，它是什么，它是如何工作的，它与 MITRE ATT&CK 的特殊区别，以及防御者如何在他们的组织中使用它来进行积极防御。在本系列的第 2 部分中，我将解释 MITRE 如何将 ATT 和 CK 与 Shield 结合起来，为防御者创建一个映射，将他们可以使用的特定主动防御技术与 ATT 和 CK 框架中定义的特定 TTP 联系起来，以及欺骗技术如何在主动防御模型中发挥不可或缺的作用。

在《说谎者与圣徒》系列的最后一部分，我将讨论虚幻网络，以及它们的欺骗技术如何彻底改变以人为中心的间谍软件的威胁检测以及对手使用溶解剂的横向移动。

# 来源

T.(未注明)。主动防御矩阵。检索于 2020 年 11 月 12 日，来自[https://shield.mitre.org/matrix/](https://shield.mitre.org/matrix/)

T.(未注明)。映射到初始访问。检索于 2020 年 11 月 12 日，发自 https://shield.mitre.org/attack_mapping/TA0001/

c .福勒、m .戈芬、b .希尔、r .拉莫宁和 Sovern(未标明)。*斜盾简介*(科技。№20–00398–1.).米特公司。

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)