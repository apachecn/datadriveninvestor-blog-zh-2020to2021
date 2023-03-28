# 熊猫数据框 101:创建数据框和加载数据

> 原文：<https://medium.datadriveninvestor.com/pandas-data-frame-101-part-1-627b9405d14f?source=collection_archive---------7----------------------->

![](img/8fcd58f7e835a709e88001f4c35af011.png)

([Image Source](https://www.open.edu/openlearn/science-maths-technology/computing-and-ict/introduction-data-and-information/content-section-0?active-tab=description-tab))

**什么是熊猫数据框？**

描述数据框的最简单方式是将其视为包含行和列的电子表格或表格。列由列名标记，行有一个索引列。然而，数据帧对于大量数据是非常有效的。它使得对数据应用函数非常有效，无论是在编码还是运行时。它可能是最常用的熊猫数据对象。

首先，我们将进口熊猫作为 pd:

```
import pandas as pd
```

**创建数据框对象:**

有几种创建数据框的方法。让我们从使用字典开始。我们可以用字典的形式定义我们的数据，其中每一列都用字典中的一个条目来表示。键是列名，值包含数据项的列表。让我们看看下面的例子。我们有一本包含我们数据的字典。

```
data = {‘Name’:[‘John’, ‘Mike’, ‘Samantha’], ‘Score’:[6,3,9], ‘Outcome’:[‘Pass’, ’Fail’, ’Pass’]}
```

现在我们可以用一行代码将其转换为熊猫数据框:

```
scores = pd.DataFrame(data)
```

我们可以通过打印来查看数据框的内容。

```
print(scores)
```

输出如下所示:

```
Name  Score Outcome
0      John      6    Pass
1      Mike      3    Fail
2  Samantha      9    Pass
```

在前面的示例中，我们使用字典来创建数据框。现在，我们将了解如何从字典列表中创建数据框。对于这样一个列表，考虑每一项，它是一个字典，代表每一行，键保存列的名称，值保存该行的值。

```
# Make list of dictionaries
data = [{‘Name’: ‘John’, ‘Score’: 6, ‘Outcome’:’Pass’ },
 {‘Name’: ‘Mike’, ‘Score’: 3, ‘Outcome’:’Fail’ },
 {‘Name’: ‘Samantha’, ‘Score’: 9, ‘Outcome’:’Pass’ },
 ]# Create DataFrame from the list
scores = pd.DataFrame(data=data)
print(scores)
```

我们将讨论的从提供的数据创建数据框的最后一种方法是从列表列表中创建。这里，您有一个包含列名的列表和另一个列表，每个项目列表包含数据框中每一行的数据。重要的是，项目保持与包含列名的列表相同的顺序。

```
# Create a list of lists
data = [[‘John’, 6, ‘Pass’],
 [‘Mike’, 3, ‘Fail’],
 [‘Samantha’,9, ‘Pass’]]# Define the column names
columns = [‘Name’, ‘Score’, ‘Outcome’]# Create a DataFrame with the data and column names
scores = pd.DataFrame(data=data, columns=columns)
print(scores)
```

**从文件中加载数据:**

pandas 最大的优点之一是易于实现。在从文件中的数据创建数据框的情况下，pandas 会为您完成所有繁重的工作。假设您在一个名为 scores.csv 的 csv 文件中保存了所有学生的分数，以下是将它加载到数据框中的方法:

```
# Read the data
scores = pd.read_csv(‘scores.csv’)
```

另一种常见的文件格式是 Excel 电子表格。你可能知道，一个 Excel 文件可能包含许多电子表格，我们可以指定数据应该从哪个电子表格加载。例如，假设我们有一个 scores.xlsx 文件，其中有一个代表学期考试的电子表格，我们对期中考试的表格特别感兴趣。

```
scores = pd.read_excel(‘scores.xlsx’, sheet_name= ‘midterm’, na_values = ‘None’)
```

na_values 告诉代码用“None”替换任何空字段。您可以在没有它的情况下运行代码，但是应用它会告诉代码如何处理空字段并减少出错的机会。

[](https://www.datadriveninvestor.com/2020/12/07/name-matching-techniques-with-python/) [## 使用 Python |数据驱动投资者的名称匹配技术

### 我们确实面临很多情况，我们必须匹配一个有很多变体的单词。这可能是因为错别字…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/12/07/name-matching-techniques-with-python/) 

现在，如果您必须将所有工作表中的数据加载到数据框中，会怎么样呢？为此，我们创建一个 Excel 文件对象，即文件中所有工作表的列表，从列表中的每个工作表加载数据，并将其附加到列表列表中，每个条目/列表代表每个工作表。然后，将所有列表连接成一个数据帧。我知道我没有很好地描述它，但当我们一步一步地做这件事时，它会变得有意义。

```
# Create pd.ExcelFile() objectxls = pd.ExcelFile(‘scores.xlsx’)# Extract sheet names and store in exchangesexams = xls.sheet_names# Create an empty list: exam_sheets
exam_sheets=[]# Now we iterate over the list containing names of the sheets (exams), loading data into a Data Frame and then appending that to exam_sheetsfor exam in exams:
    #load data into a Data Frame
    exam_sheet = pd.read_excel(xls, sheetname=exam, na_values=’n/a’) #Add a column containing name of the sheet
    exam_sheet[‘Exam’] = exam #append the Data Frame to the list
    exam_sheets.append(exam_sheet)# Concatenate the listings: listing_data
scores = pd.concat(exam_sheets)
```

这就对了。这是一个基本的教程，展示了如何创建数据框和填充数据。在第 2 部分中，我们将讨论数据过滤。

**进入专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)