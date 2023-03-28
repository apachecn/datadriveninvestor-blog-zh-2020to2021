# 对话管理模型研究进展

> 原文：<https://medium.datadriveninvestor.com/progress-in-dialog-management-model-research-444c52f4bc1a?source=collection_archive---------6----------------------->

![](img/13b60f17231b171be682d6264e447351.png)

*这篇文章是智能机器人对话式人工智能团队的以下专家和研究人员的合作成果:来自康乃尔大学的余和，以及来自阿里巴巴 DAMO 研究院的戴银培(绰号延峰)、唐成光(恩珠)、李永斌(水德)和(孙坚)。*

自从对人工智能(AI)的研究开始以来，已经进行了许多努力来开发高度智能的人机对话系统。艾伦·图灵在 1950 年提出了图灵测试[1]。他认为，如果机器通过了图灵测试，就可以被认为是高度智能的。为了通过这项测试，机器必须与一个真人交流，这样这个人就会相信他们正在与另一个人交谈。第一代对话系统主要是基于规则的。例如，麻省理工学院在 1966 年开发的 ELIZA 系统[2]是一个心理医学聊天机器人，它使用模板匹配方法。流行于 20 世纪 70 年代的基于流程图的对话系统基于有限状态自动机(FSA)模型来模拟对话流中的状态转换。这些机器内部逻辑透明，易于分析和调试。然而，由于高度依赖专家干预，它们的灵活性和可扩展性较差。

随着大数据技术的兴起，第二代统计数据驱动的对话系统(以下简称统计对话系统)应运而生。当时，强化学习在对话系统中被广泛研究和应用。一个代表性的例子是剑桥大学的 Steve Young 教授在 2005 年提出的基于部分可观测马尔可夫决策过程(POMDP)的统计对话系统[3]。该系统在鲁棒性方面明显优于基于规则的对话系统。它通过基于语音识别结果的贝叶斯推理来维护每一轮对话的状态，然后基于对话状态来选择对话策略以生成自然语言响应。通过强化学习框架，基于 POMDP 的对话系统不断地与用户模拟器或真实用户进行交互，以检测错误并相应地优化对话策略。统计对话系统是一个不高度依赖专家干预的模块化系统。但是，它的可扩展性较差，并且模型很难维护。

近年来，随着深度学习在图像、语音和文本领域的突破，围绕深度学习构建的第三代对话系统已经出现。这些系统仍然采用统计对话系统的框架，但是在每个模块中应用神经网络模型。神经网络模型具有强大的表示和语言分类生成能力。因此，基于自然语言的模型从生成模型(如贝叶斯网络)转变为深度判别模型，如卷积神经网络(CNN)、深度神经网络(DNNs)和递归神经网络(RNNs)[5]。对话状态通过直接计算最大条件概率而不是贝叶斯后验概率来获得。深度强化学习模型也用于优化对话策略[6]。此外，端到端序列对序列技术在机器翻译中的成功使端到端对话系统成为可能。脸书的研究人员提出了一个基于存储网络的面向任务的对话系统[4]，为第三代对话系统中端到端面向任务的对话系统的研究提供了一个新的方向。总的来说，第三代对话系统比第二代对话系统好，但是需要大量的标记数据来进行有效的训练。因此，提高模型的跨域迁移性和可扩展性成为一个重要的研究领域。

常见的对话系统分为以下三种类型:

**聊天-、**和 **Q &面向 A 的**。在**面向聊天的对话**中，系统生成有趣且信息丰富的自然反应，以允许人机对话继续进行【7】。

在一个面向 A 的对话中，系统分析每个问题并从库中找到正确答案。面向任务的对话(以下简称任务对话)是任务驱动的多轮对话。机器通过理解、主动查询、澄清来确定用户的需求，通过调用应用编程接口(API)进行查询，并返回正确的结果。通常，任务对话是一个顺序决策过程。在对话期间，机器通过理解用户语句来更新和维护内部对话状态，然后基于当前对话状态选择最佳动作，例如确定需求、查询限制和提供结果。

**面向任务的对话系统**按照架构分为两类。一种是管道系统，具有模块化结构[5]，如图 1 所示。它由四个关键模块组成:

*   **自然语言理解(NLU):** 识别并解析用户的文本输入，以获得计算机可以理解的语义标签，例如槽值和意图。
*   **对话状态跟踪(DST):** 根据对话历史维护当前对话状态。对话状态是对话历史的累积意义，通常用槽-值对来表示。
*   **对话策略:**根据当前对话状态输出下一个系统动作。DST 模块和对话策略模块统称为对话管理器(DM)。
*   **自然语言生成(NLG):** 将系统动作转换为自然语言输出。

这种模块化的系统结构具有高度的可解释性，易于实现，并且应用于业界大多数实际的面向任务的对话系统中。但是，这种结构不够灵活。这些模块相互独立，很难一起优化。这就很难适应不断变化的应用场景。此外，由于模块之间的误差累积，单个模块的升级可能需要整个系统的调整。

![](img/427c8c11b5cdd9ae39ae165cc8a2013b.png)

**Figure 1\. Modular structure of a task-oriented dialog system[41]**

面向任务的对话系统的另一个实现是端到端系统，这是近年来学术研究的热门领域。这种类型的结构训练了从用户端的自然语言输入到机器端的自然语言输出的整体映射关系。它具有高度的灵活性和可扩展性，降低了设计的人力成本，消除了模块之间的隔离。然而，端到端模型对数据的数量和质量提出了很高的要求，并且没有为诸如槽填充和 API 调用之类的过程提供清晰的建模。这种模式仍在探索中，目前还很少在行业中应用。

![](img/2f610a2c258e27bc552e1bb32a5ebeb3.png)

