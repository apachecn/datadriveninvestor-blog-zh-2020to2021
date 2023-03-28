# 让我们来学习角管

> 原文：<https://medium.datadriveninvestor.com/lets-learn-angular-pipes-b13586f9f8b3?source=collection_archive---------13----------------------->

## 带示例

![](img/3736fc9e426a1959aeb7a60ab88f3ce2.png)

Photo by [AltumCode](https://unsplash.com/@altumcode?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

Angular Pipes 将数据作为输入，并格式化或转换数据以在模板中显示。此外，管道用于向最终用户显示数据。在此之前，我们可以针对最终用户对数据进行一些操作。视图和管道改变数据的外观。管道永远不会修改组件类中的数据。他们将只做将在视图中显示的中间修改。原始数据不会被修改。

**角管道语法**

```
Expression|pipeOperator[:pipeArguments]
```

Expression:要转换的表达式

|:是管道字符

管道操作员:管道的名称

管道参数:管道的参数

*   **小写**:将文本转换为全部小写

![](img/6e0eca266cd2f8f55d6def36055b3b9f.png)

app.componet.ts

*   **大写**:将文本转换为全部大写

![](img/032154f4799fe05d63e48d801149b439.png)

app.componet.ts

*   **标题大小写**:将文本转换成标题大小写。将每个单词的首字母大写，并将单词的其余部分转换为小写。单词由任何空白字符分隔，如空格、制表符或换行符。

![](img/2dcf037aab5edca78575eb7c5c2a0cbe.png)

app.componet.ts

*   **slice** :创建一个包含元素子集(slice)的新数组或字符串。

![](img/a698355448f5e7f0aecf8001f6ee653c.png)

app.componet.ts

![](img/76dbfb9339a01bc892f969febb7a7abd.png)

app.componet.ts

*   **json** :将一个值转换成 json 格式的表示

![](img/ea8fe8dc304e4a60443370b6836f82ce.png)

app.componet.ts

*   **percent** :将一个数字转换成一个百分比字符串，根据地区规则格式化。

![](img/151a22b5b3e3ee5809627ce64d8281d8.png)

app.componet.ts

*   **number** :将一个数字转换成一个带小数点的字符串，根据地区规则格式化。

![](img/7bc4fcab3b8298641ef40df46e48af8b.png)

app.componet.ts

*   **货币**:将一个数字转换成货币字符串，根据地区规则进行格式化

![](img/8ce05ef0b6ef801e97e9149af01e8453.png)

app.componet.ts

*   **日期**:根据地区规则格式化日期值。

![](img/196bf7ecb8de37c3e63dbcf4377b8c33.png)

app.componet.ts

编码快乐！