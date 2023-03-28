# 机器学习智慧！=隐私

> 原文：<https://medium.datadriveninvestor.com/federated-learning-d466aba3abbd?source=collection_archive---------16----------------------->

![](img/407f9c1f62d5f5acf8a317dd0e0d3698.png)

Distributing ; [[Link](https://www.google.com/url?sa=i&url=http%3A%2F%2Fwww.thomashanning.com%2Fdistributing-ios-apps-overview%2F&psig=AOvVaw3_ShP1al7c6V0SoekHQI8G&ust=1602231809744000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCLCMquXIpOwCFQAAAAAdAAAAABAD)]

想要 smarts 机器学习提供的服务吗？这太棒了，但是你的数据到底有多安全呢？如果你可以在没有数据泄露的情况下得到好处，那会怎么样呢？我们将看看联合学习并理解它是如何工作的。我们还会看一些论文以及他们对这个问题的看法，然后去图书馆转一转。

# 为什么这是一个问题？

从一个连接你和你的医生的应用程序的角度来考虑这个问题。这是一个很棒的应用程序，甚至可以预测未来的约会，有时甚至建议常用药物。现在有一天，公司被卖掉了，你所有的数据都在别人手里。不仅仅是医疗信息，还有深度学习算法对你和你的行为的了解。对于医疗报告等标准数据来说，数据隐私非常重要。但是 DL 算法呢？一个学习你如何说话，如何给朋友发短信，你喜欢什么食物的模型怎么样？

可怕不是吗？现在，让我们来看看如何防止 X 公司掌握比你自己更多的关于你的信息。

# 进入联合学习

击鼓…让我们首先明白我们想要做什么。考虑一个键盘应用程序。假设我们的键盘应用有 200 个用户。(可悲的是不太受欢迎)。现在，这是一个智能键盘，随着时间的推移，它会学习用户如何打字，他们使用什么词，甚至能够预测他们对给定的句子会说什么。我们希望确保，如果有泄漏，无论是谁得到它，都不可能为用户识别出唯一的模型。

你可能会想，嘿，这很简单。我们就在他们的手机上训练网络吧！你是对的。差不多了。唯一的问题是我们的手机无法训练整个模型。如果我们使用预先训练好的呢？良好的..这些预测不够个性化。

那么，我们先在大型计算机集群上训练模型，然后将训练好的模型发送到手机上，怎么样？完美。个性化怎么样？为什么**不更新**手机上的型号？太好了。但是主模型怎么会变好呢？如果我们发送这个手机已经学习的模型，它将挫败我们的目的。我们把所有用户的学习汇总起来怎么样？

我们走吧..让我们称之为联合学习:)

页（page 的缩写）(键盘示例来自[谷歌键盘论文](https://arxiv.org/pdf/1903.10635.pdf))

![](img/b1a05df5df9b6d58d1382094152fdb17.png)

Magic [[Link](https://2zwmzkbocl625qdrf2qqqfok-wpengine.netdna-ssl.com/wp-content/uploads/2020/04/21303508_web1_200420-SFE-SUPERCOL-magic_1.jpg)]

# 这是什么魔法？

让我们深入研究制作深度学习算法所涉及的步骤，并确定我们需要做出哪些改变

1.  获取数据(希望很多)
2.  预处理(也称为清理)数据
3.  找到/创建一个架构
4.  使用数据(1)和架构(3)训练模型。这一步做一次。然后随着数据随时间的变化定期更新。请记住这一点。
5.  将模型推送给 n 个用户
6.  收集模型表现的数据。(拜拜隐私)
7.  将这些数据发送回主模型。7(#新)。找出原始模型和个性化模型参数之间的差异。为多个用户执行此操作。删除可识别的信息。7.1(#新)。汇总(例如平均)信息，然后将其发送到主模型
8.  根据新数据重新训练模型

[](https://www.datadriveninvestor.com/2020/08/27/what-is-a-data-catalog-and-how-does-it-enable-machine-learning-success/) [## 什么是数据目录，它如何使机器学习取得成功？数据驱动的投资者

### 数据目录是机器学习和数据分析的燃料。没有它，你将不得不花费很多…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/08/27/what-is-a-data-catalog-and-how-does-it-enable-machine-learning-success/) 

# 耶！这是做什么的？

*   您的所有信息都存储在本地，绝不会发送到任何地方
*   保护您的个人数据不被泄露
*   删除与您的所有连接
*   允许模型更新和变得更好，而不损害隐私
*   除了你自己，没有人“拥有”你的数据

# 我可以将它添加到我的模型中吗？

是啊！有很多方法，但是最简单的方法是使用 Pytorch 中的一个名为 Syft 的库。这就像在代码中添加几行代码一样简单。

(由于整个代码非常庞大，我在这里只放一些片段。完整的代码，请参考我的[库](https://github.com/SubhadityaMukherjee/pytorchTutorialRepo/tree/master/FederatedLearningPySyft)

1.  看看这篇[文章](https://blog.openmined.org/upgrade-to-federated-learning-in-10-lines/)由开矿
2.  让我们以一个简单的架构为例，它有两个 Conv 层和两个线性(全连接)层
3.  导入这个库(连同其他 pytorch 库)并添加两个用户

```
import syft as sy
hook = sy.TorchHook(torch)
bob = sy.VirtualWorker(hook, id="bob")  # person1
alice = sy.VirtualWorker(hook, id="alice")  # person2
```

1.  以这种方式修改 pytorch 火车数据加载器。测试不会因为是本地的而改变。

```
train_loader = sy.FederatedDataLoader( # this is now a FederatedDataLoader
    datasets.MNIST('/home/eragon/Documents/datasets', train=True, download=True,
            transform=transforms.Compose([
                       transforms.ToTensor(),
                       transforms.Normalize((0.1307,), (0.3081,))

            ]))
    .federate((bob, alice)), # This will simulate a federated learning system
    shuffle=True, **kwargs )
```

1.  像这样修改主训练循环

```
def train(args, model, device, train_loader, optimizer, epoch):
    model.train()  # Setting model to train
    device = torch.device("cuda")  # Sending to GPU
    for batch_idx, (data, target) in tqdm(enumerate(train_loader)):
        model.send(data.location)  # Send to location (worker)
        data, target = data.to(device), target.to(device)
        optimizer.zero_grad()  # Reset grads
        output = model(data)  # Passing batch through model

        loss = F.nll_loss(output, target )

        loss.backward()  # Backprop
        optimizer.step()  # Pass through optimizer
        model.get()  # Get it back

        if batch_idx % args.log_interval == 0:
            loss = loss.get()
            if args.dry_run:
                break
```

1.  测试循环保持不变
2.  训练模型！！
3.  写一篇关于它的博客，没人看的时候哭

# 太好了，那它用在哪里呢？

它**可以**在很多地方使用，但现在，它仍处于测试阶段。虽然已经有一些早期采用者。我找到的一些例子是:

*   谷歌键盘(Gboard):他们用它来更新他们的预测，学习初始数据集中没有的单词(比如 lmao)。
*   数字健康公司[论文](https://doi.org/10.1038/s41746-020-00323-1)；这里有巨大的希望
*   军事(显然不确定任何用例，但我确实读到它正在被使用)
*   像 OpenMined(谁制作了库)，Nvidia，谷歌，苹果等公司

# 用它！

这是一个即将到来的领域，还有许多事情要做。如果可以的话，为图书馆做点贡献，或者只是了解事物是如何工作的以及为什么会这样。想进一步阅读？查看参考资料部分。你会发现很多有趣的链接。

谢谢大家！如有任何疑问，请联系我们。

# 资源

*   [露天博客](https://blog.openmined.org/upgrade-to-federated-learning-in-10-lines/)
*   [英伟达](https://blogs.nvidia.com/blog/2019/10/13/what-is-federated-learning/)
*   [Unite.ai](https://www.unite.ai/what-is-federated-learning/)
*   [谷歌博客](https://ai.googleblog.com/2017/04/federated-learning-collaborative.html)
*   [维基](https://en.wikipedia.org/wiki/Federated_learning)
*   数字健康:Rieke，n .，Hancox，j .，Li，w .等。npj 数字。医学。3, 119 (2020).[https://doi.org/10.1038/s41746-020-00323-1](https://doi.org/10.1038/s41746-020-00323-1)
*   执板:陈，m，马修斯，r，欧阳，t .，&博费斯，F. (2019)。未登录词的联合学习。arXiv 预印本 arXiv:1903.10635[论文](https://arxiv.org/pdf/1903.10635.pdf)
*   陈，m .，马修斯，r .，欧阳，t .，，博费斯，F. (2019)。未登录词的联合学习。arXiv 预印本 arXiv:1903.10635

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)