**Figure 2\. End-to-end structure of a task-oriented dialog system[41]**

随着对产品体验要求的提高，实际对话场景变得更加复杂，DM 也需要进一步完善。传统的数据挖掘通常建立在一个清晰的对话脚本系统中(搜索匹配的答案，查询用户意图，然后结束对话)，具有预定义的系统动作空间、用户意图空间和对话体。然而，由于不可预测的用户行为，传统的对话系统响应较慢，并且在处理未定义的情况时有较大的困难。此外，许多实际场景需要在没有足够的标记对话数据的情况下冷启动，导致高数据清理和标记成本。基于深度强化学习的 DM 需要大量数据进行模型训练。根据许多学术论文中的实验，训练一个对话模型需要数百个完整的会话，这阻碍了对话系统的快速开发和迭代。

为了解决传统数据挖掘的局限性，学术界和工业界的研究人员开始关注如何加强数据挖掘的可用性。具体来说，他们正在努力解决数据管理中的以下缺点:

1.  扩展性差
2.  标记数据不足
3.  培训效率低

我将从以上几个方面介绍最新的研究成果。

# 对话管理器的前沿研究

## 缺点 1:扩展性差

如上所述，DM 由 DST 和对话策略模块组成。最具代表性的传统 DST 是剑桥大学学者在 2017 年提出的神经信念跟踪器(NBT)[12]。NBT 使用神经网络来跟踪单个域中复杂对话的状态。通过使用表示学习，NBT 对前一轮的系统动作、当前轮的用户语句和候选槽值对进行编码，以计算高维空间中的语义相似度，并检测用户在当前轮中输出的槽值。因此，NBT 可以通过使用槽值对的词向量表达式来识别不在训练集中但是语义上类似于集中的槽值。这避免了创建语义词典的需要。因此，槽值可以扩展。后来，剑桥学者进一步改进了 NBT13，将输入槽值对改为域槽值三元组。使用模型学习而不是手动规则来累积每一轮的识别结果。所有数据都是由同一个模型训练的。知识在不同的领域之间共享，随着领域数量的增加，参数的总数保持不变。在传统的对话策略研究中，最具代表性的是剑桥学者提出的基于 ACER 的策略优化 6。

通过应用经验重放技术，作者尝试了信任域行动者-批评家模型和情节自然行动者-批评家模型。结果证明，基于深度交流的强化学习算法在样本利用效率、算法收敛性和对话成功率方面都是最好的。

但是，传统的数据挖掘在可扩展性方面仍然需要改进，具体表现在以下三个方面:

1.  如何应对不断变化的用户意图？
2.  如何处理改变槽和槽值？
3.  如何处理变化的系统动作？

## 改变用户意图

如果一个系统不考虑用户的意图，它通常会提供无意义的答案。如图 3 所示，不考虑用户的“确认”意图。必须添加一个新的对话脚本来帮助系统处理这个问题。

![](img/380ee8045020a8fb6461bde0af46f732.png)

**Figure 3\. Example of a dialog with new intent[15]**

传统模型输出旧意图类别的固定的一个热点向量。一旦不在训练集中的新的用户意图出现，向量需要被改变以包括新的意图类别，并且新的模型需要被重新训练。这降低了模型的可维护性和可伸缩性。一篇论文[15]提出了一个师生学习框架来解决这个问题。在师生培训架构中，旧模型和新用户意图的逻辑规则用作教师，新模型用作学生。这种架构使用知识提炼技术。具体来说，对于旧的意图集，旧模型的概率输出直接指导新模型的训练。对于新的意图，逻辑规则被用作新的标记数据来训练新的模型。这样，新模型就不再需要与环境交互进行重新训练。论文展示了在 DSTC2 数据集上进行的实验结果。确认意图被有意删除，然后作为新的意图添加到对话体中，以验证新模型是否具有适应性。图 4 显示了实验结果。比较了新模型(扩展系统)、包含所有意图的模型(对比系统)和旧模型。实验结果表明，新模型在不同噪声水平下都能获得令人满意的扩展新意图识别成功率。

![](img/01f4dcf49460b9bb0c24ccba4750cc80.png)

**Figure 4\. Comparison of various models at different noise levels**

当然，这种架构的系统还需要进一步的训练。CDSSM[16]是一个提议的语义相似性匹配模型，可以在没有标记数据和模型重新训练的情况下识别扩展的用户意图。基于训练集中用户意图的自然描述，CDSSM 直接学习意图嵌入编码器，并将任意意图的描述嵌入到高维语义空间中。这样，模型基于新意图的自然描述直接生成相应的意图嵌入，然后识别意图。下面提到的许多提高可伸缩性的模型都是用类似的思想设计的。将标签从模型的输出端移到输入端，利用神经网络对标签(标签名称或标签的自然描述)进行语义编码，得到一定的语义向量，然后匹配它们的语义相似度。

另一篇论文[43]提供了另一种观点。通过人机协作，人工客户服务用于处理系统启动后不在训练集中的用户意图。该模型使用额外的神经解析器来基于从当前模型提取的对话状态向量来确定是否需要人工客户服务。如果是，该模型将当前对话分发给在线客户服务。如果没有，模型会做出预测。通过数据学习得到的解析器可以判断当前对话是否包含新的意图，来自客服的响应默认被视为正确。这种人机协作机制有效地处理了在线测试期间在训练集中没有发现的用户意图，并且显著地提高了对话的准确性。

## 更改插槽和插槽值

在涉及多个或复杂域的对话状态跟踪中，处理变化的槽和槽值一直是一个挑战。一些槽具有非枚举槽值，例如时间、位置和用户名。它们的时段值集，如航班或电影院时间表，是动态变化的。在传统的 DST 中，slot 和 slot 值集默认保持不变，这大大降低了系统的可扩展性。

