# AI 和机器学习有什么区别？

> 原文：<https://medium.datadriveninvestor.com/whats-the-difference-between-ai-and-machine-learning-94eb2454f176?source=collection_archive---------8----------------------->

![](img/f5c751aa3a99656c9f2fad76c30cb72c.png)

这两个主题背后有很多令人兴奋的东西，所以这是一个快速指南，介绍它们是什么以及有什么区别。

# 人工智能

人工智能这个术语是由数学博士约翰·麦卡锡创造的，他将这个领域描述为“制造智能机器，尤其是智能计算机程序的科学和工程”这是一个非常宽泛的定义；大多数专家会接受这样一个定义，即以某种方式将 [AI](https://www.datadriveninvestor.com/glossary/artificial-intelligence/) 描述为学习和/或能够解决问题的程序。[机器学习](https://www.datadriveninvestor.com/glossary/machine-learning/)是 AI 的子领域之一。人工智能还有其他子领域，如本体创建(寻求创建一个主题的分类法)，以及常识推理(你进入你的厨房，看到一个抽屉打开，你就推断有人打开了抽屉)。人工智能的其他领域没有像机器学习一样受欢迎的原因是它们更难开发，合理简单的模型对 ML 来说很好，ML 已经产生了利润。

# 机器学习

机器学习是关于数学模型的创建，这些模型针对给定的任务自我优化它们的变量(通常称为参数)。这些模型在一组称为[训练集](https://www.datadriveninvestor.com/glossary/training-set/)的数据上进行自我优化，然后应用于现实世界。其中一些模型比计算机存在的时间更长，但有了计算机，我们现在能够存储更多的数据，更快地执行计算，将训练好的 ML 模型应用于新数据。ML 有三个子域，每个子域都有不同的开发和使用方法。

[](https://www.datadriveninvestor.com/2019/01/28/ai-creativity-deep-dream-comes-true/) [## 人工智能与创造力:梦想成真|数据驱动的投资者

### 人工智能总是让我着迷。不仅作为一套有用的工具，不断发展，而且作为一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/28/ai-creativity-deep-dream-comes-true/) 

# 监督学习

在[监督学习](https://www.datadriveninvestor.com/glossary/supervised-learning/)中，我们试图预测一个特定的结果。这个结果可以是离散的(人们会购买吗？还是[热狗还是不辣做](https://www.youtube.com/watch?v=ACmydtFDTGs) g？)或者连续(这个房子要卖多少钱？这只股票 1 个月后的股价会是多少？).在监督学习中，我们以某种方式测量误差，并寻求最小化误差。

[回归](https://www.datadriveninvestor.com/glossary/regression/)是指我们试图从连续的光谱中预测一个值。最简单的例子是[线性回归](https://www.datadriveninvestor.com/glossary/linear-regression/)，它通过你的数据点画一条直线。在这个例子中，我们建立的数学模型是 ***y = m*x + b*** 并且自优化被应用于 m 和 b 参数。我们对任意给定 x 值的 y 值的预测可以在红线中找到。这里误差的度量是每个蓝点和红线之间的距离。

![](img/6061121f99036a718b7fbafe9733bfc1.png)

[https://en.wikipedia.org/wiki/Linear_regression#/media/File:Linear_regression.svg](https://en.wikipedia.org/wiki/Linear_regression#/media/File:Linear_regression.svg)

[分类](https://www.datadriveninvestor.com/glossary/classification/)是对离散值的预测，顾名思义我们尝试将数据点分为两组。例如，你可以用一个叫做[决策树](https://www.datadriveninvestor.com/glossary/decision-tree/)的机器学习模型来预测某人在泰坦尼克号上幸存的概率(如下所示)。在这里，我们试图优化模型的准确性，即我们的模型在预测中正确的时间百分比。

![](img/f64c552670ebe43adfe88f1a69961e4a.png)

[https://bigwhalelearning.files.wordpress.com/2014/11/titanic_heuristic.png](https://bigwhalelearning.files.wordpress.com/2014/11/titanic_heuristic.png)

# 无监督学习

与监督学习不同，[非监督学习](https://www.datadriveninvestor.com/glossary/unsupervised-learning/)没有一个你可以优化的正确答案。[无监督学习](https://www.datadriveninvestor.com/glossary/unsupervised-learning/)通常用于创建数据点聚类。例如，您的信用卡公司可能会查看您的消费习惯，并衡量数据点(您的购买)之间的差异。在这种情况下，差异可以通过一天中的时间、地理位置和商店类型来衡量。有了一些购买历史(训练数据)，信用卡公司可以将凌晨 4:00 在另一个国家的酒吧从你的账户购买 200 美元归类为远离正常。由于我们没有欺诈和非欺诈事件的列表，我们不能使用监督学习的模型，我们只能将事情分为普通和不普通。

# 强化学习

[强化学习](https://www.datadriveninvestor.com/glossary/reinforcement-learning/)的目标是让算法获得最大回报。新闻中强化学习最受欢迎的用途是自动驾驶汽车。在这里，运行汽车的算法获得了一些奖励，如没有撞车，让你到达目的地，并及时最小化行程长度。在强化学习中，算法是在模拟或游戏中训练的，在那里它测试事物并学习什么能最大化它的奖励函数，然后它被应用到现实世界中。监督和非监督学习模型已经使用了一段时间，但 RL 现在得到了更多的关注。

7 世纪的棋盘游戏围棋曾被认为是不可战胜的。与像国际象棋这样的游戏不同，1996 年 IBM 的“深蓝”击败了特级大师加里·卡斯帕罗夫(Gary Kasparov ),围棋的每一轮棋手可以采取的潜在行动要多很多倍。这使得在围棋中使用传统的机器学习方法变得不可能。DeepMind 的强化学习程序 AlphaGo 终于能够在 2015 年毫无障碍地战胜一名人类职业选手。类似地，像 [AWS DeepRacer](https://www.youtube.com/watch?v=dwUJVYEhxGM) 和 [Kaggle 的 Connect X](https://www.kaggle.com/c/connectx) 这样的比赛有助于增加 RL 从业者的数量。随着我们越来越擅长赢得这类游戏，我们将学习可以应用于机器人等更广泛领域的优化方法。

*原载于 2020 年 1 月 22 日 https://www.datadriveninvestor.com*[](https://www.datadriveninvestor.com/2020/01/22/whats-the-difference-between-ai-and-machine-learning/)**。**