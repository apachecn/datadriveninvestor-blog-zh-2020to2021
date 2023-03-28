# 阿里巴巴 DAMO 研究院人工智能系统如何检测冠状病毒病例

> 原文：<https://medium.datadriveninvestor.com/how-alibaba-damo-academy-ai-system-detects-coronavirus-cases-741cc1b40f4a?source=collection_archive---------20----------------------->

![](img/7ebd5a3fa3c6cd5e0414c258a2acc1bb.png)

*观看网上技术交流讲座* [*用 DataV*](https://resource.alibabacloud.com/webinar/detail.html?spm=a2c41.14153165.0.0&id=1429&topic=anti-coronavirus) *构建实时员工健康解决方案，了解阿里云如何使用 DataV 通过可视化全球所有员工的健康状况来应对公共健康危机。*

![](img/8fe2bd9b4dbc62cb75ee853924714a44.png)

2 月初，阿里巴巴集团的研究和创新机构 [DAMO 研究院](https://damo.alibaba.com/?spm=a2c41.14153165.0.0)开发了一个[人工智能系统](https://www.alizila.com/alibaba-news-roundup-tech-takes-on-the-outbreak/?spm=a2c41.14153165.0.0)，可以在 20 秒内诊断出新冠肺炎，准确率高达 96%。

人工智能系统通过胸部的计算机断层扫描来识别这种新病毒。迄今为止，该算法已经用来自 5000 多个确诊冠状病毒病例的数据和 CT 扫描进行了训练，并利用深度学习来研究感染模式。

[](https://www.datadriveninvestor.com/2020/02/12/has-general-ai-exceeded-the-intellectual-capacity-of-humans/) [## AI 将军是否已经超过了人类的智力容量？数据驱动的投资者

### 不仅在游戏中，而且在劳动力市场上，机器都比人类聪明。在今天的许多领域，使用…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/12/has-general-ai-exceeded-the-intellectual-capacity-of-humans/) 

我们联系了 DAMO 的人工智能算法专家徐敏峰，就人工智能工具以及它如何在健康危机期间帮助医生进行了电话交谈。

# DAMO 的人工智能健康工具是如何工作的？

2 月 4 日，在病毒首次被发现的武汉被封锁近两周之后，DAMO 的团队开始使用同济医学院著名放射科医生施合水发布的诊断指南，训练其诊断冠状病毒的算法。由于该团队在过去三年中已经在普通呼吸系统疾病等领域开展了人工智能医学成像工作，我们花了不到五天的时间才为新冠肺炎制作出第一套计算结果。

我们的 AI 系统做两件事:一是跟踪确诊病例的治疗反应，二是为疑似病例提供诊断。

像武汉这样受影响严重的地区的医院可能会每两三天向我们发送同一例确诊病例的 CT 扫描，我们将使用我们的人工智能系统来检测改善的迹象，例如肺部白色肿块的减少。

疫情中心周边地区的医院正越来越频繁地利用该系统的第二项功能。他们将发送疑似病例的扫描结果，以确定他们被感染的几率。该系统将结果分为确诊的冠状病毒、普通流感或其他呼吸系统疾病。

# 为什么需要人工智能？

时间和精度。

CT 机通常要对每个病人进行 300 到 400 次胸部扫描，才能开始诊断新冠肺炎。即使是非常有经验的医生也需要 10-15 分钟来处理如此大量的信息，但训练有素的人工智能系统可以在 20-30 秒内完成扫描。其次，当我们处理突发的新病毒爆发时，训练每一位医生如何发现病毒是一项艰巨的任务，因此人工智能系统被用来作为医生的分析性第二意见。

# 创建这个人工智能健康系统的最大挑战是什么？

采用人工智能驱动的系统或产品的挑战是，为了获得实际采用，算法在测试阶段必须高度精确。如果该系统未能产生准确的冠状病毒诊断，我们将立即失去医生的信心。

在最初的启动阶段，我们的团队必须对医院的反馈做出快速反应。例如，我们不得不根据武汉第六医院的当地条件进行重大调整，这是我们最早合作的医院之一。因为这是一种新型冠状病毒，随着更多研究的出现，我们正在微调我们的算法，我们也在使用来自前线工作的医务人员的反馈。到目前为止，我们已经完善了 5，000 个案例的系统，并且还在增加。

# 这个系统最大的突破是什么？

从技术上来说，我们的不断改进已经导致诊断精度和速度的重大改进。在深度学习的帮助下，我们的系统还可以填补空白，并在没有足够的 CT 扫描可用时提供额外的诊断精度。在合作方面，我们的系统目前正在中国的 26 家医院使用，并帮助诊断了超过 30，000 例病例。这一突破是因为公共和私营部门的合作伙伴联合起来推动人工智能系统的实施。

# 这个 AI 诊断系统会如何继续进化？

我们将继续与浙江大学医学院第一附属医院、万里云、创元佳和谷珀科技等合作伙伴合作，将我们的人工智能系统带到云上。医疗从业者可以使用他们的智能手机或笔记本电脑直接上传 CT 扫描，在线获得即时结果。其他可能性包括缩短反馈周期，我们实施调查功能来收集来自医疗从业者的直接反馈，以帮助改进我们的算法。

在继续与全球爆发的疾病进行斗争的同时，阿里云将发挥自己的作用，并尽其所能帮助其他人与冠状病毒进行斗争。点击[*https://www . Alibaba cloud . com/campaign/supports-your-business-anytime*](https://www.alibabacloud.com/campaign/supports-your-business-anytime?spm=a2c41.14153165.0.0)，了解我们如何支持您的业务连续性

*原文发布于:*[*https://www . Ali zila . com/how-damo-academys-ai-system-detects-coronavirus-cases/*](https://www.alizila.com/how-damo-academys-ai-system-detects-coronavirus-cases/?spm=a2c41.14153165.0.0)

# 原始来源:

[](https://www.alibabacloud.com/blog/how-alibaba-damo-academy-ai-system-detects-coronavirus-cases_595979?spm=a2c41.14153165.0.0) [## 阿里巴巴 DAMO 研究院人工智能系统如何检测冠状病毒病例

### 阿里巴巴 Clouder 2020 年 3 月 12 日 739 观看网上研讨会，利用 DataV 构建实时员工健康解决方案，以…

www.alibabacloud.com](https://www.alibabacloud.com/blog/how-alibaba-damo-academy-ai-system-detects-coronavirus-cases_595979?spm=a2c41.14153165.0.0)