Google 研究人员[17]提出了具有非枚举槽值的槽的候选集。为每个时隙维护一个候选集。候选集包含对话中最多 k 个可能的时段值，并为每个时段值分配一个分数，以指示用户对当前对话中的时段值的偏好。系统使用双向 RNN 模型来查找当前用户语句中的槽值，然后用候选集中的现有槽值对其进行评分和重新排序。这样，每一轮的 DST 只需要对有限的槽值集做出判断，允许我们跟踪非枚举槽值。为了跟踪不在集合中的槽值，我们可以使用序列标记模型[18]或语义相似性匹配模型，例如神经信念跟踪器[12]。

前面是针对非固定槽值的解决方案，但是如何改变对话框主体中的槽呢？在一篇论文[19]中，槽描述编码器用于对现有的和新的槽的自然语言描述进行编码。所获得的表示槽的语义向量与作为双 LSTM 模型输入的用户语句一起被发送，并且所识别的槽值作为序列标签被输出，如图 5 所示。本文作了一个可接受的假设，即任何槽的自然语言描述都很容易获得。因此，设计了适用于多个领域的概念标记器，并通过简单的词向量的和简单地实现了槽描述编码器。实验表明，该模型能够快速适应新的插槽。与传统方法相比，该方法大大提高了可扩展性。

![](img/90548ffec1eb623d262bf1008940ec4f.png)

**Figure 5\. Concept tagger structure**

随着近年来序列对序列技术的发展，许多研究人员正在寻找使用端到端神经网络模型将 DST 结果生成为序列的方法。使用诸如注意机制和复制机制的常见技术来改善生成效果。在著名的多域对话 MultiWOZ 数据集上，香港科技大学 Pascale Fung 教授领导的团队利用复制网络显著提高了非枚举槽值的识别精度[20]。图 6 显示了该团队提出的贸易模型。每次检测到槽值时，该模型对域和槽的不同组合执行语义编码，并将结果用作 RNN 解码器的初始位置输入。解码器通过复制网络直接产生槽值。这样，非枚举槽值和变化槽值都可以由同一模型生成。因此，插槽值可以在域之间共享，从而允许该模型被广泛使用。

![](img/bd16d3fd2c792f007f2360a7078e0549.png)

**Figure 6\. TRADE model framework**

最近的研究倾向于将多领域 DST 视为机器阅读和理解任务，并将贸易等生成模型转换为判别模型 45。非枚举槽值由类似 SQuAD[46]的机器阅读和理解任务跟踪，其中对话历史和问题中的文本跨度被用作槽值。多选择机器阅读和理解任务跟踪枚举槽值，其中从候选值中选择正确的值作为预测槽值。通过结合 ELMO 和伯特等深层上下文词，这些新模型从 MultiWOZ 数据集获得了最佳结果。

## 更改系统操作

影响可伸缩性的最后一个因素是预定义系统动作空间的难度。如图 7 所示，在设计电子产品推荐系统时，你可能会忽略诸如如何升级产品操作系统等问题，但你无法阻止用户提出系统无法回答的问题。如果系统动作空间是预定义的，则可能会向尚未定义的问题提供不相关的答案，从而极大地损害用户体验。

![](img/8d3369e96be7c5834cb204b43570ede5.png)

**Figure 7\. Example of a dialog where the dialog system encounters an undefined system action[22]**

在这种情况下，我们需要设计一个对话策略网络，帮助系统快速扩展其动作。第一次尝试这样做的是微软[21]，他修改了经典的 DQN 结构，使强化学习在一个不受限制的行动空间。本文中的对话任务是一个文本游戏任务。每一轮动作都是一句话，动作数量不确定。故事随着情节的变化而变化。作者提出了一种新的模型——深度强化关联网络(DRRN)，通过语义相似度匹配将当前对话状态与可选的系统动作进行匹配，得到 Q 函数。具体来说，在一轮对话中，每个不确定长度的动作文本都经过神经网络编码，得到一个固定长度的系统动作向量。故事背景文本由另一个神经网络编码，得到固定长度的对话状态向量。这两个向量用于通过诸如点积之类的交互函数来生成最终的 Q 值。图 8 显示了论文中设计的模型的结构。实验表明，在文本游戏“拯救约翰”和“死亡机器”中，DRRN 优于传统的 DQN(使用填充技术)。

![](img/cf505155e4e07252f4a906242e0b409c.png)

**Figure 8\. DRRN model, in which round t has two candidate actions, and round t+1 has three candidate actions**

在另一篇论文[22]中，作者想从整个对话系统的角度解决这个问题，提出了增量对话系统(IDS)，如图 9 所示。IDS 首先对对话历史进行编码，以通过对话嵌入模块获得上下文向量，然后使用基于 VAE 的不确定性估计模块，基于上下文向量来评估用于指示当前系统是否能够给出正确答案的置信度。与主动学习类似，如果置信度高于阈值，DM 会对所有可用的动作进行评分，然后基于 softmax 函数预测概率分布。如果置信度低于阈值，则要求标记者标记当前回合的响应(选择正确的响应或创建新的响应)。以这种方式获得的新数据被添加到数据池中，以在线更新模型。通过这种人教的方式，IDS 不仅支持在不受限制的行动空间中学习，还能快速收集高质量的数据，相当适合实际生产。

![](img/68438234fa8c7feba7fd0987454b6f82.png)

**Figure 9\. The Overall framework of IDS**

# 缺点 2:标记数据不足

对话系统的广泛应用导致了多样化的数据需求。为了训练一个面向任务的对话系统，需要尽可能多的特定领域的数据，但是高质量的标记数据是昂贵的。学者们试图通过三种方式来解决这个问题:(1)使用机器来标记数据，以降低标记成本；(2)挖掘对话结构以有效地使用未标记的数据；以及(3)优化数据收集策略以有效地获得高质量的数据。

