# 排名前 10 的竞争与此技巧:超参数调整与 Hyperas 的神经网络

> 原文：<https://medium.datadriveninvestor.com/rank-top-10-in-competition-with-this-tip-hyper-parameter-tuning-with-hyperas-for-neural-networks-96e2d347ffab?source=collection_archive---------1----------------------->

![](img/c150fcb6ae54535756660bef922b4047.png)

Photo by [Franck V.](https://unsplash.com/@franckinjapan?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/machine-learning?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

> 在 XGBoost 超参数调整之后，现在轮到 CNN 和通用神经网络了。

虽然给出源代码可能已经很有用了，但是我要做的是一部分一部分地解释我写的代码，这样你就可以调整选项并自己调试。

以下是完整的源代码:

# 研究案例介绍

CNN 模型的目标是将裁剪后的图片分为 4 类，即:

```
['Attire','Decorationandsignage','Food','misc']
```

这个数据集来源于黑客地球[挑战赛](https://www.hackerearth.com/en-us/challenges/competitive/hackerearth-deep-learning-challenge-auto-tag-images-gala/problems/)的 Gala 检测。在我们的笔记本中，我们对数据集进行了简单的数据分析。(如果你碰巧感兴趣，请写信给我，我可以寄给你)

Hyperas 方法的完整代码由两部分组成，即数据准备和 CNN 模型:

# 数据准备(都在我们稍后将调用的函数中)

在这一部分，我们需要把所有的数据加载，在这个函数的数据预处理，使其输出可以立即馈入神经网络。

注意事项:

*   全局变量也需要放在 data()函数中，您可能在笔记本上工作，并认为可以在作用域上找到以前分配的变量，但事实并非如此。
*   幸运的是，data()函数在给优化函数时只被调用一次。

# CNN 模型:特定于 Hyperas

这是 CNN 模型的一个样本/版本。架构的快速描述，我们这里有:

*   输入层具有形状(48，48，1)
*   4 到 5 个卷积层(使用过滤器(3×3)和(5×5))(与归一化相结合)
*   2 个最大池(2D)和 2 个密集层
*   我们只在隐藏层使用 ReLu 激活，在输出层使用 softmax
*   我们也尝试了不同的神经网络优化器，如亚当，SGD 等…

通过这些设置，我们正在尝试的超参数将会是:

*   从 Dropout(0.25)我们将其更改为 Dropout({{uniform(0，1)}}):这允许以随机方式在区间[0，1]中找到列车损失的最佳参数(这意味着我们采样并且不尝试 0 和 1 之间的每个单个值)
*   从密集(256)到密集({{choice([256，512，1024]}}):这允许我们针对该 FC 层的列车损耗再次挑选最佳参数。
*   在 optimizer 字段中输入 optimizer={{choice(['rmsprop '，' adam '，' sgd'])}}将得到这 3 个选项中的最佳优化器。
*   batch_size={{choice([64，128])}}的工作方式与前面的类似

我们决定优化这些参数，但显然你可以尝试修改其他超参数。

# 优化和拟合

模型现在设定，让我们优化所有先前陈述的超参数。

函数 minimize()将模型函数和数据函数作为参数。为了获得最佳的超参数值，您只需执行 print(best_run))。

# 根据您的设置，实施过程中可能会出现错误

这里有一些你可能会遇到的错误和处理方法。

*   **类型错误:需要字符串标签|** 您需要将您的代码包装在一个`def create_model(...): ...`函数中，然后像示例中一样从`optim.minimize(model=create_model,...`调用它。
*   **类型错误:“生成器”对象不可订阅** |只需运行 pip install networkx==1.11
*   **“没有这样的文件或目录”或 OSError，Err22 |** 在 optim.minimize 中添加以下代码，就像我们对代码所做的那样:notebook _ name = ' { your _ notebook _ name } '

如果你想了解更多关于 Hyperas 的知识，我强烈建议你查看它的原始[源代码](https://github.com/maxpumperla/hyperas)。

感谢阅读，记得评论你是否喜欢我的文章。下面是另一篇[文章](https://medium.com/swlh/xgboost-hyperparameters-optimization-with-scikit-learn-to-rank-top-20-44ea528efa58)关于机器学习模型优化的实现。

你可以在这里找到我的博客，那里有其他的文章和产品。

此外，点击这个[链接](https://direct-link.net/91830/aitechfordummies)(指向加盟计划)真的会帮我解决问题！您只需完成一些快速任务(只需等待和激活通知)，所有这些将真正帮助我了解更多未来的硬件相关内容！