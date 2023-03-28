# 重要的数据科学项目

> 原文：<https://medium.datadriveninvestor.com/non-trivial-data-science-projects-693edfe146d?source=collection_archive---------0----------------------->

![](img/f791663d2c2fd36c344c8705a7005634.png)

Image Source: [Pexels](https://www.pexels.com/photo/colorful-color-play-concentration-54101/)

## 数据科学项目并不总是这样:这是数据，用它来建立一个预测模型。

# 一.导言

数据科学项目的范围和复杂性各不相同。有时，该项目可以简单到产生汇总统计数据、图表和可视化。它还可能涉及构建回归模型、分类模型或使用时间相关数据集进行预测。该项目也可能非常复杂和困难。在这种情况下，对于使用哪种特定类型的模型，没有提供明确的指导。在这种情况下，由数据科学家的追求者来决定什么模型是合适的。在这种情况下，必须考虑所有模型，包括概率模型。本文将讨论两个不同复杂程度和难度的数据科学工作面试项目的例子。

# 二。琐碎的项目

**指令**

*这个编码练习应该用 Python 来执行(Python 是团队使用的编程语言)。你可以自由使用互联网和任何其他图书馆。请将您的作品保存在 Jupyter 笔记本中，并通过电子邮件发送给我们进行审核。*

*数据文件:cruise_ship_info.csv(该文件将通过电子邮件发送给您)*

***目标:*** *建立一个回归器，为潜在的船舶购买者推荐“船员”规模。请执行以下步骤(提示:使用 numpy、scipy、pandas、sklearn 和 matplotlib)*

*1。读取文件并显示列。*

*2。计算数据的基本统计数据(计数、平均值、标准差等)，检查数据并陈述你的观察结果。*

*3。选择对预测“团队”规模可能很重要的列。*

*4。如果您删除了列，请解释为什么要删除这些列。*

*5。对分类特征使用一次性编码。*

6。创建训练集和测试集(将 60%的数据用于训练，其余用于测试)。

7。建立一个机器学习模型来预测“船员”的规模。

8。计算训练集和测试数据集的皮尔逊相关系数。

9。描述模型中的超参数，以及如何更改它们来提高模型的性能。

*10。什么是正规化？你的模型中的正则化参数是什么？*

*为测试和训练集绘制正则化参数值与皮尔逊相关性的曲线图，并查看您的模型是否有偏差问题或方差问题。*

**评论和备注:**这是一个非常简单(琐碎)的问题的例子。数据集干净小巧(160 行 9 列)，指令非常清晰。因此，您所需要做的就是遵循指令并生成您的代码。还要注意，指令明确指定 python 作为建模的编程语言。

[](https://www.datadriveninvestor.com/2020/03/24/encoder-decoder-sequences-how-long-is-too-long/) [## 编码器解码器序列:多长是太长？数据驱动的投资者

### 在机器学习中，很多时候我们处理的输入是序列，输出也是序列。我们称这样的一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/03/24/encoder-decoder-sequences-how-long-is-too-long/) 

# 三。不平凡的项目

**指令**

*在这个问题中，你将预测贷款组合的结果。每笔贷款计划在 3 年内偿还，结构如下:*

*   *首先，借款人收到资金。这个事件被称为起源。*
*   *然后，借款人定期还款，直到发生以下情况之一:*

*(i)借款人在 3 年期限结束前停止付款，通常是由于财务困难。这一事件被称为销账，然后贷款被称为已销账。*

*(ii)借款人继续还款，直到发放日之后 3 年。至此，债务已全部还清。*

*在附加的 CSV 中，每行对应一笔贷款，列的定义如下:*

*   *标题为“自发起以来的天数”的列表示发起和数据收集日期之间经过的天数。*
*   *对于在收集数据之前已经销账的贷款，标题为“从发起到销账的天数”的列表示发起和销账之间经过的天数。对于所有其他贷款，此栏为空白。*

***目标*** *:我们希望您能估计一下，在这些贷款的 3 年期限全部结束时，它们将会被冲销的比例。请包括你如何得到你的答案的一个严格的解释，并且包括你使用的任何代码。你可以做出简化的假设，但是请明确地陈述这些假设。请随意以您喜欢的任何形式提出您的答案；特别是 PDF 和 Jupyter 笔记本都可以。此外，我们希望这个项目不会占用您超过 3-6 个小时的时间。*

**评论和备注:**这里的数据集比较复杂(有 50000 行 2 列；和许多丢失的值)，问题不是很简单。你必须严格检查数据集，然后决定使用什么模型。这个问题将在一周内解决。它还规定提交一份正式的项目报告和一份 R 脚本或 Jupyter 笔记本文件。

# 四。两个项目的建议解决方案

如果你对这两个项目的数据集和解决方案感兴趣，请发邮件给我:***benjaminobi@gmail.com***

我建议你在联系我寻求解决方案之前，先自己尝试一下这些问题。对于这个重要的问题，我必须使用我认为正确的方法来解决问题。但是请记住，数据科学问题的解决方案不是唯一的。所以欢迎你尝试自己选择的不同模式或方法。

## 其他数据科学/机器学习资源

[数据科学课程](https://medium.com/towards-artificial-intelligence/data-science-curriculum-bf3bb6805576)

[机器学习的基本数学技能](https://medium.com/towards-artificial-intelligence/4-math-skills-for-machine-learning-12bfbc959c92)

[3 个最佳数据科学 MOOC 专业](https://medium.com/towards-artificial-intelligence/3-best-data-science-mooc-specializations-d58da382f628)

[进入数据科学的 5 个最佳学位](https://towardsdatascience.com/5-best-degrees-for-getting-into-data-science-c3eb067883b1)

[2020 年开始数据科学之旅的 5 个理由](https://towardsdatascience.com/5-reasons-why-you-should-begin-your-data-science-journey-in-2020-2b4a0a5e4239)

[数据科学的理论基础——我应该关心还是仅仅关注实践技能？](https://towardsdatascience.com/theoretical-foundations-of-data-science-should-i-care-or-simply-focus-on-hands-on-skills-c53fb0caba66)

[机器学习项目规划](https://towardsdatascience.com/machine-learning-project-planning-71bdb3a44349)

[如何组织你的数据科学项目](https://towardsdatascience.com/how-to-organize-your-data-science-project-dd6599cf000a)

[大型数据科学项目的生产力工具](https://medium.com/towards-artificial-intelligence/productivity-tools-for-large-scale-data-science-projects-64810dfbb971)

[数据科学作品集比简历更有价值](https://towardsdatascience.com/a-data-science-portfolio-is-more-valuable-than-a-resume-2d031d6ce518)

[使用协方差矩阵图进行特征选择和降维](https://medium.com/towards-artificial-intelligence/feature-selection-and-dimensionality-reduction-using-covariance-matrix-plot-b4c7498abd07)

[数据科学 101 —包含 R 和 Python 代码的中型平台短期课程](https://medium.com/towards-artificial-intelligence/data-science-101-a-short-course-on-medium-platform-with-r-and-python-code-included-3cdc9d489c6d)