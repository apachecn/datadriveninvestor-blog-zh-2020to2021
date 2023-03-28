# 神经支持的决策树算法研究

> 原文：<https://medium.datadriveninvestor.com/research-on-neural-backed-decision-trees-algorithms-111af8e2f92c?source=collection_archive---------8----------------------->

![](img/a4f26fba77f552a268156dbcd3f537b8.png)

*来自先宇科技的监利*

# 背景

仙芋上很多业务场景都需要算法来实现分类，比如图像分类、组件识别、产品分层、纠纷类别预测等。在这些情况下，通常需要算法模型来提供可解释的识别结果。换句话说，模型需要识别类别，并在识别过程中使用明显的类别层次结构和来源。因此，**实现可解译影像分类**成为项目开发需求。为此，我对神经支持的决策树(NBDT)算法进行了调查。

**NBDT** 是加州大学伯克利分校和波士顿大学在 2020 年 4 月发表的一篇论文中介绍的一个模型。你可能已经注意到，字母“B”在 NBDT 不代表“助推”，而是代表“支持”。因此，熟悉 GBDT 的读者不应该把 NBDT 误解为一种新型的梯度推进决策树。NBDT 只是一棵决策树，而不是多棵。

# 介绍

NBDT 的特点是在决策树之前集成了一个神经网络(NN)。神经网络通常是卷积神经网络(CNN)。据我所知，NBDT 的结构大致由 CNN 和决策树(DT)组成。

目前，NBDT 用于图像分类。它的优势不在于准确。在笔者的实验中，其准确率略低于前面的 CNN。其真正的优势在于其平衡**模型准确性**和**模型可解释性**的能力。具体来说，NBDT 可以通过稍微牺牲 CNN 的准确性来实现比任何树模型高得多的分类准确性。此外，有了决策树，NBDT 还可以明确地逐步展示模型推理的基础。例如，NBDT 不仅能识别一只狗的图像，还能让识别过程中的每一步都清晰可见。起初，NBDT 以 99.49%的概率将图像识别为“动物”。然后，它以 99.63%的概率将图像识别为“脊索动物”。接下来，它以 99.4%的概率将图像识别为“食肉动物”。最后以 99.88%的概率将图像识别为“狗”。这种推理方法增强了模型的可解释性。

![](img/71c8a9058aa2a618751d72cf6d9bb4d6.png)

*Figure 1: Dog Classification (Referenced From Official Demo)*

详细原则

NBDT 采用预培训+微调的框架。整个过程大致分为以下三个步骤:

## 第一步:预先训练一个 CNN 模型，将 CNN 的最后一层权值作为每一类的隐向量。

例如，使用 cifar10(具有 10 个类别的图像分类数据集，包括“猫”和“狗”)来训练一个 resnet18 CNN。这种 CNN 的最后一层通常是全连接(FC)层。假设倒数第二层输出的向量维数为 d，那么，FC 层 W 的维数为 W，这样，W 的每个列向量正好对应一个类别，可以看作每个类别的隐藏向量。这种方法类似于 Word2Vec。

## 第二步:使用类别的隐向量进行层次聚类，使用 WordNet 形成层次树结构。

在本文中，这种树形结构被称为“诱导层次结构”。首先，我们对类别的隐藏向量实现层次聚类，这可以在源代码中通过直接调用 sklearn 模块的`AgglomerativeClustering`类来实现。建立聚类层次结构后，我们会遇到两个问题:

1.  两个子节点可以通过聚类算法来聚类，并且两个子节点都表示实体的类别。但是，它们的父节点没有实体描述。
2.  我们需要一种方法来表示集群子节点的父节点的隐藏向量。

