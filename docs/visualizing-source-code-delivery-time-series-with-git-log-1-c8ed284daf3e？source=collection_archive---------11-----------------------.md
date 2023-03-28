# 用 git-log 可视化源代码交付时间序列(1)

> 原文：<https://medium.datadriveninvestor.com/visualizing-source-code-delivery-time-series-with-git-log-1-c8ed284daf3e?source=collection_archive---------11----------------------->

![](img/a77d49ef778b4b3577924adcc7b9b3fe.png)

Photo: [Jack Anstey](https://unsplash.com/@jack_anstey?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

**从 Git 日志**中获取时间序列的一个简单方法是从您的 Git 存储库的根目录发出以下命令:

```
git log --format='%ad' --date=iso-local \
    | cut -d ' ' -f1 | sort | uniq -c
```

产生的时间序列是一个整数和一年中的日期的纯文本列表，类似于下面的内容(除了更长的时间，因为历史上每一天都会打印一行，表示对 Git 进行了一次提交):

```
 13 1999–04–07
  9 1999–04–08
 15 1999–04–09
 11 1999–04–10
 11 1999–04–12
```

您可以向下阅读列表的左侧，查看在初始提交之后每天进行了多少次提交，一直到 Git 存储库默认分支的当前头的提交日期。

类似于`13 1999–04–07`的一行意味着在 1999 年 4 月 7 日，有 13 个提交到这个存储库。在这个例子中，我使用了 PHP 解释器 GitHub repo 作为例子，所以现在我们知道 PHP 上的初始提交是在 1999 年 4 月 7 日进行的。

因此，我们通过相对简单的方法得到了时间序列:仅使用`cut`、`sort`、`uniq`和 Git 客户端本身，所有这些都默认安装在 Mac OS 和 Ubuntu Linux 上，因此在大多数开发环境中都可用。