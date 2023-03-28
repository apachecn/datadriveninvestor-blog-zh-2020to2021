# Google 云平台上的大型查询 SQL 第 1 部分

> 原文：<https://medium.datadriveninvestor.com/big-query-sql-on-google-cloud-platform-part-1-c714f69b6831?source=collection_archive---------7----------------------->

## 基础、技巧和技术…

![](img/43062b7ae35016d373449b2eb6dd51fa.png)

Pic from Unsplash.com

我写这篇文章不仅仅是为了让世界(好吧，至少是我的读者！；))知道我有多爱谷歌云平台，但也提供了一个快速入门，即如何开始在 GCP 大查询。Big query 是一个高度可扩展、无服务器、经济高效的多云数据仓库，旨在实现业务敏捷性，并集成在 Google 云平台上。如果你是一个处理海量数据的开发人员，你可以使用谷歌云平台快速查询数据。

# 其他一些最好的系列—

> [**三十天的机器学习 Ops**](https://medium.com/coders-mojo/day-1-of-30-days-of-machine-learning-ops-7c299e4b09be?sk=4ab48350a5c359fc157109e48b1d738f)
> 
> [**30 天自然语言处理(NLP)系列**](https://medium.com/coders-mojo/quick-recap-30-days-of-natural-language-processing-nlp-with-projects-series-ceb674e3c09b?sk=ca09b27b3d5867f23ab4dc367b6c0c32)
> 
> [**30 天数据工程与项目系列**](https://medium.com/coders-mojo/day-1-of-30-days-of-data-engineering-894822fcb128?sk=76ba558bfe2d9f85cbe741e505295531)
> 
> [**数据科学与机器学习研究(论文)简体**](https://medium.com/coders-mojo/day-1-data-science-and-ml-research-papers-simplified-a68b00a3b1c4?sk=56136229ff738bd734f19d2b6953f78c) ******
> 
> [**60 天数据科学与 ML 系列带项目**](https://medium.com/coders-mojo/day-1-day-60-quick-recap-of-60-days-of-data-science-and-ml-6fc021643d1?sk=4e75e043b7630a9f963562ebac94e129)
> 
> [**100 天:你的数据科学与机器学习学位系列与项目**](https://medium.com/coders-mojo/100-days-your-data-science-and-ml-degree-part-3-c621ecfdf711?sk=1a8c7b0c204d73432d56b7d1a3a26474)
> 
> [**你应该知道的 23 个数据科学技巧**](https://ai.plainenglish.io/23-data-science-techniques-you-should-know-61bc2c9d1b3a?sk=1680c36193eb22198974c9008d62a33c)
> 
> [**技术面试系列—编码问题精选清单**](https://medium.com/coders-mojo/mega-post-tech-interview-the-only-list-of-questions-you-need-to-practice-ee349ea197bb?sk=fac3614684daff4b50a70c0a71e4d528)
> 
> [**完成系统设计与最热门问题系列**](https://medium.com/coders-mojo/system-design-made-easy-quick-recap-of-complete-system-design-34af7e3aedfb?sk=bdd6a19edc1f3ce4a5064923f5b68721)
> 
> [**完成数据可视化及预处理系列与项目**](https://medium.com/coders-mojo/complete-data-preprocessing-and-data-visualization-with-projects-mega-compilation-part-2-41584ef0920e?sk=842390da51689b8d43148c3980570db0)
> 
> [**完整的 Python 系列与项目**](https://medium.com/coders-mojo/complete-python-and-projects-mega-compilation-7ec8f7adfe71?sk=ee0ecf43f23c6dd44dd35d984b3e5df4)
> 
> [**完成高级 Python 系列与项目**](https://medium.com/coders-mojo/complete-advanced-python-with-projects-mega-compilation-part-6-729c1826032b?sk=7faffe20f8039fa57099f7a372b6d665)
> 
> [**Kaggle 最会教你的笔记本**](https://medium.com/coders-mojo/my-list-of-kaggle-best-notebooks-topic-wise-data-science-and-machine-learning-part-2-84772863e9ae?sk=5ed02e419854a6c11add3ddc1e52947f)
> 
> [**Git 完整开发者指南**](/the-complete-developers-guide-to-git-6a23125996e1?sk=e30479bbe713930ea93018e1a46d9185)
> 
> [**打赏 Github Repos**](https://medium.com/coders-mojo/6-exceptional-github-repos-for-all-developers-part-1-21e8fa04e150?sk=9140b249af6fe73d45717185fad48962) **—第一部分**
> 
> [**打赏 Github Repos**](https://medium.com/coders-mojo/6-exceptional-github-repos-for-all-developers-part-2-3eec9a68c31c?sk=8e31d0eb7eb1d2d0bbbcecaa66bd4e7e) **—第二部**
> 
> [**所有数据科学和机器学习资源**](/best-resources-for-data-science-and-machine-learning-full-list-5ceb9a2791bf?sk=cf85b2cef95560c58509877a794577ff)
> 
> [**210 机器学习项目**](/210-machine-learning-projects-with-source-code-that-you-can-build-today-721b035649e0?sk=da5f593572a0261a6314afad99a0356c)

## 科技时事通讯—

> 如果你感兴趣，你可以加入我的时事通讯，通过它我向超过 30，000 名读者发送技术面试技巧，技术，模式，黑客——软件开发，ML，数据科学，创业公司和技术项目。可以订阅 **Tech Brew :**

[](https://naina0405.substack.com/) [## 点火器

### 数据科学，人工智能，人工智能和更多…点击阅读由 Naina Chaturvedi 撰写的 Ignito，子堆栈出版物。推出 7 个月…

naina0405.substack.com](https://naina0405.substack.com/) 

## Github —

[](https://github.com/Coder-World04) [## 编码器-world 04-概述

### 此时您不能执行该操作。您已使用另一个标签页或窗口登录。您已在另一个选项卡中注销，或者…

github.com](https://github.com/Coder-World04) 

这篇文章涵盖了高级 SQL 的最基础知识。坚持住，伙计们，让我们开始吧—

# **1。选择，从哪里和从哪里**

我们使用 SELECT 语句从数据库中检索数据。

为了检索或提取所有的列和行，我们在 SELECT 语句中使用了*。为了提取选择性列，我们用 SELECT 语句定义了列名。FROM 语句用于指定要从中检索数据的表。WHERE 用于筛选满足特定条件或标准的行

**格式使用选择，从哪里:**

```
SELECT column_namesFROM table_nameWHERE condition
```

WHERE 子句与 SELECT、UPDATE 和 DELETE 语句一起使用。

# **2。别名、日期和摘录**

别名用于为表或列提供一个简写名称。无论何时创建复杂的查询，Alias 都可以帮助您提高查询的可读性。

**格式使用别名**

```
SELECT column_name AS Alias-nameFROM table alias_nameWHERE condition
```

BigQuery 有很棒的 DATETIME 函数。

为了知道当前日期和时间，请使用 CURRENT_DATETIME 函数，该函数将以 DATETIME 对象的形式返回当前时间。

**格式—**

```
CURRENT_DATETIME([timezone])
```

因为日期时间的格式是日期时间(年、月、日、小时、分钟、秒)的形式。为了提取年、月、日、小时、分钟、秒等，可以使用 Extract 子句，该子句返回一个值，该值对应于所提供的 expression_datetime 中的指定部分。

**格式—**

```
EXTRACT(part FROM expression_datetime)
```

# 3.**聚合函数**

聚合函数对组中的行进行汇总并返回单个标量值的函数。聚合函数的例子有计数、最小值、最大值、AVG、和等。聚合函数通常与 DISTINCT、GROUP BY 和 HAVING 子句一起使用。

*   MIN 返回列的最小值。
*   MAX 返回列的最大值。
*   COUNT 返回数据值的数量。
*   SUM 返回数据值的总和。
*   AVG 返回数据值的平均值。

**格式—**

```
Syntax for COUNT is : SELECT COUNT(column_name)FROM tableSyntax for SUM syntax is: SELECT SUM(column_name)FROM tableSyntax for AVG syntax is: SELECT AVG(column_name)FROM table
```

# 4.**分组依据、拥有依据和排序依据**

GROUP BY 子句可以根据表中的一列或多列进行分组。它通常与聚合函数一起使用，将数据记录分组到汇总行中。

**简单格式—**

```
SELECT column_namesFROM tableWHERE conditionGROUP BY column_names
```

**具有聚合函数格式的分组依据—**

```
SELECT COUNT(column_name)FROM tableGROUP BY column_name
```

HAVING 子句用于汇总 GROUP BY 返回的组记录。无论何时使用 HAVING 子句，都必须使用 GROUP BY。

**格式—**

```
SELECT column_namesFROM tableWHERE conditionGROUP BY column_namesHAVING condition
```

Order by 用于返回特定排序顺序的记录，即升序或降序**。**

**格式—**

```
SELECT column_namesFROM tableWHERE conditionORDER BY column_names
```

# 5.**分析功能**

分析函数计算一组行的结果。所有分析函数都有一个 OVER 子句，该子句定义了每个计算中使用的行集，它有三个(可选)部分:

*   PARTITION BY 子句将表中的行分成不同的组。
*   ORDER BY 子句定义了每个分区内的顺序。
*   最后一个子句(EN 1 前一行和当前行之间的行)称为窗框子句。它标识每个计算中使用的行集。

## **格式—**

```
SELECT column_names,SUM(column_name)OVER (PARTITION BY column_nameORDER BY column_nameROWS UNBOUNDED PRECEDING) AS Alias_nameFROM Table
```

**格式 2 —**

```
SELECT column_namesRANK() OVER (PARTITION BY column_name ORDER BY column_name) AS rankFROM Table
```

# 6.**常用表达式表**

为了简化、简化复杂的查询，使它们更具可读性和查询性，使用了通用表表达式。公共表表达式只不过是一个查询，它的结果集可以在查询的后面部分引用，即它返回一个临时表，您可以在查询中返回这个临时表。它使用 WITH 子句。

```
WITH CTE_expression_name AS (SELECT column_nameFROM tableWHERE condition)SELECT column_nameFROM tableINNER JOIN CTE_expression_name on condition
```

# 7.**嵌套数据**

UNNEST 用于展平数组。UNNEST 接受一个数组，然后返回一个表，该表为数组中的每个元素提供一行。

```
SELECT column_name, COUNT(column_name) as countsFROM table,UNNEST(array) as alias_nameWHERE conditionGROUP BY column_nameORDER BY column_name [ASC or DESC]
```

## 以下是在 Google 云平台上使用 BigQuery SQL 时需要了解的一些重要事项:

1.  ***模式:*** *BigQuery 使用灵活的模式，这意味着即使在数据已经加载到表中之后，表的模式也可以更新。这允许数据科学家根据需要添加或修改列，而不必重写整个表。*
2.  ***分区和聚类:*** *BigQuery 支持分区和聚类，通过以一种更容易、更快检索的方式组织数据，可以提高查询性能。*
3.  ***用户定义函数(UDF):****big query 支持用户定义函数(UDF)，允许你通过定义自己的函数来扩展 SQL 的功能。*
4.  ***联接:*** *BigQuery 支持各种类型的联接，包括内联接、左联接、右联接和全外联接。*
5.  ***窗口函数:*** *BigQuery 支持多种窗口函数，可以根据同一结果集中当前行的数据和其他行的数据进行计算。*
6.  ***子查询:*** *BigQuery 支持子查询，可以将一个查询嵌入到另一个查询中。*
7.  ***CTAS(将表创建为 Select):****big query 支持 CTAS，允许您通过从现有表中选择数据来创建新表。*
8.  ***性能优化:*** *BigQuery 提供了许多性能优化技术，包括索引、缓存和物化视图。*
9.  ***成本优化:*** *BigQuery 提供了几种成本优化技术，包括通过压缩和分区降低数据存储成本，以及通过使用编写高效 SQL 查询的最佳实践来降低查询成本。*
10.  ***与其他工具的集成:*** *BigQuery 与许多其他工具集成，如 Data Studio、BigTable、Dataproc 和 TensorFlow，这使得从数据中提取洞察力变得更加容易。*

# 感谢阅读。不断学习。

*(第 2 部分即将推出)*

# 想看程序员幽默？

[](https://medium.com/datadriveninvestor/programming-humor-part-2-f92cf5a26f2b) [## 编程幽默第 2 部分

### 继续笑，因为太搞笑了…

medium.com](https://medium.com/datadriveninvestor/programming-humor-part-2-f92cf5a26f2b) [](https://medium.com/datadriveninvestor/the-most-hilarious-code-comments-ever-bae3cb1030b5) [## 史上最搞笑的代码注释

### 程序员幽默:是的，实际上是程序员写的！

medium.com](https://medium.com/datadriveninvestor/the-most-hilarious-code-comments-ever-bae3cb1030b5) [](https://medium.com/datadriveninvestor/coding-sins-hilarious-developer-confessions-f55eb342454e) [## 编码原罪:令人捧腹的开发者自白

### “白板”是如何被嘲笑的

medium.com](https://medium.com/datadriveninvestor/coding-sins-hilarious-developer-confessions-f55eb342454e) [](https://medium.com/datadriveninvestor/10-witty-programming-jokes-that-will-make-you-go-rofl-a53fbfb91943) [## 10 个让你着迷的诙谐编程笑话

### 这些太搞笑了…

medium.com](https://medium.com/datadriveninvestor/10-witty-programming-jokes-that-will-make-you-go-rofl-a53fbfb91943) 

# 推荐文章-

[](https://medium.com/python-in-plain-english/python-iterators-generators-and-decorators-made-easy-659cae26054f) [## Python 迭代器、生成器和装饰器变得简单

### 快速实施指南

medium.com](https://medium.com/python-in-plain-english/python-iterators-generators-and-decorators-made-easy-659cae26054f) [](https://medium.com/ai-in-plain-english/23-data-science-techniques-you-should-know-61bc2c9d1b3a) [## 你应该知道的 23 种数据科学技术！

### 使用这些技巧来节省你的宝贵时间

medium.com](https://medium.com/ai-in-plain-english/23-data-science-techniques-you-should-know-61bc2c9d1b3a) [](https://medium.com/datadriveninvestor/coding-sins-hilarious-developer-confessions-f55eb342454e) [## 编码原罪:令人捧腹的开发者自白

### “白板”是如何被嘲笑的

medium.com](https://medium.com/datadriveninvestor/coding-sins-hilarious-developer-confessions-f55eb342454e) [](https://medium.com/datadriveninvestor/5-cool-advanced-pandas-techniques-for-data-scientists-c5a59ae0625d) [## 面向数据科学家的 5 项酷炫先进熊猫技术

### 使用这些技巧…

medium.com](https://medium.com/datadriveninvestor/5-cool-advanced-pandas-techniques-for-data-scientists-c5a59ae0625d) [](https://medium.com/datadriveninvestor/stack-overflow-analyzed-data-from-60-000-software-developers-hours-they-work-languages-they-476ac6ca0197) [## Stack Overflow 分析了来自 60，000 多名软件开发人员的数据，包括他们的工作时间、语言…

### 以下是他们的发现…

medium.com](https://medium.com/datadriveninvestor/stack-overflow-analyzed-data-from-60-000-software-developers-hours-they-work-languages-they-476ac6ca0197) [](https://medium.com/datadriveninvestor/advanced-python-made-easy-part-4-a4996ba9fe19) [## 高级 Python 变得简单—第 4 部分

### 使用这些技巧和技术…

medium.com](https://medium.com/datadriveninvestor/advanced-python-made-easy-part-4-a4996ba9fe19) [](https://medium.com/datadriveninvestor/advanced-python-made-easy-part-1-ce1e2f17431e) [## 高级 Python 变得简单—第 1 部分

### 使用这些技巧和技术…

medium.com](https://medium.com/datadriveninvestor/advanced-python-made-easy-part-1-ce1e2f17431e)