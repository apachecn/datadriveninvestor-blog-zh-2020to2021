# [ML UTD 33]最新的机器学习—数据生活

> 原文：<https://medium.datadriveninvestor.com/ml-utd-33-machine-learning-up-to-date-life-with-data-12af85b4634f?source=collection_archive---------28----------------------->

第 33 期每周简讯来自[生活有数据](https://lifewithdata.org/)

![](img/ba92f31be4bdf206d7d02c7df25433fb.png)

Diagram of Microsoft QLib’s flow [[source](https://github.com/microsoft/qlib)]

这是来自 [**LifeWithData**](https://lifewithdata.org) 博客的 ML UTD #33！在当今软件工程和机器学习的繁忙前线，我们帮助您将信号从噪声中分离出来。

[**LifeWithData**](https://lifewithdata.org) 致力于提供精心策划的机器学习&软件工程更新，为读者指出没有多余细节的关键发展。这使得整个行业能够进行频繁、简洁的更新，而不会出现信息过载。

# 应用程序

*   给软件工程师更多的工具:工厂的重组
*   用于定量研究的 Microsoft Qlib
*   MediaPipe 整体—在设备上同时进行面部、手部和姿势预测

# 理论

*   人工智能/人工智能软件的软件工程:系统的文献综述
*   可控神经文本生成
*   解释转换器语言模型的接口

# 给软件工程师更多的工具:工厂的重组

![](img/57cd7eda1d3e12f728c545c04b47d659.png)

[Source](https://erikbern.com/assets/power-loom.jpeg)

> 开发人员中流行的态度是抱怨我们的工具和东西有多坏。也许我是一个乐观的人，因为我的观点完全相反！1999 年，我的第一份工作是软件工程师，在过去的二十年里，我目睹了软件工程的变化，使我们的生产力提高了几个数量级。只是一些我曾经做过或接近的事情的例子:
> — Spotify 用 C++建立了一个完整的 P2P 架构，以便向听众分发流媒体音乐，这在今天是一个小问题(将数据放在 CDN 上)。
> — Spotify 用 C++构建了一个完整的 P2P 架构，以便向听众分发流媒体音乐，这在今天是一个小问题(将数据放在 CDN 上)。
> —我曾经经营过一家网店，花了一周时间实现信用卡支付。今天，使用 Stripe 只需 15 分钟。
> 
> *更不用说开发人员*流程*:
> ——单元测试在行业中确实很少见——我第一次遇到它是在 2006 年谷歌工作的时候。
> —当 git 刚出现的时候，git-flow 是流行的工作流，和我一起工作的许多开发人员花费了过多的时间(比如 20-30%)仅仅是为了*重新设定*。CI 系统很脆弱，CD 基本上不存在，部署是可怕的手工事务。*
> 
> 这些只是例子，我可以说一整天。很像经典的 [*没有银弹*](https://en.wikipedia.org/wiki/No_Silver_Bullet) *关于软件生产力的论文，这些东西本身都没有一个戏剧性的改进。但是生产率的提高是累加的，而且是以对数的形式累加的，*这意味着当你的时间尺度是几十年时，我们看到数量级的提高并不是没有道理的。**
> 
> [*…继续阅读*](https://erikbern.com/2020/12/16/giving-more-tools-to-software-engineers-the-reorganization-of-the-factory.html)

《丛林奇兵》

*   [条](https://erikbern.com/2020/12/16/giving-more-tools-to-software-engineers-the-reorganization-of-the-factory.html)
*   信用: [@fulhack](https://twitter.com/fulhack)

# Qlib:面向人工智能的量化投资平台

![](img/714976f38c168e6e2e635e8f60926ffc.png)

Diagram of Microsoft QLib’s flow [[source](https://github.com/microsoft/qlib)]

> *Qlib 是一个面向人工智能的量化投资平台，旨在实现潜力，赋能研究，创造人工智能技术在量化投资中的价值。*
> 
> *包含数据处理、模型训练、回测的完整 ML 流水线；并涵盖了量化投资的整个链条:阿尔法寻求，风险建模，投资组合优化，订单执行。*
> 
> 使用 Qlib，用户可以轻松尝试各种想法，以创建更好的量化投资策略。
> 
> *更多详情请参考我们的论文*[*《Qlib:一个面向 AI 的量化投资平台》*](https://arxiv.org/abs/2009.11189) *。*
> 
> [*…继续读*](https://github.com/microsoft/qlib)

《丛林奇兵》

*   [Github 回购:微软/qlib](https://github.com/microsoft/qlib)
*   [QLib 读取文档](https://qlib.readthedocs.io/en/latest/)
*   [Qlib 纸](https://arxiv.org/abs/2009.11189)
*   鸣谢: [@MSFTResearch](https://twitter.com/MSFTResearch)

# MediaPipe 整体—在设备上同时进行面部、手部和姿势预测

![](img/06983c1f96a5020a67d17306f663acaf.png)

MediaPipe overview [[source](https://ai.googleblog.com/2020/12/mediapipe-holistic-simultaneous-face.html)]

> *在移动设备上实时、同步感知人体姿势、面部标志和手部跟踪，可以实现各种有影响力的应用，如健身和运动分析、手势控制和手语识别、增强现实效果等。*[*media pipe*](https://mediapipe.dev/)*，一个专为利用加速推理的复杂感知管道(如 GPU 或 CPU)而设计的开源框架，已经为这些任务提供了快速、准确而又独立的解决方案。将它们实时组合成语义一致的端到端解决方案是一个非常困难的问题，需要同时推断多个相互依赖的神经网络。*
> 
> *今天，我们很高兴地宣布* [*MediaPipe 整体*](https://solutions.mediapipe.dev/holistic) *，这是一个针对这一挑战的解决方案，它提供了一种新颖的最先进的人体姿态拓扑，开启了新的用例。MediaPipe 整体由一个新的管道组成，该管道具有优化的* [*姿态*](https://ai.googleblog.com/2020/08/on-device-real-time-body-pose-tracking.html)*[*面*](https://ai.googleblog.com/2019/03/real-time-ar-self-expression-with.html) *和* [*手*](https://ai.googleblog.com/2019/08/on-device-real-time-hand-tracking-with.html) *组件，每个组件都实时运行，推理后端之间的内存传输最小，并增加了对三个组件可互换性的支持，具体取决于质量/速度权衡。当包含所有三个组件时，MediaPipe 整体版为突破性的 540 多个关键点(33 个姿势、21 个手和 468 个面部标志)提供了统一的拓扑结构，并在移动设备上实现了接近实时的性能。* [*MediaPipe 整体版*](https://solutions.mediapipe.dev/holistic) *作为*[*media pipe*](http://mediapipe.dev/)*的一部分发布，可用于移动设备(Android、iOS)和桌面设备。我们还引入了 MediaPipe 的新的现成 API，用于研究(*[*Python*](https://mediapipe.page.link/holistic_py_colab)*)和 web(*[*JavaScript*](https://mediapipe.page.link/holistic_codepen)*)以方便对技术的访问。**
> 
> *[*…继续读*](https://ai.googleblog.com/2020/12/mediapipe-holistic-simultaneous-face.html)*

*《丛林奇兵》*

*   *[条](https://ai.googleblog.com/2020/12/mediapipe-holistic-simultaneous-face.html)*
*   *[MediaPipe Python 解决方案](https://mediapipe.page.link/python)*
*   *[MediaPipe Javascript 解决方案](https://mediapipe.page.link/javascript)*
*   *[Google Colab 上的 media pipe](https://mediapipe.page.link/colab)*
*   *[code pen 上的 media pipe](https://mediapipe.page.link/codepen)*
*   *鸣谢: [@GoogleAI](https://twitter.com/GoogleAI)*

# *人工智能/人工智能软件的软件工程:系统的文献综述*

*![](img/83c0ec5e221f789b31f3343bc4a865b9.png)*

*The publication selection process [[source](https://arxiv.org/pdf/2011.03751v1.pdf)]*

> **人工智能(AI)或机器学习(ML)系统已被各行各业的公司广泛采纳为价值主张，以创造或扩展它们提供的服务和产品。然而，开发人工智能/人工智能系统提出了几个工程问题，这些问题不同于非人工智能/人工智能软件开发中出现的问题。本研究旨在调查软件工程(SE)如何应用于人工智能/人工智能系统的开发，识别适用的挑战和实践，并确定它们是否满足专业人员的需求。此外，我们评估了这些 se 实践是否适用于不同的环境，以及它们可能适用于哪些领域。我们对 1990 年至 2019 年的文献进行了系统回顾，以(I)了解和总结该领域的当前技术水平，以及(ii)分析其局限性和将推动未来研究的开放挑战。我们的结果表明，这些系统是在实验室环境或大公司中开发的，并遵循研究驱动的开发过程。专业人员面临的主要挑战是在测试、人工智能软件质量和数据管理领域。大多数提议的 SE 实践的贡献类型是指南、经验教训和工具。**
> 
> *[*…继续阅读*](https://arxiv.org/abs/2011.03751v1)*

*《丛林奇兵》*

*   *[条](https://arxiv.org/abs/2011.03751v1)*
*   *鸣谢:论文作者*

# *可控神经文本生成*

*![](img/b81b2c8737bfaaed65745a512efdb639.png)*

*Examples of controllable text generation by PPLM [[Dathathri et al., 2019](https://arxiv.org/abs/1912.02164)]*

> *网络上有大量的免费文本，比标注的基准数据集多几个数量级。最先进的语言模型(LM)使用大规模的无监督 Web 数据进行训练。当通过迭代采样下一个标记从 LM 生成样本时，我们对输出文本的属性没有多少控制，例如主题、风格、情感等。许多应用程序需要对模型输出进行良好的控制。例如，如果我们计划使用 LM 为孩子们生成阅读材料，我们希望输出的故事安全、有教育意义并且易于孩子们理解。*
> 
> *如何驾驭强大的无条件语言模型？在本帖中，我们将深入探讨几种使用无条件语言模型生成受控内容的方法。请注意，模型的可操纵性仍然是一个开放的研究问题。每种引入的方法都有一定的利弊。*
> 
> *[*…继续阅读*](https://lilianweng.github.io/lil-log/2021/01/02/controllable-neural-text-generation.html)*

*《丛林奇兵》*

*   *[文章](https://lilianweng.github.io/lil-log/2021/01/02/controllable-neural-text-generation.html)*
*   *[纸张:生成式鉴别器](https://arxiv.org/abs/2009.06367)*
*   *[论文:后规范融合](https://arxiv.org/abs/1809.00125)*
*   *信用: [@lilianweng](https://twitter.com/lilianweng/)*

# *解释转换器语言模型的接口*

*![](img/74616392eea0f9ca5c949df8e1873c5e.png)*

*Methods to gain insight into the inner-workings of Transformer models. [[source](https://jalammar.github.io/explaining-transformers/)]*

> **变压器架构推动了 NLP 的许多最新进展。此处提供了该架构的细目分类。基于该架构的预训练语言模型，在其自回归(使用自己的输出作为下一时间步的输入，并从左到右处理令牌的模型，如 GPT2)和去噪(通过破坏/屏蔽输入训练的模型，并双向处理令牌，如 BERT)变体中，继续推动 NLP 和最近的计算机视觉中各种任务的发展。然而，我们对这些模型为什么如此有效的理解仍然落后于这些发展。**
> 
> **这一系列的展示继续追求解释和可视化基于 transformer 的语言模型的内部工作。我们举例说明了一些关键的可解释性方法如何应用于基于转换器的语言模型。本文主要关注自回归模型，但是这些方法也适用于其他架构和任务。**
> 
> *[*……继续阅读*](https://jalammar.github.io/explaining-transformers/)*

*《丛林奇兵》*

*   *[条](https://jalammar.github.io/explaining-transformers/)*
*   *[Github 上的笔记本](https://github.com/jalammar/ecco/tree/main/notebooks)*
*   *[Colab 中的笔记本](https://colab.research.google.com/github/jalammar/ecco/blob/main/notebooks/Ecco_Input_Saliency.ipynb)*
*   *[Ecco 库](https://github.com/jalammar/ecco/)*
*   *信用: [@JayAlammar](https://twitter.com/JayAlammar)*

# *保持最新状态*

*ML UTD #33 到此为止。然而，在学术界和工业界，事情发生得很快！除了[这个时事通讯](https://www.lifewithdata.org/newsletter)，让自己在 [LifeWithData](https://lifewithdata.org/) 博客、[媒体文章](https://medium.com/@anthonyagnone)和 [Twitter](https://twitter.com/@anthonyagnone) 上保持更新。*

# *不断学习*

*[](https://medium.com/datadriveninvestor/ml-utd-32-machine-learning-up-to-date-life-with-data-3921d18a1669) [## [ML UTD 32]最新的机器学习—数据生活

### 《生活与数据》周刊第 32 期

medium.com](https://medium.com/datadriveninvestor/ml-utd-32-machine-learning-up-to-date-life-with-data-3921d18a1669) [](https://medium.com/datadriveninvestor/checkthisout-pythons-rich-library-for-terminal-text-formatting-e4da97a0beda) [## [CheckThisOut] Python 丰富的终端文本格式化库

### Rich 是一个 Python 库，用于终端中丰富的文本和漂亮的格式。

medium.com](https://medium.com/datadriveninvestor/checkthisout-pythons-rich-library-for-terminal-text-formatting-e4da97a0beda) [](https://towardsdatascience.com/tips-to-survive-and-thrive-in-the-remote-first-data-workforce-34944abddd29) [## 在远程优先的数据工作人员中生存和发展的技巧

### 提示:它不仅仅是 Zoom 和 Github

towardsdatascience.com](https://towardsdatascience.com/tips-to-survive-and-thrive-in-the-remote-first-data-workforce-34944abddd29) 

*原载于 2021 年 1 月 27 日 https://www.lifewithdata.org*[](http://www.lifewithdata.org/newsletter/mlutd33)**。***