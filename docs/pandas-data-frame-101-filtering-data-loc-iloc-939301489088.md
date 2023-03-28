# Pandas 数据框 101:过滤数据，loc 和 iloc

> 原文：<https://medium.datadriveninvestor.com/pandas-data-frame-101-filtering-data-loc-iloc-939301489088?source=collection_archive---------8----------------------->

![](img/52363d4ba43ca8051ceee1d6350f07cf.png)

[(Image Source)](https://mysimple.name/filtering-data-in-symfony/)

本文是第一篇文章的延续，在第一篇文章中，我们学习了[如何从 CSV 和 Excel 文件](https://medium.com/datadriveninvestor/pandas-data-frame-101-part-1-627b9405d14f)创建数据框并将数据加载到数据框中。

在今天的教程中，我们将学习如何从数据框中选择数据。让我们[通过点击页面上的下载链接从雅虎财经下载](https://finance.yahoo.com/quote/%5EGSPC/history?p=%5EGSPC)股票数据，这可以让你以 CSV 文件的形式下载数据。这是标准普尔 500 指数的历史数据。我将该文件重命名为 stocks.csv。让我们从导入 pandas 开始，并从 csv 文件加载数据。你可以在这里下载包含这个代码[的 CVS 文件和笔记本。](https://github.com/doctorsmonsters/pandas_loc_iloc)

```
**import** pandas **as** pddata**=**pd.read_csv('stocks.csv')
```

让我们看看数据框架中的列。

```
data.columns
```

我们得到以下输出:

```
Index(['Date', 'Open', 'High', 'Low', 'Close', 'Adj Close', 'Volume'], dtype='object')
```

**使用‘loc’属性:**

loc 可用于基于标签检索数据。默认情况下，数据框的索引列被视为一个标注。因此，在我们的数据中，如果我们想要检索第 3 行所有列中的数据，我们将使用:

```
data.loc[3]
```

输出:

```
Date         2020-01-15
Open            3282.27
High            3298.66
Low             3280.69
Close           3289.29
Adj Close       3289.29
Volume       3716840000
Name: 3, dtype: object
```

然而，为了便于阅读，最好分配更合理的标签。所以在我们的数据中，因为它可以被认为是时间序列数据，所以我们可以将日期列指定为索引。

```
data.index**=**data['Date']
```

现在我们使用日期作为标签，检索数据将变得非常容易。假设我们想查看 1 月 4 日的数据。

```
data.loc['2021-01-04']
```

输出:

```
Date         2021-01-04
Open            3764.61
High            3769.99
Low             3662.71
Close           3700.65
Adj Close       3700.65
Volume       5006680000
Name: 2021-01-04, dtype: object
```

现在假设我们对一个特定的列感兴趣，比如收盘价。我们可以通过传递列名来做到这一点。

```
data.loc['2021-01-04', 'Close']
```

输出:

```
3700.649902
```

要从多个列中检索数据，可以将列名作为列表传递。类似地，如果需要来自多行的数据，也可以将标签作为列表传递。

```
print(data.loc['2021-01-04', ['Open', 'Close']])*# Open and close for Janurary 4 and 5.*print(data.loc[['2021-01-04','2021-01-05'], ['Open','Close']])Open     3764.61
Close    3700.65
Name: 2021-01-04, dtype: object
                   Open        Close
Date                                
2021-01-04  3764.610107  3700.649902
2021-01-05  3698.020020  3726.860107
```

现在，如果您想查看整个数据帧的某些列，可以按如下方式进行:

```
​print(data.loc[:, ['Open','Close']])Open        Close
0    3281.810059  3265.350098
1    3271.129883  3288.129883
2    3285.350098  3283.149902
3    3282.270020  3289.290039
4    3302.969971  3316.810059
..           ...          ...
247  3764.610107  3700.649902
248  3698.020020  3726.860107
249  3712.199951  3748.139893
250  3764.709961  3803.790039
251  3815.050049  3824.679932[252 rows x 2 columns]
```

**使用“iloc”:**

iloc 使您能够基于虚拟数字索引检索数据。请注意，数字索引是虚构的，这意味着它是实际的索引列。例如，在我们的数据中，日期列被指定为索引。但是使用 iloc，您可以基于从 0 开始的索引号检索数据。例如，如果您想检索索引为 0 的行，可以按如下方式进行:

```
data.iloc[0]
```

输出:

```
Date         2020-01-10
Open            3281.81
High            3282.99
Low             3260.86
Close           3265.35
Adj Close       3265.35
Volume       3212970000
Name: 0, dtype: object
```

以类似的方式，您可以使用 iloc 从特定的行和列中检索数据，方法是为这两者提供索引。假设我们想从第 2 行第 3 列检索数据。

```
data.iloc[2,3]
```

输出:

```
3277.189941
```

人们可能想知道这有什么用。在我们的数据中，想象您想要检索最后 3 行。您可以使用 iloc 实现这一点。

```
print(data.iloc[**-**1])Date         2021-01-08
Open            3815.05
High            3826.69
Low              3783.6
Close           3824.68
Adj Close       3824.68
Volume       4764180000
Name: 251, dtype: object
```

因此，就像列表一样，您可以使用索引从开头或结尾检索数据的日期或范围，也可以使用步骤。例如，你想选择每第三行，你可以这样做。

```
data.iloc[::3]
```

使用 iloc，我们实际上可以设置单元格的值。例如，在我们的数据中，假设我们希望将每隔一行的音量设置为 0。

```
data.iloc[::2,6]**=**0
```

**有条件选择数据:**

熊猫也给我们提供了有条件的挑排。例如，我们希望只显示收盘价高于平均收盘价的日期的数据。为此，首先我们定义条件，将其分配给一个对象，然后将该对象传递给 loc 属性。

```
high_close**=**data.Close**>**data.Close.mean()data.loc[high_close]
```

另一个例子是选择一个有特定价格的日期。所以我们想知道收盘价为 3700.649902 这一天的数据。

```
condition **=** data.Close **==** 3700.649902data.loc[condition]
```

就这样了，伙计们。熊猫确实有一些超能力，高效的数据过滤绝对是其中之一。