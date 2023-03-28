# 将 BatchNorm 视为理所当然

> 原文：<https://medium.datadriveninvestor.com/taking-batchnorm-for-granted-a672effbc2ad?source=collection_archive---------8----------------------->

为什么我们会忽略神经网络中某些层的魔力，以及如何更好地理解它们+来自一篇极其有趣的论文的 9 个要点。

![](img/91f719cfee97e53b63efa0de9a27d5c2.png)

A batch of flowers ([https://www.pinterest.com/pin/834503005944030902/?nic_v2=1aaBt7TUy](https://www.pinterest.com/pin/834503005944030902/?nic_v2=1aaBt7TUy))

批范数是神经网络中使用最广泛的层之一。自从它问世以来，训练更快、更准确、更抗变化的神经网络成为可能。听起来很神奇，不是吗？你可能会想，对于如此神奇的东西，实现起来一定非常困难。(你可能错了)

事实是，由于神经网络的黑盒性质，我们开始认为这种魔力是理所当然的。当然，关于它如何以及为什么会有这样的效果，有许多假设，但是我最近发现了一篇[论文](https://arxiv.org/abs/2003.00152)，它做出了**认真**的尝试去理解它。

# 什么是批量定额

在我们开始做任何事情之前，先快速了解一下批处理规范。
我们为什么需要它？标准化网络输入。这将允许网络“聚焦”并从数字上了解什么更重要。
现在，它看起来如何(注意，这些是组件，而不是整个实现)

这里我们首先生成一个随机数组。输入γ、β是可学习的参数，我们将在后面研究。ϵ是一个很小的数字，它会阻止我们的值变成 0。我们首先取平均值，然后取方差，然后用它们来标准化数据。最后，我们取一个乘积，用参数求和。

现在，考虑随机数组是一批数据，我们将它应用于整批数据，而不是单个平均值，我们取一个移动平均值。(也称为基于流数据的连续变化值)。大概就是这样。

# 火车！！

![](img/63e1069351adfaef350bdae5c601db08.png)

[Train](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.merriam-webster.com%2Fwords-at-play%2Fthe-history-of-the-word-train&psig=AOvVaw38n5cRpT5J_NpyiHo4QAmM&ust=1601922053977000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCJCz3-vGm-wCFQAAAAAdAAAAABAD) xD

好的，这一段会在 Pytorch。我会试着解释我所做的一切，但我不能在这里粘贴完整的代码，因为这会变得太大。因此，我将在这里展示与标准培训的不同之处。

完整的代码(带注释)可以在[我的资源库](https://github.com/SubhadityaMukherjee/pytorchTutorialRepo/tree/master/BatchnormOnlyBatchnorm)中找到

所以我们的主要工作流程和其他深度学习项目一样。

1.  加载数据(检查 main.py)
2.  对其进行预处理(检查 main.py)
3.  枚举批次
4.  优化损失函数
5.  测试一下

[](https://www.datadriveninvestor.com/2020/06/24/disclosure-and-resolution-program-wont-prevent-physicians-from-practicing-defensive-medicine/) [## 人工智能、深度学习和医疗实践|数据驱动的投资者

### 人工智能和深度神经学习的效用看起来可能是合法和有前途的，特别是…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/06/24/disclosure-and-resolution-program-wont-prevent-physicians-from-practicing-defensive-medicine/) 

# 密码

让我们首先得到我们需要的图书馆。又名 PyTorch 和 tqdm(这是一个非常小的进度条助手，我非常喜欢)

```
import torch
import torch.nn as nn
import torch.nn.functional as F
from tqdm import tqdm
```

在我们考虑下一步之前，让我们先试着了解我们想要什么。我们需要像往常一样训练网络，但是要确保**只训练**batch norm 层。只是想看看我们能把它拉长到什么程度。

要做到这一点，让我们创建一个函数，通过我们的整个模型，如果它发现任何层不是 batchnorm，它会告诉 pytorch 忘记该层的梯度。在此过程中，确保只对 Batchnorm 层进行培训。为此，我们冻结了权重和偏见。

```
def freezeOthers(m):
    for param in m.parameters():
        if not isinstance(m, torch.nn.modules.batchnorm._BatchNorm):
            if hasattr(m, 'weight') and m.weight is not None:
                m.weight.requires_grad_(False)
            if hasattr(m, 'bias') and m.bias is not None:
                m.bias.requires_grad_(False)
```

现在是主要的训练循环。我们首先使模型可训练，并将其发送到 GPU。然后我们迭代数据。按照 PyTorch 标准循环，我们重置梯度，并通过我们的模型传递批次。我们执行反向传播并逐步通过我们的优化器。然后我们应用之前的函数。在此之后，我们的模型将忘记每隔一层的梯度。我们还添加了一个小选项来打印当前的损失。(这有助于你观察列车)

# 那是怎么做到的？

嗯，我在 CIFAR 10 数据集上测试了 ResNet110，对于普通网络，我得到了大约 92%的测试准确率。在只训练 BatchNorm 的时候，我达到了大约 68%的测试准确率。现在你可能会想，这太遥远了。是的，它是..但是请注意，我们只使用了大约 0.48%的数据[城市 1](https://arxiv.org/abs/2003.00152)

哇…

# 不要把 BatchNorm 视为理所当然

现在我们对这些层的表达能力有了更多的了解。让我分享一些我从[论文](https://arxiv.org/abs/2003.00152)中发现的非常有趣的观点。

1.  BatchNorm 学习禁用网络中的特征，这允许它很好地学习并对特征施加稀疏度
2.  图层中的仿射参数(执行某种变换的参数)起着非常重要的作用
3.  该层帮助网络学习更好的表示
4.  随机特征在神经网络中起着重要的作用，到了我们还没有完全理解的程度。
5.  将 BatchNorm 放在激活之前可以获得更好的性能
6.  如果我们只训练层，增加深度会比增加宽度得到更好的结果
7.  可以移除网络中的许多要素，而不会对值产生太大影响
8.  ResNets 中的快捷连接实际上可能会降低性能，因为它们无法正确使用 BatchNorm

# 停业清理

到现在为止，我想我们开始意识到，也许我们不应该把我们认为我们知道的视为理所当然。有时候，要理解一篇论文是很困难的。BatchNorm 在网络中确实扮演着重要的角色。这在某种程度上证明了我们需要能够挖掘神经网络架构的结构和黑盒。

# 参考

*   [引用 1:原始论文](https://arxiv.org/abs/2003.00152)。Jonathan Frankle 等人(是的，我在文章中多次引用这一点，因为这样更容易识别)
*   [阿尔瓦罗·杜兰](https://medium.com/deeplearningmadeeasy/everything-you-wish-to-know-about-batchnorm-6055e07fdce2)
*   [蝙蝠纸](https://arxiv.org/pdf/1502.03167.pdf)
*   Sayak Paul 的博客文章如前所述
*   【pytorch 论坛的链接

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)