# 如何从 Python 打印语句创建文本文件？

> 原文：<https://medium.datadriveninvestor.com/how-to-create-text-file-from-python-print-statement-9a94b935a7ab?source=collection_archive---------14----------------------->

默认情况下，Python print()语句在屏幕上显示结果。但是有两种简单的方法可以从打印输出创建文本文件。

简而言之，让我们看看如何在 Python 中实现打印重定向。

> 方法 1:标准重定向
> 方法 2:使用 Python 代码

![](img/eeb1e13ba7c9dd2705748280b3f703f2.png)

Photo by [Morgan Harper Nichols](https://unsplash.com/@morganharpernichols?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/code?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

**方法一:标准重定向方法。**

这种方法适用于所有 Windows、Mac 和 Linux 操作系统。

[](https://www.datadriveninvestor.com/2020/12/01/how-to-build-a-twitter-scraping-app-with-python/) [## 如何用 Python |数据驱动投资者构建 Twitter 抓取应用

### 每秒发出约 6000 条推文，每天发布 5 亿条推文，普通人甚至不能…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/12/01/how-to-build-a-twitter-scraping-app-with-python/) 

例如，sample.py

```
import sysprint("Character Rachel Green was played by Jennifer Anniston")
```

默认情况下，执行 sample.py 会将结果输出到屏幕

```
# python sample.py
```

现在，通过重定向输出，它创建了一个 outputFile.txt

```
# python sample.py > outputFile.txt
```

注意:如果您想要附加到现有文件，请使用两个更大的符号>>

```
# python sample.py >> outputFile.txt
```

**方法二:使用 Python 代码**

```
import sys# Resetting the Standard Output device from Display to Text file
sys.stdout = open('outputFile.txt','w')print("Character Rachel Green was played by Jennifer Anniston")
```

现在，当脚本执行时，输出不会显示在屏幕上，而是创建一个文本文件。

```
# python sample.py
```

注意:如果您想要附加到现有文件，请用“a”替换“w”

```
sys.stdout = open('outputFile.txt','a')
```

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)