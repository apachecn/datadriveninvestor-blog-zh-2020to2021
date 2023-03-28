# Pytorch:通往数据科学家的必经之路

> 原文：<https://medium.datadriveninvestor.com/pytorch-must-to-learn-on-the-path-to-data-scientist-d59b0e2b48b5?source=collection_archive---------9----------------------->

## 了解这个库，成为优秀的数据科学家

ytorch 是众所周知的开源库，可用于构建神经网络和自然语言处理解决方案。与其他库相比，这个库有很多优点，但最明显的一个是内部处理的变化，最后，在跨向量执行的评估中实现了更快的执行。换句话说，它强调以尽可能好的方式更快地处理大量数字。

> Pytorch:开源库+ NLP +更快的处理/执行

![](img/3d639c1e15445bb118fd9d2355b39fee.png)

Another Library with advanced features and flexibility

与 tensorflow 相比，它拥有所有副本库，能够以相似的容量和更快的执行速度执行。它具有与 numpy 类似的能力，并具有在 Cuda 环境/ GPU 上执行的额外能力。

让我们以 Pytorch 与 numpy 的相似性为例:

**创建数组**
py torch:torch . sensor(<<Array>>)
Numpy:NP . Array(<<Array>>)
**Dot Product**
py torch:torch . matmul(a，b)
Numpy : np.dot(a，b)
**创建单位矩阵**
Pytorch : torch

Numpy 和 Pytorch 有类似的命令来计算和执行给定数组上的不同事情。这使得 pytorch 覆盖了 numpy，并增加了性能改进和更高级的特性。

## **深度学习基础知识**

在我们进一步深入之前，访问深度学习基础知识很重要。从提取问题陈述到问题解决方案，深度学习已经有了既定的步骤。同样，在训练模型和根据给定数据获得最佳模型以更好地进行概括时，也有一些步骤。

下面是训练模型的常规深度学习步骤:
1。初始化权重向量
对于 NLP 问题中初始化权重向量，我们可以应用随机权重、一次热编码或预训练嵌入。

2.正向传播:
这在使用深度学习训练任何模型时都很常见。顾名思义，我们对给定的数据进行进一步的加权处理。并且，达成解决方案。重要的步骤是:点积，适用于点积和激活函数，重复这两个步骤，直到你达到你的预测阶段。

3.计算损失
定义损失函数，并根据正向传播给出的预测和实际预期值计算损失。一些重要的例子是:L1(MAE)、MSE、CE

4.反向传播
这是每一次深度学习训练的重要步骤。在这一步中，基于损失率和偏导数，它将设置新的权重。至少，我们可以说，在每一步，我们都在向 w.r.t .问题陈述靠拢。这有助于设置权重，所以我们可以说随机定义权重将在这里标准化，问题在我们的控制之下。我希望在第一步中随机选择权重不会影响我们的模型更好地训练是有意义的。在数学术语中，我们在这里应用链规则来获得新的权重。

5.应用优化器:
这是我们将利用上述内容并设置新权重来重复向前传播的步骤的步骤。并且，公式是:新权重=旧权重-导数率*学习率
这也可以称为德尔塔法则。这些都是流行语，但重要的是，我们应该知道的概念和基本知识。名称可能会随着时间的推移而改变，但不管问题陈述如何，这些步骤都应该是相同的。

以上步骤反复运行，以获得解决您的问题陈述所需的模型。由此可见，正确的数据、正确的激活函数和损失函数是模型训练的核心。如果您能够正确选择它们，您的模型将能够更好地概括测试数据。

让我们回顾一下 Pytorch 编程的一些基础知识，感受一下我们的学习和理解。这也有助于了解这个图书馆的重要性。

```
#import torch as below commands and it shows what are the other things already inbuilt like nn, tensor, optimizer etc. # do install torch using pip install torch
import torch
from torch import nn
from torch import tensor
from torch import optim
```

使用上面导入的库的示例顺序模型定义

```
# Simple model definition to use feed forward network 
# here we assume hidden_dim is set as any numeric value, input dimensions are input features and output dim are depended variablesmodel = nn.Sequential(
            # this is for setting up perceptron
            nn.Linear(input_dim, hidden_dim),
            # activation fuction as sigmoid
            nn.Sigmoid(),
            # second layer defined 
            nn.Linear(hidden_dim, output_dim),
            # activation function 
            nn.Sigmoid()
        )
```

用一行隐藏层定义模型看起来是多么容易。这就是你在使用 torch 时所期望的简单性和灵活性。现在，让我们定义优化器

```
# model parameters are passed as first parameter 
# learning rate can be defined by us as variable in numeric value i.e, 0.001 or so
optimizer = optim.SGD(model.parameters(), learning_rate)
```

在这里我们可以看到，我们能够初始化优化器，一旦损失函数也被初始化，一切就都设置好了。

```
# MSE is used for loss function 
# nn is coming from the import section which is equivalent to torch.nn
lossFunction = nn.MSELoss()
```

现在，使用上述初始化来训练模型的时候到了。另一件重要的事情是在模型的训练中，即纪元。简单来说，当你在训练模型时，你需要有结束时间。你想要达到的可能是迭代或者模型的准确性。这有两个原因。首先，您将定义想要迭代的次数，并获得训练好的模型。第二，您将定义最大次数，但您将保留一个条件，以便在您认为您的模式能够更好地收敛时中断迭代。

最后，您可以有一种方法，它将应用这种理解，但它将保存超出您的预期精度或收敛模型的条件集的模型。我希望它能让我们很好地理解训练模型。

> epochs 是对训练数据集执行训练以达到最终模型的次数。如果整个数据集是批量大小，那么 epochs 就是迭代次数。

```
for _ in range(<epochs>):
    # Every epoch initializing the values 
    optimizer.zero_grad() 
    # Step 2: Foward Propagation using input as X
    predictions = model(X)

    # Step 3: Back Propagation 
    # Calculating the loss using the loss function initialized earlier    # Here, Y is actual prediction
    loss = lossFunction(predictions, Y)
    # back propagating based on the loss got from the above step
    loss.backward()

    # Step 4: Optimizing steps to update the weights
    optimizer.step()
```

就是这样，我们在这里很好，因为我们能够初始化我们的模型，损失函数和优化器。最后，我们为历元定义一些数值，并按照上面讨论的步骤训练模型。

## 结论

我们已经讨论了 pytorch 与 numpy 的相似性。然后，我们通过编码示例来学习更多关于 pytorch 的知识。我们还讨论了训练模型所需的步骤，然后使用 torch 为顺序模型实现相同的步骤非常简单，并鼓励学习更多内容。总的来说，pytorch 是一个具有许多特性的库，可以很容易地应用于给定的数据集。而且，它有直接的方法，可以灵活地实现正常情况下可能需要键入许多命令的功能。pytorch 的另一个优点是它兼容 gpu 训练，这使它在其他库的比较中脱颖而出。所有的内置功能和承诺的处理速度使它成为一个完整的库，以解决您的问题陈述。Tensorflow 是另一个可用于相同处理的库。再次强调，这完全取决于您的实践和对库的熟悉程度。在我看来，理解和实现神经网络是必须学习的库。我希望我能让你的学习离 Pytorch 更近一步。**快乐学习编码！**