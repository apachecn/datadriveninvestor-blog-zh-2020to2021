# 谷歌研究人员是如何在使用较少资源的情况下击败 ImageNet 的？

> 原文：<https://medium.datadriveninvestor.com/how-did-google-researchers-beat-imagenet-while-using-fewer-resources-267243071ee4?source=collection_archive---------4----------------------->

## 他们发明了新模型吗？请继续阅读…

为了帮助我了解您[请填写此调查(匿名)](https://forms.gle/7MfQmKhEhyBTMDUD7)

图像分类算法主要通过使用更多的资源(数据、计算能力和时间)而变得更好。最好的算法使用额外的**35 亿张标签图像。** [本文](https://arxiv.org/abs/1911.04252)，由谢启哲等人撰写。它能够击败当前的算法，同时仅使用*额外的 **300 M 未标记图像**(两种算法都使用相同的标记图像数据集，在其上我们分别有额外的 3.5 B 和 300 M 图像)**。**这意味着新方法使用了 **12 倍于**的较小图像，同时也不需要对这些图像进行标记。因此，它便宜很多很多倍，但效果更好。*

## 这个团队有什么不同？

要理解这篇论文和实验设置，请观看这个视频。

![](img/d197b3b48b52d8ceb29c5a88ca5f7543.png)

An illustration from the paper showing how they trained their models

从表面上看，他们的方法似乎是标准的 SSL。他们优异表现的关键在于训练前和训练中采取的步骤。无标签学生模型比老师大。该团队还将**不同类型的噪声**注入到数据和模型中，*确保每个学生比他们的老师学到更多类型的数据分布*。这与迭代训练相结合特别有效，因为这利用了不断提高的教师。

![](img/8b3fddbc28ac0951ca1414434acf1dab.png)

Noisy Student uses lesser extra Data still outperforms. Looks like ResNet was ended.

## 关于那噪音

由于我们已经在本次培训中确立了噪音的重要性，所以了解不同种类的噪音也很重要。有两大类噪声可以实现。**模型噪音**是指在训练过程中对模型进行干扰。这可以防止过度拟合，并通过允许模型从不同的“角度”评估数据，实际上可能会提高准确性和稳健性。另一种称为**输入噪声**，在这种情况下，您会向输入端注入噪声。研究人员特别使用 RandAugment 来实现这一点。这有两个目的，一是增加数据的多样性，二是提高预测的准确性(特别是对于真实世界的数据，这是非常嘈杂的)。

![](img/9b2038f651ceda1324d257167c2fc765.png)

Real Picture of the researchers in this paper

## 图表 1:输入噪声的随机增大

![](img/62a89f01f50e3001f42b66973ab2eccb.png)

The GOAT at work

世界上有一些非常复杂的噪声函数。RandAugment 不在其中。不过不要被愚弄了，这是最有效的算法之一。它以一种非常容易理解的方式工作。想象一下，有 N 种方法可以扭曲一幅图像。这可以是任何事情，从改变一些像素为白色，到沿轴剪切。RandAugment 采用 2 个输入(n，m ),其中 n 是应用的失真数量，m 是失真的幅度。它返回最终图像。失真是随机应用的，通过增加可变性来增加噪声。

在该图中，我们看到 RandAugment 在不同的幅度下仅应用了两个(固定的)变换。这三个样本已经非常不同了。不需要天才就能算出通过改变多个图像的两个值可以得到多少(答案:很多)。不应忽视数据扩充。这也确保了学生模型总是至少和老师一样大，因此需要更少

## 附件 2:模型噪声的损失

辍学是一个过程中使用的神经网络等。它的过程非常容易描述:每次运行网络时忽略一些神经元。图片:

![](img/271f29855451434f956c71d7870a3a4c.png)

Standard DropOut Procedure

应用放弃是因为它停止过度拟合。通过忽略不同的单位，你改变了输出。反馈使它能够更好地概括。此外，可以实现 dropout 来创建来自一个网络的迷你学习者列表。通过集成，迷你学习者可以胜过父网络。

![](img/1bb41fbada73c5e0beb13774efa075b6.png)

The Mini-learner Ensemble to the parent network

## 附件 3:模型噪声的随机深度

坦率地说，我对这个概念不是很熟悉。但是，嘿，这就是谷歌的目的。对此进行解读是令人惊讶的。这可能是整篇论文中我最喜欢的东西。如果我必须重新开始只有一个记忆的生活，这将是它。现在我们已经建立了宣传…

随机深度包括以下步骤。

1.  从非常深的网络开始
2.  在训练期间，对于每个小批量，随机丢弃一个层子集，并使用 identity 函数绕过它们。
3.  重复(如果需要)

![](img/704399f89e75a37749754f5f2b812d31.png)

Since we love visualizations

这似乎非常类似于辍学。在某种程度上的确如此。可以把它想象成深度网络的放大版。但是，确实有效。*“它大大减少了训练时间，并显著改善了我们用于评估的几乎所有数据集的测试误差。利用随机深度，我们可以增加剩余网络的深度，甚至超过 1200 层，并且仍然可以在测试误差方面产生有意义的改进(在 CIFAR-10 上为 4.91 %)。”这一点我不能否认。将很快对此进行深入研究。现在，看看这个图的绘图错误:*

![](img/7d393be7abff86461ae5efbb8631a4dc.png)

See that Billy? That is Peak Performance

这三种噪音都以独特的方式对训练有所贡献。这三种方法都通过增加输入的变化来增加预测的稳健性。这是它在健壮性方面区别于所有其他先进模型的地方。事实上，它们非常有效，即使没有迭代训练过程，该过程也能够改进当前的网络技术水平(更多细节请见第 2 部分)。

![](img/cce19a4f9a22f34b362f10c7b7b427d3.png)

Just applying noise has consistent improvements.

# 培训过程

现在我们已经了解了不同的步骤和调整是如何改进分类的，我们应该研究一些实现细节。

![](img/9c8d7f5d688a1e93c9d6b79f73a51750.png)

对我来说，训练中最重要的部分是第三步。研究人员表示*“具体来说，在我们的方法中，教师通过读取干净的图像来产生高质量的伪标签，而* ***学生需要复制那些带有增强图像的标签作为输入*** *。”正如我们所见，给图像(或模型)添加噪声会极大地改变它们的外观。通过强迫学生使用增强图像，它允许模型以很高的准确性预测非常不清晰的图像。这方面的细节将在第 2 部分。但是现在，这里有一个例子来说明这对于预测模糊图像是多么重要。*

![](img/5e282ccfe17fea8cea5a41a9941e13c4.png)

Take my money already, you beautiful model

# 后续步骤

请在下面留下您对这篇文章的反馈。如果这对你有用，请分享并跟我来这里。

查看我在 Medium 上的其他文章。:[https://rb.gy/zn1aiu](https://rb.gy/oaojch)

我的 YouTube。这是一个正在进行中的工作哈哈:[https://rb.gy/88iwdd](https://rb.gy/88iwdd)

在 LinkedIn 上联系我。我们来连线:[https://rb.gy/m5ok2y](https://rb.gy/m5ok2y)

我的推特:[https://twitter.com/Machine01776819](https://twitter.com/Machine01776819)

我的子任务:[https://devanshacc.substack.com/](https://devanshacc.substack.com/)

如果你想和我一起工作，请发邮件给我:devanshverma425@gmail.com

twitch 现场对话:[https://rb.gy/zlhk9y](https://rb.gy/zlhk9y)

获取我的内容更新-insta gram:[https://rb.gy/gmvuy9](https://rb.gy/gmvuy9)

获得罗宾汉的免费股票:[https://join.robinhood.com/fnud75](https://www.youtube.com/redirect?redir_token=QUFFLUhqa0xDdC1jTW9nSU91WXlCSFhEVkJ0emJvN1FaUXxBQ3Jtc0ttWkRObUdfem1DZzIyZElfcXVZNGlVNE1xSUc4aVhSVkxBVGtHMWpmei1lWWVKNzlDUXVJR24ydHBtWG1PSXNaMlBMWDQycnlIVXNMYjJZWjdXcHNZQWNnaFBnQUhCV2dNVERQajFLTTVNMV9NVnA3UQ%3D%3D&q=https%3A%2F%2Fjoin.robinhood.com%2Ffnud75&v=WAYRtSj0ces&event=video_description)

这是承诺的文件。请务必下载并阅读它，因为我已经定义了重要的定义并强调了关键部分。这会帮助你更好地理解这篇论文。