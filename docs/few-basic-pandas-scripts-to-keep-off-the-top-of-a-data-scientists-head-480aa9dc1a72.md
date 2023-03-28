# 几个基本的熊猫脚本让数据科学家摸不着头脑。

> 原文：<https://medium.datadriveninvestor.com/few-basic-pandas-scripts-to-keep-off-the-top-of-a-data-scientists-head-480aa9dc1a72?source=collection_archive---------0----------------------->

## 31 个熊猫基本代码概要。

![](img/828c9f3ccaede6229894f7cd73302dc6.png)

Photo by [Erik Mclean](https://unsplash.com/@introspectivedsgn?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

有时候我们努力记住简单的事情。它们很简单，我们都知道，但我们就是在最需要的时候抓不住它们。

此外，任何数据科学项目的第一步也是最重要的一步是理解数据，尽可能多地了解我们遇到的信息。

[](https://www.datadriveninvestor.com/2020/02/19/five-data-science-and-machine-learning-trends-that-will-define-job-prospects-in-2020/) [## 将定义 2020 年就业前景的五大数据科学和机器学习趋势|数据驱动…

### 数据科学和 ML 是 2019 年最受关注的趋势之一，毫无疑问，它们将继续发展…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/19/five-data-science-and-machine-learning-trends-that-will-define-job-prospects-in-2020/) 

因此，牢记这些事情，我在本文中从 pandas 库中编译了一些非常基本的 python 代码，它们将帮助我们更快地执行我们的任务。

整个笔记本在 Github 都有，可以参考:[熊猫基础剧本](https://github.com/anjuraj-ops/Projects-in-data-science/blob/master/Basic%20pandas%20scripts%20in%20python%20that%20should%20be%20in%20your%20finger%20tips%20to%20be%20a%20productive%20Data%20Scientist..ipynb)。

# 1 >导入库。

```
**import** **pandas** **as** **pd**
**import** **numpy** **as** **np**
```

# 2 >检查已安装软件包的版本。

```
*# Not mandatory but in case, we want to check.*print('np:**{}**'.format(np.__version__))
print('pd:**{}**'.format(pd.__version__))Output:
np:1.18.1
pd:0.25.3
```

# 3 >读取数据集。有两种方法可以导入数据集。

***A >:指定文件存放的路径*** *，直接从本地系统读取数据。*

```
df = pd.read_csv("C:/Users/Name/Desktop/Data science misc/datasets for practice/US border crossing data/Border_Crossing_Entry_Data.csv")
```

***B >:定义工作库的路径，加载文件。***

```
*# define the path of the work library*
path = 'C:**\\**Users**\\**name**\\**Desktop**\\**R**\\**Datasets**\\**'
*# open the dataset*
dataset = pd.read_csv(path + 'insurance.csv')
```

# 4 >查看数据。

***头是用来看前几条记录的。***

![](img/0ce574a1762956b5157c67c9821d3397.png)

***尾是用来查看最后几条记录的。***

![](img/6bfac2a41cdc318f7695dcf405ac0e13.png)

***选择‘n’个行数。***

![](img/fe6c166645bbdaee35b0bbd15988426b.png)

# 5 >获取列的列表

```
df.columns
```

Out[7]:

```
Index(['Port Name', 'State', 'Port Code', 'Border', 'Date', 'Measure',
       'Value'],
      dtype='object')
```

# 6 >获取列数和行数。

在[8]中:

```
df.shape     *# This means my dataset has 7 columns and 355511 rows.*
```

Out[8]:

```
(355511, 7)
```

在[9]中:

```
len(df.columns)  *#gives the count of columns.*
```

Out[9]:

```
7
```

在[10]中:

```
df.count()   *#Gives the count of rows for each column.*
```

Out[10]:

```
Port Name    355511
State        355511
Port Code    355511
Border       355511
Date         355511
Measure      355511
Value        355511
dtype: int64
```

# 7 >获取列的数据类型

在[11]中:

```
df.dtypes
```

Out[11]:

```
Port Name    object
State        object
Port Code     int64
Border       object
Date         object
Measure      object
Value         int64
dtype: object
```

# 8 >获取数据集的基本信息。

在[12]中:

```
df.info()<class 'pandas.core.frame.DataFrame'>
RangeIndex: 355511 entries, 0 to 355510
Data columns (total 7 columns):
Port Name    355511 non-null object
State        355511 non-null object
Port Code    355511 non-null int64
Border       355511 non-null object
Date         355511 non-null object
Measure      355511 non-null object
Value        355511 non-null int64
dtypes: int64(2), object(5)
memory usage: 19.0+ MB
```

# 9 >根据需要转换数据类型的语法。

![](img/f14561625461c1b26cd90f2025327165.png)![](img/fa3e1ebcf7dec1e30ff5f9c43ee94fdd.png)

After converting ‘data type of ‘Date’ from object to datetime.

# 10 >获取数据集的描述性统计数据

```
df.describe()     *# statistics will be calculated only on numeric data type*
```

![](img/2e2a1d6fbb42469f3cd8b68c0bfddb99.png)

# 11 >获取各列的相关系数。

*这是特征缩放的一部分，将用于检查一对列之间的相关性，并确定哪一列可以删除，因为它们传递相同的信息。*

![](img/cea5df4e136a1cd8b9b4c19a46fc9e14.png)

# 12 B2 >寻找任何栏是否有遗失的值。

![](img/e38ca616f2f0af1e3699a2004b48aeca.png)

# 13 >查找每列中缺失值的数量

在[19]中:

```
df.isnull().sum().sort_values(ascending=**False**)
```

Out[19]:

```
Value        0
Measure      0
Date         0
Border       0
Port Code    0
State        0
Port Name    0
dtype: int64
```

# 14 >删除丢失的数据

在[ ]:

```
df.dropna(axis=0)
```

# 15 >选择和删除特定功能。

```
*#Selecting a particular feature.*df['Measure'] 
```

![](img/5242e6c1f5aa6ed89d2c0c62d866edf1.png)

```
*#Dropping a particular feature.* **df.drop['Measure',axis=1]**
```

# 16 >使用 iloc 选择数据帧的特征。

![](img/a2f09cfae09926cd384620541926f741.png)

## 让我们尝试其中的几个:

```
*# first row of data frame*df.iloc[0] 
```

Out[21]:

```
Port Name                          Alcan
State                                 AK
Port Code                           3104
Border                  US-Canada Border
Date                 2020-02-01 00:00:00
Measure      Personal Vehicle Passengers
Value                               1414
Name: 0, dtype: object
```

在[25]中:

```
*# last row of data frame*df.iloc[-1] 
```

Out[25]:

```
Port Name             Skagway
State                      AK
Port Code                3103
Border       US-Canada Border
Date           1/1/1996 00:00
Measure                 Buses
Value                       3
Name: 355510, dtype: object
```

在[22]中:

```
*# first column of data frame* df.iloc[:,0]
```

Out[22]:

```
0           Alcan
1           Alcan
2           Alcan
3           Alcan
4           Alcan
           ...   
355506     Antler
355507     Tecate
355508     Calais
355509    Carbury
355510    Skagway
Name: Port Name, Length: 355511, dtype: object*# first two columns of data frame with all rows*df.iloc[:, 0:2] 
```

![](img/8d56ef6ca3cb7692ded47194a3a552b9.png)![](img/db197f013c4454933e7b8b08fab53e3a.png)

# python 中的 Replace 函数——在很多方面都很有用。

![](img/4384ef461e8a59ea44d3b8b55af09d9f.png)![](img/3e5b31c3ee8c8ce9f84b469884fbd702.png)![](img/e0430479fd5b0123448c8ea6372550cf.png)

# 18 >将数据帧转换为数组。

![](img/59e070ac2b6545f859da0c763048e2ff.png)

# 19 >重命名数据帧中的列

![](img/67c93b36f646a7c77b97635b9ae49da5.png)

# 20 >向数据帧添加新列。

![](img/20d1840a527a03a773b123038c29a526.png)

# 21 >将函数应用于数据帧。

![](img/0ebd6bd26ff258dbbf7c3f89c8a56d6f.png)![](img/9dbfc485b9999bca2d44bff56b6ea1d7.png)

# 22 >排序数据。

![](img/922476da30766382eae391ec4ed66ffc.png)

## 按“值”列对记录进行排序。

![](img/0e042e7a2c2ca10f78dfc7f5838c10ae.png)![](img/919bdea1e0127926f14b5c8b91eba053.png)

# 23 >列中唯一值的计数

![](img/db43ca63c06481da8c6f874d678674cc.png)

# 24 >显示列中的唯一值。

![](img/1b599eb53bcda7ee8115c883e5bb55c0.png)

# 25 >获取基本摘要的功能。

![](img/cdf74a584d84e3a5734f839de9bcae6c.png)

# 26 >子集化数据帧-选择几列。

![](img/15db4e84a8068c2699fd5f2459c87280.png)

# 27 >过滤栏。

![](img/ecac06c61b2a73532b80210a3d8aae3c.png)![](img/e177ce851965c871b3fc066f4488b769.png)

We can see 864 rows are returned with the criteria queried.

![](img/f9738a4004a7915c9f2f217e035b3349.png)

# 28 >检索特定列的特定索引中的变量值。

![](img/e69817a076f7ec5190d31e166cd96ff5.png)

# 计算各种函数，如 log，sqrt-这在数据转换时很方便。

![](img/a7b82095e8bb8f14e62fa9e833ce9088.png)![](img/06eb7d707814c001e92badbd3e6fdef6.png)

# 30 >写入数据帧。

![](img/fac16aac80025b7381e306dd4500b3b9.png)

# 31 >熊猫简介。

通过独立脚本/功能获得的上述信息的大部分可以在一个交互式报告中生成。我们知道 df.describe()、df.info()是理解数据的第一步，但是它们通常给出一个非常基本的视图。因此，为了在不编写多个脚本的情况下获得数据的详细信息/统计/EDA，pandas profiling 非常有用。我们将看到如何。

![](img/a1b6e8796d86bf5d7550b6a589349204.png)![](img/f352ce7ebe74b50350506c5eb359b198.png)

Sample of the report which is interactive.

在 pandas profiling 报告中，我们可以在不同的选项卡之间切换，并检查所需的信息。

我们可以使用下面的代码将报告保存到一个可以在任何浏览器中打开的 HTML 文件中。

![](img/b223da7969561b76bd30cc849fd6789c.png)![](img/a5b5282d2d4aedb5b7cadd05d14a4f98.png)

Sample HTML report.

Interactive Pandas-Profiling Report

更多关于熊猫简介的信息可以在这里找到[。](https://pypi.org/project/pandas-profiling/)

# 结论:

在本文中，我列出了项目初始阶段日常使用的一些重要 python 代码。希望，会有用。