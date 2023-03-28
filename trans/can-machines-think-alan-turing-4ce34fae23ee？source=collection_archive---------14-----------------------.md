# “机器会思考吗？”—艾伦·图灵

> 原文：<https://medium.datadriveninvestor.com/can-machines-think-alan-turing-4ce34fae23ee?source=collection_archive---------14----------------------->

![](img/6b7f2dd718a9aed4dd96bb2e11a9c4fd.png)

Photo by [Andy Kelly](https://unsplash.com/@askkell?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/machine-learning?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

艾伦·图灵(Alan Turing)在《计算机器与智能》(Computing Machinery and Intelligence)中提出了一个简单而复杂的问题，他因破解“谜”(Enigma)而闻名，这是一种在二战期间用于纳粹战争通信的密码设备。

图灵领先于他的时代。

今天，我们能够看到图灵质疑“思考”的这些机器。多年来，人工智能(AI)和机器学习(ML)迅速发展并改变了我们的生活。从如何煎鸡蛋的快速谷歌搜索到“嘿 Siri/Alexa”的语音命令，到未来可能的自动驾驶汽车，这些都是依赖于人工智能和机器学习的技术。

![](img/c16756d53a10f6670e09e947ffedccae.png)

Photo by [Omid Armin](https://unsplash.com/@omidarmin?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/siri?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

对于那些一直生活在岩石下的人来说，简单地说，人工智能就是让机器变得聪明并能够执行通常需要人类智能的任务的代码。机器学习是人工智能的一个子领域，它允许计算机程序通过经验来改善其最终结果。把它想象成一个婴儿。起初，婴儿不知道如何走路，但慢慢地，随着他们获得更多的经验，婴儿(现在是蹒跚学步的孩子)将知道如何用双脚走路。

像网飞、Youtube、Spotify、Instagram、抖音等日常技术。都依靠 AI 和机器学习为你提供个性化的体验，根据你的兴趣显示建议。

![](img/823c9752104e12a2f61e6c67e1d855ba.png)

Photo by [Arseny Togulev](https://unsplash.com/@tetrakiss?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/machine-learning?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

# 是什么让机器学习？

我们人类可以通过三种不同的方式进行机器学习:监督、非监督和强化。

## 监督学习

在监督学习中，数据被标记，并告诉机器应该寻找什么样的确切模式。把它想象成一个寻宝游戏，给你一个物品清单。这种方法在当今世界非常普遍，在这里，简单的点击、滚动、喜欢、评论或悬停将允许像网飞这样的技术最好地建议新的电视节目推荐，或者抖音在你的“为你页面”上向你展示定制的内容。

![](img/7760f511e4b268549dc2ca39bbfce13a.png)

[Netflix Website](https://www.netflix.com/ca/)

## 无监督学习

在这种方法中，你正在参加的寻宝游戏不再有一个物品列表。相反，你可以发现任何物品，并根据你观察到的模式对它们进行分类。一组中比手掌大的物品，另一组中比手掌小的物品)。虽然这种方法用于网络安全，但由于其不太明显的应用，在主流中并不经常使用。

## 强化学习

这是机器学习的最新方法之一，机器通过反复试验来学习，以达到目标。当机器做了“错误”的事情时，就会受到惩罚。当它做对一件事时，机器会得到奖励。通过这样做，计算机程序将致力于获得尽可能多的奖励和尽可能少的惩罚，每次都从错误中学习。这与我们人类非常相似，我们能够从错误中学习和改进。强化学习最受欢迎的应用是谷歌的 AlphaGo，这是一个在围棋比赛中战胜人类选手的著名程序。

AlphaGo

如果你是一个电影爱好者，我肯定会推荐你去看 [AlphaGo 纪录片](https://www.youtube.com/watch?v=WXuK6gekU1Y)！观看人工智能机器与世界知名的围棋冠军李·塞多尔(Lee Sedol)对弈，不仅信息量大，而且很有吸引力。**如果你还不相信，就看这个** [**快速预告片**](https://www.youtube.com/watch?v=8tq1C8spV_g) **。**

> 强化学习的另一个真正有趣的应用是机器狗学习如何抵挡人类。点击阅读更多相关信息[。](https://www.wired.com/story/watch-a-robot-dog-learn-how-to-deftly-fend-off-a-human/?utm_campaign=Artificial%2BIntelligence%2BWeekly&utm_medium=email&utm_source=Artificial_Intelligence_Weekly_195)

# 但是这到底是怎么做到的呢？

## ***1。*数据集**

计算机的目标是分析什么？

以之前的例子为例，在你的寻宝游戏中，你会寻找什么样的东西？工艺品？树的部分？这个数据集将决定创建程序的目标是什么。在监督学习中，训练数据将被标注上模型应该识别的特征。另一方面，无监督学习中的数据是未标记的，由机器来确定特征并对每个对象进行分类。这个数据集应该分成两部分:用于训练的数据和用于测试的数据。划分比例通常取决于数据集有多大，但一般建议 80%用于训练，20%用于测试。

这一步的很大一部分是确保训练数据不是完美的。像随机化和消除偏见这样的事情将确保机器学习模型能够真正学习识别现实世界中的事情，在现实世界中，任何事情都可能发生。

## 2.数据集上的算法选择。

不管是哪种情况，都需要选择一种算法来训练数据。对于那些不熟悉术语“算法”的人来说，它基本上是机器执行某项任务所遵循的一组指令。选择算法时要记住的事情有:数据类型(标签/未标签)、数据量和问题已解决。

对于带标签的数据，以下机器学习算法是流行的:

*   回归算法
*   决策树
*   聚类算法
*   关联算法
*   神经网络

如果你想了解更多关于机器学习算法的知识，这里的是一个非常好的资源。

## 3.训练算法并创建模型

接下来，在准备数据集和选择要使用的算法之后，终于到了使用材料和创建模型的时候了。为了使模型在预测中表现良好，需要对算法进行训练。这非常类似于狗在学会诸如“坐”、“躺”或“翻滚”等技巧之前被训练。基于第一次训练，算法将反复迭代，将输出与正确的结果进行比较，同时消除可能导致它在现实世界中不起作用的偏差(过度拟合)，直到算法在大多数情况下返回正确的结果(90%以上被认为是好的)。

## 4.改进模型

现在，是时候继续改进模型了！可以使用新数据来提高机器学习模型的准确性和有效性。一旦模型被证明足够准确，你就可以在市场上看到它，就像 Youtube、Spotify 和 Tiktok 的机器学习模型一样。

虽然所有这些信息都很翔实，但让我们来回答一下**最重要的问题**。

## 由 AI 驱动的机器人会接管世界吗？

截至目前，可能不会。为了让机器人真正接管世界，AGI(人工智能)需要存在。这意味着机器需要能够理解世界，并且知道如何像人类一样完成不同的任务。目前，这种技术只是科幻小说，因为不同的电影如 2001:太空漫游或甚至钢铁侠的 J.A.R.V.I.S .而流行

![](img/09aec6122d085c79b7dc62303543cdda.png)

Iron Man using J.A.R.V.I.S, a machine that has AGI ([source](https://onereach.ai/if-you-had-your-own-j-a-r-v-i-s-what-artificial-intelligence-in-business-might-be-like/))

# **TL；博士**

*   艾伦·图灵(Alan Turing)在他的论文《计算机械与智能》(Computing Machinery and Intelligence)中首次引入了机器学习的思想。
*   机器学习模型主要有三种方式:监督学习、无监督学习、强化学习。
*   要建立一个机器学习模型，有四个不同的步骤:选择和准备数据集，选择正确的算法，训练和测试算法，最后改进机器学习模型。
*   未来的下一步是什么？好消息是，机器人不会接管世界，因为人工通用智能还有点遥远。

*感谢阅读！我是克洛伊，17 岁，热衷于通过人工智能在未来的世界做社会公益。如果你喜欢读这篇文章，请给我一个“掌声”。*

*在* [*中*](https://medium.com/@chloelam2407)*[*LinkedIn*](https://www.linkedin.com/in/chloe-lam-2407/)*或我的* [*个人网站*](https://chloelam.ca/) *上跟上我对 AI 等有趣话题的探索。**