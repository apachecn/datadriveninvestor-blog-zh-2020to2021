# 如何使用 python 在没有机器学习的情况下扩展数据集(更新)

> 原文：<https://medium.datadriveninvestor.com/expand-your-dataset-without-machine-learning-d82d8174ac11?source=collection_archive---------6----------------------->

![](img/70871633552a464427351c970c53b521.png)

有时，我们会遇到这样的情况:我们想要解决现实生活中的数据科学问题，但由于没有好的数据集可用，我们无法开始解决问题。有很多机会，你开始制作自己的数据集，你开始收集一些数据，以便制作一个好的数据集，但你将面临许多障碍，其中之一是制作一个大型数据集。这是你陷入困境的时候，因为我们没有太多的现实生活资源或数字资源，对于那些不太懂编程的人来说，开始失望了。

**预备步骤:-**

根据您的资源开始制作数据集。开始时可能有 40-100 条记录，但要尽可能增加记录的数量。

**第一步:-**

所以第一步是不要担心。

**Python** 来帮你了。

**第二步:-**

无论有没有 ML，您都可以轻松地扩展数据集。在我的下一个故事中，我们将扩展来自机器学习的数据集。
因此，在本文中，我们将借助 Python 以一种非常简单的方式来完成这项工作。

> **需要 Python 库:-**

**Random:-** 这个库有函数choice()，这是 Random 库的内置函数，从列表、元组或字符串中返回一个随机项。

因此，我们给出现有的值，或者你可以说现有的数据框，它会给你从我们的数据框中随机选择的值。

**必要进口:-**

```
import pandas as pd

from random import choice
```

现在制作一个包含数据帧值的列表。

```
choice_list= []
```

现在像往常一样阅读 csv 文件。

```
dforignal = pd.read_csv(r"dataset.csv", encoding='utf8', low_memory=False)
```

现在将所有的列名放入列表中，因为我们想要迭代所有这些列，以便展开所有这些列。

```
colnames = dforignal.columns.values
print(colnames)
```

现在我们根据我们简单的技术/算法来到这里。

保持第一列正常，它有索引值。所以请留意它是否有索引值。如果第一列中没有索引值，请跳过这一步。

```
dforignal = pd.DataFrame(df.drop(colnames[0],axis=1))
```

因此，为了基于现有值生成新值，我们必须将数据帧转换为列表。为此，我们必须这样做:

注意:-如果您是逐行复制代码，则不能复制粘贴这一行。

```
valueslist=dforignal[column_name].tolist()
```

现在从最左边的列开始，也就是第二列。我们将从最左边到最右边的列开始迭代所有的列名。

注意:-如果你是逐行复制代码，这一行不能被复制粘贴。

```
for i in range(0,len(colnames)):
   column_name=colnames[i]
```

因此，在编写了一个循环之后，我们可以通过。to_list()函数。

然后写一个你选择长度的环。该长度将决定输出数据集的长度。如果你想要一个包含 6000 条记录的数据集，那么把它写在内循环中。

选择函数将从我们现有的数据中随机选择一个值，然后我们将这个值添加到列表中。

```
for i in range(0,len(colnames)):
   column_name=colnames[i]
   print(column_name)
   valueslist=dforignal[column_name].tolist()
   for _ in range(6000):
      selection = choice(valueslist)
      choice_list.append(selection) 
```

在这个长度为 6000 的环路之外，但在外环之内。从该值列表中创建一个具有相同列名的数据框，并赋予它与现有数据框相同的列名。

为两个列，即旧的现有列和新生成的列取相同的名称，这是一个必要的步骤，以便创建一个正确的数据框架。

```
df[column_name]= pd.DataFrame(choice_list, columns=[column_name])
   print(df[column_name])
   choice_list.clear()
```

我们算法的整个代码块**可以复制粘贴** :-

```
for i in range(4,len(colnames)):
   namee=colnames[i]
   print(namee)
   valueslist=dforignal[namee].tolist()
   for _ in range(5879):
      selection = choice(valueslist)
      choice_list.append(selection)
   df[namee]= pd.DataFrame(choice_list, columns=[namee])
   print(df[namee])
   choice_list.clear()
```

现在添加新制作的数据帧和原始数据帧。

```
dfnew = dforignal.append(df, ignore_index=True)
```

然后将这个扩展的数据帧导出到 csv 或 excel 格式。

```
print(dfnew.to_csv("expanded.csv", encoding='utf-8', index=False))
```

只有当数据集反复显示索引时，“忽略索引”和“索引”才是重要的参数。所以请密切关注。