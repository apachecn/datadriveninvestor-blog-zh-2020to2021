# 测试机器学习算法准确性的基本指标

> 原文：<https://medium.datadriveninvestor.com/metrics-to-test-the-accuracy-of-machine-learning-algorithms-67adf367f60?source=collection_archive---------3----------------------->

## 它们是:磷、氮、总磷、总氮、FP、FN、TPR、SPC、TNR、PPV、NPV

![](img/a2bec26e1cf9da5c85fc50efb6a0f386.png)

Photo by [Dominik Scythe](https://unsplash.com/@drscythe?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

假设你是一名医生，你正在预测某人是否会感染冠状病毒。你评估 1000 人的数据，并预测 450 人将有冠状病毒。到赛季末，你会发现只有 400 人感染了冠状病毒。有 50 个人幸运地没有感染冠状病毒。但是你的预测并不好。

我们会一步一步来。

# 什么是实际上的正样本和实际上的负样本？

```
|     P     |     N     |
|-----------|-----------|
|    400    |    600    |
|-----------|-----------|
```

## **实际阳性样本**

实际正样本(P)是真实世界的可观察状态的`“true”`状态的数值计数。

例如:在一个一千人的群体中，有四百人感染冠状病毒，那么`P=40`。

## **实际阴性样本**

实际负样本(N)是现实世界中一个可观测状态的`“false”`状态的数值计数。

[](https://www.datadriveninvestor.com/2020/02/19/five-data-science-and-machine-learning-trends-that-will-define-job-prospects-in-2020/) [## 将定义 2020 年就业前景的五大数据科学和机器学习趋势|数据驱动…

### 数据科学和 ML 是 2019 年最受关注的趋势之一，毫无疑问，它们将继续发展…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/19/five-data-science-and-machine-learning-trends-that-will-define-job-prospects-in-2020/) 

举个例子:在一个一千人的群体中，有六百人没有感染冠状病毒，那么`N=60`。

# 基本指标

```
Total: 1000  | Predicted | Predicted |
             |    as: X  | as: not X |
-------------|-----------|-----------|
 True: X     |    300    |    100    |
-------------|-----------|-----------|
 True: not X |    150    |    450    |
-------------|-----------|-----------|
```

## **真阳性**

真阳性(TP 或`hit`)是所有被正确分类为`positive`的`positive samples`的数字计数。

例如:在一个 1000 人的小组中，有 300 人预计会感染冠状病毒，并被证明感染了冠状病毒`TP=30`。

## **真底片**

真正的负数(TN 或`correct rejection`)是所有被正确分类为`negative`的`actual negative samples`的数字计数。

例如:在一个 1000 人的小组中，有 450 人预计不会感染冠状病毒，并被证明没有感染冠状病毒`TN=45`。

## **误报**

误报(FP 或`false alarm`)是所有被错误分类为`positive`的`actual negative samples`的数字计数。

例如:在一个 1000 人的群体中，有 150 人预计会感染冠状病毒，然后被证明没有感染冠状病毒`FP=15`。

## **假阴性**

假阴性(FN 或`miss`)是所有被错误分类为阴性的`actual positive samples`的数字计数。

例如:在一个 1000 人的小组中，有 100 人预计不会感染冠状病毒，但被证明感染了冠状病毒`FN=10`。

# 如何为你的机器学习计算一个指标叫做灵敏度、特异性、精度或者负预测值？

```
Total: 1000  |    Predicted     |     Predicted      |
             |      as: X       |     as: not X      |
-------------|------------------|--------------------|
 True: X     |   TP/(TP+FN)     |    TP/(TP+FN)      |
-------------|------------------|--------------------|
 True: not X |    FP/(FP+TN)    |    TN/(FP+TN)      |
-------------|------------------|--------------------|
```

## 灵敏度*或真阳性率*

真阳性率(TPR)也称为召回率，是测试为阳性的标签和所有实际为阳性的标签的比例。

```
TPR = TP/P = TP/(TP+FN)
```

所以，举我们的例子:`TPR = 30/40 = 0.75`。这将被报告为`75%` 灵敏度。

## **特异性或真阴性率**

特异性(SPC)或真阴性率(TNR)是测试为阴性的标记与所有实际为阴性的标记的比例。

```
TNR = TN/N = TN/(TN+FP)
```

我们计算如下:`TNR = 450/600 = 0.75`。这将被报告为`75%`特异性。

## **精度或阳性预测值**

阳性预测值(PPV)，也称为精度。阳性预测值回答了“如果测试结果为阳性，那么它对疾病实际存在的预测有多好？”。

```
PPV = TP/(TP+FP)
```

所以，对于我们的例子:`PPV = 30/(30+15) = 30/45 = 66.67%`。这将被报告为`66.67%`精度。

## **阴性预测值**

负预测值(NPV)是相同的 PPV，但对于负值，它是预测结果为负的记录确实应该为负的概率。

```
NPV = TN/(TN+FN)
```

我们计算如下:`45/(45+10) = 45/55 = 81.82%`。这将被报告为`81.82%` NPV。

# 结论

结果显示你可以`75%`正确预测人得冠状病毒，也就是灵敏度为`75%`。也说明你可以通过`75%`正确预测人不会得冠状病毒，也就是特异性为`75%`。