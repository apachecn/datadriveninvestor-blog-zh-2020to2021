# 强化学习——一种交互式学习

> 原文：<https://medium.datadriveninvestor.com/reinforcement-learning-an-interactive-learning-b1fa29166fc8?source=collection_archive---------6----------------------->

![](img/29f5575974110efaba6ae458e30c2dcf.png)

**Reinforcement Learning Methods and working style**

**互动学习**

强化学习是机器学习的一部分，代理通过与环境交互来自主学习。RL 不需要数据集。

强化学习的历史和 MDP 由于它的流行和更先进的研究今天被更详细地覆盖，它适用于主要的应用，如自动驾驶汽车，机器人，未知和艰苦的环境。

本文通过例子探讨了动态编程的 MDP & RL 方法。这篇文章特别适合初学者和那些想知道 RL 是如何进入画面的人。由于代理人行为的不确定性，在线学习是热门和必要的。在上面的标题图中，我更详细地介绍了绿色矩形框主题。

RL 不像监督学习或模仿数据集，因为它在没有任何干预的情况下，独自在**已知**和**未知**环境中表现出色。

![](img/7999d38e2e2b0de9ed255a0ad1e8ade2.png)![](img/d1616ff04afdd276c3a1c546d934ed8f.png)

强化学习是一种机器学习，它与环境交互来学习，这种行为的组合产生了最有利的结果。

![](img/f057bf04451c6b4efcbf4f54d41fb07b.png)![](img/3cc9ee5be3c9488febfb9bfc817eff88.png)

**Picture describe RL appearance in ML**

![](img/ab09b8c43960598ee31484083a13e324.png)

为了对环境中的主体进行推理，RL 引入了两个新概念，即:状态和动作。世界在特定时间停止的状态称为**“状态”**。代理可以执行一个可能的**【动作】**来改变当前状态。

为了驱动代理执行动作，每个状态产生一个相应的**奖励**。一个代理计算每个状态的期望总报酬，称为一个状态的**值**。

RL 作品图片如下:

![](img/30306fd2db7a2bcced8226116bc0a344.png)

Reinforcement Learning working style

![](img/f8fa9877fd63b999121d6cd400b89dbe.png)

一个代理在环境中的时间“t”执行状态中的动作，并在时间 t+1 获得新的状态和该动作的奖励。

在每个步骤中，代理

> *执行一个动作*
> 
> *观察新状态*
> 
> *领取奖励*

![](img/21e6cf653b854ab88d938202cccc1576.png)

**Environment, State, Action,Agent,etc., described in Maze Example**

在强化学习中，我们不知道一系列行为的最终成本或回报，直到它被执行。代理人的目标是找到一系列能最大化**回报**的行动。基本强化学习处理最大化回报。

自主智能体应该学会在没有人类操作员任何指导的情况下，通过反复试验来执行任务。RL 允许我们建造智能机器。它为行为提供了形式主义。RL 不需要数据来训练智能代理。

RL 代理可以通过分层学习显著减少学习时间——首先解决初级学习问题，然后组合解决方案来解决一个复杂的问题。

RL 通过对过去的记忆来处理非马尔可夫环境。

> 强化学习不需要训练数据，而是适用于未知环境。

![](img/c5c490b56e5e994a692052991b06cfcb.png)

这些元素及其变体在马尔可夫决策过程中被很好地定义。在这篇文章中，我们将简要地去 MDP。

![](img/3f590a5c3dbc9cd4ac0765c615a56d94.png)

RL 动态地而非离线地学习马尔可夫决策过程(MDP)。它评估每个状态的值，无论哪个状态值最大，都将进入该状态。

除了下面的主题，还需要理解它的符号。

![](img/2b70a8281dd106d38cf47ec806afd383.png)

**Major Concepts used in Reinforcement Learning**

**注意，动态规划、蒙特卡罗评估和时间差学习是迭代方法。**

![](img/b799aaf823abe40921bb65d9de57af4d.png)

请注意，不同的作者、大学和博客使用不同的符号，以下符号是基于理查·萨顿的《T2 强化学习》这本书

我试图探索不同的符号，以便读者熟悉这些符号。

我试图探索不同的符号，以便读者熟悉这些符号。例如，以下 3 个符号是相同的。

![](img/a7f72bff06cfdabcd83439ebef2a79c3.png)![](img/e53bd8b633cd625d8a78da5261d69897.png)

**Notations used in Reinforcement Learning and Markov Decision Processes (MDPs)**

