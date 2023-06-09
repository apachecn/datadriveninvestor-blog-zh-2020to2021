# 在车道检测中实现 U-Net

> 原文：<https://medium.datadriveninvestor.com/using-u-net-in-lane-detection-343bc7b08c2b?source=collection_archive---------3----------------------->

> 本文期望您了解卷积神经网络如何工作的基础知识，并对深度学习有很好的理解。如果你没有很好的理解，将这篇文章加入书签，阅读[这篇文章](https://medium.com/datadriveninvestor/how-you-can-figure-out-your-teachers-age-without-embarrassing-yourself-f4f4363113d6)和[这篇文章](https://medium.com/analytics-vidhya/the-ultimate-ai-textbook-dc2cf5dfe755)。

车道检测可能是自动驾驶汽车最令人兴奋的任务之一。本文讲述了我如何使用 U-Net 模型和自定义损失+度量函数(如 dice 系数和聚焦 tversky 损失)完全从头开始构建车道检测模型。所有的代码都可以在[这里](https://github.com/srianumakonda/Lane-Detection)找到。如果你想联系我，请通过推特[联系我](https://twitter.com/srianumakonda)。

# 资料组

该数据集取自 Kaggle 上托马斯·费米的“卡拉驾驶模拟器的车道检测”数据集。它最初是为自动驾驶课程的[算法创建的，但费米已经在 Kaggle 上发布了数据集。看一下数据集](https://thomasfermi.github.io/Algorithms-for-Automated-Driving/Introduction/intro.html)[这里](https://www.kaggle.com/thomasfermi/lane-detection-for-carla-driving-simulator)。

数据集最初由训练和验证文件夹组成。训练数据集由 3075 个文件组成，验证集由 129 个文件组成。由于模型无法成功地在这方面进行训练，我使用 PIL 通过以 5 度的间隔旋转图像，水平和垂直翻转来执行数据增强，我还尝试了改变阈值。例如，如果我将值设置为 150，那么小于 150 的每个像素值都将被设置为 0。我在玩这种增强，看看去掉这种“噪音”后会有多大的不同。

我的一些结论是，消除这些噪音确实会导致骰子点数的增加，但这种增加是非常微小的。损失从 0.8937(没有降噪)上升到 0.8951。我决定继续下去，在没有“降噪技术”的情况下训练数据模型，因为白线并不总是在 255。

我把图像的最大旋转角度设为 25 度。我让阈值保持原样。我还添加了 0.2 的验证分割。在数据扩充之后，我已经生成了 23376 幅训练图像、1224 幅验证图像和 1032 幅测试图像。

# 模型

我使用了 Ronneberger 等人在 2015 年创建的 U-Net 模型，该模型最初用作生物医学图像分割的目的。该模型通过转置卷积利用跳过连接和上采样。它遵循一个编码器-解码器神经网络结构，我们传入一个输入图像并得到一个图像输出。请看下图，获得模型架构的可视化。

![](img/342f2c88bc2f14bea027a44026df8a50.png)

现在你可能明白为什么这个模型被称为 U-Net 模型了。在对输入图像执行卷积和下采样以提取越来越多的特征供模型学习之后，它接着对其进行上采样以生成新的图像。

我敢打赌，你根本不知道为什么我会首先增加样本，而不是通过基本的 CNN 运行模型。语义分割的目标是在给定输入图像的情况下生成新的输出图像。卷积神经网络返回给定图像的输出标签。例如，如果我正在进行二进制分类，我将得到一个输出标签 0 或 1(或基于激活函数的概率)。

在语义分割的情况下，模型的输出应该是图像。车道线所在的模型的图像。

![](img/034ba55b3924a7c12bb6cdba6cc739d1.png)

下面是一个功能和标签的示例。输入图像是车道线，右边的图像是输出特征，这是另一幅图像，其中车道线是白色的，其他都是黑色的。这是我们的模型输出应该实现的一个例子。

这可以通过转置卷积来实现。当我们对图像进行卷积和下采样时，我们提取特征并从图像中学习。现在我们要做的是，一旦我们提取了输入图像的关键特征，我们就要生成与输入图像相关联的输出图像。这可以通过转置卷积来实现。

![](img/e3a64eeab2920375a9e52ee45324aee5.png)

转置卷积的要点是输入较小的图像，我们将在一个特殊的核上执行图像的矩阵乘法。例如，我的向量为 1，因为较小的图像包含一个像素。然后，我们将这个向量乘以一个内核(我把它保持为 3x3，尽管你可以随意使用它)，输出值现在被附加到输出图像上。如果给我一张图片的一个像素，那么这个像素向量 1 就变成了一个 3x3 的矩阵。因此，我们能够仅通过使用内核的矩阵乘法来生成 9x 的像素。

由 Apache MXNet 撰写的这篇文章很好地解释了转置卷积。更多内容请访问[https://medium . com/Apache-mxnet/transposed-convolutions-explained-with-ms-excel-52d 13030 C7 E8](https://medium.com/apache-mxnet/transposed-convolutions-explained-with-ms-excel-52d13030c7e8)。

我们也可以使用跳过(剩余)连接。跳过连接是一种我们可以用来避免消失/爆炸梯度问题的方法，这主要是因为它们直接流经神经网络，而不必经过非线性激活函数。

该模型学习 U-Net 模型的前几层中的特征。当我们对图像进行上采样以生成最终输出时，我们会想要存储和使用该信息。如果我们没有使用跳过连接，模型需要上采样的信息就会丢失，或者太抽象而无法使用。

![](img/35540daa128bf5e2bbd4f34b3e6c14c0.png)

Notice how we concatenate F(x) → the second layer, with the input value X.

看一看[https://theaisummer.com/skip-connections/](https://theaisummer.com/skip-connections/)会有更好的理解。

# 替代解决方案

确实存在其他解决方案，例如使用霍夫变换来检测车道线。我会假设替代解决方案会比模型表现得更好，主要是因为它不涉及任何机器学习。相反，诸如霍夫变换的算法简单地分割图像，假设线的位置在中间。

我想玩玩增强，让车道线不在图像的中心，这就是为什么我决定在这种情况下执行语义分割。

# 韵律学

我使用了 dice 系数指标和一个自定义的损失函数，称为聚焦特沃斯基损失。

dice 系数损失的要旨是我用的是 2016 年 made Milletari 等人的 3D 医学图像分割。在 https://arxiv.org/pdf/1606.04797.pdf 的[阅读更多。](https://arxiv.org/pdf/1606.04797.pdf)

![](img/ff1a826f9848beb8a2b34869d436654b.png)

pi 和 gi 表示预测像素值和地面真实值。我们现在要做的是，把每一次 pi = gi 的和乘以 2。然后，将最终值除以预测值和实际值的总像素之和。

骰子点数的最大值将介于 0 和 1 之间。这提供了一种非常直接的方法来计算模型的损失，因为我们可以简单地做 1-D (dice coef)。相反，我选择了一个被称为聚焦特沃斯基损失的自定义损失函数，并使用我的度量标准 dice 系数。

我使用了由亚伯拉罕等人([https://arxiv.org/pdf/1810.07842.pdf](https://arxiv.org/pdf/1810.07842.pdf))引入的损失函数的定制变体，它是为语义分割而产生的。我不打算深入这篇文章，因为[罗宾·维诺德](https://medium.com/u/5e2c08907591?source=post_page-----343bc7b08c2b--------------------------------)在[这篇文章](https://towardsdatascience.com/dealing-with-class-imbalanced-image-datasets-1cbd17de76b5)中做了很好的解释。

# 结果

我已经让模型训练了大约 20 个时代。得到的最终分数是骰子系数分数 0.9 和聚焦特沃斯基损失分数 0.1。总的来说，这个模型表现很好，我认为对它进行更长时间的训练会带来更高的分数和更低的损失。

我还将这个模型放在 CARLAs 开源模拟器中进行了测试。下面的 gif 显示这个模型做得很好，但是更多的训练在某些情况下肯定会有帮助。

为低质量的视频道歉。因为该模型是在 128x128 的图像上训练的，所以图像的分辨率非常低，尤其是全屏显示时。

我也确实在知识社会上做了一个演讲。如果你想了解更多关于这个项目的信息，请随时给我发信息。

看看这里的代码([https://github.com/srianumakonda/Lane-Detection](https://github.com/srianumakonda/Lane-Detection))，如果你有任何反馈，请发送给 info@srianumakonda.com 或在 [twitter](https://twitter.com/srianumakonda) :)上给我发短信

点击这里订阅我的简讯[。](http://subscribepage.com/srianumakonda)