为了解决第一个问题，作者使用了 [WordNet](https://en.wikipedia.org/wiki/WordNet) ，这是一个包含名词之间上下位关系的词网。在 Python 中，WordNet 模块可以直接导入到 NLTK 模块中，在那里可以调用它。由于一个叶节点有一个实体描述，比如 cifar10 的 10 个类别，所以可以通过 WordNet 找到两个叶节点最近的共同祖先。WordNet 中猫狗最近的共同祖先是食肉动物这个词。所以把食肉动物作为猫和狗这两个词的父节点。根据层次聚类的结果，可以自下而上地命名父节点，直到只有一个根节点。这样就形成了一个诱导层次，如图 2 的**步骤 1** 所示。诱导层次也是图 1 中用于狗分类的决策树。

![](img/7f1ed7396aadb82ebe3274a23033fe0d.png)

*Figure 2: Training and Inference (Referenced From the Original Paper)*

为了解决第二个问题，作者使用子节点隐藏向量的平均值来表示父节点的隐藏向量。*参见图 3 中* ***步骤 C*** *的描述。*

![](img/ed70c03c3c1486d2a173215af0df00a0.png)

*Figure 3: Building Induced Hierarchies (Referenced From the Original Paper)*

## 步骤 3:将诱导层次的分类损失添加到总损失中，并微调模型。

诱导层次结构(树形结构，以下简称 DT)建立后，完整的模型不再是 CNN，而是 CNN + DT。为了迫使模型基于从根节点到叶节点的树结构来预测新样本，我们需要将树结构的分类损失添加到总损失中，并对模型进行微调。

首先，我们需要了解完整模型使用的预测方法:我感觉作者的思路直击事情的本质。当一个新的样本(图像)进入模型时，图像首先到达 CNN。在图像到达最后的 FC 层 W 之前，CNN 向图像输出 d 维向量 x。

然后，对 x 和 W(本质上是与每个列向量的内积)执行矩阵乘法，以获得样本在每个类别中的 logits 分布。如果设置了 softmax 参数，则可以获得概率分布。因为 W 的每个列向量表示 DT 叶节点的隐藏向量，所以这个 DT 可以完全替换 W。这意味着不直接对 x 和 W 执行矩阵乘法，而是从根节点开始遍历 DT，以依次计算 x 和 DT 的每个子节点的内积。遍历 DT 节点有两种方式:**硬**和**软**。假设 DT 是一棵二叉树。如果使用硬模式，则分别计算 x 和左右两个子节点的内积。每次，x 被分类到具有较大内积的子节点中，直到 x 到达最后一个叶节点，这表示 x 所属的最终类别。如果使用软模式，则遍历所有中间节点，并计算 x 的内积。叶节点的最终概率是 x 到达叶节点的路径上所有中间节点的概率积。最终，基于所有叶节点的最终概率的比较来确定 x 所属的类别。

![](img/680711bc6b9bcc4635ddce8337fcd75a.png)

*Figure 4: Node Probability Calculation (Referenced From the Original Paper)*

在了解了完整模型的预测细节后，我们可以解释诱导层次(树结构)的分类损失。相应的，损失函数也有硬和软两种模式，如图 5 所示。如果使用硬模式，损失函数将样本沿着 DT 中的真实路径所属的叶节点的分类损失(以特定权重)相加。不沿着真实路径的节点(图 A 中虚线 w3 和 w4)不被考虑。基于交叉熵计算每个节点的分类损失。如果使用软模式，则叶节点上的最终概率分布和真实的独热分布之间的交叉熵被直接计算为损失。**简而言之，硬模式下的损失函数计算路径的交叉熵，而软模式下的损失函数计算叶节点的交叉熵。**在 Pytorch 中，交叉熵是这样计算的:

![](img/79256bfffeaa081fc4bace295acf8937.png)

`CrossEntropy(x,class)=-log⁡(exp⁡(x[class])Σjexp⁡(x[j]))=-x[class]+log⁡(Σjexp⁡(x[j]))`

最终模型的总损失还考虑了原 CNN 的分类损失(Lossoriginal)。因此，需要微调的总损耗如下:

![](img/63d70b65cf9da36cd5e1b5e044bac76b.png)

`Losstotal=Lossoriginal+Losshard or soft`

根据我对源代码的理解，当损失函数执行反向传播(BP)时，它仍然优化了 CNN 的网络权重。损失函数迫使前一个 CNN 的输出满足后一个 DT 的期望。这样，样本按照 DT 的推理路径输出的预测类别就尽可能符合真实类别。

![](img/839e1127df99e0fe16a9df8e22541780.png)

*Figure 5: Loss in Hard and Soft Modes (Referenced From the Original Paper)*

# 源代码分析

[NBDT 的 Python 代码在 GitHub](https://github.com/alvinwan/neural-backed-decision-trees) 上开源。一般来说，代码是用 Pytorch 和 Networkx 实现的。总共有 4000 多行代码，四个核心脚本分别是 **model.py、loss.py、graph.py、hierarchy . py**代码几乎没有注释和参数解释，不容易读懂。下图显示了对几个核心代码段的分析。

## 构建诱导层次

核心函数是 **build_induced_graph** ，用于输入叶子节点的 WordNet IDs 和 CNN 模型。然后，该函数从 CNN 模型中获取 FC 权重，执行层次聚类，并使用 WordNet 来“命名”聚类结果。这形成了一个 DT，它的节点具有实体意义。该函数对应于本文详细原理一节中的要点 2。该功能描述如下:

![](img/e28811716c0961255ca177c4606f0835.png)

## 正向计算节点概率

如前所述，新样本进入模型后，首先到达 CNN。在样本到达 FC 层之前，模型输出 d 维向量 x，然后计算 x 和 DT 节点的隐向量的内积。DT 节点的隐藏向量等于其子节点的隐藏向量的平均值。 **get_node_logits** 方法优化:**由于向量均值的内积等于向量**的内积均值(如下式所示)，所以不需要显式求解隐向量，计算其内积。相反，一个节点的所有子节点的 logit 的平均值可以用作该节点本身的 logit。具体代码如下:

![](img/51536928243dd7c86e59e1feb2f16a2e.png)![](img/702828ebc78c9baade9f3983a936b7b2.png)

## 总损失函数

如前所述，总损耗等于原始 CNN 损耗和树形结构损耗之和。让我们以硬模式为例。下面的代码解释了如何计算沿着 DT 路径的树结构的损失，然后将损失合并到总损失中。

![](img/4c37c341f37cf27714571de26a9f5a59.png)

## 实验

作者在多个数据集上将原始 CNN (WiderResnet28×10)与多个可解释神经网络模型进行了比较。下表显示，NBDT 的精确度略低于原来的 CNN，但远远超过其他模型。这表明 NBDT 已经达到了最先进的状态。**在 NBDT，使用软模式时的得分高于硬模式。**这很容易理解，因为软模式考虑的是全局优化，而硬模式考虑的是连续的局部优化。

![](img/584d0d853e9b8a8302774180e8bd45e3.png)

*Figure 6: Experimental Results (Referenced From the Original Paper)*

## 使用

> *有关安装和使用的更多信息，请参见 GitHub 官方页面。本文仅总结常用方法。*

## 在命令行中预测

您可以直接运行 nbdt 命令，后跟图像路径(URL 或本地路径)。在第一次执行期间，您必须下载 WordNet 和官方的预培训模型。预训练模型适用于 cifar10 数据集。因此，最好输入 10 个类别之一的图像。输出显示预测是逐步执行的。

![](img/c51e6c56b4958ef819f507ca8c44ea2d.png)

## 用 Python 预测

![](img/396a250bcb971f1e9dc7c3a77d45d751.png)

## 完全使用

![](img/1a411fdf541f99b8c525b3c16d412a8e.png)

# 后续计划

NBDT 研究的目标是找到一种方法，使分类可以解释。这种可解释的方法可以用在分类期间需要 DT 的任何场景中。尽管这篇文章关注的是一个图像分类场景，但是任何分类过程都可以使用 NBDT 来解释，只要前面的 CNN 被其他网络所取代。例如，在仙寓的高质量产品分层项目中，我们可以根据我们的业务知识建立产品的诱导层次。例如，第一层可以将输入分类为专业销售者和个人销售者，第二层可以将输入分类为高、中、低销售率。然后，最后一层可以将投入分为不同级别的高质量产品。然后，我们可以基于这些层次训练 NBDT 来执行分类。

另一个典型的例子是图片分类，一个卖家上传一张图片给仙宇。在这里，卖家希望算法能够自动识别出他想要销售的产品的类别。卖家可能会上传一张椅子或桌子的图片，但正确的类别是“家具”基于层次结构的 NBDT 可以自动将销售者发布的产品识别为“家具”或者，NBDT 也可以提供推荐选项，允许卖家选择他们的类别。这消除了手动填充的需要。未来，NBDTs 可能会用于其他任务。

## 参考

*   [论文](https://arxiv.org/abs/2004.00221)
*   [源代码](https://github.com/alvinwan/neural-backed-decision-trees)

# 原始来源:

[](https://www.alibabacloud.com/blog/research-on-neural-backed-decision-trees-algorithms_597094) [## 神经支持的决策树算法研究

### 先宇科技 2021 年 1 月 4 日 292 作者:先宇科技监利先宇上的很多商业场景都需要算法…

www.alibabacloud.com](https://www.alibabacloud.com/blog/research-on-neural-backed-decision-trees-algorithms_597094)