## 自动标记

为了解决人工标注的成本和效率低下的问题，学者们希望使用监督学习和非监督学习来允许机器辅助人工标注。有一篇论文[23]提出了 auto-dielabel 架构，通过使用层次聚类的无监督学习方法自动对对话数据中的意图和槽位进行分组，以自动标记对话数据(类别的具体标签需要手动确定)。该方法基于相同意图的表达可能共享相似的背景特征的假设。该模型提取的初始特征包括词向量、词性(POS)标签、名词词簇和潜在狄利克雷分配(LDA)。自动编码器将所有特征编码成相同维度的向量并拼接。然后，利用径向偏置函数(RBF)计算的类间距离进行动态层次聚类。彼此最接近的类被自动合并，直到类之间的类间距离大于阈值。图 10 显示了模型框架。

![](img/b200b1cc97a2c1e528685ec83c413fe6.png)

**Figure 10\. Auto-dialabel model**

在另一篇论文[24]中，监督聚类用于实现机器标记。作者将每个对话数据记录视为一个图节点，并将聚类过程视为识别最小生成森林的过程。该模型使用支持向量机(SVM)通过监督学习来训练问答数据集中节点之间的距离评分模型。然后，它使用结构化模型和最小子树生成算法来导出对应于对话数据的类信息作为隐藏变量。它生成最佳的聚类结构来表示用户意图类型。

## 对话结构挖掘

由于缺乏用于训练对话系统的高质量标记数据，寻找充分挖掘未标记对话数据中隐含的对话结构或信息的方法已经成为一个热门的研究领域。隐含的对话结构或信息在某种程度上有助于对话策略的设计和对话模型的训练。

一篇论文[25]提出在变分 RNN (VRNN)中使用无监督学习来自动学习对话数据中的隐藏结构。作者提出了两种获取对话中动态信息的模型:离散 VRNN (D-VRNN)和直接离散 VRNN (DD-VRNN)。如图 11 所示，`x_t`表示第 t 轮对话，`h_t`表示对话历史的隐藏变量，`z_t`表示对话结构的隐藏变量(一维一热离散变量)。两个模型的区别在于，对于 D-VRNN，隐变量`z_t`依赖于`h_(t-1)`，而对于 DD-VRNN，隐变量`z_t`依赖于`z_(t-1)`。基于整个对话的最大似然，VRNN 使用 VAE 的一些常用方法来估计隐藏变量`z_t`的后验概率分布。

![](img/7d53642bcfc66d865d1e956fabd669d5.png)

**Figure 11\. D-VRNN and DD-VRNN**

实验表明，VRNN 优于传统的 HMM 方法。VRNN 还将对话结构信息添加到奖励函数中，支持强化学习模型的更快收敛。图 12 显示了 D-VRNN 挖掘的餐馆中隐藏变量`z_t`的转移概率。

![](img/432d2dd09e138412bba8800c1dcf259d.png)

**Figure 12\. Dialog stream structure mined by D-VRNN from the dialog data related to restaurants**

CMU 学者[26]也试图使用 VAE 方法将系统动作推断为隐藏变量，并直接将其用于对话策略选择。这可以减轻由不充分的预定义系统动作引起的问题。如图 13 所示，为了简单起见，本文使用了一个端到端的对话系统框架。基线模型是单词级的 RL 模型(也就是说，对话动作是词汇表中的单词)。该模型使用编码器对对话历史进行编码，然后使用解码器对其进行解码并生成响应。奖励函数直接将生成的响应语句与真实的响应语句进行比较。与基线模型相比，潜在动作模型在编码器和解码器之间增加了后验概率推理，并使用离散的隐藏变量来表示对话动作，无需任何人工干预。实验表明，基于潜在动作的端到端 RL 模型在语句生成多样性和任务完成率方面优于基线模型。

![](img/cdbec5bb003e588cbdfa5107a0734e65.png)

Figure 13\. Baseline model and latent action model

## 数据收集政策

