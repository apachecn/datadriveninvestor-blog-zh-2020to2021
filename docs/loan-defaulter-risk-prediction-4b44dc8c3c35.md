# 贷款违约风险预测

> 原文：<https://medium.datadriveninvestor.com/loan-defaulter-risk-prediction-4b44dc8c3c35?source=collection_archive---------8----------------------->

建立了一个逻辑回归模型，预测某个候选人是否有拖欠贷款的倾向

![](img/3c015e2365a1501e4405e13f75a1f8a6.png)

贷款已经成为我们日常生活的重要组成部分。尽管这对借贷双方都有利可图。有一个巨大的困境，贷款人在制裁时，特别是如果借款人没有足够的或不存在的信用记录。如果借款人拖欠贷款，会导致贷方的损失。因此，了解借款人是否有能力偿还债务或违约，对所有贷款机构来说都是一个非常关键的问题。在本文中，我们将建立一个逻辑回归模型，预测某个候选人是否会拖欠贷款:

这个模型是根据 Murilã在 kaggle 上提供的[信用风险数据集](https://www.kaggle.com/upadorprofzs/credit-risk)训练出来的。

**准备数据:**

1.首先，我使用 pandas 库读取 CSV 文件:

```
# Loading CSV File
data = pd.read_csv('original.csv')
# Dropping rows with NaN values
input = data.dropna()
```

2.然后我删除了包含 NaN 值的列

3.然后，我使用 sklearn 的“train_test_split”将数据集分别拆分为测试值和训练值。

```
# Splitting Dataset into train and test
y = input['default']
X = input.drop(columns=['default'])

X_train**,** X_test**,** y_train**,** y_test = train_test_split(X**,** y**,** test_size=**0.2**)
```

**创建模型:**

在 Model.py 中，我创建了两个函数:

1.  train():调用这个函数在给定的数据集上训练模型

```
#Function to train model
def train(X_train**,** y_train):
    model = LogisticRegression()
    model.fit(X_train**,** y_train)
    return model
```

我们在这个例子中使用了逻辑回归。逻辑回归是分类问题中非常著名的算法。我们可以很容易地用几行代码实现逻辑回归，并得到满意的结果。逻辑回归类似于线性回归，只是函数不同。

2.predict():这个函数用于对给定的数据进行预测

```
#Fuction for prediction
def predict(model**,** X_test):
    return model.predict(X_test)
```

**训练模型:**

一旦数据被分别分成训练和测试组件，我们就从 model.py 文件中调用 train 函数来训练/拟合 X_train 和 y_train 数据上的模型。

```
# Training the model
model = train(X_train**,** y_train)
```

**预测:**

完成训练后，我们将测试值传递给 model.py 文件的 predict 函数，以测试预测

```
# making Prediction
pred = predict(model**,** X_test)
print(pred)
```

**绩效指标:**

为了衡量性能，我们查看分类报告和混淆矩阵:

```
# Printing perfomance Metrics
print(classification_report(y_test**,** pred))
print('===================================')
print(confusion_matrix(y_test**,** pred)) precision    recall  f1-score   support 0       0.94      0.99      0.96       350
      1       0.87      0.52      0.65        50accuracy                           0.93       400
   macro avg       0.90      0.75      0.81       400
weighted avg       0.93      0.93      0.92       400===================================
[[346   4]
 [ 24  26]]Process finished with exit code 0
```

如你所见，通过这个数据集，我们预测某个人是否会拖欠贷款的准确率达到了 93%。你可以在 [Github](https://github.com/nischalmadiraju/Loan-Risk-Prediction) 上找到代码。