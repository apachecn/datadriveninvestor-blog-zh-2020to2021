# 金融风险管理

> 原文：<https://medium.datadriveninvestor.com/financial-risk-management-using-python-6c412a32b83f?source=collection_archive---------11----------------------->

学习如何使用统计方法来评估投资的财务风险和财务回报

![](img/7727f83d53923f98907ddab704dc2fe5.png)

Photo by [Alexander Schimmeck](https://unsplash.com/@alschim?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/money?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

# 摘要

*   在最小化投资风险的同时最大化收益是数量金融学最重要的原则之一
*   对投资回报分布的分析是任何投资组合风险管理过程的起点
*   分析回报分布可以让我们直观地看到给定回报范围的频率
*   风险管理对每个金融机构都变得至关重要(尤其是在 2008 年金融危机之后)

# 什么是投资风险？

在量化金融中，投资风险或金融风险可以有多种定义:

*   投资赔钱的可能性或概率
*   衡量市场不确定性的标准
*   财务回报的方差(对于那些经验丰富的统计学家来说)

正如我之前提到的，最小化风险对于大多数金融机构来说至关重要(说起来容易做起来难！).在下一节中，我们将讨论各种可以用来衡量风险的统计技术；毕竟，如果我们想最小化一项投资的财务风险，我们首先需要找到一种方法来衡量它，对吗？

[](https://www.datadriveninvestor.com/2020/08/20/financial-crimes-compliance-and-covid-19/) [## 金融犯罪、合规和新冠肺炎|数据驱动型投资者

### 非法行为者利用全球经济紧张的脆弱性和供应链中断造成的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/08/20/financial-crimes-compliance-and-covid-19/) 

# 如何衡量财务风险？

在衡量投资的财务风险时，通常会使用多个指标:

*   每日财务收益的 [**标准差**](https://www.investopedia.com/terms/s/standarddeviation.asp)
*   每日收益率分布的[](https://en.wikipedia.org/wiki/Kurtosis)
*   ****每日收益分布的 [**偏度**](https://en.wikipedia.org/wiki/Skewness)****
*   ****最大历史提款****
*   ****风险价值(VAR)****

******访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)****