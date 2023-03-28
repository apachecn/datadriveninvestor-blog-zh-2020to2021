# 评估分类模型性能

> 原文：<https://medium.datadriveninvestor.com/evaluating-classification-model-performance-3bcadfafa1c7?source=collection_archive---------11----------------------->

## *用简单的英语解释准确度、精确度、召回率和 F1 分数*

![](img/8859f2a1f42d91899370ee752b05d652.png)

Photo by [Mika Baumeister](https://unsplash.com/@mbaumi?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

当谈到分类模型时，用于确定性能的度量标准与用于评估回归模型的度量标准有很大的不同。在我看来，用来描述一个分类模型性能的度量标准*更加*直观。当这些指标被用来描述一项确定你是否患病的医学测试时，你可能对其中的一些指标有过体验，例如新冠肺炎测试。如果您正在接受新冠肺炎病毒检测，该检测有四种可能的结果:

*   真阳性:你感染了病毒，并且病毒检测呈阳性。
*   假阳性:您没有感染病毒，但您的病毒检测呈阳性。
*   真阴性:您没有感染病毒，并且病毒检测呈阴性。
*   假阴性:你感染了病毒，但测试结果呈阴性。

每项测试，包括 Covid 测试，都必须根据具体情况在假阳性和假阴性之间取得平衡。这四类测试结果将帮助我们计算决定模型性能的评估指标。

在这篇文章中，我将解释四个评估指标的含义——准确度、精确度、召回率和 F1——以及在什么情况下每个分数最重要。然后，我将向您展示如何计算每个分数，并使用 Python 可视化测试结果。阅读后，您应该能够确定在您的分类问题的上下文中哪个指标是最重要的，并且您将能够用简单的英语将这些指标传达给利益相关者。为了简单起见，我们将把重点放在二进制分类问题上。

# 准确(性)

准确性可能是最容易理解的评估指标之一，但也是最不相关的。准确性衡量分类模型做出的正确预测的总数，包括真阳性和真阴性。您可以使用下面的公式来计算:

![](img/92642acc053272677b4450be78bb34cf.png)

accuracy formula

使用我们的 COVID 测试示例，这将是总预测的百分比，其中测试正确预测一个人具有 Covid *并且*正确预测一个人没有 COVID；换句话说，真正的积极加上真正的消极。

## 什么时候准确性最重要？

如果您有一个平衡的分类问题，其中正案例的数量几乎等于负案例的数量，则准确性可能是衡量整体模型性能的有用度量。然而，在不平衡的类的情况下，准确性可能是一个非常没有意义的度量。

例如，假设样本的 90%是真阴性，而 10%是真阳性。如果模型只是简单地预测所有负面因素，它将达到 90%的准确率，这使得模型看起来比实际情况好得多。这给我们带来了下一个评估指标的有用性。

# 精确

Precision 测量所有预测阳性中真正阳性的数量。保守模型通常具有非常高的精度分数，因为预测阳性的阈值很高。其计算方法如下:

![](img/fb6b20fb31965797f1f425cadd7b1403.png)

precision calculation

就我们的 Covid 示例而言，精确度将被计算为所有阳性检测结果中某个病毒检测为阳性的次数。

## 什么时候精度最重要？

在预测阳性的阈值较高的情况下，精确度可能是非常有用的度量。例如，在垃圾邮件过滤的情况下，将某些东西分类为垃圾邮件的阈值较低可能会导致重要的电子邮件被垃圾邮件过滤器捕获。在这种情况下，我们希望我们的精度高，这样我们就不会有太多的预测阳性被我们的垃圾邮件过滤器捕获。然而，在医学案例中，高精度值并不总是最优先考虑的。

# 回忆

召回衡量所有实际总阳性数中的真阳性数(真阳性加上假阴性)。你也可能听说过被称为*真实阳性率的回忆。*这可以计算为:

![](img/711ce6fe4d46a5641c8420fb780bbf41.png)

recall calculation

回想一下我们的 Covid 测试，它回答了这样一个问题:在一个被测试的人实际上携带病毒的所有次数中，我们的测试有多少次正确地预测了这个人是阳性的？

## 什么时候回忆最重要？

在我们的 Covid 测试示例中，召回率是我们最应该关注的指标，它是大多数医疗案例的主要指标。当某人接受 Covid 测试时，两种不正确的结果是，一个没有感染病毒的人被告知他们感染了，一个感染了病毒的人被告知他们没有感染。虽然假阳性并不理想，但有人不必要的隔离是一个比有人传播疾病更好的社会结果，因为他们不认为自己有疾病。这是精确召回权衡的一个很好的例子。Covid 测试需要达到一定的召回水平，因为假阴性的结果比假阳性的结果更差。因此，我们会用更多的假阳性来换取更少的假阴性，并且预测阳性的门槛更低。真阳性率和假阳性率之间的权衡可以在模型的接收器操作特征(ROC)曲线中可视化。

![](img/50c68f46f2cd27ed8d00faf80a13dcbc.png)

ROC Curve Example

# F1 分数

F1 得分是精确度和召回率的调和平均值，或者是这两个指标的加权平均值。F1 分数可以计算为:

![](img/bf14da46caa9b15e24909245c4664450.png)

F1 score calculation

基本上，F1 分数会惩罚过于偏向精度或召回的模型，使其成为衡量整体模型性能的良好指标。

## F1 成绩什么时候重要？

尽管在我们的 Covid 示例中，召回比精度更重要，但是具有一定程度的精度仍然很重要，否则我们的测试将毫无用处。f1 分数考虑了这两个指标。

现在您已经从概念上理解了这些指标，让我们看看如何用 Python 来计算这些指标。

# 可视化和计算评估指标

## 分类报告

一次获得所有这些指标的简单方法是打印 scikit-learn 内置的分类报告。参见下面的示例代码:

```
from sklearn.metrics import classification_reportprint(classification_report(y_test, y_hat_test))
```

和输出:

```
 precision    recall  f1-score   support

           0       0.83      0.73      0.77        33
           1       0.81      0.88      0.84        43

    accuracy                           0.82        76
   macro avg       0.82      0.81      0.81        76
weighted avg       0.82      0.82      0.81        76
```

现在，您可以在一个报告中轻松找到模型的精确度、召回率、F1 分数和准确性。

## 混淆矩阵

可视化分类模型性能的一种简单方法是创建混淆矩阵。幸运的是，scikit-learn 还有一个内置的 *plot_confusion_matrix* 函数，可以自动输出美观的矩阵。参见下面的代码和输出示例:

```
sns.set(font_scale=1.5)
fig, ax = plt.subplots(figsize=(10, 6))
ax.set_title('Confusion Matrix')
disp = plot_confusion_matrix(logreg, X_test, y_test, ax = ax,
                             normalize=None)
plt.grid(False)
```

![](img/9ea8cccc8fa317f799c8a503d9ae0afd.png)

confusion matrix output

决策矩阵的每个象限代表我们前面提到的四个潜在结果之一。将矩阵中的 0 视为阴性，1 视为阳性，例如，真实标签:0 和预测标签:0 相交的方框表示真实阴性的数量，而真实标签:1 和预测标签:0 表示假阴性的数量。

知道了我们现在对每个指标的计算的了解，您可以从这个混淆矩阵中的值计算出所有 4 个指标！

*   *准确率=(真阳性+真阴性)/总观测值=(38+24)/(24+9+5+38)= 62/76 = . 82*
*   *精度=真阳性/预测阳性= 38 / (38+9) = 38/47 = .81*
*   *召回=真阳性/实际阳性= 38 / (38+5) = 38/43 = .88*

既然我们已经计算了精度和召回率，我们还可以计算 F1:

*   *F1 得分= 2*(召回率*精度)/(召回率+精度)= 2 *(0.81 * . 88)/(. 81+. 88)= 2 *(0.71/1.69)= . 84*

## sci kit-学习内置函数

尽管理解这些指标背后的概念很重要，但有更简单的方法来自动计算这些值。如果您想快速检查这些指标中的一个，而不打印完整的报告或可视化，scikit-learn 也有内置的功能。参见下面的代码和输出示例:

```
from sklearn.metrics import precision_score, recall_score, accuracy_score, f1_scoreprint(f'Accuracy is {round(accuracy_score(y_test, y_hat_test),2)}')
print(f'Precision is {round(precision_score(y_test, y_hat_test),2)}')
print(f'Recall is {round(recall_score(y_test, y_hat_test),2)}')
print(f'F1 Score is {round(f1_score(y_test, y_hat_test),2)}')Accuracy is 0.82 
Precision is 0.81
Recall is 0.88
F1 Score is 0.84
```

现在您拥有了快速而正确地解释分类模型性能的工具！如果有疑问，值得计算这些评估指标，从多个角度检查您的模型的表现。就新冠肺炎测试而言，这些概念是非常有趣的——参见下面一些讨论实际测试结果的资源:

[](https://www.fda.gov/medical-devices/letters-health-care-providers/potential-false-positive-results-antigen-tests-rapid-detection-sars-cov-2-letter-clinical-laboratory) [## 新型冠状病毒抗原检测可能出现假阳性结果

### 美国美国食品药品监督管理局(FDA)警告临床实验室工作人员和卫生保健提供者，虚假…

www.fda.gov](https://www.fda.gov/medical-devices/letters-health-care-providers/potential-false-positive-results-antigen-tests-rapid-detection-sars-cov-2-letter-clinical-laboratory)  [## 用于诊断新冠肺炎的实验室测试有多准确？麻省理工学院医学院

### 4 月 29 日:麻省理工医学院回答你的新冠肺炎问题。有关于新冠肺炎的问题吗？发送到 CovidQ@mit.edu 给我们…

medical.mit.edu](https://medical.mit.edu/covid-19-updates/2020/06/how-accurate-diagnostic-tests-covid-19) 

感谢阅读！