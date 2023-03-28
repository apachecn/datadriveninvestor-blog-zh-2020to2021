# 第七十二条规则

> 原文：<https://medium.datadriveninvestor.com/amount-calculation-rule-of-72-6e9d4b99ee1?source=collection_archive---------10----------------------->

![](img/7895671e0aba3ba71c3223991c7881b3.png)

Photo by [Ali Yılmaz](https://unsplash.com/@zamansizturk?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/calculation?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

> “复利是世界第八大奇迹。理解它的人赢得了它……不理解它的人付出了它”——阿尔伯特·爱因斯坦

在这篇文章中，我将涵盖一个简单的方法，通过它你可以计算本金，利率，任期或金额的基础上，其他三个给定的。

[](https://www.datadriveninvestor.com/2020/05/25/shors-algorithm-the-bane-of-rsa/) [## 肖尔算法:RSA 的克星|数据驱动的投资者

### RSA 加密是一种公钥加密系统。这意味着它有一个所有人都可以访问的公钥和一个私钥…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/05/25/shors-algorithm-the-bane-of-rsa/) 

这是知道一个投资计划是否对你有利可图的最快方法。例如，计算以一次总付方式投资时，您的共同基金投资将在多少年内以平均回报率(基于其过去的表现)翻倍。

这是一个近似的方法，不能给出一个实际值。您可以在以下场景中使用此方法。

*   计算最终金额—给定本金、期限和利率时
*   计算任期—当金额、本金和利率给定时
*   计算利率——给定金额、本金和期限时
*   计算本金——给定金额、期限和利率时

**假设:**

*   当 X(本金)被投资时，在 T 年内，以 R%的利息，A 的金额翻了一倍。
*   此处提到的利率是以每一保有权单位(每季度/每半年/每年)计算的复利。
*   在任期开始时进行一次性投资，在任期内没有部分定期投资

**这是怎么算出来的？**

如果你将 X 卢比投资到一个计划中，期限为 8 年，那么如果每年复利，金额应该变成 9%的 2 倍卢比。在这里，我们用 72 除以 8 年得到了数字 9。

让我们看一些例子:

示例 1:

```
Principal = Rs 1000
Rate of interest = 9% (compounded annually)
Amount = Rs 2000Approximate time to be taken in doubling the amount = 72/9 = 8 years
```

示例 2:

```
Principal = Rs 1000
Tenure = 6 years
Amount = Rs 2000Approximate interest rate required to double the amount = 72/6 = 12 % compounded annually
```

示例 3:

```
Principal = Rs 1000
Tenure = 12 years
Amount = Rs 2000Let R be the rate which is compounded semi-annually (half yearly)R = 72 / ( 12 * 2) = 3% compounded half yearly (6% compounded yearly)
```

在半年或季度复利的情况下，我们必须用 72 除以任期数。在上述案例中，保有权期为 6 个月，保有权期总数为 24 (12 乘以 2)。

示例 4:

```
Principal = Rs 1000
Rate of interest = 3% (compounded quarterly)
Amount = Rs 2000Tenure = 72 / 3 = 24 quarters (6 years)
```

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)