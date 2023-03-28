# Quora 虚假问题分类问题探讨

> 原文：<https://medium.datadriveninvestor.com/approaching-the-quora-insincere-question-classification-problem-eb27b0ad3100?source=collection_archive---------9----------------------->

![](img/3c3901ed0c412e5d3dbde45cd463cee5.png)

Quora 无诚意问题分类是 kaggle 在自然语言处理领域组织的一次挑战。挑战的主要目的是找出有毒和分裂的内容。这是一个二元分类问题，其中 0 类代表不真诚的问题，1 类代表不真诚的问题。这个博客将专门讨论数据建模部分。

# 预处理:

第一步，我们将使用 pandas 读取数据。这段代码片段会将文件读入熊猫数据帧。

```
train=pd.read_csv(‘/kaggle/input/quora-insincere-questions-classification/train.csv’)
test_df=pd.read_csv(‘/kaggle/input/quora-insincere-questions-classification/test.csv’)
sub=pd.read_csv(‘/kaggle/input/quora-insincere-questions-classification/sample_submission.csv’)
```

我们可以用 shape 方法知道数据的形状。

最初，我们会尝试将训练数据集分为训练和验证两部分。为此，我们可以借助 sklearn。下面的代码片段将帮助我们实现它。

```
train_df,val_df=train_test_split(train,test_size=0.1)
```

在第一步中，我们将尝试填充包含空值的问题。为此我们可以使用 ***fillna*** 方法。下面的代码片段会做同样的事情。

```
train_x=train_df['question_text'].fillna('__na__').values
val_x=val_df['question_text'].fillna('__na__').values
test_x=test_df['question_text'].fillna('__na__').values
```

现在是选择一些重要参数的时候了。这些是*嵌入尺寸*、*最大特征*和*最大长度*。这里，embedd_size 表示我们要表示的每个单词的单词向量大小，而 max_features 表示我们应该考虑的最高频率单词的数量。例如，如果我们考虑 max_feature 为 50000，这将意味着我们在将 50000 个最常出现的单词转换成向量时，应该将它们考虑在内。类似地 *max_len* 将暗示我们将从头开始多少单词。例如 *max_len* 100 意味着我们只考虑前 100 个单词。以下是为此选择的参数。

```
embedd_size=300
max_features=50000
max_len=100
```

现在考虑下面的代码片段。

```
tokenizer=Tokenizer(num_words=max_features)
tokenizer.fit_on_texts(list(train_df))
train_x=tokenizer.texts_to_sequences(train_x)
val_x=tokenizer.texts_to_sequences(val_x)
test_x=tokenizer.texts_to_sequences(test_x)
```

在这里，我们将在第一行中考虑最常见的 50000 个单词。第二行将根据每个单词在句子中出现的位置将其转换成一个唯一的数字。第三、第四和第五行中的 text_to_sequence 方法会将每个句子转换成数字。例如，要转换"*India wind the match*"我们将在前面的方法 ***fit_on_texts*** 中查找分配给每个单词的整数，并相应地更改句子。

```
train_x=pad_sequences(train_x,maxlen=max_len)
val_x=pad_sequences(val_x,maxlen=max_len)
test_x=pad_sequences(test_x,maxlen=max_len)
```

上面的代码片段将确保每个句子都被转换成特定的长度。这样做是为了在成批给出这些序列时，它们将适合特定的长度。因此，需要填充或截短一些序列。

[](https://www.datadriveninvestor.com/2020/07/31/using-machine-learning-in-brain-computer-interfaces/) [## 在脑机接口中使用机器学习|数据驱动的投资者

### 神经技术是一个刚刚开始大步前进的前沿领域。有了所有的技术…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/07/31/using-machine-learning-in-brain-computer-interfaces/) 

# 建模:

为了建立这个分类模型，我们将采用双向 lstm。在此之前，我们必须将文本转换成数字。我们在最后一段做了第一步，每个单词都被转换成唯一的整数。下一步，我们将使用 keras 嵌入层将单词转换成矢量。我们也可以选择使用任何预训练的单词嵌入，但这里我们选择了嵌入层来在训练时学习单词嵌入。嵌入层最初给单词分配随机向量，但是随着模型训练的进行，学习每个单词的嵌入。下面的片段告诉我们整个建模策略。

```
inp=Input(shape=(max_len))
x=Embedding(max_features,embedd_size)(inp)
x=Bidirectional(LSTM(128,return_sequences=**True**))(x)
x=GlobalMaxPool1D()(x)
x=Dense(16,activation='relu')(x)
x=Dropout(0.2)(x)
x=Dense(1,activation='sigmoid')(x)
model=Model(inputs=inp,outputs=x)
model.compile(loss='binary_crossentropy',optimizer='adam',metrics=['accuracy'])
```

在嵌入之后，我们将使用双向 lstm。这里的参数***return sequence = True***暗示我们希望得到每个隐藏状态的输出。最差的一个是假的，这意味着我们只想要最终状态的输出。类似地， ***GlobalMaxPool1D*** 意味着对于每个句子向量，我们将只取最高值。添加脱落层以处理过拟合。具有 sigmoid 激活函数的密集层将输出 0 和 1 之间的值。compile 方法在尚未执行任何训练的情况下构建模型。

在编译方法中，我们只定义了架构并初始化了它。现在我们必须调整参数，以获得最佳模型。为此，我们通过模型传递训练数据。*拟合*方法通过模型传递数据并计算损失。同样基于损耗，它进行反向传播并调整参数。下面的代码片段做了同样的事情。

```
model.fit(train_x,train_out,batch_size=256,epochs=2,validation_data=(val_x,val_out))
```

经过 2 个时期的训练，该模型达到了 93%的准确率。我们可以改变参数并进行超参数调整以获得更好的模型。

本次比赛的绩效指标是 F1 分数。因为数据集是不平衡的。

来预测我们可以写的模型

```
pred_y=model.predict([test_x],batch_size=256)
```

完整的代码可以在[https://github . com/mohantyaditya/quora-ulgency-classification/blob/master/quora % 20 ulgency . ipynb](https://github.com/mohantyaditya/quora-insincere-classification/blob/master/quora%20insincere.ipynb)找到

这是解决问题的一个非常基本的方法。我们可以尝试使用预先训练的嵌入向量来获得更好的结果。

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)