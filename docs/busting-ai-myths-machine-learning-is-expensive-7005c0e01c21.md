# 打破人工智能神话:“机器学习很昂贵”

> 原文：<https://medium.datadriveninvestor.com/busting-ai-myths-machine-learning-is-expensive-7005c0e01c21?source=collection_archive---------3----------------------->

## 真相。

![](img/6b2cc50e3359337d3c4cc3234ed8be0e.png)

Photo by [rupixen.com](https://unsplash.com/@rupixen?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

无数文章谴责机器学习模型的“惊人”成本。

然而，这些说法具有误导性，因为它们主要着眼于训练最先进的深度学习模型的成本，如 OpenAI 的 GPT-3。

GPT-3 只训练过一次，就永远改变了这个行业。现在，全世界成千上万的研究人员和企业家都在使用它。考虑到这一点，突然之间，400 万美元的培训预算听起来就不那么惊人了。

# 训练模型可能很贵，但使用它们并不贵

事实上，*推论*，或者简单地用机器学习模型进行预测，是非常便宜的，几乎是免费的。这是因为计算已经取得了长足的进步，芯片每秒可以进行数十亿次，甚至数万亿次 T4 运算。

使用 CPU [的双层神经网络进行预测的成本](https://www.researchgate.net/publication/335373358_Benchmarking_Keyword_Spotting_Efficiency_on_Neuromorphic_Hardware)约为 0.0063 焦耳，或 0.00000000175 千瓦时。使用神经形态计算硬件，成本下降到 0.00027 焦耳，或 0.00000000075 千瓦时(即 10 个零)。

同时，中央空调平均每小时每吨使用 1 度电。这相当于用一个小型神经网络做出 13.3̅3̅3 十亿次预测。

# 甚至 GPT-3 推论也是廉价的

当然，GPT-3 不是一个小的神经网络。这可能是有史以来最大的神经网络。即便如此，截至发稿时，GPT-3 最昂贵的引擎每 1000 个代币的价格为 0.06 美元，或每枚代币 0.00006 美元(千分之六便士)。最便宜和最快的引擎 ada 每 1000 个令牌的成本仅为 0.0008 美元，即每个令牌 0.0000008 美元。

我们可以假设这一成本不仅仅包括电费。你可能要支付 OpenAI 的 120 多名员工的工资，他们的办公室，税收和其他费用。即便如此，单个预测也便宜得惊人。

我在 GPT 三中的操场上举了一个例子:

```
The following is a list of companies and the categories they fall intoFacebook: Social media, Technology
LinkedIn: Social media, Technology, Enterprise, Careers
FedEx: **Shipping, Transportation**
```

最后一部分，用粗体显示的，是 GPT-3 的 ada 引擎所预测的。转到`Usage`选项卡，我可以看到我对 ada 的 1 个请求，花费了 41 个令牌(37 个提示+ 4 个完成)。

让我们来计算一下成本:

```
41 * $0.0000008 = $0.0000328
```

换句话说，一个推论甚至没有接近一分钱。

不完全是“惊人”

[](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) [## 机器学习和人工智能如何改变电子商务的面貌？|数据驱动…

### 电子商务开发公司，现在，整合先进的客户体验到一个新的水平…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) 

# 正常的模特培训也很便宜

在许多方面，称机器学习模型训练昂贵，并引用 GPT-3，是不真诚的。

![](img/bbd0fe43f12704fccb197255f3d35d80.png)

[“‘The Rent is Too Damn High Party says if you want to marry a shoe, I’ll marry her.’ #nygov”](https://www.flickr.com/photos/8490404@N08/5094726339) by [MikeWren](https://www.flickr.com/photos/8490404@N08) is licensed under [CC BY-NC 2.0](https://creativecommons.org/licenses/by-nc/2.0/?ref=ccsearch&atype=rich)

这就像说“租金太高了！”，然后引用情人的深海豪华海底酒店——每晚 15 万美元——作为你观点的证据。

事实上，你甚至可以用 Google Colab 这样的工具免费训练相当强大的人工智能模型。

显然，即使没有钱*或*技术技能，你也可以使用像[这样的无代码人工智能工具，廉价而轻松地部署人工智能模型。AI](http://obviously.ai) 。

# 摘要

总之，训练世界上最大的神经网络，GPT-3，看起来很昂贵，而且没有成为行业游戏规则改变者的前景。

实际上，使用这些模型是非常便宜的，使用典型的模型，训练和预测都是非常便宜的。

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)