最近 Google 的研究人员提出了一种快速收集对话数据 [27](https://www.alibabacloud.com/blog/see) 的方法:首先使用两个基于规则的模拟器交互生成一个对话大纲，这是一个用语义标签表示的对话流框架。然后，将语义标签转换成基于模板的自然语言对话。最后，通过众包重写自然语句，丰富对话数据的语言表达。这种逆向数据采集方式的特点是采集效率高，数据标签完整且高度可用，降低了数据采集和处理的成本和工作量。

![](img/e0b5a019a9d39855f0ccab5962578720.png)

**Figure 14\. Examples of dialog outline, template-based dialog generation, and crowdsourcing-based dialog rewrite**

这种方法是一种机器对机器(M2M)的数据收集策略，在这种策略中，为对话数据生成大范围的语义标签，然后众包生成大量的对话话语。然而，生成的对话框不能涵盖真实场景中的所有可能性。另外，效果还要看模拟器。

在相关学术界，另外两种方法也常用于从对话系统中收集数据:**人机(H2M)** 和**人对人(H2H)** 。H2H 方法要求用户(由一个众包员工扮演)和客户服务人员(由另一个众包员工扮演)之间进行多轮对话。用户根据指定的对话目标提出需求，如购买机票，客服人员标注对话标签并做出响应。这种模式被称为绿野仙踪框架。许多对话数据集，如 WOZ[5]和 MultiWOZ [28]，都是在这种模式下收集的。H2H 方法帮助我们获得与实际服务场景最相似的对话数据。然而，为不同的任务设计不同的交互界面和清理不正确的注释是很昂贵的。H2M 数据收集策略允许用户和经过训练的机器相互交互。这样可以直接在线收集数据，通过 RL 不断完善 DM 模型。著名的 DSTC2 & 3 数据集就是这样收集的。H2M 方法的性能很大程度上取决于 DM 模型的初始性能。此外，在线收集的数据存在大量噪声，导致清理成本高，影响模型优化效率。

# 缺点三:训练效率低

随着 deep RL 在围棋游戏中的成功应用，这种方法也被广泛应用于任务对话系统中。例如，一篇论文[6]中的 ACER 对话管理方法将无模型深度 RL 与经验重放、信念域约束和预训练等其他技术相结合。这大大提高了任务对话系统中 RL 算法的训练效率和稳定性。

然而，简单地应用 RL 算法不能满足对话系统的实际需求。一个原因是，对话框缺乏清晰的规则、奖励功能、简单明了的动作空间，以及能够产生上亿条优质交互数据记录的完善的环境模拟器。对话任务包括改变槽值、动作和意图，这显著增加了对话系统的动作空间，并使其难以定义。当使用传统的平面 RL 方法时，由于所有系统动作的一次性编码，可能会出现维数灾难。因此，这些方法不再适合处理具有大动作空间的复杂对话。为此，学者们尝试了许多其他方法，包括**无模型强化学习、基于模型强化学习和人在回路。**

## 无模型 RL — HRL

分层强化学习(HRL)将一个复杂的任务分成多个子任务，以避免传统平面强化学习方法中的维数灾难。在一篇论文[29]中，HRL 首次被应用于任务对话系统。作者将一个复杂的对话任务按时间划分为多个子任务。例如，一个复杂的旅行任务可以分成多个子任务，比如订票、订酒店和租车。因此，他们设计了一个两层的对话策略网络。一层选择并排列所有子任务，另一层执行具体的子任务。

他们提出的 DM 模型由两部分组成，如图 15 所示:

*   **顶层策略:**根据对话状态选择子任务。
*   **低级策略:**在子任务中完成特定的对话动作。
*   全局对话状态跟踪器记录整体对话状态。整个对话任务完成后，顶层策略会收到一个外部奖励。

该模型还有一个内部评价模块，用于根据对话状态估计完成子任务的可能性(子任务的槽填充程度)。基于子任务的完成程度，低级策略从内部评论家模块接收内在奖励。

![](img/0631c8e0dada9edff8e1400fafb001fe.png)

**Figure 15\. The HRL framework of a task-oriented dialog system**

对于复杂的对话，在传统 RL 方法的每一步都选择一个基本的系统动作，例如查询槽值或确认约束。在 HRL 模式中，基于顶层策略选择一组基本操作，然后基于底层策略从当前组中选择一个基本操作，如图 16 所示。动作空间的这种层次划分覆盖了不同子任务之间的时序约束，有利于复合任务的完成。此外，内在奖励有效缓解了奖励稀疏的问题，加速了 RL 训练，防止了不同子任务之间对话的频繁切换，提高了动作预测的准确性。当然，动作的分层设计需要专家知识，子任务的类型需要专家来确定。最近，能够自动发现对话子任务的工具已经出现 30。通过使用无监督学习方法，这些工具自动拆分整个对话历史的对话状态序列，而不需要手动构建对话子任务结构。

![](img/366dc7e01e95cc6944835fb313d96e97.png)

**Figure 16\. Policy selection process of HRL**

## 无模型 RL — FRL

封建强化学习(FRL)是解决大规模问题的合适方法。HRL 在时间维度上根据不同的任务阶段将对话策略划分为子策略，降低了策略学习的复杂性。FRL 在空间维度上划分一个策略，限制每个子策略的作用范围，降低了子策略的复杂度。FRL 没有将任务划分为子任务。相反，它使用状态空间的抽象函数从对话状态中提取有用的特征。这种抽象允许 FRL 在不同的域之间应用和迁移，实现高可伸缩性。

剑桥学者首次将 FRL[32]应用于任务对话系统，根据动作空间与插槽的相关性来划分动作空间。这样做后，只使用动作空间的自然结构，不需要额外的专家知识。他们提出了如图 17 所示的封建政策结构。该结构的决策过程分为两步:

1.  确定下一个操作是否需要插槽作为参数。
2.  根据第一步的决定，为相应的槽选择低级策略和下一个操作。

![](img/f02d347b5edee237d48c72efc7590e72.png)

**Figure 17\. Application of FRL in a task-oriented dialog system**

一般来说，HRL 和 FRL 都以不同的方式划分高维复杂动作空间，以解决传统 RL 方法因动作空间维数大而导致的训练效率低的问题。HRL 根据人类的理解恰当地划分任务。然而，将一个任务分成子任务需要专家知识。FRL 根据动作的逻辑结构划分复杂任务，不考虑子任务之间的相互约束。

## 基于模型的 RL

前面的 RL 方法是无模型的。利用这些方法，通过与环境的试错交互获得大量弱监督数据，然后据此训练一个价值网络或策略网络。该过程独立于环境。还有一种基于模型的 RL，如图 18 所示。基于模型的 RL 直接建模并与环境交互，以学习状态和回报的概率转移函数，即环境模型。然后，系统与环境模型交互以生成更多的训练数据。因此，基于模型的 RL 比无模型的 RL 更有效，尤其是当与环境交互的成本很高时。但是，最终的性能取决于环境建模的质量。

![](img/79dba4a737dba570be688372e2387404.png)

**Figure 18\. Model-based RL process**

利用基于模型的强化学习来提高训练效率是当前一个活跃的研究领域。微软首先在 dialogs[33]中应用了经典的 Deep Dyna-Q (DDQ)算法，如图 19 所示。在 DDQ 训练开始之前，我们使用少量的现有对话数据来预训练策略模型和世界模型。然后，我们通过重复以下步骤来训练 DDQ:

*   **Direct RL:** 与真实用户在线交互，更新策略模型，存储对话数据。
*   **世界模型训练:**根据收集的真实对话数据更新世界模型。
*   **规划:**利用与世界模型交互获得的对话数据训练策略模型。

世界模型(如图 20 所示)是一个神经网络，它对环境状态转换和奖励的概率进行建模。输入是当前对话状态和系统动作。输出是下一个用户动作、环境奖励和对话终止变量。世界模型减少了 DDQ 在线 RL 所需的人机交互数据(如图 19 的图(a)所示)，避免了与用户模拟器的无效交互(如图 19 的图(b)所示)。

![](img/181d4293845c2577f4c4401faf837755.png)

**Figure 19\. Three RL architectures**

![](img/2afc303aa26b41255b1a7ab5e9574baf.png)

**Figure 20\. Structure of the world model**

与对话框中的用户模拟器类似，世界模型可以模拟真实的用户动作，并与系统的 DM 进行交互。然而，用户模拟器本质上是一个外部环境，用于模拟真实用户，而世界模型是系统的内部模型。

微软的研究人员在 DDQ 的基础上进行了改进。为了提高世界模型生成的对话数据的真实性，他们提出[34]通过对抗性训练来提高生成的对话数据的质量。考虑到何时使用通过与真实环境交互生成的数据，以及何时使用通过与世界模型交互生成的数据，他们在一篇论文中讨论了可行的解决方案[35]。他们还在另一篇论文中讨论了一个统一的对话框架，以包括与真实用户的交互[36]。这种人工教学的概念已经引起了业界的关注，因为它可以帮助建立 DMs。这将在下面的章节中进一步解释。

## 人在回路中

我们希望充分利用人类的知识和经验，生成高质量的数据，提高模型训练的效率。人在回路 RL[37]是一种将人类引入机器人训练的方法。通过设计的人机交互方法，人类可以有效地指导 RL 模型的训练。为了进一步提高任务对话系统的训练效率，研究人员正致力于设计一种基于对话特征的有效的人在回路方法。

![](img/7d73076d557c7522180e34375b937db4.png)

**Figure 21\. Composite learning combining supervised pre-training, imitation learning, and online RL**

谷歌研究人员提出了一种结合人类教学和 RL [37](https://www.alibabacloud.com/blog/as) 的复合学习方法，该方法在监督预训练和在线 RL 之间增加了一个人类教学阶段，允许人类标记数据，以避免监督预训练引起的协变量偏移[42]。亚马逊的研究人员也提出了类似的人类教学框架[37]:在每一轮对话中，系统向客服专家推荐四个回答。客户服务专家确定是选择这些响应之一还是创建新的响应。最后，客户服务专家将选择或创建的响应发送给用户。通过这种方法，开发人员可以快速更新对话系统的功能。

在前面的方法中，系统被动地接收由人标记的数据。但是，一个好的系统应该主动提出问题，寻求人类的帮助。一篇论文[40]介绍了同伴学习架构(如图 22 所示)，它将教师(人)的角色添加到传统的 RL 框架中。教师可以对对话系统(学生，图左侧的开关代表)的反应进行纠正，并以内在奖励的形式对学生的反应进行评估(图右侧的开关)。为了实现主动学习，作者提出了对话决策确定性的概念。学生策略网络通过辍学进行多次采样，以获得所需操作的估计近似最大概率。然后通过最大概率计算几轮对话的移动平均值，作为学生政策网络的决策可信度。如果所计算的确定性低于目标值，则系统基于所计算的决策的确定性和目标值之间的差异来确定是否需要教师纠正错误并提供奖励函数。如果计算的确定性高于目标值，系统停止向老师学习，并自行做出判断。

![](img/bdd502572023fb7d04d7321c1129c786.png)

**Figure 22\. The teacher corrects the student’s response (on the left) or evaluates the student’s response (on the right).**

主动学习的关键是估计对话系统关于它自己的决定的确定性。除了丢弃策略网络，其他方法还包括使用隐变量作为条件变量来计算策略网络的 Jensen-Shannon 散度[22]以及基于当前系统的对话成功率做出判断[36]。

# 智能机器人对话式人工智能团队的对话管理框架

为了确保稳定性和可解释性，业界主要使用基于规则的数据挖掘模型。阿里巴巴 DAMO 研究院的智能机器人对话式人工智能团队去年开始探索数据挖掘模型。在构建一个真实的对话系统时，我们需要解决两个问题:(1)如何在特定场景下获取大量的对话数据，(2)如何利用算法实现数据价值的最大化。

目前，我们计划分四步完成模型框架设计，如图 23 所示。

![](img/578984a3e33e11358a88a9001e1c03c9.png)

**Figure 23\. Four steps of DM model design**

*   **第一步:**首先，使用智能机器人对话式 AI 团队自主研发的 dialog studio，基于基于规则的对话流，快速构建一个名为 TaskFlow 的对话引擎，并构建一个具有相似对话流的用户模拟器。然后，让用户模拟器和任务流不断地相互交互，以生成大量的对话数据。
*   **第二步:**通过监督学习训练一个神经网络，建立一个初步的 DM 模型，其能力基本相当于一个基于规则的对话引擎。该模型可以通过结合语义相似度匹配和端到端生成进行扩展。使用 HRL 方法划分具有大动作空间的对话任务。
*   **第三步:**在开发阶段，使系统与改进的用户模拟器或 AI 训练器进行交互，并基于非策略的 ACER RL 算法不断增强系统对话能力。
*   **第四步:**人机交互体验通过验证后，启动系统，引入人工角色，收集真实的用户交互数据。此外，使用一些 UI 设计来轻松引入用户反馈，以不断更新和增强模型。获得的人机对话数据将被进一步分析和挖掘，以获得客户洞察。

目前，我们开发的基于 RL 的 DM 模型可以用用户模拟器完成 80%的对话，用于中等复杂的对话任务，例如预订会议室，如图 24 所示。

![](img/99173ff37f176ff297fd8a444f777c1b.png)

**Figure 24\. Framework and evaluation indicators of the DM model developed by the Intelligent Robot Conversational AI team**

# 摘要

本文详细介绍了数据挖掘模型的最新研究成果，重点讨论了传统数据挖掘模型的三个缺点:

*   扩展性差
*   标记数据不足
*   培训效率低

为了解决可扩展性问题，处理用户意图、对话体和系统动作空间变化的常用方法包括语义相似性匹配、知识提取和序列生成。为了解决标记数据不足的问题，方法包括自动机器标记、有效的对话结构挖掘和有效的数据收集策略。针对传统数据挖掘模型训练效率低的问题，采用 HRL 和 FRL 等方法将动作空间划分为不同的层次。基于模型的 RL 方法也用于对环境建模并提高训练效率。将人在回路引入对话系统训练框架也是当前的研究热点。最后，我讨论了由阿里巴巴 DAMO 研究院智能机器人对话式人工智能团队开发的数据挖掘模型的最新进展。希望这个总结能提供一些新的见解，支持你自己对 DM 的研究。

# 参考

[1].TURING A M. I. — COMPUTING MACHINERY AND INTELLIGENCE[J]. Mind, 1950, 59(236): 433–460.
[2].Weizenbaum J. ELIZA — -a computer program for the study of natural language communication between man and machine[J]. Communications of the ACM, 1966, 9(1): 36–45.
[3].Young S, Gašić M, Thomson B, et al. Pomdp-based statistical spoken dialog systems: A review[J]. Proceedings of the IEEE, 2013, 101(5): 1160–1179.
[4].Bordes A, Boureau Y L, Weston J. Learning end-to-end goal-oriented dialog[J]. arXiv preprint arXiv:1605.07683, 2016.
[5].Wen T H, Vandyke D, Mrksic N, et al. A network-based end-to-end trainable task-oriented dialogue system[J]. arXiv preprint arXiv:1604.04562, 2016.
[6].Su P H, Budzianowski P, Ultes S, et al. Sample-efficient actor-critic reinforcement learning with supervised data for dialogue management[J]. arXiv preprint arXiv:1707.00130, 2017.
[7]. Serban I V, Sordoni A, Lowe R, et al. A hierarchical latent variable encoder-decoder model for generating dialogues[C]//Thirty-First AAAI Conference on Artificial Intelligence. 2017.
[8]. Berant J, Chou A, Frostig R, et al. Semantic parsing on freebase from question-answer pairs[C]//Proceedings of the 2013 Conference on Empirical Methods in Natural Language Processing. 2013: 1533–1544.
[9]. Dhingra B, Li L, Li X, et al. Towards end-to-end reinforcement learning of dialogue agents for information access[J]. arXiv preprint arXiv:1609.00777, 2016.
[10]. Lei W, Jin X, Kan M Y, et al. Sequicity: Simplifying task-oriented dialogue systems with single sequence-to-sequence architectures[C]//Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers). 2018: 1437–1447.
[11]. Madotto A, Wu C S, Fung P. Mem2seq: Effectively incorporating knowledge bases into end-to-end task-oriented dialog systems[J]. arXiv preprint arXiv:1804.08217, 2018.
[12]. Mrkšić N, Séaghdha D O, Wen T H, et al. Neural belief tracker: Data-driven dialogue state tracking[J]. arXiv preprint arXiv:1606.03777, 2016.
[13]. ¬Ramadan O, Budzianowski P, Gašić M. Large-scale multi-domain belief tracking with knowledge sharing[J]. arXiv preprint arXiv:1807.06517, 2018.
[14]. Weisz G, Budzianowski P, Su P H, et al. Sample efficient deep reinforcement learning for dialogue systems with large action spaces[J]. IEEE/ACM Transactions on Audio, Speech and Language Processing (TASLP), 2018, 26(11): 2083–2097.
[15]. Wang W, Zhang J, Zhang H, et al. A Teacher-Student Framework for Maintainable Dialog Manager[C]//Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing. 2018: 3803–3812.
[16]. Yun-Nung Chen, Dilek Hakkani-Tur, and Xiaodong He, “Zero-Shot Learning of Intent Embeddings for Expansion by Convolutional Deep Structured Semantic Models,” in Proceedings of The 41st IEEE International Conference on Acoustics, Speech, and Signal Processing (ICASSP 2016), Shanghai, China, March 20–25, 2016\. IEEE.
[17]. Rastogi A, Hakkani-Tür D, Heck L. Scalable multi-domain dialogue state tracking[C]//2017 IEEE Automatic Speech Recognition and Understanding Workshop (ASRU). IEEE, 2017: 561–568.
[18]. Mesnil G, He X, Deng L, et al. Investigation of recurrent-neural-network architectures and learning methods for spoken language understanding[C]//Interspeech. 2013: 3771–3775.
[19]. Bapna A, Tur G, Hakkani-Tur D, et al. Towards zero-shot frame semantic parsing for domain scaling[J]. arXiv preprint arXiv:1707.02363, 2017.
[20]. Wu C S, Madotto A, Hosseini-Asl E, et al. Transferable Multi-Domain State Generator for Task-Oriented Dialogue Systems[J]. arXiv preprint arXiv:1905.08743, 2019.
[21]. He J, Chen J, He X, et al. Deep reinforcement learning with a natural language action space[J]. arXiv preprint arXiv:1511.04636, 2015.
[22]. Wang W, Zhang J, Li Q, et al. Incremental Learning from Scratch for Task-Oriented Dialogue Systems[J].arXiv preprint arXiv:1906.04991, 2019.
[23]. Shi C, Chen Q, Sha L, et al.Auto-Dialabel: Labeling Dialogue Data with Unsupervised Learning[C]//Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing. 2018: 684–689.
[24]. Haponchyk I, Uva A, Yu S, et al. Supervised clustering of questions into intents for dialog system applications[C]//Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing. 2018: 2310–2321.
[25]. Shi W, Zhao T, Yu Z. Unsupervised Dialog Structure Learning[J]. arXiv preprint arXiv:1904.03736, 2019.
[26]. Zhao T, Xie K, Eskenazi M. Rethinking action spaces for reinforcement learning in end-to-end dialog agents with latent variable models[J]. arXiv preprint arXiv:1902.08858, 2019.
[27]. Shah P, Hakkani-Tur D, Liu B, et al. Bootstrapping a neural conversational agent with dialogue self-play, crowdsourcing and on-line reinforcement learning[C]//Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 3 (Industry Papers). 2018: 41–51.
[28]. Budzianowski P, Wen T H, Tseng B H, et al. Multiwoz-a large-scale multi-domain wizard-of-oz dataset for task-oriented dialogue modelling[J]. arXiv preprint arXiv:1810.00278, 2018.
[29]. Peng B, Li X, Li L, et al. Composite task-completion dialogue policy learning via hierarchical deep reinforcement learning[J]. arXiv preprint arXiv:1704.03084, 2017.
[30]. Kristianto G Y, Zhang H, Tong B, et al. Autonomous Sub-domain Modeling for Dialogue Policy with Hierarchical Deep Reinforcement Learning[C]//Proceedings of the 2018 EMNLP Workshop SCAI: The 2nd International Workshop on Search-Oriented Conversational AI. 2018: 9–16.
[31]. Tang D, Li X, Gao J, et al. Subgoal discovery for hierarchical dialogue policy learning[J]. arXiv preprint arXiv:1804.07855, 2018.
[32]. Casanueva I, Budzianowski P, Su P H, et al. Feudal reinforcement learning for dialogue management in large domains[J]. arXiv preprint arXiv:1803.03232, 2018.
[33]. Peng B, Li X, Gao J, et al. Deep dyna-q: Integrating planning for task-completion dialogue policy learning[J]. ACL 2018.
[34]. Su S Y, Li X, Gao J, et al. Discriminative deep dyna-q: Robust planning for dialogue policy learning.EMNLP, 2018.
[35]. Wu Y, Li X, Liu J, et al. Switch-based active deep dyna-q: Efficient adaptive planning for task-completion dialogue policy learning.AAAI, 2019.
[36]. Zhang Z, Li X, Gao J, et al. Budgeted Policy Learning for Task-Oriented Dialogue Systems. ACL, 2019.[37]. Abel D, Salvatier J, Stuhlmüller A, et al. Agent-agnostic human-in-the-loop reinforcement learning[J]. arXiv preprint arXiv:1701.04079, 2017.
[38]. Liu B, Tur G, Hakkani-Tur D, et al. Dialogue learning with human teaching and feedback in end-to-end trainable task-oriented dialogue systems[J]. arXiv preprint arXiv:1804.06512, 2018.
[39]. Lu Y, Srivastava M, Kramer J, et al. Goal-Oriented End-to-End Conversational Models with Profile Features in a Real-World Setting[C]//Proceedings of the 2019 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 2 (Industry Papers). 2019: 48–55.
[40]. Chen L, Zhou X, Chang C, et al. Agent-aware dropout dqn for safe and efficient on-line dialogue policy learning[C]//Proceedings of the 2017 Conference on Empirical Methods in Natural Language Processing. 2017: 2454–2464.
[41]. Gao J, Galley M, Li L. Neural approaches to conversational AI[J]. Foundations and Trends® in Information Retrieval, 2019, 13(2–3): 127–298.
[42]. Ross S, Gordon G, Bagnell D. A reduction of imitation learning and structured prediction to no-regret online learning[C]//Proceedings of the fourteenth international conference on artificial intelligence and statistics. 2011: 627–635.
[43]. Rajendran J, Ganhotra J, Polymenakos L C. Learning End-to-End Goal-Oriented Dialog with Maximal User Task Success and Minimal Human Agent Use[J]. Transactions of the Association for Computational Linguistics, 2019, 7: 375–386.
[44]. Mrkšić N, Vulić I. Fully Statistical Neural Belief Tracking[C]//Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (Volume 2: Short Papers). 2018: 108–113.
[45]. Zhou L, Small K. Multi-domain Dialogue State Tracking as Dynamic Knowledge Graph Enhanced Question Answering[J]. arXiv preprint arXiv:1911.06192, 2019.
[46]. Rajpurkar P, Jia R, Liang P. Know What You Don’t Know: Unanswerable Questions for SQuAD[J]. arXiv preprint arXiv:1806.03822, 2018.
[47]. Zhang J G, Hashimoto K, Wu C S, et al. Find or Classify? Dual Strategy for Slot-Value Predictions on Multi-Domain Dialog State Tracking[J]. arXiv preprint arXiv:1910.03544, 2019.

*你渴望了解阿里云的最新科技趋势吗？在我们新推出的系列产品中，请听听我们的顶级专家的意见，* [*科技展*](https://resource.alibabacloud.com/webinar/topic/tech-show.html) *！*

# 原始来源:

[](https://www.alibabacloud.com/blog/progress-in-dialog-management-model-research_596140) [## 对话管理模型研究进展

### 阿里巴巴云 2020 年 4 月 20 日 455 本文是以下专家和…

www.alibabacloud.com](https://www.alibabacloud.com/blog/progress-in-dialog-management-model-research_596140)