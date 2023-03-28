# 用序列对序列模型理解机器翻译

> 原文：<https://medium.datadriveninvestor.com/understanding-machine-translation-with-sequence-to-sequence-model-4ee8bab318b9?source=collection_archive---------4----------------------->

![](img/e168c76a96e49e36d012c6f3474c8078.png)

(Picture By Simon Migaj On Unsplash)

机器翻译是现代深度学习技术的最大应用之一，它使语言翻译变得非常容易，几乎准确。我们有基于变压器的架构，这种架构现在被认为是完成相同任务的最先进技术。在本文中，我们将重点关注序列对序列模型，这是以前的 SOTA。

## 编码器-解码器架构:

LSTMs 非常适合处理长期序列。但是对于这个机器翻译任务，我们将使用 lstm 的一个变体，称为编码器-解码器模型。编码器-解码器模型的前半部分是编码器，它在一些处理之后将原始自然语言表示转换成上下文向量。另一半是解码器，它根据从编码器获得的上下文向量以及原始翻译生成输出(在机器翻译模型中为*)。*

## 为什么选择编码器-解码器架构:

假设我们正在创建一个英语-印地语翻译模型。因此，对句子“*我想去印度*”的翻译将是“ *Main bharat jana chahta hun”。这两个句子长度不同。因此，基本语言模型(*多对多 lstm* )在这些情况下无法工作。因此，我们必须得到一个能够处理这两种情况的模型，也就是说，如果我们有相同的实际翻译长度，以及当我们有不同的长度。编码器-解码器架构有望解决这个问题。下图显示了编码器/解码器架构的基本结构。*

![](img/268fea229a2e68fdd85960858d43b9af.png)

(Encoder-Decoder Model For Machine Translation)

编码器部分产生作为解码器输入的上下文向量。然后，解码器在文本生成阶段使用这些向量作为输入来输出一系列标记。除了上下文向量，解码器还采用一种特殊的令牌，称为<start token="">。在每一个时间步骤中，解码器也获得期望的文本作为输入。但是在推理过程中不会发生同样的事情，因为我们没有预期的目标。这个问题被称为曝光偏差问题。在这种情况下，由解码器生成的第一令牌成为下一时间步的输入，依此类推。</start>

[](https://www.datadriveninvestor.com/2019/03/03/editors-pick-5-machine-learning-books/) [## DDI 编辑推荐:5 本让你从新手变成专家的机器学习书籍|数据驱动…

### 机器学习行业的蓬勃发展重新引起了人们对人工智能的兴趣

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/03/03/editors-pick-5-machine-learning-books/) 

这里，编码器的唯一目的是创建上下文向量，并且这样做编码器将需要解码器的帮助，因为没有目标上下文向量。具有反向传播的编码器将被训练以创建适当的上下文向量。

## 解码器的重要性:

解码器的结构与编码器相似，只是现在我们有了一个目标输出，基于该输出我们的模型的正确性将被评估。为了达到同样的目的，我们将把 lstm 的输出传递给一个密集层。致密层将具有一定数量的神经元，其数量将等于我们的语料库中的独特表征的数量。每一个时间步，我们将输出最可能的令牌作为输出。这将通过在密集层之后的 softmax 激活功能来完成。我们将简单地输出概率最高的令牌。这里要注意的一件重要事情是输入语料库和输出 vocab 的标记数量不需要相同。

## 预处理:

作为预处理步骤，我们将把每个序列填充到一定的长度，这将是最长句子的长度。不建议截断，因为我们可能会丢失一些信息。除此之外，输出序列必须用<start>和<end>标记进行注释，以告诉模型序列在哪里开始，在哪里结束。此外，我们不能将原始英语单词作为模型的输入，因此我们必须使用一些单词嵌入模型(如 word2vec 或 glove)将它们转换为向量，否则我们还可以借助嵌入层，这将使模型在训练时学习每个向量的单词嵌入。</end></start>

## Keras 中的序列到序列模型:

我们将使用 keras 功能 api 来编码编码器-解码器模型。下面的代码片段展示了如何用 keras 做到这一点

```
encoder_inputs= Input(shape=(None,input_vocab_size))
encoder = LSTM(num_neurons,return_state=True)
encoder_outputs,state_h,state_c=encoder(encoder_inputs)
encoder_states=(state_h,state_c)
```

关键字 ***return_state*** 设置为真，以返回每个时间步长的内部状态。正如我们所见，输出存储在*编码器 _ 输出*和 state_h 中。另外 *state_c* 代表最终的存储单元。一起*状态 _h* 和*状态 _c* 将形成最终的上下文向量。

```
decoder_inputs=Input(shape=(None,output_vocab_size))
decoder_lstm = LSTM(num_neurons,return_sequences=True,return_state=True)
decoder_outputs,_,_=decoder_lstm(decoder_inputs,initial_state=encoder_states)
decoder_dense= Dense(output_vocab_size,activation=’softmax’)
decoder_outputs=decoder_dense(decoder_outputs)model= Model(inputs=[encoder_inputs,decoder_inputs],outputs=decoder_outputs)
```

上面的代码片段显示了解码器单元的 keras 代码。我们可以看到初始状态被保存为 ***编码器 _ 状态，*** 是编码器的输出。我们保持参数***return _ sequences***为真，因为我们希望模型在每个时间步输出一个令牌。对于我们的机器翻译模型，我们将给出预期的输出作为解码器的输入，例如英语句子的印地语翻译。如前所述，我们有一个带有 softmax 激活的密集层，用于在每个时间步长中输出最可能的单词。

## 推论:

在用数据集训练我们的模型之后，数据集将具有英语句子的实际翻译，轮到我们实时生成翻译。这一次我们不会有真正的翻译，所以前一时间步的输出作为解码器的输入。推理会一直继续，直到达到最大字数或任何定制的停止条件。

这是一种理论方法，可以看出机器翻译是如何使用序列对序列模型进行工作的。在下一篇文章中，我们将看到如何使用相同的模型从头开始构建 chatbot。