# 有毒评论分类:Kaggle 案例研究

> 原文：<https://medium.datadriveninvestor.com/toxic-comment-classification-a-kaggle-case-study-a929b37150b?source=collection_archive---------0----------------------->

![](img/23a430609fff34690b1384c611114fdd.png)

(Photo By Dimitri Karastev On Unsplash)

**毒性评论分类**是 nlp 领域流行的 kaggle 比赛。这场比赛大约两年前就结束了。挑战的主要目的是在网上评论中发现不同类型的毒性，如 ***【威胁】******淫秽******侮辱******基于身份的仇恨*** 。该数据集是从维基百科的对话页面链接中收集的。要了解更多关于比赛的信息，请访问比赛主页[https://www . ka ggle . com/c/jigsaw-toxic-comment-class ification-challenge](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge)。

## 数据集:

收集的数据集已经被人类评级员标记为有毒行为。毒性类型分别标注为 ***毒性******重度 _ 毒性******淫秽******威胁******侮辱*** 和***身份仇恨*** *。*我们的目标是建立一个能获取仇恨程度的模型。

为了加载数据集，我们可以使用 pandas 库。包含培训、测试和提交文件的数据集已在竞赛主页中提供。

为了读取数据帧，我们将使用下面的代码。

```
train=pd.read_csv(‘/home/aditya123/Downloads/jigsaw-toxic-comment-classification-challenge/train.csv’)
test=pd.read_csv(‘/home/aditya123/Downloads/jigsaw-toxic-comment-classification-challenge/test.csv’)
```

上面的代码片段加载数据集。现在我们可以使用下面的代码片段来了解更多。知道

```
train.head()train.describe()
```

## 预处理:

按照预处理步骤，我们将检查列中是否存在任何空值。如果它存在，那么我们将通过 *fillna* 方法填充它。此外，我们会把所有的字符变成小写形式。在目标值中我们将列值作为等级，分别为****【严重 _ 中毒】******淫秽******威胁******侮辱******身份 _ 仇恨*为此，我们可以编写以下代码片段。***

```
*train[‘comment_text’].fillna(‘fillna’)
test[‘comment_text’].fillna(‘fillna’)
x_train=train[‘comment_text’].str.lower()
y_train=train[[“toxic”, “severe_toxic”, “obscene”, “threat”, “insult”, “identity_hate”]].values
x_test=test[‘comment_text’].str.lower()*
```

## *特色化:*

*深度学习或机器学习模型无法理解人类语言。因此，我们需要将它们转换成数学形式，这将是一个特定维度的向量，将其作为模型的输入。有许多方法可以做到这一点，例如我们可以使用 tfidf 等统计方法，或者我们可以借助 word2vec 或 glove 等预训练模型将它们转换为向量。我们还可以使用 gensim 包从头开始构建一个单词嵌入模型。然而，在这种情况下，我们将采取 keras 嵌入层的帮助。因此嵌入层获取索引并将它们映射到密集向量中。它将**将整数作为输入**，并在字典中寻找其**对应的密集向量**，并将其返回，作为深度学习模型的输入。*

*[](https://www.datadriveninvestor.com/2019/01/23/deep-learning-explained-in-7-steps/) [## 深度学习用 7 个步骤解释-更新|数据驱动的投资者

### 在深度学习的帮助下，自动驾驶汽车、Alexa、医学成像-小工具正在我们周围变得超级智能…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/23/deep-learning-explained-in-7-steps/) 

# 嵌入层:

嵌入层采用整数的 2D 张量作为输入，其将样本数和序列长度作为输入。要成批嵌入可变长度的序列，我们必须使它们具有相同的长度。采取这一步是因为我们应该把它们带到张量。因此，这确保了大于某个阈值的序列将被截断，另一方面，小于某个阈值的序列必须用零填充。

## 如何在嵌入层中调整权重:

最初，嵌入层的权重以随机权重的任意方式开始。在训练过程中，模型通过反向传播学习找到合适的权重。完成训练后，它将能够找到一个合适的结构。

## 双向 LSTM:

调整嵌入向量后，我们将建立模型。这里，我们将使用一种称为双向 lstm 的深度学习模型，而不是传统的机器学习。虽然****是对 RNNs 的改进，在一定程度上解决了消失梯度问题，但是双向也允许 LSTM 从相反方向获得上下文。****

## ****GlobalMaxPool1D:****

****Globalmaxpool 类似于任何其他池，池长度等于整个输入长度。例如，如果我们有一个池长度为 3 的输入[2，3，4，5，6，6，7]，则输出将分别为 4，5，6，6，7，而 globalmaxpool1d 将获取输出 7。****

## ****辍学:****

****Dropout 随机忽略某些神经元，从而避免过度拟合的问题。这意味着所选择的神经元在训练时的向前或向后传递期间将不被考虑。****

****![](img/c9839959a28b0a070c62e100c202a778.png)****

****(Pic Credit: Srivastava, Nitish, et al. ”Dropout: a simple way to prevent neural networks from
overfitting”, JMLR 2014)****

## ****回访:****

****我们几乎不可能决定模型需要多少个历元才能获得最佳参数集。因此，我们应该对模型进行监控，并在验证损失不再改善时停止训练，而不是对任意数量的时期任意训练模型。因此*回调*是在拟合模型时传递的对象，并在训练的各个部分被调用。****

## ****代码:****

****理论到此为止！！！！现在让我们直接构建模型。我们将使用 keras 功能 api 对其进行编码。****

```
****embed_size=100
max_features=20000
max_len=100****
```

****这里我们指定了 3 个参数。嵌入大小将把每个单词转换成 100 维向量。 *max_features* 参数告诉要考虑的前 20000 个常用词。类似地， *max_len* 参数表示要考虑的每个输入的大小，这里取为 100。如果我们的句子长度超过 100，它将被截断，否则它将用零填充。下面的代码片段完成了上述的大部分任务，这是不言自明的。****

```
****tokenizer= Tokenizer(num_words=max_features,lower= True)
tokenizer.fit_on_texts(list(x_train))
tokenized_train=tokenizer.texts_to_sequences(x_train)
tokenized_test=tokenizer.texts_to_sequences(x_test)
train_x=pad_sequences(tokenized_train,maxlen=max_len)
test_x=pad_sequences(tokenized_test,maxlen=max_len)****
```

****因为我们有 6 个不同的类，我们将有一个有 6 个神经元的密集层。我们会把它附加在模型的末尾。参见下面的代码片段，了解如何使用 keras functional api 构建模型。****

```
****inp = Input(shape=(max_len,))
x = Embedding(max_features,embed_size)(inp)
x = Bidirectional(LSTM(64, return_sequences=True))(x)
x = GlobalMaxPool1D()(x)
x= Dropout(0.1)(x)
x= Dense(6,activation=”sigmoid”) (x)
model = Model(inputs=inp, outputs=x)
model.compile(loss=’binary_crossentropy’,optimizer= Adam(lr=1e-3),metrics=[‘accuracy’])
print(model.summary())****
```

****当我们使用函数式 api 来构建模型时，它以张量的形式接受输入。我们之前已经讨论过模型架构。这里需要注意的重要一点是 ***编译*** 方法。它构建了模型架构，其中**还没有执行**训练。****

****如前所述，我们可以利用回调对模型进行适当的训练。我们还将使用模型检查点来存储模型在不同训练点的权重。下面的代码片段实现了同样的目的****

```
****callbacks_list = [keras.callbacks.EarlyStopping(monitor=’acc’,patience=2,), keras.callbacks.ModelCheckpoint(filepath=’my_model.h5',monitor=’val_loss’,save_best_only=True,)]****
```

****这里，耐心参数表示我们希望看到没有改善的时期的数量。****

****在编译方法中，我们只定义了架构并初始化了它。现在我们必须调整参数，以获得最佳模型。为此，我们通过模型传递训练数据。*拟合*方法通过模型传递数据并计算损失。同样基于损耗，它进行反向传播并调整参数。下面的代码片段做了同样的事情****

```
****model.fit(train_x,y_train,epochs=epochs,batch_size=batch_size,validation_split=0.1,callbacks=callbacks_list,verbose=1)****
```

****我们可以根据产生的结果改变参数。运行 5 个时期后，达到的验证精度为 0.98。我们可以尝试更多数量的 lstms 和更多的 epochs 来改善这一点。****

****现在，为了进行预测，我们将使用 ***预测*** 方法。****

```
****y_pred=model.predict(test_x,batch_size=batch_size,verbose=1)****
```

## ****提交:****

****在培训并获得输出后，我们将提交输出。同样，我们将使用 csv 文件来写入结果。下面的代码片段实现了同样的目的****

```
****submission=pd.read_csv(‘/home/aditya123/Downloads/jigsaw-toxic-comment-classification-challenge/sample_submission.csv’)
submission[[“toxic”,”severe_toxic”,”obscene”,”threat”,”insult”,”identity_hate”]]=y_pred
submission.to_csv(‘submission.csv’,index=False)****
```

****提交后，我们获得了 0.96670 的分数。我们可以通过更好的超参数调整和运行更多的历元来改善它。****

****完整代码可在[https://github . com/mohantyaditya/Toxic-Comment-identificati on](https://github.com/mohantyaditya/Toxic-Comment-identification)获得。*****