# 在 Keras 中创建自定义数据生成器

> 原文：<https://medium.datadriveninvestor.com/creating-a-custom-data-generator-in-keras-534fd3098a58?source=collection_archive---------1----------------------->

![](img/fb0a563d26d4578ba10798b9642120b8.png)

(Pic Source Unsplash)

这是数据时代。随着大量数据的出现，有时我们对内存有很高的要求。当训练深度学习模型时，我们还需要大量数据来让模型创建任何有意义的东西。但是由于我们内存的限制，如果数据很大的话，不可能把所有的数据都加载到内存中。如果我们将所有数据都加载到内存中，很可能会耗尽内存。因此，我们不得不寻找一种替代方法，而不是将全部数据加载到内存中。

# 自定义数据生成器:

如果我们加载部分数据，而不是将全部数据加载到内存中，会怎么样？所以我们会把数据分批次。并在需要时将每一批数据加载到内存中。这样我们可以节省大量的内存，剩下的部分 ram 可以用来训练模型。在深入研究 keras 的定制数据生成器之前，让我们先了解一下 python 生成器。

[](https://www.datadriveninvestor.com/2019/01/23/deep-learning-explained-in-7-steps/) [## 深度学习用 7 个步骤解释-更新|数据驱动的投资者

### 在深度学习的帮助下，自动驾驶汽车、Alexa、医学成像-小工具正在我们周围变得超级智能…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/23/deep-learning-explained-in-7-steps/) 

## Python 生成器:

生成器类似于 python 中的任何其他函数，但它没有使用 ***return*** 关键字，而是使用了 ***yield*** 关键字。 ***return*** 关键字终止函数并完全返回所有值，而 yield 关键字保存状态并从该处继续。另外需要注意的一点是 yield 关键字返回一个对象，该对象的值可以通过使用 ***next()*** 方法来访问。所以基本上这些生成器帮助我们节省了 RAM，因为它不像 return 语句那样一次返回所有的值。下面的程序给出了一个 python 生成器的例子。

```
def gen(n):
 for i in range(n):
   yield ig=gen(2)print(g.__next()__)
print(g.__next()__)
```

在上面的代码片段中，第一条 print 语句输出的值是 0，而第二条 print 语句输出的值是 1。当函数产生一个值时，在保存状态之后，控制被转移到调用者。

现在我们对 python 生成器的工作原理有了一点了解，让我们创建一个定制的数据生成器。为此，我们将创建一个 ***数据生成器*** 类，它将继承***keras . utils . sequence***类。我们可以创建一个构造函数来初始化参数。让我们看看下面的代码片段。

```
def __init__(self, list_IDs, labels, batch_size=32, dim=(32,32,32), n_channels=1,
 n_classes=10, shuffle=True):
 ‘Initialization’
 self.dim = dim
 self.batch_size = batch_size
 self.labels = labels
 self.list_IDs = list_IDs
 self.n_channels = n_channels
 self.n_classes = n_classes
 self.shuffle = shuffle
 self.on_epoch_end()
```

正如我们所看到的，我们已经初始化了参数，其中包括关于数据的相关信息，如批量大小、标签、通道数量、类别等。现在让我们来看看 _epoch_end 上的方法 ***。*** 让我们看看同样的功能。

```
def on_epoch_end(self):
  self.indexes = np.arange(len(self.list_IDs))
  if self.shuffle == True:
    np.random.shuffle(self.indexes)
```

该方法在每个历元之后更新索引。此外，shuffle=True 参数可确保不同时期之间的批次不同。

还可以看看下面的方法，它得到每批的历元数。

```
def __len__(self):
 return int(np.floor(len(self.list_IDs) / self.batch_size))
```

数据生成的核心是方法***_ _ 数据生成*** 。它生成包含数据样本的数据。看看下面的代码片段。

```
def __data_generation(self, list_IDs_temp):
 ‘Generates data containing batch_size samples’ # X : (n_samples, *dim, n_channels)
 # Initialization
 X = np.empty((self.batch_size, *self.dim, self.n_channels))
 y = np.empty((self.batch_size), dtype=int)# Generate data
 for i, ID in enumerate(list_IDs_temp):
 # Store sample
 X[i,] = np.load(‘data/’ + ID + ‘.npy’)# Store class
 y[i] = self.labels[ID]return X, keras.utils.to_categorical(y, num_classes=self.n_classes)
```

这种方法有助于生成批量数据。作为一个参数，它接受目标批处理的 id。The keras.utils.to _ categorical 生成标签的一次性编码值。

最后，为了生成所有的数据，我们将使用下面的方法。

```
def __getitem__(self, index):
 ‘Generate one batch of data’
 # Generate indexes of the batch
 indexes = self.indexes[index*self.batch_size:(index+1)*self.batch_size]# Find list of IDs
 list_IDs_temp = [self.list_IDs[k] for k in indexes]# Generate data
 X, y = self.__data_generation(list_IDs_temp)return X, y
```

该方法使用前面代码片段的数据生成方法，并生成所需的数据批次。

下面的代码片段展示了如何实际使用它来训练我们的模型。

```
import numpy as npfrom keras.models import Sequential
from my_classes import DataGenerator params = {‘dim’: (32,32,32),
 ‘batch_size’: 128,
 ‘n_classes’: 6,
 ‘n_channels’: 1,
 ‘shuffle’: True} partition = # IDs
labels = # Labels training_generator = DataGenerator(partition[‘train’], labels, **params)
validation_generator = DataGenerator(partition[‘validation’], labels, **params) model = Sequential()
[…] # Architecture
model.compile() model.fit_generator(generator=training_generator,
 validation_data=validation_generator,
 use_multiprocessing=True,
 workers=6)
```

从上面可以看出，我们使用了*拟合生成器*方法，而不是拟合方法。这在我们处理大型数据集时特别有用，因为我们不应该一次将整个数据放入 ram。workers 参数确保批处理是并行生成的。

在领英
[https://www.linkedin.com/in/aditya-mohanty-7982451a9/](https://www.linkedin.com/in/aditya-mohanty-7982451a9/)联系我

代码可以在[https://github.com/mohantyaditya/Datagenerator](https://github.com/mohantyaditya/Datagenerator)找到。

## 参考资料:

[](https://stanford.edu/~shervine/blog/keras-how-to-generate-data-on-the-fly) [## 使用 Keras 的数据生成器的详细示例

### python keras 2 fit _ generator Afshine Amidi 和 Shervine Amidi 的大型数据集多重处理您是否曾经不得不…

stanford.edu](https://stanford.edu/~shervine/blog/keras-how-to-generate-data-on-the-fly)