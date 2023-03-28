# 3 个很少使用的 Python 3 特性

> 原文：<https://medium.datadriveninvestor.com/3-rarely-used-python-3-features-4419643a4f99?source=collection_archive---------17----------------------->

![](img/83f41b60b6f58ac9bfe28673fa4f8931.png)

Python 3 已经出现了一段时间，相当多的开发者，尤其是那些刚刚开始使用 Python 的人，已经在使用这个版本的语言了。虽然许多新功能被广泛使用，但似乎有一些被遗忘了。在本文中，我们将介绍三个最不为人知但很有用的特性。我们从其他编程语言中了解到它们，它们使 Python 3 成为一种很酷的语言。

我们主要在 Java 和 Swift 中使用枚举。现在我们继续在 [Python](https://geniusee.com/tools/python-web) 中使用它们。

用 Python 声明一个枚举非常容易，在第三版之前就可以了(尽管有一些限制):

```
from enum import Enum
class State(Enum):
AIR = 0
LAND = 1
SEA = 2
myState = State.AIR
# Outputs 0
print(myState.value)
# Outputs AIR
print(myState.name)
```

在上面的代码中，通过声明一个从 Enum 继承的类来引入枚举。然后简单描述所有必要的状态。在我们的情况下，这些是空气，土地和海洋。

Python 3 中添加的一个功能是使用。值和. name。它们允许您获取与枚举相对应的数字和字符串。

例如，State 的输出。土地。名字是土地。

当您需要一些常量的文本标识符时，枚举在代码中很有用。例如，与其将状态与 0 或 1 进行比较，不如将其与状态进行比较更能说明问题。移动或状态。静止。常数可以改变，如果有人后来看代码，单词移动会比 0 更容易理解。因此，代码的可读性大大提高了。

fstrings 是在 3.6 版本中添加的，是一个强大的文本格式化工具。它们允许更多的可读和无错的代码(这是我们从 Java 转换过来后所享受的)。这比以前在 Python 中使用的格式要好。下面是使用该格式的一个示例:

```
name = 'Taras'
blog_title = 'codeatcpp.com'
# Hi, my name is Taras and I write on my blog geniusee.com
a = "Hi, my name is {} and I am writing on my blog {}.". format (name, blog_title)
```

很容易注意到字符串中的空花括号，以及以特定顺序排列的变量名。

现在让我们看看相同的代码，但是使用了 fstring，它可读性更好，非常类似于 Swift 的格式化方式。

```
name = 'Taras'
blog_title = 'codeatcpp.com'
# Hi, my name is Taras and I am writing on my blog geniusee.com.
a = f "Hi, my name is {name} and I am writing on my blog {blog_title}."
```

要得到这么整齐的字符串，只需要在引号前面加上字母 f，然后不用空括号，直接在字符串中直接写上变量或数据的名称就可以了。由于变量直接写在一行中，所以不需要计算元素的数量，也不需要跟踪变量放在最后的顺序。他们正好在需要他们价值的地方。

与传统方法相比，使用 fstring 可以使代码更易读，更易于维护。

与前面的主题相比，数据类可能是一个更令人困惑的主题，因此需要更多的解释。数据类是我们真正喜欢的 Kotlin 的东西，所以我们也喜欢在 Python 中使用它们。

数据类是其唯一目的是存储数据的类。该类包含可读写的变量，但没有额外的逻辑。

假设您有一个程序，需要在不同的类之间传递一个字符串和一个数字数组。您可以使用像 pass (str，arr)这样的方法，但是创建一个只包含一个字符串和一个数组作为类成员的类要方便得多。

使用数据类可以更好地展示您正在尝试做的事情，也可以更容易地创建单元测试。

以下示例显示了一个简单的数据类，它是一个 3D 矢量，但可以轻松扩展为表示不同数据的任意组合:

```
from dataclasses import dataclass
@dataclass
class Vector3D:
x: int
y: int
z: int
# Create a vector
u = Vector3D (1,1, -1)
# Outputs: Vector3D (x = 1, y = 1, z = -1)
print (u)
```

这里很容易看出，数据类的定义与常规类的定义非常相似，只是使用了@dataclass 装饰器，然后将每个字段定义为 name: type。

虽然创建的 Vector3D 的功能非常有限，但使用 data 类的目的是提高效率，减少代码中的错误数量。毕竟，传递一个 Vector3D 作为参数要比传递一组 int 变量好得多。

关于@dataclass decorator 的更多信息可以在官方 Python 3 文档中找到。

如果您尝试过这些新功能，请在[联系我们](https://geniusee.com/single-blog/3-rarely-used-python-3-features#contact)表单中告知我们。听到它们的新用途将会很有趣。

如果你想阅读更多文章，请访问[天才博客](https://geniusee.com/blog)。

编码快乐！

*原载于 2020 年 8 月 31 日 https://geniusee.com**[*。*](https://geniusee.com/single-blog/3-rarely-used-python-3-features)*