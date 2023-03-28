# Python 列表——面向初学者的内置函数和方法

> 原文：<https://medium.datadriveninvestor.com/python-list-built-in-functions-and-methods-for-beginner-ea2e9ddd007e?source=collection_archive---------11----------------------->

## 这里我们将讨论 python 列表的基本概念、Python 列表内置的列表函数以及列表内置的方法，并给出例子

![](img/8a7dfc91e1e9744b2b515ea22c74ccdd.png)

Photo by [Hitesh Choudhary](https://unsplash.com/@hiteshchoudhary?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

在 **Python** 编程中，一个**列表**是通过将所有项目(元素)放在方括号[]内，用逗号分隔而创建的。它可以有任意数量的项，并且它们可以是不同的类型(整型、浮点型、字符串型等。).

**如何创建 python 列表？**

要创建 python 条目列表，您需要在方括号中提到条目，用逗号分隔。

***重要:不需要声明数据类型，因为 Python 是动态类型的。***

[](https://www.datadriveninvestor.com/2020/10/23/fourier-transform-for-image-processing-in-python-from-scratch/) [## Python 中用于图像处理的傅里叶变换从零开始|数据驱动投资者

### 首先，处理数学问题真的很有趣。对吗？我知道答案可以是是也可以不是…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/10/23/fourier-transform-for-image-processing-in-python-from-scratch/) 

让我们看看如何创建一个列表并打印它

**如何从列表中访问元素？**

列表项被编入索引，您可以通过引用索引号来访问它们。

***重要:第一项的索引为 0。这意味着 0 表示第一项，1 表示第二项，依此类推。***

***消极索引:*** 它从结尾开始。`-1`指最后一项，`-2`指倒数第二项，以此类推。

**指标范围:**

您可以通过指定范围的开始和结束位置来指定索引范围。当指定一个范围时，返回值将是一个包含指定项的新列表。

***重要提示:搜索将从索引 2(包含)开始，到索引 4(不包含)结束。***

**检查列表中是否有项目**

**如何使用 for 循环打印列表项**

**更改列表中的项目值**

要更改特定项目的值，请参考索引号。若要插入多个项目，请用新值创建一个列表，并指定要插入新值的索引号。

**可以创建空数组吗？**

是的，可以

**如何选择数组中的随机项？**

**如何对数组中的项目进行洗牌？**

**如何删除 python 列表？**

使用 **del** 关键字。

**删除列表中的单个元素或几个元素**

**使用 remove()、pop()和 clear()方法删除元素**

remove(item):从列表中删除指定的项目。pop(index):从给定的索引中删除元素。
pop():删除最后一个元素。
clear():从列表中删除所有元素。

**我们来谈谈内置列表函数**

*   cmp(list1，list2)-比较两个列表的元素
*   len(list)-给出列表的总长度。
*   max(list)-从列表中返回具有最大值的项目。
*   min(list)-从列表中返回具有最小值的项目。
*   list(seq)-将元组转换为列表。
*   sum(list)-返回列表中所有元素的总和

**python 列表中的内置方法**

*   append()-将项目添加到列表的末尾
*   insert()-在指定位置插入项目
*   index() —返回指定项目的第一个匹配索引
*   count() —返回指定项目的计数
*   sort()-按升序对列表进行排序
*   reverse()-颠倒 python 列表中元素的顺序

**现在是时候检查你的知识了。**

尝试构建一个密码生成器项目。用户输入应该包括多少个符号、数字和字母来创建密码。你应该随机选择数字，符号和字母，并想洗牌。然后将密码打印成字符串

解决方案:

让我们在下一篇文章中讨论 python 函数。注意安全。

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)