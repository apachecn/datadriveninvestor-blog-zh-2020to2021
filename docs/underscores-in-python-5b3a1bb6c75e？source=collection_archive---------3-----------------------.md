# Python 中的下划线(_)

> 原文：<https://medium.datadriveninvestor.com/underscores-in-python-5b3a1bb6c75e?source=collection_archive---------3----------------------->

## 如何在您的代码中使用它们…

![](img/db2adca65cb83ef39ad7a93e1c5fb021.png)

Pic credits : Unsplash.com ( [Shahadat Rahman](https://unsplash.com/@hishahadat) )

你必须熟悉 Python 中的双下划线(__)，例如方法。下划线是 Python 中的独特字符，有助于用户高效地编写代码。在这篇文章中，我们将探索如何在你的代码中使用单下划线和双下划线。

**Python 中的下划线有多种用途，包括:**

1.  *命名约定:在命名约定中使用下划线来表示变量、类、方法或其他标识符的含义和用途。比如* `*private_variable*` *、* `*_private_method*` *、* `*__protected_method*` *都是 Python 中常见的命名约定。*
2.  可读性:下划线可以用来提高长的或复杂的数字或名字的可读性。比如 `*num_of_users*` *比* `*numofusers*` *更容易读懂。*
3.  分隔单词:下划线可以用来分隔变量名中的单词，以便于阅读和理解。比如 `*first_name*` *比* `*firstname*` *更容易理解。*
4.  *占位符变量:下划线可以作为 for 循环中的占位符来表示一个未使用的循环变量。*
5.  *数字文字:通过将数字分组，下划线可用于提高大型数字文字的可读性。比如* `*1_000_000*` *比* `*1000000*` *更容易读。*

[](https://medium.com/datadriveninvestor/hacker-earth-surveyed-16000-developers-from-76-countries-heres-what-i-found-dbd5d7c422b0) [## 黑客地球调查了来自 76 个国家的 16000 名开发者——以下是我的发现

### 惊人的洞察力…

medium.com](https://medium.com/datadriveninvestor/hacker-earth-surveyed-16000-developers-from-76-countries-heres-what-i-found-dbd5d7c422b0) 

让我们开始吧。

# 1)__ 姓名 _ _

在 Python 中，__name__ 是编写 main 函数时必须使用的内置变量。作为魔术方法之一调用，它计算当前模块的名称，如下面的代码所示。

[](https://naina0412.medium.com/read-and-process-large-datasets-in-seconds-part-1-1ce12ed95c71) [## 在几秒钟内读取和处理大型数据集—第 1 部分

### 在几秒钟内处理十亿行..

naina0412.medium.com](https://naina0412.medium.com/read-and-process-large-datasets-in-seconds-part-1-1ce12ed95c71) 

## 实施—

```
if __name__ == "__main__":
   print("F_2")
else:
   print("F_2_imported")
print("File 2 __name__ has set to {}" .format(__name__))
```

## 输出—

```
F_2
File 2 __name__ has set to __main__
```

[](https://naina0412.medium.com/analyzing-video-using-python-opencv-and-numpy-5471cab200c4) [## 使用 Python、OpenCV 和 NumPy 分析视频

### 通过代码实现…

naina0412.medium.com](https://naina0412.medium.com/analyzing-video-using-python-opencv-and-numpy-5471cab200c4) 

# 其他一些最好的系列—

> [**30 天的机器学习 Ops**](https://medium.com/coders-mojo/day-1-of-30-days-of-machine-learning-ops-7c299e4b09be?sk=4ab48350a5c359fc157109e48b1d738f)
> 
> [**30 天自然语言处理系列**](https://medium.com/coders-mojo/quick-recap-30-days-of-natural-language-processing-nlp-with-projects-series-ceb674e3c09b?sk=ca09b27b3d5867f23ab4dc367b6c0c32)
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
> [**用最热门的问题系列**](https://medium.com/coders-mojo/system-design-made-easy-quick-recap-of-complete-system-design-34af7e3aedfb?sk=bdd6a19edc1f3ce4a5064923f5b68721) 完成系统设计
> 
> [**与项目**](https://medium.com/coders-mojo/complete-data-preprocessing-and-data-visualization-with-projects-mega-compilation-part-2-41584ef0920e?sk=842390da51689b8d43148c3980570db0) 一起完成数据可视化及预处理系列
> 
> [**完整的 Python 系列与项目**](https://medium.com/coders-mojo/complete-python-and-projects-mega-compilation-7ec8f7adfe71?sk=ee0ecf43f23c6dd44dd35d984b3e5df4)
> 
> [**完成高级 Python 系列与项目**](https://medium.com/coders-mojo/complete-advanced-python-with-projects-mega-compilation-part-6-729c1826032b?sk=7faffe20f8039fa57099f7a372b6d665)
> 
> [**Kaggle 最会教你的笔记本**](https://medium.com/coders-mojo/my-list-of-kaggle-best-notebooks-topic-wise-data-science-and-machine-learning-part-2-84772863e9ae?sk=5ed02e419854a6c11add3ddc1e52947f)
> 
> [T5【Git】完全开发者指南 ](/the-complete-developers-guide-to-git-6a23125996e1?sk=e30479bbe713930ea93018e1a46d9185)
> 
> [**打赏 Github Repos**](https://medium.com/coders-mojo/6-exceptional-github-repos-for-all-developers-part-1-21e8fa04e150?sk=9140b249af6fe73d45717185fad48962) **—第一部分**
> 
> [**打赏 Github Repos**](https://medium.com/coders-mojo/6-exceptional-github-repos-for-all-developers-part-2-3eec9a68c31c?sk=8e31d0eb7eb1d2d0bbbcecaa66bd4e7e) **—第二部分**
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

# 2)赋值

如果在解包时不想使用任何特定的变量名/值，那么使用特殊的 variable _ 来赋值，如下面的代码所示。

## 实施—

```
a, *_, b = ['USA', 'Australia', 'Canada','Germany']
print(a, b)
```

## 输出—

```
USA Germany
```

## 实施—

```
n1, _, n3, n4 = [1,2,3,5]
print(n1, n3, n4)
```

[](https://naina0412.medium.com/6-exceptional-github-repos-for-all-developers-part-2-3eec9a68c31c) [## 6 面向所有开发者的特殊 GitHub 回购—第二部分

### 把它加入书签…它会给你很大的帮助

naina0412.medium.com](https://naina0412.medium.com/6-exceptional-github-repos-for-all-developers-part-2-3eec9a68c31c) 

## 输出—

```
1 3 5
```

[](https://naina0412.medium.com/writing-efficient-python-code-part-1-e02763632080) [## 编写高效的 Python 代码—第 1 部分

### Python 是科技界最流行、使用最广泛的编程语言之一。

naina0412.medium.com](https://naina0412.medium.com/writing-efficient-python-code-part-1-e02763632080) 

# 3.环

您可以在循环中使用特殊字符 _ 来遍历可迭代对象，如列表、元组、字典和集合，如下面的代码所示。

[](https://naina0412.medium.com/holidays-alert-top-5-free-data-science-ai-ml-courses-you-can-finish-8067ecff7c1d) [## 【假期提醒】:你可以完成的前 5 名免费数据科学、AI & ML 课程

### 令人惊叹的课程…

naina0412.medium.com](https://naina0412.medium.com/holidays-alert-top-5-free-data-science-ai-ml-courses-you-can-finish-8067ecff7c1d) 

## 实施—

```
countries = ['USA', 'Australia', 'Canada','Germany', 'Switzerland', 'Argentina', 'Brazil', 'Kenya', 'Britain']
for _ in countries:
    print(_)
```

## 输出—

```
USA
Australia
Canada
Germany
Switzerland
Argentina
Brazil
Kenya
Britain
```

## 实施—

```
_ = 20
while _ < 50:
    print(_, end = '\n') 
    _ += 2
```

[](https://medium.com/coders-mojo/6-exceptional-github-repos-for-all-developers-part-1-21e8fa04e150) [## 6 面向所有开发者的特殊 GitHub 回购—第 1 部分

### 把它加入书签…它会给你很大的帮助

medium.com](https://medium.com/coders-mojo/6-exceptional-github-repos-for-all-developers-part-1-21e8fa04e150) 

## 输出—

```
20
22
24
26
28
30
32
34
36
38
40
42
44
46
48
```

[](/introduction-to-statistics-in-python-part-1-14e69ef05abe) [## Python 中的统计简介—第 1 部分

### 统计很容易…真的吗？

medium.datadriveninvestor.com](/introduction-to-statistics-in-python-part-1-14e69ef05abe) 

# 4)使用下划线的命名约定

类型是—

-内部使用的单个前置下划线: **_var**

-单个后置下划线，当您想在代码中使用 Python 关键字作为变量时使用: **var_**

-双前置下划线用于名称混淆: **__var**

-双下划线(前后都有)用于方法名，如第 1 点所示: **__var__**

[](https://www.datadriveninvestor.com/2020/12/01/how-to-build-a-twitter-scraping-app-with-python/) [## 如何用 Python |数据驱动投资者构建 Twitter 抓取应用

### 每秒发出约 6000 条推文，每天发布 5 亿条推文，普通人甚至不能…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/12/01/how-to-build-a-twitter-scraping-app-with-python/) 

## 实施 1 —

```
def _test_func():
    return 20
_test_func()
```

## 输出—

```
20
```

## 实施 2 —

```
def test_function(list_):
    return list_* 2
test_function([1,2,4,5])
```

## 输出—

```
[1, 2, 4, 5, 1, 2, 4, 5]
```

## 实施 3—

```
class test_function():def __init__(self):

        self._b = 20
        self.__c = 30

t1 = test_function()
dir(t1)
```

## 输出—

```
['__class__',
 '__delattr__',
 '__dict__',
 '__dir__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__getattribute__',
 '__gt__',
 '__hash__',
 '__init__',
 '__init_subclass__',
 '__le__',
 '__lt__',
 '__module__',
 '__ne__',
 '__new__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__setattr__',
 '__sizeof__',
 '__str__',
 '__subclasshook__',
 '__weakref__',
 '_b',
 '_test_function__c']
```

# 所有完整的系统设计系列零件—

> [***1。系统设计基础知识***](https://medium.com/coders-mojo/complete-system-design-series-part-1-45bf9c8654bc)
> 
> [***2。水平和垂直缩放***](https://medium.com/coders-mojo/complete-system-design-series-part-2-922f45f2faaf)
> 
> [**3。负载平衡和消息队列**](https://medium.com/coders-mojo/part-3-complete-system-design-series-e1362baa8a4c)
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
> [***9。***](https://medium.com/coders-mojo/part-9-complete-system-design-series-df975c85ec51) 预估与策划、绩效
> 
> ***10。*** [***地图缩小，图案和微服务***](https://medium.com/coders-mojo/part-10-complete-system-design-series-523b4dd978bf?sk=741f92929c8639a2e4cf218521e8cc4a)
> 
> **11*。***[***SQL vs NoSQL***](https://naina0412.medium.com/part-11-complete-system-design-series-9c8efbc0237a?sk=5bddf2adc78ea4947ae88ab21c94af1c)
> 
> [***12。最受欢迎的系统设计问题***](https://medium.com/coders-mojo/most-popular-system-design-questions-mega-compilation-45218129fe26)

# Github —

 [## Complete-System-Design/readme . MD at main Coder-world 04/Complete-System-Design

### 这个存储库包含了精通系统设计主题所需的一切，您应该了解系统…

github.com](https://github.com/Coder-World04/Complete-System-Design/blob/main/README.md) 

# 感谢阅读。继续给你们编码:)

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

medium.com](https://medium.com/datadriveninvestor/advanced-python-made-easy-part-1-ce1e2f17431e) [](https://medium.com/datadriveninvestor/pythons-f-strings-d7dc11c30d1c) [## Python 的 F 字符串

### 包含代码的完整实施指南…

medium.com](https://medium.com/datadriveninvestor/pythons-f-strings-d7dc11c30d1c) 

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)