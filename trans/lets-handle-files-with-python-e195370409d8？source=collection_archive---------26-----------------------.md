# 让我们用 Python 来处理文件

> 原文：<https://medium.datadriveninvestor.com/lets-handle-files-with-python-e195370409d8?source=collection_archive---------26----------------------->

![](img/1395ac593db85892076fb38d6769c3c4.png)

Photo by [Maarten van den Heuvel](https://unsplash.com/@mvdheuvel?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

web 应用程序中有我认为重要的部分，文件处理是其中之一。它可以定义为“**将各种数据存储在一个文件中，或者借助于程序**提取存储在文件中的数据”。与任何其他编程语言不同，我们可以使用 python 进行文件处理。

用其他编程语言实现文件处理是非常繁琐复杂的，但是有 python 在又何妨。与其他概念不同，python 使得文件处理对用户来说也很容易。

![](img/9406d00f75acf9dbc46e9cb67dc38924.png)

Photo by [Riku Lu](https://unsplash.com/@riku?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

在 python 的帮助下，我们可以**写入、删除、读取**和**甚至更新**系统中任何文件中的数据。在 python 中，文件处理的实现简单而简短。需要注意的是，python 将文件区分为**二进制**或**文本**。

## 重要的功能

“ [open()](https://docs.python.org/3/library/functions.html#open) ”是 python 的内置函数之一。“open()”函数在用 python 处理文件时起着重要的作用。它用于打开文件并将打开的文件作为对象返回。open()函数的语法如下所示。

## 让我们更深入地理解 open()

1.  **文件-** 提供要打开的路径/文件名。
2.  **模式-**r，w，a，x，b，t，+等各种模式。
3.  **缓冲-** 可选，用于缓冲策略。
4.  **编码-** 使用哪种编码对文件进行编码或解码。
5.  **错误-** 这是可选的，不能用于二进制模式。它规定了如何处理编码和解码错误。
6.  **换行符-** 适用于文本模式。控制换行模式的工作方式。

*要深入理解上述术语，请参考* [*文档*](https://docs.python.org/3/library/functions.html#open) *。*

![](img/97e32eb5c4dbfae3e9b664bb00efa600.png)

Photo by [Markus Spiske](https://unsplash.com/@markusspiske?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

## 让我们了解各种模式

1.  **【r】**—用于读取文件。
2.  **【w】**—用于写入文件。
3.  **“a”**—用于写入文件，并在文件末尾追加数据。
4.  **【x】**—用于打开文件进行独占创建。
5.  **【b】**—使用二进制模式处理文件。
6.  **【t】**—使用文本模式处理文件。
7.  **"+"** —用于更新(读写)文件。

## 文件处理示例

a.打开和关闭文件

b.创建文件

c.读取文件

*filename.read()* 显示文件中的所有数据。 *filename.readline()* 显示文件中的第一行，而*filename . readline()*读取文件中的所有行。我们还可以在上面代码中所示的 loop 的帮助下读取文件中的数据。

d.写入文件

e.删除文件

# 注意

*关闭* *打开的文件总是很重要的，因为在某些情况下，由于缓冲，在我们的文件中所做的更改直到文件被关闭时才显示出来。*

## 摘要

这就是我们如何用 python 处理文件。我们应该永远记得关闭我们打开的文件。还有另一种方法可以处理文件，即“用 open() ”处理**。在这个方法中，我们不需要关闭文件，因为它是自动处理的，我们不需要显式调用" **close()** "方法。**

*详细理解请参考* [*文档*](https://docs.python.org/3/library/functions.html#open) *。*

## 在你走之前

*感谢阅读！如果你想和我取得联系，可以随时在*[*LinkedIn*](http://in.linkedin.com/in/praffullakumardubey)*上联系我。请到我的* [*中*](https://praffullakrdubey.medium.com/) *账号查看我的其他故事。*