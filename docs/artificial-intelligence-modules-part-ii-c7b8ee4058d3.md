# 人工智能-模块第二部分

> 原文：<https://medium.datadriveninvestor.com/artificial-intelligence-modules-part-ii-c7b8ee4058d3?source=collection_archive---------4----------------------->

![](img/95f91a56d3ee03ffc0e6fe54b07fee61.png)

探索深度学习、RL、NLP、感知和整合模块/子领域。

![](img/b0a6998dd0c342d330093ad5d046bb7c.png)

> 阅读《问题解决—机器学习》的第一部分。在这篇文章中，人工智能模块或子领域涵盖了像深度学习，强化学习，NLP，感知和集成模块。

完成这篇文章(连同其他文章的链接)将会介绍主要的人工智能子领域或模块，以及通过数学观点的例子。在每个子领域提供了必要的主题，应用，实施主题和一个例子。这篇文章可以以互动的方式阅读(同[第一部分](https://shafi-syed.medium.com/artificial-intelligence-modules-27cb7a9d9466))。

> 请注意，如果您遵循提供的链接，您将从数学角度对算法的内部工作以及每个模块的示例感到欣慰。提供链接的目的是不能在一篇文章中涵盖所有的内容。对于流行的概念，这里提供了链接，对于难懂的概念，这里简单解释一下。

![](img/6b71376b6d67bd43762c3661d855e116.png)![](img/fa6f771953f17662a386c1b4ee468c34.png)

深度学习是机器学习的一个分支，它特别用于非结构化数据，如文本行(无结构)、图像和视频。

> 深度学习基于生物神经元的连接主义哲学。

神经网络架构如下。神经网络[概念](https://medium.com/analytics-vidhya/linear-algebra-how-uses-in-artificial-intelligence-2e1e001c65?sk=7734226c0b2b92b782fb2b11d9de7a5a)和[实现](https://medium.com/swlh/ai-mathematics-699a9ea2a0d6?sk=81c51e208e1b0586080a143ff4f225ec)通过数学的角度得到很好的解释。

![](img/6e7c0ff17bbf592156eb28956b3d9045.png)

> **问题:使用深度学习并概述其概念需要什么？**

深度学习完全基于神经网络哲学和数学，正如你在上图中看到的很容易得出结论，神经网络使用线性代数、统计学、信息论、矩阵微积分、神经元概念(不需要博士学习)、实分析等。，你可以在这篇[文章](https://medium.com/swlh/ai-mathematics-699a9ea2a0d6?sk=81c51e208e1b0586080a143ff4f225ec)的第二部分找到包括向前向后计算的神经网络的完整示例。本文通过一个例子描述了这两种必备的东西。

下图探索了硬件(红色)、必修科目(蓝色)及其概念或技术或架构。神经网络分为架构(神经网络，CNN，RNN 和胶囊网络)。

下图描述了所需的数学知识。

![](img/a4696ef40ed649f74650f0e1bee334e0.png)

**Required Mathematics for Neural Networks , described where Mathematical subject involved at every step in Neural Network**

![](img/28d529fdada058aaa81fc2f130ec6eca.png)

**Deep Learning required Subjects, Hardware and Concepts/Architectures.**

> **问题:神经网络有哪些常见的架构和用法？**

深度学习基本上有神经网络(NN)、卷积神经网络(CNN)、递归神经网络(RNN)和胶囊神经网络，每一种都有特定和自己的用法。对于一些架构，需要将 AI 的其他模块结合到深度学习架构中，最好的例子就是 HMM 可以集成到 RNN 中。有时 CNN 包括 RNN 的图像字幕任务。上面描述的神经网络结构。

# 卷积神经网络(CNN)

CNN 可用于图像处理，尤其是计算机视觉任务，如图像的分类、定位、检测和分割。计算机视觉任务需要每次观察处理大量的输入特征(即像素)。

![](img/62e69209b68c869a27f184652d891462.png)

**Well known CNN architecture contains Feature Extraction and Classification**

上图中有许多需要理解的概念，对这些概念的简要解释超出了本文的范围，您可以在这里找到。这些是内核或过滤器，Relu，池，卷积，步幅，扁平化，完全连接。

# 递归神经网络

RNNs 可广泛应用于文本分析、序列模型、时间序列分析和视频处理。而在语言中，建模任务需要对每个输入特征的大量可能值(词汇表中的单词)进行建模。RNN 和它的变体可以在 [Colah 的](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)博客中很容易理解。

# 胶囊网络

胶囊网络是最新的网络，用于图像处理。纯粹用向量代数概念实现的胶囊网络。胶囊网络在这篇[文章](https://towardsdatascience.com/capsule-networks-the-new-deep-learning-network-bd917e6818e8)中有很好的解释。胶囊网论文可以在[这里](https://arxiv.org/pdf/1710.09829.pdf)找到。Caps Networks 使用带有不同过滤器的 Relu、Conv 图层。

![](img/5387964758093bdf8f8e9a6111fbaa2e.png)

**Architecture of Capsule Networks**

# 编码器-解码器

它由读取输入序列的编码器 RNN 和产生输出序列的解码器 RNN 组成。这里输出序列不一定是相同的长度。这种体系结构用于许多应用中，例如语音识别、机器翻译或问题回答，其中训练集中的输入和输出长度不相同。

![](img/425e963e3fa2ede81529dddcffb3481f.png)

**Encoder-Decoder architecture for Machine Translation task using Attention mechanism, it is Sequence to sequence RNN architecture.**

在上述体系结构中，上下文 C 可以是概括输入序列的向量或向量序列。向量 X 是输入序列，Y 是输出序列。

> **问题:深度学习可以用在哪里？**

深度学习是目前最热门的研究领域，可以应用于自动驾驶汽车/SDC、诊断、图像处理、自然语言处理等领域。DL 使用 CNN 应用计算机视觉，NLP 使用 RNNs，Deep RL 用于感知外部世界并估计适当的动作。

神经网络至关重要，DL 需要高性能的硬件和软件基础设施。下图描述了神经网络架构和用途。

![](img/223c5741576d5789c73638e4aba16320.png)

**Popular architectures in Neural Networks and its applications.**

## **生成性对抗网络**

[GANs](https://arxiv.org/pdf/1406.2661.pdf) 包含两个被称为**生成器**和**鉴别器**的神经网络，生成器生成新的数据点，而鉴别器对生成的数据点(观察或对象或例子)进行评估。

给定一个训练数据集，GAN 学习生成与训练集具有相同统计数据的新数据。gan 对于监督、非监督、半监督和强化学习是有用的。

## 甘斯建筑

还有 GAN 的变体，如 [cGAN](https://arxiv.org/abs/1411.1784) 、StyleGAN、infoGAN、AC-GAN、上下文编码器、Pix2Pix、WGAN、CycleGAN、Progressive GAN、BigGAN。下图显示了 cGAN 和 [StyleGAN](https://arxiv.org/abs/1812.04948) 架构。

![](img/525431d8fe9246760a44c7b7daec65c3.png)

**Conditional GAN Architecture**

![](img/c0428b0480274ad368035416b59adc51.png)

**StackGAN Architecture**

## 氮化镓的应用

GANs 适用于各种领域，如时尚、艺术、广告、科学、视频游戏、恶意应用程序、3D 模型等。，[来源—维基](https://en.wikipedia.org/wiki/Generative_adversarial_network)。使用氮化镓有很多应用。

## gan 在科学(天体物理学)中的应用

GANs 可以改善天文图像，模拟引力透镜，用于暗物质研究。它们在 2019 年被用于成功模拟暗物质在空间特定方向的分布，并预测将发生的 [g](https://en.wikipedia.org/wiki/Gravitational_Lensing) 引力透镜化。— [来源—维基](https://en.wikipedia.org/wiki/Generative_adversarial_network)。

**问题:深度学习可以用什么硬件？**

这些天，研究人员使用 3 个硬件平台进行深度学习应用。它们是 CPU、GPU 和 TPU。

## 使用硬件的动机:

> 对于培训，它允许我们试验更多的模型架构。
> 
> 在生产系统中，向最终用户快速提供结果至关重要。

**CPU(中央处理器)**:在某些情况下被认为是一个合适的、重要的培训平台。CPU 针对串行任务进行了优化。CPU 架构必须最小化每个线程内的延迟。CPU 针对缓存数据集的低延迟访问进行了优化。无序和推测执行的控制逻辑。

**GPU(图形处理单元):**对于小批量、非矩阵乘法计算等不规则计算表现出更好的灵活性和可编程性。GPU 针对并行任务进行了优化。它针对数据并行、吞吐量计算进行了优化。容忍内存延迟的体系结构。更多专用于计算的晶体管。GPU 架构隐藏了计算延迟。

**TPU(张量处理单元):**对大批量和 CNN 高度优化，训练吞吐量最高。你可以在这个[链接](https://cloud.google.com/tpu)中了解更多关于 TPU 的信息。

如果我们在内部考虑矩阵、向量、逐点和其他函数(tanh、sigmoid ),我们会选择合适的硬件(CPU、GPU、TPU)。

考虑任务的 CPU、GPU 优化以及下图中的低延迟、高吞吐量。

![](img/1bcb005b548dae48f7d2ff28fd57c8d7.png)

以下概念更广泛地用于深度学习。这些是数据扩充、迁移学习和元学习。

# 数据扩充

> **问题:什么是数据增强、迁移学习和元学习？**

数据扩充是一种通过应用变换来增加训练数据集多样性的技术。它是一种数据分析技术，用于通过添加现有数据的稍微修改的副本或从现有数据中新创建的合成数据来增加数据量。— [数据扩充，维基](https://en.wikipedia.org/wiki/Data_augmentation)

通常我们使用 CNN 对图像进行数据增强。以下示例给出了应用增强技术后同一对象的不同姿态。

![](img/f595c92f3fb583c9ea095a9065463833.png)

> **数据扩充中最流行的技术是颜色修改、随机擦除、翻转、旋转、缩放、裁剪、平移和噪声。**

**翻转:**您可以水平或垂直翻转图像。

**缩放**:图像可以向外或向内缩放。在向外缩放时，最终的图像尺寸会比原始图像大，而向内缩放会缩小图像尺寸。

**裁剪:**您可以裁剪图像中需要的部分。

**旋转:**你可以把图像旋转到你想要的角度，除了 180 度外，图像的大小不会被保留。

**平移:**沿 X 轴或 Y 轴或两者移动图像。

**高斯噪声:**其均值为零，本质上在所有频率都有数据点，有效扭曲了高频特征。加入适量的噪音可以提高学习能力。

# 迁移学习

迁移学习是一种在针对一个问题进行训练的同时获取知识，并将其应用于同一领域的不同问题的技术。在神经网络术语中，我们为一个任务训练神经网络，并获取参数，然后在相同的数据分布上应用于不同的任务。训练任务和不同任务的数据分布是相同的。例如，识别汽车的知识可以应用于识别卡车。

使用 CNN 的迁移学习是普遍的(它对于不同的任务是分布式的)。

下图对此进行了描述。

![](img/56745a81dc546fdf95f81935e577ff18.png)

# 元学习

从元数据开始—关于数据的数据称为元数据。元数据包含关于文件的信息，如名称、大小、创建日期、修改日期、类型和路径。

同样，元学习描述的是学会学习。通常是从其他机器学习算法的输出中学习的机器学习算法。

元学习算法通常指**、【集成学习】、**学习如何组合来自其他算法的预测。

## **合奏学习**

**集成学习**的主要思想是组合一组模型，每个模型解决相同的原始任务。

主要的集成学习技术是 Bagging，Boosting。这些是对回归和分类算法的处理。

![](img/8614bca06f1fec82b5df13ec7bd77408.png)

**Ensemble Learning has 2 techniques Bagging and Boosting**

众所周知的分类算法是 K-最近邻( **KNN** )、分类和回归树、用于分类的神经网络、逻辑回归、朴素贝叶斯和贝叶斯网络。

分类模型的集成学习比单一分类模型的好处在于

1.  集成分类器可能具有较低的错误率(提升)。
2.  对于不稳定分类器如决策树和神经网络等具有高度可变性的分类器，集成分类器的性能将低于不稳定分类器。

它也指多任务学习，学习如何在一系列相关的预测任务中学习。

集成学习的目的是减少预测误差。预测误差定义如下:

![](img/b400018043e65c7c90b6251d3d2c5fed.png)

其中**偏差**是指预测值和目标值之间的平均距离。**方差**测量预测本身的可变性，**噪声**表示预测器可能达到的预测误差的下限。

**注意**迁移学习和元学习是从其他任务中学习的。元学习描述了学会学习。

![](img/b946baccd0658aa7b403ef4906537e75.png)

由于今天强化学习的普及和更先进的研究，强化学习在更多的[细节](https://medium.com/datadriveninvestor/reinforcement-learning-an-interactive-learning-b1fa29166fc8?source=friends_link&sk=cb3faf7dae11fe358c8ac81113b6ec09)中有所涉及，这适用于自动驾驶汽车、机器人、未知和艰苦环境等主要应用。

![](img/d9425e81d6ce69c1f4a17ca7feb87cbc.png)

强化学习是一种与环境交互的机器学习，这是一种产生最有利结果的动作组合。它是基于学习的决策的数学形式。RL 是一种从经验中学习决策和控制的方法。

下图描述了监督学习、非监督学习和强化学习是如何出现和分类的。

![](img/dd3043c76c542bc3bbaee876df6a127a.png)

**Categorizing ML Algorithms**

简单地说，一个代理在环境中的时间“t”执行状态中的动作，并在时间 t+1 获得新的状态和该动作的奖励。

在每个步骤中，代理

> 执行一个动作
> 
> 观察新状态
> 
> 接受奖励

> **问:学习强化学习需要什么？**

RL 动态地而非离线地学习马尔可夫决策过程(MDP)。下面给出了最低要求和主要概念。RL 和 MDP 的主要内容是符号必须理解清楚，否则有时很难理解方程。

![](img/5fb1578aa7733ecf297cce48a3dca0de.png)

强化学习的迭代方法之一是动态编程，在这篇[文章](https://shafi-syed.medium.com/reinforcement-learning-an-interactive-learning-b1fa29166fc8)中解释了它的概念和例子。

[](https://shafi-syed.medium.com/reinforcement-learning-an-interactive-learning-b1fa29166fc8) [## 强化学习——一种交互式学习

### 以互动的方式学习

shafi-syed.medium.com](https://shafi-syed.medium.com/reinforcement-learning-an-interactive-learning-b1fa29166fc8) 

> **问题:强化学习中有哪些概念？**

使用强化学习可以实现的主要主题如下所述。

![](img/7cbc520ac04722c2fc7e3fcf891db29d.png)

> **问题:强化学习中有哪些算法？**

强化学习有两种算法，**基于模型的**学习和**无模型的**学习。都是用来做决策的。

基于模型的学习算法使用转移函数和奖励函数以及在控制探索期间获得的样本。

无模型学习(Model-free learning)，试图直接估计状态的值或 q 值，而不使用转换和奖励。

![](img/178ca77a3dfb8b5a74901314d0cc28fd.png)

**下面列出强化学习算法。**

![](img/58c520bffa004bdee22e6a6e54f89a99.png)

> **问题:有哪些应用，举一个使用 RL 的例子？**

在接下来的[文章中](https://medium.com/datadriveninvestor/reinforcement-learning-an-interactive-learning-b1fa29166fc8?source=friends_link&sk=cb3faf7dae11fe358c8ac81113b6ec09)清楚地解释了使用动态编程以及公式、评估等进行基于模型学习的赛车示例。,

![](img/081fd6e049176f5e14a90c3dc453c1a6.png)

它的主要应用列在左边。强化学习是热点，在未知环境下表现良好。它有足够的方法去探索环境。它与神经网络相结合来执行复杂的计算，以及代理所感知的内容并采取适当的行动。

![](img/a33c6c6602756b9941405c9e8512800c.png)![](img/ade0d2868057386deed06e0ed8ce26a5.png)

强化学习可以自然地与人工神经网络集成，以获得高质量的泛化能力，从而显著加快学习速度。— **林立杰，使用神经网络的机器人研究中心，1933 年。**

深度模型是**，它允许**强化学习算法端到端地解决复杂问题。Deep RL 在深度学习、强化学习和计算能力方面取得进展。

在深度强化学习中，深度学习可以处理复杂的感官输入，也可以计算非常复杂的功能，强化学习可以选择复杂的动作。

深度 RL 方法由于处理复杂的感觉输入和复杂而通常很慢。在深度学习中，动作可以在神经网络中计算，并最终输出动作。

![](img/a5d3499a19b4bc6eea27bb8c559d6301.png)![](img/fdb39cb2a2d49b79ee2ee1508d73bd84.png)

简单地说，自然语言处理(NLP)是计算机对人类语言的使用。例如英语、德语或法语等。它包括语言模型、机器翻译、摘要、语音识别、问答、依存句法分析、文本分类等应用。,

语言建模是 NLP 的核心，因为许多 NLP 应用程序都是基于语言模型，这些模型定义了单词序列的概率分布。这在下图中有很好的定义。

> **问题:什么是语言模型？**

语言模型预测句子中的下一个单词。它使用了被称为概率链规则的概念。语言模型是一种语言的概率模型，并且更有用，并且说人们通常说的话(接下来)。

例如:在 Siri 应用程序中，当我们输入单词时，它会自动填充下一个单词。

语言模型是 NLP 的秘密武器。使用的主要应用是

![](img/f2d3075a2efae1d667b6ceca87ee3d89.png)

**Major Applications using Language Model (LM)**

下面简单地通过使用关于单词及其度量的概率链规则来描述语言模型算法。将联合概率转换成条件概率序列。

![](img/ea260f2ef09ce4921ee514eb4e8b28dc.png)

**Decomposition of words/tokens using chain rule**

# 评估语言模型

它可以用交叉熵(CE)来度量，定义为

![](img/aa3fd7e8513366d208073272c8007ca5.png)

CE 描述了用模型编码文本需要多少位。

或者，我们可以使用困惑度，这是一个衡量模型如何看待每个单词的标准。

![](img/5608c9bcb9f972782e3a771a6390f72a.png)

## **语言模型(LM)的实现**

语言建模可以通过三种方式实现。1)基于计数的 N 元语法 LM 2)神经 N 元语法 LM 3)递归神经网络 LM

例如 N 元模型

如果 N=2，那么 2-Gram 模型描述如下

![](img/7d45ca4724bdfb5c29c532ac2a279b4d.png)

对于 N=2 的神经 N 元模型，则 2 元模型在神经网络中描述如下

![](img/76c36464c0bd22809a53013302fb4ea6.png)

**Neural Network implementing Language Model**

对于 RNN 语言模型描述如下，在 RNN 隐藏单元是通过网络共享的(即在隐藏层)。RNN 通常被描述为

![](img/f233d37c10579e0a65673cb4f3b008d1.png)

**Recurrent Neural Network for Language model**

上面提到的是 RNN 的第 n 层，用同样的方法我们添加其他层。RNN 成本函数被定义为(注意在某些地方我们把 p 或 y 写成每一层中的每一个计算值)。

![](img/75f3cc820e1f7a0ee672ea88242b3e9e.png)![](img/541aae7bffce89f26155677c662745b4.png)

NLP 的子分支以及内部策略如下所述。

![](img/3422d2d1b8dca62bb7233d1e8252059c.png)

**NLP, NLG and NLU**

NLP 在 NLG 和 NLU 有两家分公司。 **NLG** 基本上用于由机器(计算机、细胞、机器人等)生成自然语言。,). **NLU** 负责机器理解我们说话的能力。

![](img/8d192b4c87b8c3741919c0d127d83814.png)

> **理论部分:**

线性代数、概率论、深度学习(神经网络和 RNNs)、矩阵演算、语言学基础知识理解、上下文语法、解析等。,

> **实施部分:**

NLP 在神经网络中实现，与非神经网络方法(n-grams)相比具有各种优势。

在 NLP 中，你必须使用单词嵌入(W2V)、语言模型(LMs)和条件语言模型(CLMs)来完成 NLP 中的其他任务。

![](img/5b494a6675c45f8e545959d850442621.png)

**Typical RNNs for NLP tasks**

![](img/4c0f874725f1d402d4b311043dc41915.png)

NLP 任务大致分为句法、语义、话语、语音和对话，下图描述了所有的任务。

![](img/a7001e449aa01f38ab174650c5c0589d.png)

**基于语法的任务:**这些任务描述了句子、单词是如何根据语法规则构成的。简单地说，它是文本的语法结构。例:**解析**。

**基于语义的任务:**这些任务处理文本的含义。它是理解单词、符号和句子结构的意义和解释的过程。

**基于语音的任务:**将口语翻译成文本。主要是它基本上识别单词并翻译成文本。最好的例子是**语音识别**，它主要专注于与**机器**、汽车、手机等进行交流。,

**基于语篇的任务:**识别相连文本的语篇结构，即句子间语篇关系的性质。另一项任务是对文本块中的言语行为进行识别和分类。

**基于对话的任务:**一个系统(机器、计算机、细胞等。，)意在与人类交谈。例子**聊天机器人**，你可以全天候交流和提问。

![](img/eb40f8af2535ce23a60189a71fc406e6.png)

NLP 可以在神经网络中实现，特别是在递归神经网络(RNNS)中。由于梯度消失和爆炸问题，标准 RNNs 没有提供太多支持，为了克服这些困难，使用[长短期记忆(LSTMs)](https://colah.github.io/posts/2015-08-Understanding-LSTMs/) 和[门控循环单元(GRUs)](https://colah.github.io/posts/2015-08-Understanding-LSTMs/) 代替。

LSTM 和 GRU 是众所周知的最好的处理数据序列的架构，这两个是 RNN 的变体。

![](img/dad84bc0ae8541a529b3ea8264271b03.png)

由于与机器和车辆(汽车、手机和机器人)通信的能力，语音识别非常热门。由于大量使用 LM 和 NLP 语法材料，语音识别不是 NLP 的特别部分，它被认为是 NLP 的一部分。

![](img/0da7cd434c0ff5232dd5f938248fc394.png)

**Simple Speech Recognition Architecture**

![](img/4439df67129a2745fc84e148252b8106.png)

今天，自然语言处理的应用是为了处理机器(非生物，如机器人、机器、网站等)。,).下面描述了 NLP 的可能的和众所周知的应用。

![](img/cc2037b6b0931ff36b20c7f199acb111.png)![](img/7403b42817c6cd1c980b0c9916a00a4c.png)![](img/417d68d0d78b0c14f3607ec10323aed1.png)

**感知通过解释传感器的反应，为智能体提供所需的关于环境或世界的信息。**

传感器是硬件，它测量环境的某些方面，可以作为代理程序的输入。

![](img/a28c5f25b040fe38852daf03c1d1e3bb.png)

**Types of Sensors used for AI Agents**

在上图中，代理使用传感器数据作为输入在人工智能环境中工作。有不同的传感器，如用于视觉的传感器(用于计算机视觉的传感器:摄像机、雷达、激光雷达等。、)、听觉(用于语音识别和 NLP)和触觉(用于机器)。

下图说明了代理所需的组件以及这些组件之间的关系。

![](img/86896928ba5ec83aeabb6b74b26cc8f3.png)

**Relationship between agent, environment perception and action.**

在上图中，代理感知环境，通过传感器接收数据，并根据其效应器执行操作。

为了理解感知，你需要理解几个主题，下面的图表描述了这一点。这些主题超出了本文的范围。

![](img/a9bb567e7adc80d9cc53549710ecdf5d.png)

**Perception Concepts, Operations and types.**

计算机视觉是感知的整体实现之一，在这里我们可以使用对大型数据集的深度学习来实现所需的概念。

![](img/52c5ec4df5884f4cf7f754cc8e1279d4.png)

嗯，感知可以用深度学习实现，也可以不用深度学习。对于小数据集，不需要深度学习，我们可以用。对于大型数据集和实时应用，如使用卷积神经网络(CNN)在深度学习中实现的自动驾驶汽车和机器人。以下架构描述了为 Imagenet 数据集实现 CNN。

![](img/eead39f777df596500de0be856c25dce.png)

**The activations of an example ConvNet architecture**

正如 CNN 上面提到的，基于 CNN 有不同的架构。下面是 Alexnet 的图像网络数据集的对象检测。

![](img/cdbd4694b9946533a51d91bc160e1aec.png)

**Object Detection using Alexnet for** [**Image-net Dataset**](http://www.image-net.org/challenges/LSVRC/2014/)

![](img/1b361eddf79d3d922e6f5a2df608adc7.png)

感知有各种各样的任务，但最常见的是分类、定位、检测和分割。基于这些任务，可能会生成各种其他任务。下面是每一个的例子。

这些任务是在计算机视觉中实现的，特别是使用 CNN 及其架构，如 LeNet、AlexNet、ZF 网、Resnet、谷歌网、VGG 网。

![](img/e881021a27fa9c972e5cf4ab998b4c3b.png)

**Tasks for single and multiple objects**

# **分类**

也可以称为认可。一个有物体的图像，找出那个物体是什么。简而言之，从一组预定义的类别中将其分类。

# 本地化

找到特定对象的位置，并在图像中围绕它画一个边界框。

# 侦查

对图像中的所有对象进行分类和检测，并为每个对象分配一个类别，并在其周围绘制一个边界框。

# 分割

切分有两种方法，语义切分和实例切分。在**语义分割**中，将图像中的每个像素分类到一个类中，这样每个像素被分配到一个对象的不同实例中。在**实例分割**中，将图像中的每个像素分类到一个类中，这样每个像素被分配到一个对象的不同实例中。

![](img/be22568246eb68d0cda33d4c44dca200.png)

感知可以应用在各种应用中，尤其是人工智能主体可以从环境中感知并相应地执行动作。机器人、自动驾驶汽车等应用。,

# **整合模型**

对于现实世界的应用，我们需要结合一个以上的人工智能子领域或模块来完成任务。以下示例 NLP 机器翻译(西班牙语-英语)描述了 AI 模块的使用。在这个任务中，最小的概念是(嵌入矩阵——用于单词，语言模型——用于单词序列，RNN——用于实现，HMM——用于预测，等等。, ).同样，我们为自动驾驶汽车组合(例如:问题解决、概率方法、深度学习、感知、强化学习等。,

对于大型实时应用程序，我们必须组合多个模块。

![](img/4503f68d7d43ae46246a30d55f6c19a6.png)

**Machine Translation Model stack**

# 结论

这篇和[上一篇](https://shafi-syed.medium.com/artificial-intelligence-modules-27cb7a9d9466)文章简单探讨了问题解决、知识、推理、规划和学习(机器学习)、深度学习、强化学习、NLP 和感知(计算机视觉)。请注意，我尽了最大努力来涵盖初学者或研究人员所需的内容。这些文章(第一部分，第二部分)的直觉是，AI 爱好者应该清楚地知道子领域或模块，并开始增强其用法，以实现复杂的实时任务。