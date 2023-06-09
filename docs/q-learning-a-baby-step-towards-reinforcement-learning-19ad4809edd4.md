# Q-Learning:强化学习的一小步

> 原文：<https://medium.datadriveninvestor.com/q-learning-a-baby-step-towards-reinforcement-learning-19ad4809edd4?source=collection_archive---------19----------------------->

![](img/f52ba6d9b9abc28309c5be83a12f6956.png)

(Picture By Jessica Rocowitz On Unsplash)

# 强化学习简介:

机器学习主要用于监督和非监督学习任务。在这里，我们将研究另一个有趣的学习范例，它有一个称为代理的特殊组件。代理人主要通过接收被称为奖励信号的信号来学习。一个例子可以是通过接收信号来学习向哪里移动的机器人。

## 与强化学习相关的术语:

在这里，我们将看到一些与强化学习相关的重要术语。

## 代理人:

这是一个应该完成预期任务的模型。举个例子 ***自动驾驶汽车*** 可以是一个代理来完成自动驾驶的任务。

## 环境:

这是一个代理执行所有动作的世界。它还负责向代理提供关于它如何工作的反馈。以自动驾驶汽车的 ***路为例。***

## 行动:

这基本上是代理在环境中做出的决定。例子可以是 ***驾驶汽车。***

## 奖励信号:

这是代理由于其标量值的动作而得到的响应或反馈。

[](https://www.datadriveninvestor.com/2019/01/23/deep-learning-explained-in-7-steps/) [## 深度学习用 7 个步骤解释-更新|数据驱动的投资者

### 在深度学习的帮助下，自动驾驶汽车、Alexa、医学成像-小工具正在我们周围变得超级智能…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/23/deep-learning-explained-in-7-steps/) 

## 观察/状态:

代理观察到的环境的描述

## 终端状态:

这是我们无法采取进一步行动的状态。例子可以是通过自动驾驶汽车到达目的地或被困状态。

# Q-学习:

了解了强化学习的基本概念后，现在让我们跳到称为 q 学习的技术。这是一个基本的算法，它试图学习一个使回报最大化的策略。

## 创建 Q 表:

创建 Q 表是这个算法的核心。我们将这个矩阵的值初始化为零。每走一步，我们就更新并存储 q 值。该表被视为我们进一步行动的参考表。

```
q-table=np.zeros((state size,action size))
```

## 更新表格:

初始化表格后，我们应该更新表格。这发生在代理与环境交互并相应地更新[动作，状态]对时。

动作可以有两种类型，例如**探索**和**利用**。让我们理解他们。

## 利用:

基于利用的动作使得代理做出在给定状态下可以利用的最大可能奖励的决定。

## 探索:

在这种方法中，我们允许代理随机选择动作，而不是做出贪婪的选择。这样，代理就能够学习新的状态，而不像以前的方法，代理的行为很大程度上依赖于奖励。

强化学习需要探索和利用。没有探索，代理将无法了解环境，而没有开发，代理将无法采取正确的决策。因此，我们会以平衡的方式选择任何一个行动。我们可以选择一个值ε来表示我们想要探索或利用的程度。

## 等式:

现在轮到我们更新 q 表了。这可以通过使用下面的等式来实现。

```
Q(state,action)=Q(state,action)+alpha[R(state,action)+gamma*max(Q(new state,action)- Q(state,action)]
```

这里的 ***状态*** 是指当前状态。 ***新状态*** 是指代理在某个动作后达到的状态。学习率是α，它表示在旧值的基础上，我们想要改变多少。还有一点需要注意的是 ***gamma*** 是用来平衡未来和眼前回报的贴现因子。在于[0，1]。值为 1 表示代理对当前奖励比对过去奖励更重视。我们看到的函数 R 基本上也是奖励，它表示代理人在完成某个动作后得到了多少。

上面的等式和上面讨论的所有因素将帮助我们填写 q 表。

在下一篇文章中，我们将展示一个基于 q 学习的例子。