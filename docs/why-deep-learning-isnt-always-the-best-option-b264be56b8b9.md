# 为什么深度学习不总是最好的选择

> 原文：<https://medium.datadriveninvestor.com/why-deep-learning-isnt-always-the-best-option-b264be56b8b9?source=collection_archive---------6----------------------->

## 以及用什么来代替。

![](img/09d1030b8041f1d369075f7c49815ecf.png)

深度学习——机器学习的一个子集，大数据被用来训练神经网络——可以做不可思议的事情。

即使在 2020 年的所有混乱中，深度学习也在多个行业带来了惊人的突破，包括自然语言(OpenAI 的 GPT-3)、自动驾驶(特斯拉的 FSD beta)和神经科学(Neuralink 的神经解码)。

然而，深度学习在几个方面受到限制。

# 深度学习缺乏可解释性

2018 年 3 月，沃尔特·黄(Walter Huang)正在山景城(Mountain View)的自动驾驶系统上驾驶他的特斯拉，当时它突然以 70 英里/小时的速度撞上了安全护栏，夺走了他的生命。

今天的许多人工智能系统做出生死决定，而不仅仅是自动驾驶汽车。我们相信人工智能可以对癌症进行分类，跟踪新冠肺炎病毒的传播，甚至检测监控摄像系统中的武器。

当这些系统失败时，代价是毁灭性的和最终的。我们不能让一条人命复活。不幸的是，人工智能系统总是失败。这叫做“错误”当他们失败时，我们需要解释。我们想了解*为什么是*。

然而，深度神经网络和集成并不能轻易地给出我们需要的答案。它们被称为“黑盒”模型，因为我们无法看透它们。

透明度不仅在生死攸关的系统中至关重要，在日常金融模型、信用风险模型等等中也是如此。如果一个为退休储蓄的中年人突然失去了他们的金融安全网，最好有一个合理的解释。

# 深度学习有过度适应的倾向

过度拟合是指模型很好地学习了训练数据，但未能推广到新数据。例如，如果您要使用神经网络建立一个交易模型来预测金融价格，您将不可避免地得出一个过于复杂的模型，该模型在训练数据上具有很高的准确性，但在现实世界中却失败了。

一般来说，神经网络——尤其是深度学习——比像逻辑回归这样的简单模型更容易[过度拟合](https://www.sciencedirect.com/science/article/pii/S1532046403000340)。

> “在逻辑回归中，模型的复杂性已经很低了，尤其是在没有或很少使用交互项和变量转换的情况下。在这种情况下，过度拟合不是问题...与逻辑回归相比，**神经网络模型更灵活，因此更容易过拟合**

[](https://www.datadriveninvestor.com/2020/11/27/deep-learning-amid-increased-physician-administrative-workload/) [## 医生管理工作量增加时的深度学习|数据驱动的投资者

### 行政工作量是我们这个时代大多数医生所经历的众多负担之一。医生，尤其是…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/11/27/deep-learning-amid-increased-physician-administrative-workload/) 

# 深度学习更贵

建立深度学习模型可能很昂贵，因为人工智能人才的收入很容易达到六位数。它不止于此。部署深度学习模型也很昂贵，因为这些大型、沉重的网络消耗了大量的计算资源。

例如，截至本文撰写之时，OpenAI 的自然语言引擎 GPT-3 达芬奇每 1000 个令牌的价格为 0.06 美元。这看起来很便宜，但是当你面对成千上万甚至上百万的用户时，这些成本会很快增加。

我们来对比一下传统的机器学习模型。

用 CPU 上的两层神经网络进行预测[花费](https://www.researchgate.net/publication/335373358_Benchmarking_Keyword_Spotting_Efficiency_on_Neuromorphic_Hardware)大约 0.0063 焦耳，或 0.00000000175 千瓦时。对于所有的意图和目的，单次预测的成本可以忽略不计。

# 解决方案——可解释、简单、负担得起的模型

幸运的是，使用一种名为 *AutoML* 或自动化机器学习的技术，创建可解释、简单且负担得起的机器学习模型比以往任何时候都更容易，这种技术可以自动创建给定数据集的各种机器学习模型，并选择最准确的模型。

AutoML 并不是一个新现象，但近年来由于无代码的兴起，它变得特别容易，显然使像[这样的轻松机器学习工具成为可能。AI](http://obviously.ai) 。

2010 年，麻省理工学院[讨论了](https://news.mit.edu/2010/brain-mapping)一种“被称为自动化机器学习的通用计算机科学技术”，但那时，你仍然需要开发人员使用 AutoML 工具。

今天，任何人都可以构建和部署可解释的、简单的、负担得起的人工智能，而无需任何编码或技术技能。

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)