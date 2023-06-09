# 生成对抗网络及其对自动化的影响

> 原文：<https://medium.datadriveninvestor.com/generative-adversarial-network-and-its-impact-on-automation-39b9659f47ac?source=collection_archive---------8----------------------->

拉斯马尼拉德洛斯桑托斯

# **什么是甘？**

一个**生成对抗网络** (GAN)是一个深度学习网络，它使两个神经网络相互对抗(*因此，单词‘对抗’*)，以获得一个可以生成模拟现实生活对象的数据的模型。

GAN 被认为是机器学习领域出现的最有趣的想法，因此，在过去的几年里，越来越多的 GAN 用例出现。然而，它的影响在积极和消极之间大大缩小，成为一把双刃剑。一方面，你可以使用 GAN 生成逼真的图像和演讲，但另一方面，它主要用于创建假的演讲和视频，俗称 **deepfakes** 。

![](img/40e337455fc8889a1e200082c2162753.png)

# **生成网络与判别网络**

gan 主要由两个相互竞争的网络组成——生成网络和鉴别网络。为了进一步理解这两个网络的概念，让我们假设一个文本分类的用例，它有两个类，分别叫做 *spam* 和 *ham* 。

对于判别模型，给定 x 个特征，给定 y 的概率， **P(y|x)** 。在我们的用例中，我们尝试在给定训练数据的特征 x 的情况下，获得一个*垃圾邮件*或一个*垃圾邮件*的概率。我们在给定输入的特征的情况下预测输出。

[](https://www.datadriveninvestor.com/2020/02/27/how-to-use-automation-to-get-more-out-of-your-data/) [## 如何使用自动化从您的数据中获得更多价值？数据驱动的投资者

### 去年的新闻故事不停地谈论机器学习变得多么先进。电脑现在…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/27/how-to-use-automation-to-get-more-out-of-your-data/) 

这与生成模型截然相反，因为它是关于预测获得输出 y 所需的一组特征 x。在这种情况下，我们试图在给定 y 的情况下获得 x 的概率， **P(x|y)。**这就是模型生成的原因。对于我们的用例，给定一个*垃圾邮件*类别，生成模型将尝试生成能够创建垃圾邮件文本的特征，就像我们许多人过去在电子邮件中收到的那样。这些特征可以是语法、文本中需要的单词集等等。

# **关于自动化**

尽管成功集成了 GAN 功能的 [**机器人过程自动化**](https://blog.raxsuite.com/best-automation-practices-to-be-ready-for-the-future-of-work/) (RPA)产品有限，但自动化部门仍有几个 GAN 的应用和研究领域。

一个很好的例子是自然语言处理领域。一个好的 GAN 可以使用训练好的数据集独立地生成文本。事实上，OpenAI 发布了一项关于该应用的研究，名为“*语言模型是无监督的多任务学习者，*”，他们训练了一个无监督的模型，以根据输入文本生成连贯的段落。如果该模型可以在 RPA 工具中用作电子邮件回复机器人或聊天机器人，那该有多酷？一旦 GANs 被成功地整合到自动化产品中，电子邮件服务现在就可以不受帮助了，因为人工智能可以理解接收到的电子邮件的上下文，因此至少可以适当地或用更多的上下文来响应。

![](img/d46736a5e7c360ae3b5bc773211f11ee.png)

*A snippet of the Q&A model using GAN available at the OpenAI website (*[*https://openai.com/blog/better-language-models/*](https://openai.com/blog/better-language-models/)*)*

GANs 在自动化中的另一个好用途与计算机视觉有关。2019 年，一项使用 GAN 进行文档清理的提案发表 *(Sharma，et al.* )扫描的文档有时会有打印、水印或噪声，这些会影响扫描质量，从而使 [**光学字符识别**](https://medium.com/datadriveninvestor/why-ocr-93c898bb0cb4) (OCR)引擎更难识别字符。有了这样的扫描图像作为输入，GAN 现在可以生成一个无噪声的版本，留下重要的字符准备用于图像识别工作流。

![](img/9e9e6e6dde1ff50b2b54685d38f2f135.png)

*An image cleaned by GAN presented in the paper of Sharma, et al (*[*https://arxiv.org/pdf/1901.11382.pdf*](https://arxiv.org/pdf/1901.11382.pdf)*)*

**立即获得免费的机器人过程自动化(RPA)软件！** [下载这里](https://www.raxsuite.com/freedownload?utm_source=Medium%20Post&utm_medium=medium&utm_campaign=medium_footer)

来源:

[](https://openai.com/blog/better-language-models/) [## 更好的语言模型及其含义

### 我们已经训练了一个大规模的无监督语言模型，它可以生成连贯的文本段落，实现…

openai.com](https://openai.com/blog/better-language-models/) [](https://pathmind.com/wiki/generative-adversarial-network-gan) [## 生成对抗网络初学者指南

### 你可能不认为程序员是艺术家，但编程是一个极具创造性的职业。这是基于逻辑的…

pathmind.com](https://pathmind.com/wiki/generative-adversarial-network-gan)