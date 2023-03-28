# 什么是随机化算法？

> 原文：<https://medium.datadriveninvestor.com/what-is-a-randomized-algorithm-9bca4307665c?source=collection_archive---------17----------------------->

基于执行过程中产生的随机选择做出决策的算法称为**随机化算法。….
*懂了 Ryt？***

是的，我知道，这很难理解，所以我想出了一个可以用随机算法解决的问题，这样我们就可以很容易地理解它。

**招聘问题**

假设你是一个招聘人员，你需要招聘一个由代理机构派来的人来代替当前的雇员。

基本上，你需要雇佣比现在的员工更优秀的人。

你知道，中介从来不会免费提供你需要为中介付费的服务。

*   面试费→你需要支付给中介一小笔面试费
*   雇佣费→当你决定雇佣一个人时，你需要支付给代理公司一大笔费用。

> 注→ **贵公司总是希望有一个最佳人选**

如果被面试的人比现在的员工更好，那就雇佣这个新人。

让我们做一个假设，当你雇佣一个人时，你需要支付面试费+雇佣费，你可能已经雇佣了一个人，第二天面试的人比你雇佣的人更好，那么你也需要雇佣这个人并支付面试费+雇佣费。

我相信问题是清楚的，所以

## 你如何估算代理公司的报酬？

我们的候选人被命名为 1，2，3 …为简单起见

面试候选人 I 后，确定我是否是目前为止最好的人选，然后我们雇用他

成本定义如下

面试费——Ci

租用费——Ch

让我们用 python 写一个小算法

```
current_employee, Ci, Ch;// define Ci, Ch, current employeecost = 0def hire_assitant(candidates):    for i in range(len(candidates)):
        candidate = get_candidate(candidate[i].name)
        result = interview_candidate(candidate)
        if result == "hired":
           cost = cost + Ci + Ch
        else:
           cost = cost + Cidef interview_candidate(candidate):
    if candidate is better than current employee:
       current employee = candidate
       return "hired"
    else:
       return "Not hired"def get_candidate(candidate_name):
    return the candidate to the interview by agency
```

所以基本上成本等式如下

> ***cost = nCi * mCh*** 其中 m 人从 n 名候选人中聘用，如果 Ci 较小，我们可以只关注 **mCh**

## 最糟糕的情况

在最坏的情况下，我们会雇佣所有的人，在雇佣前一天每个人都是最好的。那么成本将是 nCh (n 和 m 相同)。

[](https://www.datadriveninvestor.com/2021/01/07/alpha-fold-and-gpt-how-radical-technology-disruptions-will-affect-our-future/) [## 阿尔法折叠和 GPT -激进的技术颠覆将如何影响我们的未来|数据驱动…

### 2019 年，我写了如果你关心 AI，你需要关注的前 10 个人。最近有两个机构提到…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2021/01/07/alpha-fold-and-gpt-how-radical-technology-disruptions-will-affect-our-future/) 

## **但是很有可能，它不会发生，**

我们需要有一个随机的顺序来选择面试的候选人。所以我们能做的是，我们要求代理机构给出候选人名单。然后我们可以每天随机选择一个人进行面试。它使我们减少得到最坏情况的概率。我们如何做到这一点？这里我们把我们的算法变成一个随机算法。

简单地说，我们在要求代理机构带人来之前，先把名单打乱。

所以我们的算法如下

```
current_employee, Ci, Ch;// define Ci, Ch, current employeecost = 0def hire_assitant(candidates):
 **candidates = shuffle(candidates)**    for i in range(len(candidates)):
        candidate = get_candidate(candidate[i].name)
        result = interview_candidate(candidate)
        if result == "hired":
           cost = cost + Ci + Ch
        else:
           cost = cost + Cidef interview_candidate(candidate):
    if candidate is better than current employee:
       current employee = candidate
       return "hired"
    else:
       return "Not hired"def get_candidate(candidate_name):
    return the candidate to the interview by agency
```

我们通过洗牌随机选择下一个候选人。这是在算法中完成的。我们的输入(候选列表)可能是随机的或预先排序的，但我们的算法使它成为随机的，并基于随机选择作出决定

**现在看看定义**

> 基于在**执行**期间生成的**随机选择**做出决策的算法被称为*随机化算法。*

在我们的招聘算法中，候选人是随机抽取的。所以这类算法被称为随机化算法。

## 随机化算法的几个关键点

*   这使我们降低了最坏情况发生的可能性
*   在执行过程中进行随机选择的算法
*   这些随机的选择被用来做决定
*   它不会产生不好的输入，但可能会产生不好的随机选择(候选列表可能会按照从差到好的顺序排序，但这不是问题，因为我们在算法中对它进行了洗牌)

## 当我们可以使用这种方法时

当我们有这么多的方法来进行，同时我们很难找到一个可以保证好的方法，那么我们可以选择这个方法。在这里，我们有好的方法，但可能没有最好的方法。

![](img/580e4da54b9b5d9e22b20faec1118a8b.png)

Photo by [Brett Jordan](https://unsplash.com/@brett_jordan?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/random?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

好了，这个博客到此为止。我相信你对随机化算法有了一些基本的了解。不仅如此，我还计划写一篇关于随机快速排序的博客。

## 参考

Cormen，Leiserson，Rivest，Stein (CLRS 图书)，《算法导论》，第 3 版(2009)，印度版，可在书店购买。ISBN:978–81–203–4007–7

> ***感谢阅读本博客！！！希望你会喜欢它。如果你有任何问题，请在下面留言或通过 Twitter 问我。***

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)