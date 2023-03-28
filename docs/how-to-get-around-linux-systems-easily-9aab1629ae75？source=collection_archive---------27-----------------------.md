# 如何轻松绕开 Linux 系统！

> 原文：<https://medium.datadriveninvestor.com/how-to-get-around-linux-systems-easily-9aab1629ae75?source=collection_archive---------27----------------------->

## Linux 有时会很难。所以，你可能需要这个！

在 Linux 系统上工作时，您有时会迷失方向。直到你在一个图形系统上工作的时候，事情看起来都很好。但是，有时，在使用服务器时(或者在学习过程中)，您可能会在某一点上卡住。这些问题可能包括以下内容:

*   迷失在文件系统中
*   不知道命令的用途
*   不知道使用什么命令来执行特定的动作
*   无法关闭文本编辑器(尤其是 vi)

这些是从初级到中级 Linux 人员都可能面临的一些常见问题。

**解决方案**

***pwd*前来救援**

```
username@group:~$ pwd
```

您正在一个系统上工作，并且不记得您在哪个目录中。所以， ***pwd*** 是一个很有用的命令。它会给你一个你所在的确切目录的输出。

**ls-al**

```
username@group:~$ ls -al
```

有时，您需要知道目录的内容，包括隐藏的*文件及其权限和其他元数据。键入如上所示的命令，系统将显示当前目录中文件和目录的完整详细列表。

***信息【命令名】***

```
username@group:~$ info [command name]
username@group:~$ info ls
```

当你不知道如何处理一个特定的命令时， ***info*** 命令可以被认为是 Linux 系统中最有用的命令。它通过将您带到终端内部的帮助文档来帮助您。该文档从命令的定义开始，然后解释其用法。一些命令甚至可能包含实际的例子。

***man -k【搜索词】***

```
username@group:~$ man -k [search-term]
username@group:~$ man -k delete
.....
timer_delete (2)     - delete a POSIX per-process timer
tr (1)               - translate or delete characters
unlink (2)           - delete a name and possibly the file it refers to
unlinkat (2)         - delete a name and possibly the file it refers to
***userdel (8)          - delete a user account and related files
...........*****And then to get information about any command, type:
man (number next to command) (command)
FOR EXAMPLE:**username@group:~$ man 8 userdel   #this will display the help for               the command
```

有时你会被困在一个地方，不知道执行某个特定动作的命令。有时，你可以进行网络搜索，但对这些系统来说最好的是使用 ***man -k*** 命令。

[](https://www.datadriveninvestor.com/2020/03/04/on-artificial-intelligence-and-surveillance-capitalism/) [## 人工智能和监督资本主义|数据驱动的投资者

### 大科技，总是现在:人工智能推动的大科技，已经使购物，搜索，在你的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/03/04/on-artificial-intelligence-and-surveillance-capitalism/) 

为了清楚起见，考虑上面提到的例子。假设您想从系统中删除一个用户帐户，但不知道确切的命令。因此，您可以键入命令 ***man -k delete*** ，它会显示所有可以帮助您删除用户的命令。然后，从结果中找出带有所需描述的命令以及与之对应的编号。尽管这个例子听起来有些多余，但它被证明在大多数时候非常有用，并且是获得即时系统帮助的最有效的方法。

这些简单的命令变成了绕过 Linux 系统的基本命令，如果您被困在某个地方，这些命令可以帮助您。