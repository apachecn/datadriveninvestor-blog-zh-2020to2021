# 为什么小数据很重要

> 原文：<https://medium.datadriveninvestor.com/why-small-data-is-a-big-deal-83c17e118785?source=collection_archive---------29----------------------->

## 以下是小数据如何产生大影响。

![](img/ca9bfd7260bdae9b28a9ccbcfc0adf4a.png)

# 新闻中的大数据

当我们在新闻中听到人工智能时，通常是关于一些利用大数据建立的闪亮的新突破——比如特斯拉的自动驾驶汽车、OpenAI 的文本生成器或 Neuralink 的脑机接口。

# 现实生活中的小数据

然而，正如我们在新闻中读到的一样，这些都是离群值。现实中，大多数 AI 项目看起来完全不一样。我们中的大多数人并没有试图创造超级智能，我们只是试图优化 KPI，无论是客户流失率、流失率、销售额、流量，还是一百万个其他指标中的任何一个。

为了优化 KPI，*你不需要大数据*。KPI 优化最常见的数据来源是日常业务工具，如 [Hubspot](https://www.obviously.ai/post/7-hubspot-integrations-to-become-a-power-user) 、 [Salesforce](https://www.obviously.ai/post/7-salesforce-integrations-to-boost-your-productivity) 、 [Google Analytics](https://www.obviously.ai/post/how-to-make-predictions-with-your-google-analytics-data) ，甚至 [Typeform](https://www.obviously.ai/post/how-to-make-data-predictions-from-your-typeform-responses) 。除非您是离群值之一，否则这些工具的输出可能不符合大数据的标准。

如果你*用大数据做*工作，那么你就更有力量。您可能能够创建更精确的模型，但这不是为组织增加价值的先决条件。

# 用于对象检测的小数据

当我们听到“大数据”时，它通常与“对象检测”相提并论事实上，对象检测模型的标准是对大量数据进行训练。

直到现在。

滑铁卢大学的研究人员发表了一篇论文，讨论了“不到一次”学习，即模型准确识别比训练样本数量更多的物体的能力。

计算机视觉实验的一个流行数据集叫做 [MNIST](http://yann.lecun.com/exdb/mnist/) ，由 6 万张手写数字从 0 到 9 的训练图像组成。

麻省理工学院研究人员之前的一项实验表明，从这个巨大的 60，000 幅图像的数据集“提取”出仅仅 10 幅图像是可能的，这些图像经过精心设计，在信息上与全套图像相同，达到几乎相同的精确度。

## loshot 学习

在这篇新的 LO-Short 论文中，研究人员发现他们可以创建将多个数字混合在一起的图像，这些图像被输入到带有“软”标签的模型中，比如一个人和一匹马如何具有半人马的部分特征。

在 MNIST 的上下文中，这指的是数字共享一些特征的想法，例如数字 3 看起来有点像 8，有点像 0，但不像 1 或 7。因此，训练图像可以用来理解比训练集中更多的对象。

令人惊讶的是，这个概念似乎没有任何限制，这意味着精心设计的软标签可以编码任何数量的类别。

> “有了这两点，你就可以分出一千节课或者一万节课或者一百万节课。”([来源](https://www.technologyreview.com/2020/10/16/1010566/ai-machine-learning-with-tiny-data/))

## 不仅仅是理论

该论文用 kNN(k-最近邻)方法证明了这一概念，该方法在图形方法中通过沿着特征轴的可分离平面对对象进行分类。通过创建微小的合成数据集，加上精心设计的软标签，kNN 算法能够检测到比数据点更多的类别。

[](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) [## 机器学习和人工智能如何改变电子商务的面貌？|数据驱动…

### 电子商务开发公司，现在，整合先进的客户体验到一个新的水平…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) 

## 限制

虽然这种方法非常适用于可视的、可解释的 kNN 算法，但这种方法可能不适用于复杂和不透明的神经网络。

前一个“数据提炼”的例子也不适用，因为它要求您从一个非常大的数据集开始。

## 暗示

这项研究不仅令人着迷，还对人工智能行业具有重要意义，即减少数据需求。

密集的数据需求使得训练人工智能模型极其昂贵。例如，GPT-3 的训练成本超过了[400 万美元](https://bdtechtalks.com/2020/08/17/openai-gpt-3-commercial-ai/#:~:text=According%20to%20one%20estimate%2C%20training,increase%20the%20cost%20several%2Dfold.)。也有人担心推论，或者用模型做预测，对于研究人员来说[太昂贵了。这更多地反映了 GPT-3 的极端规模和计算要求，一个 1750 亿参数模型，而不是其他任何东西。](https://syncedreview.com/2020/09/04/is-openais-gpt-3-api-beta-pricing-too-rich-for-researchers/)

当前最先进模型的现状是在尽可能多的数据上训练。语言模型 GPT-3 将这一点发挥到了极致，在几乎整个互联网上进行训练。

随着新的 LO-Shot 学习突破，有一天可能只用几个数据点就能完成 SOTA，从而产生极其轻量级和高效的模型。

总之，*最常见的*人工智能应用不需要大数据。此外，传统上需要大数据的任务，如自然语言处理和物体检测，正在看到能够使用微小数据集的进步。

## 获得专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)