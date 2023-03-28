# 针对新冠肺炎的人工智能和数据科学解决方案

> 原文：<https://medium.datadriveninvestor.com/ai-and-data-science-solutions-against-covid-19-70b1cee56a24?source=collection_archive---------2----------------------->

## 在正确的时间产生正确的影响

## 当今疫情和未来公共安全的数据集和 R&D 方向

![](img/21049ae16b0e7ff38ed7c548820ff46e.png)

[https://www.cdc.gov/coronavirus/2019-ncov/index.html](https://www.cdc.gov/coronavirus/2019-ncov/index.html)

在过去的几个月里，新冠肺炎病毒爆发是网上和空荡荡的街道上讨论最多的话题。我们对它有不同的看法，从阴谋论到与普通流感的比较，但今天我们面对的事实是，新冠肺炎是疫情，我们需要以某种方式保护它，阻止它的传播，并最终战胜它。

作为一个在人工智能领域工作的人，在这篇博客中，我想分享一些我和我的同事可以帮助世界各地公共和私营部门的方向。我希望企业家和政府成员不仅能看到临时致富计划或控制公民的机会，还能看到改善公共健康和安全的**战略路线图的重要部分。**

# 公共卫生监督

Neurons Lab’s team research on deep learning for detection of symptoms in the visual feed

冠状病毒的主要危险是它的传播速度。这就是为什么政府采取了全国隔离的措施，因为他们不能有效地控制局部爆发。在对我们周围的闭路电视摄像机进行分析时，检测病人的最直接的步骤之一是找到表现出严重疾病症状的人，并隔离他们，他们与谁接触，并对相应的表面进行消毒。在神经元实验室，我们开发了一个演示解决方案，你可以在上面的视频中看到。开始自己研究的数据集在[这里](https://web.bii.a-star.edu.sg/~chengli/FluRecognition.htm)有。

# 远程生物信号测量

一些症状，如体温或脉搏，非常重要，可以忽略它们，只依赖于可能令人困惑的视觉外观。但是当然，我们不能让任何人停下来测量他们的脉搏、血压或体温。也许我们可以远程遥控？事实上，在计算机视觉方面有一些发展，可以根据面部皮肤分析来估计脉搏和血压:

[](https://towardsdatascience.com/ai-discovers-the-heart-beat-in-your-face-e129320a8bab) [## 人工智能发现你脸上的心跳

### 对从视频中读取生命体征的技术进行中等深度的探究

towardsdatascience.com](https://towardsdatascience.com/ai-discovers-the-heart-beat-in-your-face-e129320a8bab) [](https://www.engadget.com/2019/08/07/blood-pressure-selfie-video-smartphone-research/) [## 研究人员发现一种用自拍视频测量血压的方法

### 根据加拿大和中国研究人员的一项研究，自拍视频可能是你了解血压的唯一方法…

www.engadget.com](https://www.engadget.com/2019/08/07/blood-pressure-selfie-video-smartphone-research/) 

关于体温，也有一些发展，但在这种情况下，为了实际应用，我们希望研究热成像的方向，而不是常规相机。至少现在是这样。

 [## 基于图像处理的热视频序列体温估计

### 体温是人体调节系统中最重要的生命体征，如果体温升高到一定水平，就可能导致…

ieeexplore.ieee.org](https://ieeexplore.ieee.org/document/8282585) 

# 物联网和可穿戴设备

当然，从几乎每个人都已经拥有的可穿戴设备(如健身追踪器和智能手表)上收集脉搏等测量数据会更加舒适和方便。但这和脉搏有关系吗？它能告诉我们身体和情绪状态，也许还有心律不齐，但是流感呢？一些研究表明，心率变异性分析及其与正常状态的偏差可以显示流感的早期模式，在我们的情况下，冠状病毒。

[](https://www.trainingpeaks.com/blog/how-to-use-hrv-to-predict-illness/) [## 如何使用 HRV 预测疾病

### 没有人喜欢生病后不得不暂停训练；尤其是在密集训练区或…

www.trainingpeaks.com](https://www.trainingpeaks.com/blog/how-to-use-hrv-to-predict-illness/) 

# 聊天机器人和通信

除了在公共场合“扫描”人们，我们可能要依靠他们的意识和自我评估。如果你能每天测量你的体温和脉搏，并不时地记录你的咳嗽，你也可以把它写进你的日记里。然后，要么是远程医生，要么是一种算法可以建议你呆在家里，采取一些其他预防措施，或者如果症状太严重，请医生来看你。你可以在这里找到这样一个解决方案:

[](https://www.statnews.com/2020/02/05/chatbots-screening-for-new-coronavirus-are-turning-up-flu/) [## 聊天机器人筛查新型冠状病毒，并引发流感

### 旧金山——随着新型冠状病毒的传播，拥有医疗聊天机器人的医疗科技初创公司正在争相更新…

www.statnews.com](https://www.statnews.com/2020/02/05/chatbots-screening-for-new-coronavirus-are-turning-up-flu/) 

# 社交媒体和开放数据

也许你不喜欢写健康日记或在网上分享东西，但我们中有很多人会在 Instagram 或 Twitter 上与完全陌生的人分享。这些数据有助于更广泛地分析这种疾病消失了多远。有了关于用户的信息，我们还可以分析社交网络图，并尝试估计哪些社交群体有被传染的风险。关于数据，你们都知道从哪里得到它，以及什么是公共 API:)

[](https://wired.me/business/how-ai-tracking-coronavirus-outbreak/) [## 人工智能是如何追踪冠状病毒爆发的

### 随着冠状病毒在中国变得越来越致命，人工智能研究人员正在应用机器学习…

wired.me](https://wired.me/business/how-ai-tracking-coronavirus-outbreak/) 

加拿大初创公司 BlueDot 分析的不仅仅是社交媒体数据:例如，每年超过 40 亿乘客乘坐商业航班在全球范围内流动；人类、动物和昆虫种群数据；来自卫星的气候数据；以及来自记者和医护人员的当地信息，每天有超过 10 万篇跨越 65 种语言的在线文章涌入。

[](https://diginomica.com/how-canadian-ai-start-bluedot-spotted-coronavirus-anyone-else-had-clue) [## 加拿大人工智能初创公司蓝点如何在任何人都没有线索之前发现冠状病毒

### 2019 年 12 月 30 日，总部位于多伦多的初创公司 BlueDot 使用围绕人工智能构建的平台…

diginomica.com](https://diginomica.com/how-canadian-ai-start-bluedot-spotted-coronavirus-anyone-else-had-clue) 

# 数学建模

![](img/72d41cf0746e4efbc5584ffde83d7dd2.png)

The logistic curve describing the infectious disease evolution over time

显然，在冠状病毒之前，我们已经遇到了许多其他感染疾病，并研究了它们的生命周期规律。我们已经创建了数学模型，可以描述疾病在人群中的演变，我们可以一次又一次地重复使用它们，来解释新的爆发，甚至预测它们处于哪个阶段(又名“一切有多糟糕”)。你自己分析世界各地冠状病毒病例的良好起点在这里，同时拟合逻辑曲线，以了解意大利目前的确切情况(同时提供获取最新数据的教程):

[](https://towardsdatascience.com/covid-19-infection-in-italy-mathematical-models-and-predictions-7784b4d7dd8d) [## 意大利的新冠肺炎感染。数学模型和预测

### logistic 和指数模型在意大利新冠肺炎病毒感染中的比较。

towardsdatascience.com](https://towardsdatascience.com/covid-19-infection-in-italy-mathematical-models-and-predictions-7784b4d7dd8d) 

此外，不仅要对病毒进化本身进行建模，还要对所使用的对策进行建模，这一点非常重要。数学模型可以帮助我们理解如何在疫情爆发的早期阶段更有针对性和更优化地分配预防资源，而不是盲目地关闭整个边界。查看下面的论文中的数学优化应用；关于图像:无测量值(A)与其他纯数学测量值的比较。

![](img/12d8437c03209d8417fdd299f43373c8.png)

[https://www.nature.com/articles/s41598-019-38665-w.epdf](https://www.nature.com/articles/s41598-019-38665-w.epdf)

# 自动化诊断

新冠肺炎向我们揭示了当今医疗保健的另一个问题:当患者数量快速增长时，医疗保健无法扩展(实际上，疲惫的医生只会工作得更糟)，而且总体而言，假阴性诊断的数量相当高。机器学习诊断不会厌倦，只会随着计算能力的增加而自然扩展。我们已经看到了基于深度学习的肺部图像分析在当前的疫情中也运行良好:

[](https://medium.com/syncedreview/ai-enables-doctors-to-diagnose-covid-19-infection-in-seconds-64db82757f91) [## 人工智能使医生能够在几秒钟内诊断新冠肺炎病毒感染

### 易图“冠状病毒胸部 CT 智能评估系统”可以将疑似病例的诊断时间压缩到 2-3 秒。

medium.com](https://medium.com/syncedreview/ai-enables-doctors-to-diagnose-covid-19-infection-in-seconds-64db82757f91) 

# 药物开发研究

最后但同样重要的是，除了检测和预防疾病的传播，我们需要考虑大规模生产疫苗。创造它的一个重要步骤是了解我们对抗的病毒的结构和性质。DeepMind 凭借其在蛋白质折叠分析方面的经验，也在预测病毒的蛋白质结构方面迈出了一步，并将其开源。

[](https://deepmind.com/research/open-source/computational-predictions-of-protein-structures-associated-with-COVID-19) [## 与新冠肺炎相关的蛋白质结构的计算预测

### 科学界已经为应对最近的新冠肺炎疫情而振奋起来，建立在几十年的基本…

deepmind.com](https://deepmind.com/research/open-source/computational-predictions-of-protein-structures-associated-with-COVID-19) 

关于 COVID 蛋白质结构和其他流感的数据集供您自己分析，您可以在这里找到:

[](https://www.gisaid.org/) [## GISAID -共享所有流感数据的全球倡议

### 世界上越来越多的实验室正在通过 GISAID 计划发布人类基因组序列。

www.gisaid.org](https://www.gisaid.org/) 

最后但同样重要的是，AI 可以帮助分析已经发表的关于病毒的学术著作，如 SARS 和 current COVID。你可以在 Kaggle 上找到相关的数据集:

[](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge) [## 新冠肺炎开放研究数据集挑战(CORD-19)

### AI2 大学、CZI 大学、MSR 大学、乔治城大学、美国国家卫生研究院和白宫的人工智能挑战

www.kaggle.com](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge) 

# 结论

当然，大多数描述的方法都是研究性的，需要付出巨大的努力才能对大多数人真正有用。然而，我发现它们中的大多数确实是 360 度全方位防御的整个生态系统的重要组成部分:

*   **利用视频监控、远程生物信号测量和可穿戴数据分析的本地疫情检测**；
*   **借助基于人工智能的样本诊断，大规模高效处理**；
*   **利用社交媒体分析和聊天机器人进行地区级分析**；
*   **全球发展预测**根据定期更新的本地和区域数据进行数学建模；
*   与此同时，基于人工智能的模拟和分子生成推动了**药物开发**。

在[神经元实验室](http://neurons-lab.com/)，我们正在上述几个方向投入资源。你可以看到一个用于症状检测的视频监控分析的演示，我们也在研究感染传播的数学模型。我们正在邀请有兴趣的合作者，请告诉我们！

**附言**
你也可以在[脸书](https://www.facebook.com/rachnogstyle.blog)博客或者 [Linkedin](https://www.linkedin.com/in/alexandr-honchar-4423b962/) 上和我联系，在那里我会定期发布一些对媒体来说太短的人工智能文章或者新闻，还有 [Instagram](http://instagram.com/rachnogstyle) 上一些更私人的内容:)