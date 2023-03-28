# Python 中的“填充”对 NLP 项目的贡献

> 原文：<https://medium.datadriveninvestor.com/padding-used-in-nlp-are-they-improvers-2f4613bd3648?source=collection_archive---------1----------------------->

## 使用 Python-tensor flow，我们可以在 NLP 阶段使用促进填充进行句子分段和分析。那怎么做呢？

![](img/b0317fa20c1a97f3ece58791b1abeca0.png)

Photo by [João Vítor Heinrichs](https://www.pexels.com/de-de/@joao-vitor-heinrichs-862489?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels) from [Pexels](https://www.pexels.com/de-de/foto/bestand-an-holzstammen-mit-kratzern-5022456/?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels)

NLP 告诉我们，要按顺序做很多类似的事情。由于 TensorFlow 和 Keras 库，这些非常实用，可以很容易地集成到系统中。所以第一件事就是进口它们。事实上，我们的工作是能够使用现有的 API。因为轮子已经发明了！

NLP 是一组操作，旨在帮助机器在向量的帮助下对句子结构进行有意义的编码。当我们从这些现有的基础出发时，我们可以在小规模和类似的工作中看到标准。但是，随着数据的增长，不可避免地需要一些补丁。

**我们指的是什么？**

换句话说，当你进入作品的时候，是的，很多基本表达上的相似之处在句子编号的时候是非常容易的。例如，如下所示:

'我喜欢这个游戏'
'你喜欢打网球'
'我和你一样喜欢'

虽然这三个句子总共有 12 个单词，但当我们除去常见的，只有 8 个保持独特。所以在用记号赋予器引导它们之前，在 NLP 过程中很容易枚举它们。以下是代码:

首先，我们需要导入我们将使用的 TensorFlow 库。

```
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras.preprocessing.text import Tokenizer
```

然后，我们把上面的例子作为代码的延续，扔给一个变量。

```
sentences=[
'I like this game’
‘You like tennis play’
‘i like as you'
]
```

现在我们让编号过程从 tokenizer 变量开始。

```
tokenizer = Tokenizer(num_words = 100)
tokenizer.fit_on_texts(sentences)
word_index = tokenizer.word_index
```

**让我们看看代码做了什么:**

首先，我们有几个已知的或可以在这里统计的例句，实际上，很明显我们会为此对单词进行编号。我们已经数过了，开头也说过了。然而，当处理`num_words`更大的数据时，等式对于大的数字可以是一致的。因为这里的目标是优化训练时间，所以在给出数字时要小心。但是，我们将为 num_word 输入数字 100,“假设”这是一个常规的默认值。

在我们的第二个观察中，`fit_on_texts`获取 value=sentences 变量中的数据，并开始对内容进行编码。

最后，`word_index`返回一个包含键值对的字典。在这里，该关键字将被赋予一个唯一的值。现在让我们看看打印的结果:

![](img/b7323d1cba88889fad580bce13a0bdfb.png)

我们可以看到，重复的单词被赋予了唯一的值。这就像用 Python 中的 set 参数返回列表中的 unique，但是字典在表达式中带有格式 key & value。首先理解这一点很重要。

## 我们正在向需要补丁的地方前进

我们上面只是想解释如何快速构建句子间有相似性的小系统。然而，这个 NLP 对于我们的业务来说还是太小了。

所以让我们把事情弄得更复杂一点。首先，我们的目标是用我们现在用数字表达的单词来创建向量句子结构。对此，我们可以用`texts_to_sequence`进入神经网络创建和训练数据准备阶段。拟合不同尺寸的类似过程也用于利用图像的模型训练。在理解和使用正确的 API 方面，我们处于一个重要的位置。

这里，让我们通过检查上面的例子来继续。首先，样本三个句子由相同的数字和相似的单词组成。现在让我们来看看这个:

**补充一句:**‘你到底喜欢哪个游戏？’
我们可以如下创建“序列变量”。文本中字符串表达式的标记器:

```
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras.preprocessing.text import Tokenizersentences = [
    'I like this game',
    'You like tennis play',
    'i like as you',
    'Which game do you like really?'
]tokenizer = Tokenizer(num_words = 100)
tokenizer.fit_on_texts(sentences)
word_index = tokenizer.word_indexsequences=tokenizer.texts_to_sequences(sentences)print(word_index)
print(sequences)
```

**输出:**

![](img/1aac3a959500a79d7d499fae0e03d7bc.png)

正如您所看到的，当我们将数字替换为我们指定的关键字`word_index`时，我们的最后一句话可以像前三句话一样进行排序。文本之间的单词被机器识别、编码和排列。

在这个阶段，我们可以说这是所有情感分析研究不可或缺的。因为如果我们想要从文本中提取的单词不能由相同的数字和它们在字符串中的位置来确定，那么一切都将变得毫无意义。

现在让我们根据列举的词语考虑一个新的测试数据:

```
test= [
    'i really like this game',
    'your husband likes this tennis'
]test_sequences=tokenizer.texts_to_sequences(test)print(test_sequences)
```

![](img/2d4fc89f165e3244a3d2e57a21ce7312.png)

对于第一句，我们有足够的数字，但对于第二句，我们不能说同样的话。好吧，我们的问题是:

*   "我们是接受这种形式的第二句，还是忽略它？"

是的，我们会忽略一些东西，但我们会为此人为地填补空白。当我们遇到一个在我们的系统中不可见的值时，我们不会将其留空，而是再次输入一个特殊的值。

**所以参数**中的< OOV >

一个特殊的令牌执行这个功能。在 tokenizer 变量的参数中用`oov_token("<OOV>"`表示。

```
tokenizer=Tokenizer(num_word=100, oov_token="<oov>") 
```

因此，我们的记号赋予器变量获得了新的特性。然后输出相同的测试结果:

```
print(test_sequences)output:[[4, 12, 2, 6, 5], [1, 1, 1, 6, 7]]
```

如您所见，被分配了编号 1，这也影响了其他现有的编号。

作为这个过程的延续，填充是我们填充数组中空白空间的材料，用于创建相同大小的向量。为此，必须首先从库中导入它:

```
from tensorflow.keras.preprocessing.sequence import pad_sequences
```

现在让我们来看看如何显示我们在开始时举例的句子中的 4 个句子:

```
sentences = [
 ‘I like this game’,
 ‘You like tennis play’,
 ‘i like as you’,
 ‘Which game do you like really?’]padded=pad_sequences(sequences)print(word_index)
print(padded)
```

**输出:**

```
{'<OOV>': 1, 'like': 2, 'you': 3, 'i': 4, 'game': 5, 'this': 6, 'tennis': 7, 'play': 8, 'as': 9, 'which': 10, 'do': 11, 'really': 12}[[ 0  0  4  2  6  5]     #i like this game
 [ 0  0  3  2  7  8]     #you like tennis play
 [ 0  0  4  2  9  3]     #i like as you
 [10  5 11  3  2 12]]    #which game do you like really
```

结果，我们达到了目的。换句话说，对列表中句子的数字表达式进行了必要的分配，我们能够创建一个行长度相同的矩阵。

当然要感谢 padding！

# 结论

在开始神经网络创建过程的训练之前，数据的符合性是模型的最重要的步骤。由于统一的尺寸，模型馈送有望给出更准确的结果。

对于这一切，我们试图理解导致我们“填充”的原因。我希望通过这个小例子，我们能更好地理解。其实对于很多看似无法编辑的流程，就像我们开头说的，API 都在等你在合适的时间用在 TensorFlow 里。

感谢您的阅读！