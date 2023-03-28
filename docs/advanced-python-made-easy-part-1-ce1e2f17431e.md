# 高级 Python 变得简单—第 1 部分

> 原文：<https://medium.datadriveninvestor.com/advanced-python-made-easy-part-1-ce1e2f17431e?source=collection_archive---------2----------------------->

## 使用这些技巧和技术…

![](img/43062b7ae35016d373449b2eb6dd51fa.png)

Pic from Unsplash.com

Python 是由吉多·范·罗苏姆于 1991 年创建的一种解释型高级通用编程语言。我们大多数在软件工程领域工作的人，在工作中一定使用过 Python。在这篇文章中，我将介绍高级 python 结构，以及如何有效地使用它们来提高代码可读性和性能。这是第 1 部分，接下来是第 2 部分(即将推出)。

[](https://medium.com/datadriveninvestor/hacker-earth-surveyed-16000-developers-from-76-countries-heres-what-i-found-dbd5d7c422b0) [## 黑客地球调查了来自 76 个国家的 16000 名开发者——以下是我的发现

### 惊人的洞察力…

medium.com](https://medium.com/datadriveninvestor/hacker-earth-surveyed-16000-developers-from-76-countries-heres-what-i-found-dbd5d7c422b0) 

# 1.（听力或阅读）理解测试

你一定听说过列表理解(Python 2.0)。Python 中的理解是允许从其他序列构建序列的构造，虽然列表理解非常流行/常用，但 Python 3.0 引入了字典和集合理解。

```
#Example Codelist_one=[5,10,15, 20]
new_list=[]
for x in list_one:
    new_list.append(x**3)
print(new_list)
```

输出—

```
[125, 1000, 3375, 8000]
```

用列表理解—

```
list_two=[5,10,15,20]
new_list=[x**3 for x in list_two]
print(new_list)
```

输出—

```
[125, 1000, 3375, 8000]
```

有条件的—

```
#With conditionlist_three=[13,20,25,45]
new_list=[x**3 for x in list_three if x%2==0]
print(new_list)
```

输出—

```
[8000]
```

## 词典理解

```
dict_one=[10,20,30,40]
new_dict={x: x**2 for x in dict_one if x%2==0}
print(new_dict)
```

输出—

```
{10: 100, 20: 400, 30: 900, 40: 1600}
```

[](https://naina0412.medium.com/writing-efficient-python-code-part-1-e02763632080) [## 编写高效的 Python 代码—第 1 部分

### Python 是科技界最流行、使用最广泛的编程语言之一。

naina0412.medium.com](https://naina0412.medium.com/writing-efficient-python-code-part-1-e02763632080) 

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
> [**科技面试系列—编码问题精选清单**](https://medium.com/coders-mojo/mega-post-tech-interview-the-only-list-of-questions-you-need-to-practice-ee349ea197bb?sk=fac3614684daff4b50a70c0a71e4d528)
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
> [**Git**](/the-complete-developers-guide-to-git-6a23125996e1?sk=e30479bbe713930ea93018e1a46d9185)完全开发者指南
> 
> [**打赏 Github Repos**](https://medium.com/coders-mojo/6-exceptional-github-repos-for-all-developers-part-1-21e8fa04e150?sk=9140b249af6fe73d45717185fad48962) **—第一部**
> 
> [**打赏 Github Repos**](https://medium.com/coders-mojo/6-exceptional-github-repos-for-all-developers-part-2-3eec9a68c31c?sk=8e31d0eb7eb1d2d0bbbcecaa66bd4e7e) **—第二部**
> 
> [**所有数据科学和机器学习资源**](/best-resources-for-data-science-and-machine-learning-full-list-5ceb9a2791bf?sk=cf85b2cef95560c58509877a794577ff)
> 
> [**210 机器学习项目**](/210-machine-learning-projects-with-source-code-that-you-can-build-today-721b035649e0?sk=da5f593572a0261a6314afad99a0356c)

## 科技时事通讯—

> 如果你感兴趣，你可以加入我的时事通讯，通过它我向超过 30，000 名读者发送技术面试技巧，技术，模式，黑客——软件开发，ML，数据科学，创业公司和技术项目。可以订阅**科技 Brew :**

[](https://naina0405.substack.com/) [## 点火器

### 数据科学，人工智能，人工智能和更多…点击阅读由 Naina Chaturvedi 撰写的 Ignito，子堆栈出版物。推出 7 个月…

naina0405.substack.com](https://naina0405.substack.com/) 

## Github —

[](https://github.com/Coder-World04) [## 编码器-world 04-概述

### 此时您不能执行该操作。您已使用另一个标签页或窗口登录。您已在另一个选项卡中注销，或者…

github.com](https://github.com/Coder-World04) 

# 2.默认字典

默认 dict 是高性能容器数据类型的一部分，它是 Dict 的一个子类，返回一个 dictionary 对象。它从不引发键错误，并使用默认的工厂函数进行初始化。

```
from collections import defaultdicttuition_balance= defaultdict(lambda:200)tuition_deposits = {'Naina' : 100, 'Steve' : 300, 'Benedict' : 200}for name,deposits in tuition_deposits.items():
    tuition_balance[name]+=deposits
print(dict(tuition_balance))
```

输出—

```
{'Naina': 300, 'Steve': 500, 'Benedict': 400}
```

# 3.命名元组

NamedTuples 是属于 collections 模块的轻量级、内存高效的对象类型。这些是类似 dict 的构造，可以通过索引、键名或 getattr()函数访问属性值。

```
from typing import NamedTuple
class Account(NamedTuple):
    name:str
    value: float

Account(name='Naina',value=100)
```

输出—

```
Account(name='Naina', value=100.1)from collections import defaultdict
tuition_balances= defaultdict(lambda:200)tuition_deposits = [Account(name='Naina', value=100),
                    Account(name='Steve', value= 300),
                    Account(name='Benedict',value=200)]for deposit in tuition_deposits:
    tuition_balances[deposit.name]+=deposit.value
print(dict(tuition_balances))
```

输出—

```
{'Naina': 300, 'Steve': 500, 'Benedict': 400}
```

# 4.类型提示

如果您正在处理复杂的数据结构，那么类型提示非常有助于理清复杂性，并使您的代码更具可读性(特别是当您希望以后引用代码时)。

```
def calc(x:set, y:set) ->set:
    var_one = x + y
    var_two = x | y
    var_three = x & y
    return var_three
a: set = {5,6,20,30,10,4,22}
b: set = {20,30,45,6,7,3,22}
result : set=calc(a,b)
print(result)
```

输出—

```
{6, 20, 22, 30}
```

# 以下是一些供数据科学家使用的 Python 高级技术:

1.  ***Pandas:****Pandas 是 Python 中一个强大的数据分析库。数据科学家可以使用它轻松清理、操作和分析大型数据集。*
2.  ***Numpy:****Numpy 是 Python 中用于数值计算的库。它为数组和矩阵操作提供了高级功能，使其成为数据科学家的必备工具。*
3.  ***Matplotlib 和 Seaborn:****Matplotlib 和 Seaborn 是 Python 中数据可视化的库。它们为创建有意义和有见地的可视化提供了多种选择，以帮助数据科学家理解和交流他们的发现。*
4.  ***sci kit-learn:****sci kit-learn 是用 Python 编写的机器学习的库。它为诸如回归、分类、聚类等任务提供了广泛的算法。*
5.  ***TensorFlow 和 PyTorch:****tensor flow 和 py torch 是 Python 中的深度学习库。它们为构建和训练神经网络提供了必要的工具和资源，使它们对于处理大型复杂数据集的数据科学家来说至关重要。*
6.  ***多线程和多处理:*** *多线程和多处理是 Python 中并行处理的技术。它们允许数据科学家利用多个内核和处理器，使他们的计算更快、更高效。*
7.  ***函数装饰器:*** *函数装饰器是 Python 中修改函数行为的强大工具。数据科学家可以使用它们来添加自定义功能，使代码更具可读性，并实施编码标准。*
8.  ***上下文管理器:*** *上下文管理器是 Python 中管理资源的一种方式，比如打开和关闭文件、获取和释放锁等等。数据科学家可以使用它们来简化代码，提高程序的可靠性和性能。*
9.  ***生成器:*** *生成器是 Python 中生成值序列的一种方式。数据科学家可以使用它们以节省内存的方式处理大型数据集，因为它们一次只生成一个值。*
10.  ***元类:*** *元类是 Python 中修改类行为的一种方式。数据科学家可以使用它们来创建定制的类，执行编码标准，并简化他们的代码。*

# 所有完整的系统设计系列零件—

> [***1。系统设计基础***](https://medium.com/coders-mojo/complete-system-design-series-part-1-45bf9c8654bc)
> 
> [***2。水平和垂直缩放***](https://medium.com/coders-mojo/complete-system-design-series-part-2-922f45f2faaf)
> 
> [***3。负载平衡和消息队列***](https://medium.com/coders-mojo/part-3-complete-system-design-series-e1362baa8a4c)
> 
> [***4。高层设计和低层设计、一致散列、单片和微服务架构***](https://medium.com/coders-mojo/part-4-complete-system-design-series-138bc9fbcfc0)
> 
> [***5。缓存、索引、代理***](https://medium.com/coders-mojo/part-5-complete-system-design-series-4b9b04f23608)
> 
> [***6。联网、浏览器如何工作、内容网络交付(CDN)***](https://medium.com/coders-mojo/part-6-complete-system-design-series-59a2d8bbf1ed)
> 
> [***7。数据库分片、CAP 定理、数据库模式设计***](https://medium.com/coders-mojo/part-7-complete-system-design-series-1bef528923d6)
> 
> [***8。并发、API、组件+ OOP +抽象***](https://medium.com/coders-mojo/part-8-complete-system-design-series-57bc88433c8e)
> 
> [***9。***](https://medium.com/coders-mojo/part-9-complete-system-design-series-df975c85ec51) 绩效评估与规划
> 
> **10*。*** [***地图缩小，图案和微服务***](https://medium.com/coders-mojo/part-10-complete-system-design-series-523b4dd978bf?sk=741f92929c8639a2e4cf218521e8cc4a)
> 
> ***11。***[***SQL vs NoSQL 和云***](https://naina0412.medium.com/part-11-complete-system-design-series-9c8efbc0237a?sk=5bddf2adc78ea4947ae88ab21c94af1c)
> 
> [***12。最受欢迎的系统设计问题***](https://medium.com/coders-mojo/most-popular-system-design-questions-mega-compilation-45218129fe26)

# Github —

 [## Complete-System-Design/readme . MD at main Coder-world 04/Complete-System-Design

### 这个存储库包含了精通系统设计主题所需的一切，您应该了解系统…

github.com](https://github.com/Coder-World04/Complete-System-Design/blob/main/README.md) 

# 感谢阅读。继续编码。

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