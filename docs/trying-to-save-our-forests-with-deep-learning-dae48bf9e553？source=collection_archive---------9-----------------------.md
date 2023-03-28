# 试图用深度学习拯救我们的森林

> 原文：<https://medium.datadriveninvestor.com/trying-to-save-our-forests-with-deep-learning-dae48bf9e553?source=collection_archive---------9----------------------->

![](img/b88ef58201f115beebf70fb014a79e34.png)

[Link](https://www.google.com/url?sa=i&url=https%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FFile%3ASad_Tree_In_A_Sad_Place_(248389635).jpeg&psig=AOvVaw1iiIL7f630GsqLQGdB9790&ust=1602599825041000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCJDFn92jr-wCFQAAAAAdAAAAABAD)

在过去的几个世纪里，文明发展迅速，但却是以环境为代价的。由于当前的形势和人类的贪婪，非法砍伐森林和狩猎正处于历史最高水平。我们能通过深度学习尽绵薄之力拯救我们的森林吗？试着识别是否有声音对应于伐木或射击的声音怎么样？

让我们看看如何使用 PyTorch 以简单易懂的方式实现这一点。

>这篇文章受到了[博客 1](https://blog.google/technology/ai/fight-against-illegal-deforestation-tensorflow/) 和[博客 2](https://medium.com/@aakash__/classifying-audio-using-pytorch-84861f3505ea) 的极大启发

# 目标

在我们进入任何代码之前，让我们试着更清楚地定义我们的问题。

我们试图辨别树木被砍伐的声音以及森林中的枪声。将不涉及硬件实现，而仅涉及神经网络方面。

# 流动

我们首先需要获取我们需要的声音数据集。这显然是训练我们的模型所需要的。为了获得所需的声音，我们可以很容易地在网上搜索，找到我们每个班级的大约 50 个。我不会提供数据集的链接，因为它很容易管理，我可能会在某个时候上传到谷歌。一旦我们有了数据集，我们将尝试对其进行预处理，使其适合我们的训练格式。然后，我们将创建一个数据加载器，通过它我们可以将数据批量传递给模型。我们还需要定义一个损失函数和一个适合我们情况的优化器。最后，我们需要训练我们的模型，也有一个功能，将允许我们测试我们的模型做得有多好。作为对这个主题的进一步解释，一些技巧以及制作更好的模型的方法将在最后讨论。

(注意:-整个代码相当长，因此本文只讨论了要点。一切都已经解释过了，但是把整个代码放在这里会浪费空间，所以你可以在这个[库](https://github.com/SubhadityaMukherjee/pytorchTutorialRepo/tree/master/AudioClassification)中找到它。)

# 数据加载器

我将假设我们有所需的数据。在本教程中，我将遵循 [8K 声音数据集的数据模式。](https://urbansounddataset.weebly.com/urbansound8k.html)这意味着数据被直接分成文件夹，并且有定义了标签的文件。请参考链接，以同样的方式格式化您的数据，或者使用本教程进行修改，以适应您的数据模式。

让我们先进口我们需要的一切。

```
 import torch

import torch.nn as nn

import torch.nn.functional as F

import torch.optim as optim

from torchvision import datasets, transforms

from torch.optim.lr_scheduler import StepLR

from tqdm import tqdm

import librosa

import numpy as np

from torch.utils.data import TensorDataset, DataLoader, random_split

import pandas as pd

import os
```

需要注意的最重要的事情是，我们打算使用一种叫做梅尔频率倒谱或 MFCC 的东西来转换我们的数据。这是一种声音处理技术，其中波的短期功率表示通过一种变换来传递，这种变换使其缩放并更易于处理。你可以把它想象成允许数据中巨大变化的表示接近人类听觉系统的反应。实际上，它使声音更接近我们所听到和理解的。我们使用一个名为 librosa 的库(pip install librosa 来获得它)来为我们执行转换。

```
def extract_mfcc(path):

    audio, sr = librosa.load(path)

    mfccs = librosa.feature.mfcc(audio, sr, n_mfcc=40)

    return np.mean(mfccs.T, axis=0)
```

现在我们有了一个定义这个变换的函数，我们就可以创建数据集了。我们在折叠中迭代数据，并且对于每个折叠，我们执行 MFCC。我们首先把这些都保存在数组中，然后转换成张量。因为我们可能有很多数据，所以我们将这些数据保存为。pt 文件，允许我们下次运行脚本时直接加载张量，而不必再次处理它。

```
# Making a custom dataset

features = []

labels = []

folds = []

print("[INFO] Making dataset")

for i in range(len(df)):

     fold = df["fold"].iloc[i]

     filename = df["slice_file_name"].iloc[i]

     path = "/home/eragon/Documents/datasets/Def/audio/fold{0}/{1}".format(

         fold, filename)

     mfccs = extract_mfcc(path)

     features.append(mfccs)

     folds.append(fold)
     labels.append(df["classID"].iloc[i])
features = torch.tensor(features)
labels = torch.tensor(labels)
folds = torch.tensor(folds)

print("[INFO] Done making dataset")

# Save to disk

torch.save(

features, "/home/eragon/Documents/datasets/Def/features_mfccs.pt")

torch.save(labels, "/home/eragon/Documents/datasets/Def/labels.pt")

torch.save(folds, "/home/eragon/Documents/datasets/Def/folds.pt")

# For the next time 

#features = torch.load("/home/eragon/Documents/datasets/Def/features_mfccs.pt")

#labels = torch.load("/home/eragon/Documents/datasets/Def/labels.pt")

#folds = torch.load("/home/eragon/Documents/datasets/Def/folds.pt")
```

现在我们有了所有这些，我们用上面提到的折叠创建一个张量数据集。这是 8K 数据集格式所特有的，这就是为什么要这样做的原因。如果你不这样做，可能有更简单的方法。目标是有一种迭代存储在数组中的音频数据的方法。完成这些后，我们将数据集分成训练集和验证集。

[](https://www.datadriveninvestor.com/2020/06/24/disclosure-and-resolution-program-wont-prevent-physicians-from-practicing-defensive-medicine/) [## 人工智能、深度学习和医疗实践|数据驱动的投资者

### 人工智能和深度神经学习的效用看起来可能是合法和有前途的，特别是…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/06/24/disclosure-and-resolution-program-wont-prevent-physicians-from-practicing-defensive-medicine/) 

```
def get_dataset(skip_fold):

    local_features = []

    local_labels = []

    for i in range(len(folds)):

        if folds[i] == skip_fold:

            continue

        local_features.append(features[i])

        local_labels.append(labels[i])

    local_features = torch.stack(local_features)

    local_labels = torch.stack(local_labels)

    return TensorDataset(local_features, local_labels)

# Loading dataset
dataset = get_dataset(skip_fold=10)

print("Length of dataset: ", len(dataset))

val_size = int(0.1*len(dataset))

train_size = len(dataset) - val_size

train_data, test_data = random_split(dataset, [train_size, val_size])

train_loader = torch.utils.data.DataLoader(train_data, **kwargs)

test_loader = torch.utils.data.DataLoader(test_data, **kwargs)
```

![](img/48bf85f01292561aafc602c9514b8a28.png)

[Sort](https://blog.hubspot.com/marketing/how-to-sort-in-excel)

# 模型

我们使用一个简单的神经网络模型作为概念验证。这个网络本身可以被修改以给出更好的结果。将讨论这样做的一些方法。

```
class Net(nn.Module):

    def __init__(self):

        super(Net, self).__init__()

        self.network = nn.Sequential(

            nn.Linear(40, 128),

            nn.ReLU(),

            nn.Linear(128,256),

            nn.ReLU(),

            nn.Linear(256, 512),

            nn.ReLU(),

            nn.Linear(512, 64),

            nn.ReLU(),
            nn.Linear(64, 10),
            nn.Tanh()

        )

    def forward(self, x):
        return self.network(x)
```

我们的初始模型仅由线性以及校正的线性单位层/激活函数组成。请注意，必须根据您的数据修改初始输入通道。在我的例子中，我的输入是 40，这就是为什么你会在代码中看到它。现在要注意的是，最终激活不是一个整流线性单位，而是一个 tanh。这仅仅是因为根据实验，它表现得更好。

我们怎样才能使这个模型变得更好？首先我们可以考虑使用卷积。我们也可以尝试使用 [swish 激活](https://arxiv.org/abs/1710.05941)功能来代替 ReLU。我们可以尝试更深层次的网络以及稍微不同的架构。实际上，这只是一个非常基本的模型，但它似乎表现得相当好。

# 培养

把我们需要的所有东西放在一起，让我们试着写代码来使用数据训练我们的模型。我们需要选择一个优化器，在我们的例子中，我们应该选择随机梯度下降而不是 Adam。不知何故，这表现得更好。至于我们的损失函数，我们使用交叉熵损失，因为我们有多类数据。我们遵循标准语法。我们首先采用模型，并将其设置为可训练的，这将允许我们存储梯度，并在神经网络中执行反向传递。我们将模型推送到 GPU，批量迭代数据。

对于每个批次，我们将数据及其相应的标签推送到 GPU。我们也将梯度归零。这样做可以使我们不累积前一批次的梯度，这可能会破坏我们的结果。在此之后，我们将我们的批次通过模型，并使用输出来计算我们的损失。因为目标是最小化这种损失，所以我们执行向后传递并更新我们的优化器。由于训练可能需要很长时间，我们想知道我们在这期间的训练状态。因此，我们还编写了一个小片段，在培训进行时打印出指标。

```
def train(args, model, device, train_loader, optimizer, epoch):

    model.train() # Setting model to train

    device = torch.device("cuda") # Sending to GPU

    for batch_idx, (data, target) in tqdm(enumerate(train_loader)):

        data, target = data.to(device), target.to(device)

        optimizer.zero_grad() #Reset grads

        output = model(data) # Passing batch through model

        loss = F.cross_entropy(output, target) # Will need to change everytime. Loss

        loss.backward() # Backprop

        optimizer.step() # Pass through optimizer

        if batch_idx % args.log_interval == 0:

            #print("Loss: ", loss.item())

            if args.dry_run:

                break
```

另一个小技巧被用来给出更好的结果。这是一次循环训练。这最初是在本文的[中提到的，它基本上允许我们通过首先提高学习率，然后在一段设定的时期内降低学习率来制作一个更好的模型。因此，我们也对此进行了更新。](https://arxiv.org/abs/1812.01187)

```
optimizer = optim.SGD(model.parameters(), lr=args.lr,

                       weight_decay=args.weight_decay)

scheduler = optim.lr_scheduler.OneCycleLR(
    optimizer, max_lr=args.max_lr, steps_per_epoch=len(train_loader), epochs=10)
```

# 测试

仅仅训练模型当然是不够的，我们需要确定我们的模型做得有多好。我们遵循与培训几乎相同的程序，只有一些小的不同。首先，我们将模型设置为评估模式，而不是训练模式。我们还定义了一个测试损失变量，这将有助于我们累计一批的损失。

```
def test(model, device, test_loader):

    model.eval()  # Setting model to test

    test_loss = 0
    with torch.no_grad():

        for data, target in tqdm(test_loader):

            data, target = data.to(device), target.to(device)

            output = model(data)

            test_loss = F.cross_entropy(output, target)

            acc = accuracy(output, target)

            print(f"Acc: {acc}")

            print(f"Val loss: {test_loss.detach()}, Val acc : {acc}")
```

我们还需要定义一个精度函数。在我们的例子中，我们首先获取输出，并找出第一维上的最大值。然后，我们对预测标签与所需标签相同的所有值求和，并返回该值除以预测总数的张量。这将基本上给我们一个介于 0 和 1 之间的十进制值，这将帮助我们确定我们的模型做得有多好。

```
def accuracy(outputs, labels):

    _, preds = torch.max(outputs, dim=1)

    return torch.tensor(torch.sum(preds == labels).item() / len(preds))
```

这样做之后，我们可以保存我们的模型，以备将来的推断。这样我们就能识别出我们需要的声音。

# 履行

我在本文中没有涉及的一件事是它的物理实现。我在文章开头提供的链接谈到了一个[组织](https://www.rfcx.org/home.html)如何使用类似的东西并在森林中实际实现它。抛开硬件部分不谈，我们在软件方面还有两件事没有深入讨论。

首先，我们的火车模型只能处理固定长度的信号，但在森林中会有连续的声音，那么我们如何处理这个问题呢？很简单，我们取一个特定的时间单位，比如说几秒钟，每隔几秒钟我们就进行一次识别。然后，我们对一段时间(可能是几分钟)的结果进行平均，然后我们可以使用结果来识别我们需要的声音是否确实出现。

第二是部署问题。因为我们需要一个物理设备来执行这种识别，所以我们可以使用一个带有 WiFi 的设备，比如 raspberry pi，并在该设备上部署我们的模型。当然，我们不能把笔记本电脑放在外面的森林里，所以这将是一个更有效的解决方案。

当然，做同样的事情有不同的方法，但这超出了本文的范围。如果你确实想了解更多，你可以参考[这篇文章。](https://link.medium.com/qTSSO6iAwab)和[这一个。](https://medium.com/datadriveninvestor/reducing-model-footprint-in-deep-learning-c500b3ff50b)

# 几乎结束了

我们今天讨论的是一种相对简单的方法。虽然对于大多数用例来说，这种方法已经足够了，但是对这种方法的任何形式的更改大多是架构更改的一部分，而不是这里介绍的大部分代码。这样，就有可能缩放或修改所需的部分，以制作更好的模型。

# 结束语

在我结束这篇文章之前，我想补充一些东西。

首先是效率问题。这些模型在神经元之间有很多联系。他们中的许多人可能并不需要。通过删除不必要的连接，可能会使任何模型(尤其是这个模型)更加高效。实际上我已经在[的另一篇文章](https://medium.com/datadriveninvestor/reducing-model-footprint-in-deep-learning-c500b3ff50b)中详细介绍了这一点，如果你对这个话题感兴趣，可以参考一下。

![](img/0ab5cab95bd0203035f15c664e36839c.png)

[Protect puppy](https://www.readersdigest.ca/home-garden/pets/6-things-know-owning-puppy/)

我想补充的第二个也是最后一个想法是我们的责任。这是我们的世界，我们做的每一件小事都会影响它。思考我们对环境的行为符合我们和其他人的最佳利益。试图修复一个已经破碎的局面是可以做到的，但是从一开始就不要这个局面不是更好吗？下次你有机会的时候，请想想我们的日常行为是如何影响自然的。

小事改变大事。我们只能制造微小的涟漪。有一天，他们可能会帮助我们生活在另一个时代。

> 谢谢:)
> 欢迎任何评论。你也可以在 [Github](http://www.github.com/SubhadityaMukherjee/) 上和我联系。

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)