![](img/aed0a5078f918f1e02d0a06639a41ec8.png)

在我们开始研究 RL 概念的例子之前，我们先考虑一下马尔可夫决策过程(MDPs ),它可以被视为离线规划，而 RL 则被视为在线规划。

让我们考虑状态和动作如何有助于**问题解决**、 **MDPs** 和**强化学习**。

在任何时候，代理都应该处于环境中任何可能的状态。

动作是确定性的和非确定性的。确定性动作在当前状态下执行并仅产生一个后继状态，而非确定性状态在当前状态下执行动作并产生多个后继状态。

![](img/b23932f28d3b072e590124ef1a5aa506.png)![](img/3f8061b444ec2899efc76cfab9b6c6a2.png)

马尔可夫决策过程(MDPs)在非确定性搜索问题中起着至关重要的作用，它以一种有效的方式处理多个后继状态，它主要被认为是离线规划，并且主体对变迁和报酬(或环境)有充分的了解。MDP 提供了通常提出 RL 问题的形式主义。

马尔可夫决策过程由几个属性定义。马尔可夫决策过程是一个元组，它被定义为

![](img/ef76846f8f338ca27384a7e0c8a43c0a.png)

其中:

![](img/4f44707b26884a9d35e94f9c1bb8fc9c.png)![](img/2c44a8d86f06ea1ef8185addf4cadf00.png)

鉴于现在，未来独立于过去。一个状态被称为马尔可夫的当且仅当:

![](img/ae1a5fdb6c71d1b8b5b519634371316f.png)

状态从历史中获取所有相关信息。一旦状态是已知的，历史可以被丢弃，即状态是未来的充分统计。

MDP 可以被建模为国家行动奖励序列

![](img/209d8f762aebc9160f0bb878b5cee68b.png)![](img/6f083678c8805cef0ee1eeb7517e3eea.png)

奖励函数被定义为，

![](img/b5efa4486ebd6b19ba352e75018c326b.png)

回报函数是从时间步长 t 开始的总折扣奖励，定义为

![](img/393d5f7d7e4b80622236e67487e14385.png)![](img/ddd71dbd457da0dcec47b280c904b1b4.png)

价值函数 V(s)描述了状态 s 的长期价值。价值函数有不同的变体，下面简单介绍。

状态值函数 V(s)是从状态 s 开始的期望收益

![](img/6f66dc45b842b3b8573497c44b8b32e4.png)

价值函数可以分解为即时报酬和后继状态的贴现值。

![](img/40533c5310cdf53965fe2df7506f424d.png)

**Value Function Decomposition**

继承国的直接回报和贴现值

![](img/afd2c286426ad6d39466ae8226a432d9.png)

这是与被称为[动态规划](https://en.wikipedia.org/wiki/Dynamic_programming)的数学优化方法相关的最优性的必要条件。

![](img/b5f625955aadaa633e2eddcb269390e6.png)

DP 通过以递归方式分解成简单的子问题来简化复杂的问题。

![](img/a83b1ff54568d9cc5a5d240e257d0bc0.png)

**Image from Wiki**

**最优子结构:**一个复杂的问题可以通过分解成子问题，并使用递归概念寻找子问题的最优解而得到最优解决，那么它就是最优子结构。

![](img/a2527b97b49f6faaa4e6e07dfb1b9ddc.png)

**DP solves complex problem by decomposing into sub-problems and find optimal solution using recursive concept**

子问题可以递归地嵌套在更大的问题中，因此 DP 方法是适用的，那么在更大的问题的值和子问题的值之间存在关系。在最优化文献中，这种关系被称为**“贝尔曼方程”。**

![](img/747095edd052fb1415c5923b6c4d8d51.png)

**This Relationship is called Bellman Equation**

贝尔曼方程可以用矩阵简明地表达，

![](img/c6ddcddac8ef6d0e8bb8cc7ff746c5c5.png)

价值函数具有需要策略的变量。它们是状态-价值函数和行动-价值函数，这将在政策定义之后讨论。

![](img/402d8b002470328f8b8a4845e3417ba2.png)

策略是给定状态的动作分布，

![](img/61f1949497ea667f4f9f88083cba0ce4.png)

策略完全定义了代理的行为。MDP 策略取决于当前状态(而非历史)，即策略是固定的(与时间无关)

![](img/ceb84024451e86db70368dafb901fcd9.png)

状态转换和奖励功能与策略结合在一起，定义如下

![](img/98a3ebbd9e4da0fe9fadc8898a7ef2b0.png)

状态值函数是从状态 s 开始的期望收益，然后遵循策略

![](img/ec7994a93d6ab10e3e63f87b17074b61.png)

行动价值函数是从状态 s 开始的期望收益，采取行动 a，然后遵循政策

![](img/9505e7f3b7c360c709613923767264a6.png)

状态-价值和行动-价值函数可以分解为直接回报加上后继状态的贴现值

![](img/e42c053a6111c54153b084a68b8ef774.png)

**State-value Function**

![](img/acf745785eefadedcb002795f89a5dd8.png)

**Action-value Function**

![](img/9ceb38e9b879b3720240740ab784a715.png)![](img/a43cb25246e6ae3f003477db20e3d469.png)![](img/f292abd66d15dd7530f9780ef1807964.png)![](img/ff7487e410671b44e6a26d4163866bbd.png)![](img/db0e827c0bb5b0d0f2d60a35dfde6db2.png)![](img/0f2802787b1e6d56f7228400e4663319.png)![](img/5d7acdd48c0f26b7bcac3c7c52262e77.png)

状态-价值函数的贝尔曼期望方程可以用矩阵形式表示如下

![](img/38fd4b7fad9bd1bf2341a8a94ec5a7c9.png)![](img/8df63f83cd21b36bd23261d63247f7b2.png)![](img/3046d4833aaaf9d5aa2f5b44fa762c4b.png)

**Optimality for state-value, action-value and policy.**

**最佳状态值函数**

![](img/6c13c6344adc2439f38f257f665efc1d.png)

**最佳动作值函数**

![](img/606923c7bcf7958ba15ff22c6bd83a22.png)

最佳值函数指定了可能的最佳性能，一旦知道，它将被标记为已在 MDP 解决。

**最优策略**

定义策略的偏序如下

![](img/a5478089391939c061236b15fedfc8c1.png)

最优策略可以通过最大化最优价值行动来找到

![](img/591cfa4bffe99f9e5fdbefea6ff83220.png)![](img/790b5299f33736459f194baf787a5646.png)

最佳值函数通过贝尔曼最优方程递归关联:

![](img/82312b32de3abb4e0d3db79cd6858975.png)![](img/bd742d12b189f36a663bcc52b669d837.png)![](img/3ba13a36621f84f61cb35a8c2293623e.png)![](img/4d3130652882ab6340100757fe634fa1.png)![](img/c1a89da1ca96deb386f9c5afb1e18f84.png)![](img/7c4beba35b01c54cac50004235bd39e5.png)![](img/04f691bda3ed412333ecb7f051b354ee.png)

**Bellman Optimality Equation for action-state function**

RL 导出了算法的 MDP 的一些概念，正如已经陈述的，它提供了 RL 问题通常被提出的形式。

![](img/1c624d9538c9a781b22af1b6c7a0d1aa.png)

让我们考虑一个汽车有三种状态的例子，并从这些状态中评估所需的功能。

![](img/5eb7c9482038ad4d2ef368609354ee66.png)

State-space graph for a race car (search problem)

正如你在这个例子中看到的，奖励用(+/-)符号表示，动作(慢、快)和过渡没有符号。基于这个图表，我们需要计算**价值函数**和**策略**。

[](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) [## 机器学习和人工智能如何改变电子商务的面貌？|数据驱动…

### 电子商务开发公司，现在，整合先进的客户体验到一个新的水平…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) 

让我们构造转换函数和奖励函数表，并在价值和政策迭代中使用。

![](img/a900e27951438f16e247f10504bb3a3d.png)

在我们开始评估或检查之前，我们需要价值迭代、策略提取和策略迭代。

![](img/f2c3b585a5a7fd716e88c50a78188fa7.png)

> *值迭代用于计算状态的最优值，通过迭代更新直到收敛。*

值迭代是一种动态规划算法，它使用迭代更长的时间限制来计算时间限制值，直到收敛，即在时间**‘k’**和**‘k+1’时，每个状态的 V 值是相同的。**根据定义，它应该是

![](img/31360a7794c713c999506602f68d9fcc.png)![](img/ba28320409044ae3bc2aedfa96ec0686.png)

它的操作如下

![](img/961d11e21e759fdbe277020c1ff2e0f4.png)

**值迭代的计算:**

**步骤 1** :我们开始将初始状态设置为零，即，

![](img/c5c100e2ec3750ee30c0412adc5f060d.png)![](img/af6e3397922ceb2546fa932c923ae289.png)

**步骤 2:** 在我们的第一轮更新中，我们可以计算第一状态(冷状态)

![](img/31573030d1a65a61fbd5e375cc6c1f55.png)

计算状态后，状态值如下:

![](img/9b7347da414b012fc386d40fb35576ff.png)![](img/1a9d368091d42b0083d5bb07993e51d4.png)![](img/dd2df5c0de151ce76cb4bcca931c3329.png)![](img/e6b9ada41bdd0906a6bce51800fd97e3.png)

求解 MDP 的最终目标是确定一个最优策略，一旦使用一种叫做**“策略提取”**的方法确定了状态的所有最优值，就可以得到最优策略。

如前所述，最佳策略是

![](img/f3d55d5b0af62e0ba2ccc0f587a2862d.png)![](img/87720b4873c148577808e9abe772b6e9.png)

策略迭代是一种算法，它保持值迭代的最优性，同时提供显著的性能增益。

策略迭代需要策略评估和策略改进。

![](img/5863b9a331c46d7df23cb6de01a6dab4.png)![](img/a6f294f5711822c22179a464c66153df.png)![](img/ed82fe61fd3b6fba31a7f5bcb2cf6675.png)

它封装了策略评估和策略提取

策略改进用于生成更好的策略。它对由策略评估生成的状态值使用策略提取来生成这个新的和改进的策略。

![](img/593d88dfc5a942a4f9b6a6f7b4476206.png)

算法如下:

1.  定义初始策略。
2.  反复进行政策评估和政策改进，直至达到收敛。

从图像上看，政策改进如下:

![](img/b71c3c5a0b772729bb206bb27dcc2c56.png)

我们为赛车示例计算策略迭代如下:

1.  定义初始策略。

![](img/63724c766d482e73e9340dd3afc86b65.png)

终端状态(过热)没有传出操作，没有策略可以为其赋值。因此，我们简单地为任何终端状态赋值 0。

![](img/a0d4e81fabd1f571413e4264e1b39226.png)

下一步是对初始状态运行一轮策略评估。即，

![](img/b8ae78da71889e7a10ffd75f172a8a40.png)![](img/cdd5d1cae0fd703440152e1ca397d303.png)![](img/125b436b26912a912a9a8fb3de825dcd.png)

我们现在可以使用这些值运行策略提取。

![](img/d495bf162c3aa772f80f14923928be99.png)

策略提取

![](img/23784dd7c9cf13e3c2532160992c0102.png)![](img/277e4653bc87e65c6709d998d83ed51f.png)

这个例子给出了策略迭代的真正威力，只需要 2 次迭代。

因此，我们在底层工作中完成了赛车示例的价值迭代和策略迭代。

![](img/e5c5848660c6e23ae93a11b6ee9651c6.png)![](img/c1c82fbccff1b3b59bdca43dd943d929.png)

**Achievements of using Reinforcement Learning**

![](img/da3f45f7a6b89f2df120f6adac7e7997.png)![](img/98aec7aabf04daea3071be590d014595.png)

**Examples along with States , Actions and Rewards.**

![](img/2d376df9415571572409b36bf0019525.png)

有两种类型的强化学习，基于模型的学习和无模型的学习。都是用来做决策的。

基于模型的学习算法使用转移函数和奖励函数以及在控制探索期间获得的样本。。

无模型学习(Model-free learning)，试图直接估计状态的值或 q 值，而不使用转换和奖励。

![](img/a8ddc6f9a3a65c5d6d5980e530dbcfec.png)

**Types of RL Algorithms**

下图描述了强化学习算法。

![](img/553b55592df8a0d8a545970aa8b1f052.png)![](img/9f4fa06a0e7d07567e4cbcd0001b1b1c.png)![](img/71d9b2468cfc946947794300b93afbd2.png)

强化学习可以应用在艰苦的环境中，下图描述了它的典型应用。

![](img/1412ae225c52dd3ab20f67c92ab26201.png)![](img/c2d44d83840bb25fd18ddfb91fc9377a.png)

强化学习并不容易理解，它要求用户应该完全了解其方法的内部工作原理。虽然我们有 3 种不同的迭代方法，但本文涵盖了一种类型的迭代方法，即带有赛车示例的动态编程。虽然有许多主题需要涵盖，但它们将在以后的文章中得到证明。在机器人、自主车辆、机器、发动机等领域的应用中，虚拟现实是一个非常热门的研究领域。,

感谢您阅读本文，感谢您的反馈、评论和分享。如果评论中有错误，请告诉我。

**进入专家视角—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)