# 如何使用 Algorithmia 将您的 NLP 模型作为 API 部署到生产中

> 原文：<https://medium.datadriveninvestor.com/how-to-deploy-your-nlp-model-to-production-as-an-api-with-algorithmia-e4081854d524?source=collection_archive---------1----------------------->

## 一种在无服务器产品上逐步部署 NLP 模型的简单方法。

![](img/4c992699bd1c24c2da9dbb6d1b6e9493.png)

Photo by [cottonbro](https://www.pexels.com/@cottonbro?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels) from [Pexels](https://www.pexels.com/photo/person-in-blue-denim-jacket-holding-black-smartphone-5053740/?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels)

你知道 90%的机器学习模型从未真正投入生产吗？

这意味着当人们学习机器学习时，很少讨论机器学习部署的话题。因此，许多 AI 从业者知道如何创建有用的 ML 模型，但他们发现很难将它们部署到生产中。

不用说，如果你要使用 ML 模型，机器学习部署是你应该拥有的更重要的技能之一。

![](img/d63634756e94ca363dd0be91a100a221.png)

模型部署是将模型集成到现有生产环境中的过程。该模型将接收输入并预测输出，以便针对特定用例做出决策。

例如，可以在电子商务网站中部署一个模型，它可以预测关于特定产品的评论是正面的还是负面的。

> *只有当一个模型与业务系统完全整合时，我们才能从它的预测中提取真正的价值。—克里斯托弗·萨米乌拉*

有不同的方法可以将机器学习模型部署到生产中。但是在今天的文章中，您将学习如何使用 Algorithmia 将您的 NLP 模型作为 API 部署到生产中。

在本文中，您将了解到:

*   如何创建检测垃圾短信的 NLP 模型
*   如何使用 MLOps 平台 Algorithmia？
*   如何将您的模型部署到 Algorithmia 平台
*   如何在任何 Python 应用程序中使用您部署的 NLP 模型。

我们的第一步是创建一个可以检测垃圾短信的机器学习模型。所以我们开始吧！

# 如何建立 ML 模型

首先，我们需要建立我们的模型。下面是你应该遵循的步骤。

# 导入 Python 包

我们首先导入所有重要的 python 包，这些包将用于加载数据、预处理数据和创建文本分类模型。

```
# import important modules
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from string import punctuation # sklearn modules
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import MultinomialNB
from sklearn.svm import SVC
from sklearn.metrics import (
    accuracy_score,
    classification_report,
    plot_confusion_matrix,
    f1_score,
    roc_auc_score,
)
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.model_selection import cross_val_score, RandomizedSearchCV# text preprocessing modules
from nltk.tokenize import word_tokenize
from cleantext import cleanimport nltk
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer 
import re #regular expression from wordcloud import WordCloud, STOPWORDS# Download dependency
for dependency in (
    "brown",
    "names",
    "wordnet",
    "averaged_perceptron_tagger",
    "universal_tagset",
    "stopwords"
):
    nltk.download(dependency)#nltk.download('stopwords')import warnings
warnings.filterwarnings("ignore")
# seeding
np.random.seed(123)
```

# 加载垃圾邮件数据集

然后，我们从数据目录加载垃圾邮件数据集，如下所示:

```
# load data
data = pd.read_csv("../data/spam.tsv", sep="\t")
```

让我们看看数据集的前五行。

```
# show top five rows
data.head()
```

![](img/c836a987cf1bcf7f070d8cf8cd2642bc.png)

数据集有四列，但是我们将只关注消息和标签列。

让我们来看看数据集的形状:

```
# check the shape
data.shape
```

输出:(5572，4)

我们有 5572 行和 4 列。

# 如何处理缺失值

有时数据可能会有缺失值。我们可以使用 pandas 的 **isnull()** 方法来检查我们的数据集是否有任何缺失值。

```
# check missing values
data.isnull().sum()
```

![](img/ca2e72c67c18c6b872cdbc5b82eb1fe7.png)

输出显示我们的数据集没有任何缺失值。

# 如何评价班级分布

我们可以使用 pandas 包中的 **value_counts()** 方法来评估数据集的类分布。

```
# evalute class distribution
data["label"].value_counts()
```

![](img/3b40497477b82d87efb2fa7ba0c4abe9.png)

在该数据集中，合法邮件(ham)比垃圾邮件多。

# 探索性数据分析

这是创建你的机器学习项目非常重要的一步。它有助于您更好地了解数据集。

在这一步中，我们将找到合法邮件和垃圾邮件中经常使用的单词。

```
# collect words from the dataset
def collect_words(data, label):
    collected_words = " " # iterate through the csv file
    for val in data.message[data["label"] == label]: # typecaste each val to string
        val = str(val) # split the value
        tokens = val.split() # Converts each token into lowercase
        for i in range(len(tokens)):
            tokens[i] = tokens[i].lower() for words in tokens:
            collected_words = collected_words + words + " " return collected_words
```

上面这个名为 **collect_words()** 的函数会根据标签(ham 或 spam)从数据集中收集所有单词。

然后我们可以通过使用 **wordcloud** Python 包来可视化常用词。我们将从标记为 ham(合法)的消息开始。

```
# visualize ham labeled sms
cloud_stopwords = set(STOPWORDS)
ham_words = collect_words(data, label="ham")print("Total words {}".format(len(ham_words)))wordcloud = WordCloud(
    width=1000,
    height=1000,
    background_color="white",
    stopwords=cloud_stopwords,
    min_font_size=10,
).generate(ham_words)# plot the WordCloud image
plt.figure(figsize=(15, 8), facecolor=None)
plt.imshow(wordcloud)
plt.axis("off")
plt.tight_layout(pad=0)plt.show()
```

总字数:349132

![](img/5d569c010756090975d1f354edcf6e92.png)

在合法的留言里可以看到，出现频率最高的词是 *will，gt，now，ok，call，want，got，*等等。

现在，我们可以将标记为垃圾邮件的邮件中最常见的单词可视化。

```
# visualize spam labeled sms
cloud_stopwords = set(STOPWORDS)
spam_words = collect_words(data, label="spam")print("Total words {}".format(len(spam_words)))wordcloud = WordCloud(
    width=1000,
    height=1000,
    background_color="white",
    stopwords=cloud_stopwords,
    min_font_size=10,
).generate(spam_words)# plot the WordCloud image
plt.figure(figsize=(10, 8), facecolor=None)
plt.imshow(wordcloud)
plt.axis("off")
plt.tight_layout(pad=0)plt.show()
```

总字数:104304

![](img/1aef5db2b1d2346e49866a2a54ded2b2.png)

上图中显示，出现频率最高的词是那些像*来电、认领、免费、txt、移动、回复、优惠、*等等。

# 如何处理数据

在探索和分析数据集之后，下一步是在创建我们的机器学习模型之前，将数据集预处理成正确的格式。

我们首先用数值替换 ham 和 spam 类。ham 类将被标记为 0，而 spam 类将被标记为 1。

```
# replace ham to 0 and spam to 1
new_data = data.replace({"ham": 0, "spam": 1})
new_data.head()
```

![](img/22fe44e8b7d93bb9206c0f6035c741e4.png)

这个数据集中的消息包含了很多我们在创建机器学习模型时不需要的不必要的单词和字符。

我们将通过删除停用字词、数字和标点来清理邮件。然后我们将单词转换成小写，最后通过使用 NLTK 包中的词汇化过程将每个单词转换成它的基本形式。

函数将处理所有必要的步骤来清理我们的数据集。

```
stop_words =  stopwords.words('english')

def text_cleaning(text, remove_stop_words=True, lemmatize_words=True):
    # Clean the text, with the option to remove stop_words and to lemmatize word

    # Clean the text
    text = re.sub(r"[^A-Za-z0-9]", " ", text)
    text = re.sub(r"\'s", " ", text)
    text = re.sub(r"n't", " not ", text)
    text = re.sub(r"I'm", "I am", text)
    text = re.sub(r"ur", " your ", text)
    text = re.sub(r" nd "," and ",text)
    text = re.sub(r"\'d", " would ", text)
    text = re.sub(r"\'ll", " will ", text)
    text = re.sub(r" tkts "," tickets ",text)
    text = re.sub(r" c "," can ",text)
    text = re.sub(r" e g ", " eg ", text)
    text =  re.sub(r'http\S+',' link ', text)
    text = re.sub(r'\b\d+(?:\.\d+)?\s+', '', text) # remove numbers
    text = re.sub(r" u "," you ",text)
    text = text.lower()  # set in lowercase 

    # Remove punctuation from text
    text = ''.join([c for c in text if c not in punctuation])

    # Optionally, remove stop words
    if remove_stop_words:
        text = text.split()
        text = [w for w in text if not w in stop_words]
        text = " ".join(text)

    # Optionally, shorten words to their stems
    if lemmatize_words:
        text = text.split()
        lemmatizer = WordNetLemmatizer() 
        lemmatized_words = [lemmatizer.lemmatize(word) for word in text]
        text = " ".join(lemmatized_words)

    # Return a list of words
    return(text)
```

现在我们可以通过使用 **text_cleaning()** 函数来清理我们的数据集。

```
#clean the dataset 
new_data["clean_message"] = new_data["message"].apply(text_cleaning)
```

然后，我们将数据集分成训练和测试数据。测试规模是整个数据集的 15%。

```
# split data into train and test
X_train, X_test, y_train, y_test = train_test_split(
    new_data["clean_message"],
    new_data["label"],
    test_size=0.15,
    random_state=0,
    shuffle=True,
    stratify=data["label"],
)
```

scikit-learn 的 CountVectorizer 方法将帮助我们将清理后的数据集转换为数值。方法将文本文档的集合转换为令牌计数的矩阵。

```
# Transform text data 
vectorizer = CountVectorizer(lowercase=False)
vectorizer.fit(X_train)#transform train data 
X_train_trans = vectorizer.transform(X_train)#transform test data
X_text_trans = vectorizer.transform(X_test)
```

# 如何实际创建我们的模型

我们将训练多项式朴素贝叶斯算法来分类消息是合法的还是垃圾邮件。这是文本分类最常用的算法之一。

```
# Create a classifierspam_classifier = MultinomialNB()
```

然后，我们使用交叉验证来训练我们的分类器，以避免过拟合。

```
# Train the model with cross validation
scores = cross_val_score(spam_classifier,X_train_trans,y_train,cv=10,verbose=3,n_jobs=-1)
```

![](img/152a300989496c313a55b3f1a7baf720.png)

让我们看看平均分数。

```
# find the mean of the all scores
scores.mean()
```

输出:0.976713936539371

分数的平均值在 97.68%左右。我们的模型表现良好，但我们可以通过使用 scikit-learn 的随机搜索方法优化其超参数值来提高其性能。

```
# fine turning model parametersdistribution = {"alpha": [1, 0.1, 0.01, 0.001, 0.0001, 0, 0.2, 0.3]}grid = RandomizedSearchCV(
    spam_classifier,
    param_distributions=distribution,
    n_jobs=-1,
    cv=10,
    n_iter=20,
    random_state=42,
    return_train_score=True,
    verbose=2,
)
```

我们将优化模型中的 **alpha** 超参数，以获得提高模型性能的最佳值。

```
# training with randomized search
grid.fit(X_train_trans, y_train)
```

![](img/5125ff3a7eb1b3664838f6923fd01634.png)

要显示超参数优化结果:

```
# summarize the results of the random parameter search
print(grid.best_score_)
print(grid.best_estimator_)
print(grid.best_params_)
```

0.9767713936539371
多项式 inb(alpha = 1)
{ ' alpha ':1 }

最好成绩和上一个一样。现在让我们用测试数据来测试我们的模型。

```
# predict on the test data
y_pred = spam_classifier.predict(X_text_trans)
```

将使用 **accuracy_score** 评估指标来评估模型的性能。

```
# check accuracy score
accuracy_score(y_test, y_pred)
```

输出:0.976076550239234

我们的模型准确率在 **97.6%** 左右，表现不错。

当数据集中存在类别不平衡时，另一个有用的评估指标是 **f1_score** 。

```
# check f1_ score
f1_score(y_test, y_pred)
```

输出:0.908256880733945

分数为 **0.91** 更接近 **1** 。这意味着我们的模型具有良好的性能，我们现在可以将它部署到生产中。

[](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) [## 机器学习和人工智能如何改变电子商务的面貌？|数据驱动…

### 电子商务开发公司，现在，整合先进的客户体验到一个新的水平…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) 

模型将被保存在模型的目录中。

```
#save model 
import joblib joblib.dump(spam_classifier, '../models/spam-detection-model.pkl')
```

['../models/spam-detection-model . pkl ']

我们的计数矢量器也将保存在预处理目录中。

```
#save Vectorizer
joblib.dump(vectorizer,'../preprocessing/count_vectorizer.pkl')
```

['../preprocessing/count _ vector izer . pkl ']

在创建了我们的垃圾邮件检测模型之后，是时候在 Algorithmia 平台上部署它了。

# 什么是 Algorithmia？

[Algorithmia](https://algorithmia.com/) 是一个 MLOps 工具，它提供了一种简单而快速的方法来将您的机器学习模型部署到生产中。

Algorithmia 专门研究**“算法即服务”**。它允许用户创建运行 ML 模型的代码片段，并将它们托管在 Algorithmia 上。然后你可以调用你的代码作为一个 API。

现在，您的模型可以用于您选择的不同应用程序，如 web 应用程序、移动应用程序或电子商务，只需从 Algorithmia 调用一个简单的 API。

![](img/58dd529a2450353526119255b282f9b9.png)

Algorithmia 支持 R、Python、Java、Scala 等不同编程语言开发的机器学习模型。它还支持流行的机器和深度学习框架，如 Pytorch、Tensorflow、scikit-learn、XGBoost 和 Keras。

Algorithmia 在其无服务器人工智能层上使用 CPU 和 GPU 来优化成本，并最大限度地提高其性能，以满足您的需求。
目前，该平台拥有超过 60，000 名开发者，拥有 4，500 种算法。

以下是在 Algorithmia 上部署机器学习模型需要遵循的六个步骤。

# 步骤 1:在 Algorithmia 上创建一个帐户

第一步是通过访问这个页面在 Algorithmia 中创建一个账户:[https://algorithmia.com/signup](https://algorithmia.com/signup)。

# 步骤 2:创建一个新算法

创建并确认您的帐户和电子邮件后，下一步是通过单击名为**“新建”**的下拉菜单按钮来创建新的算法。然后你只要选择页面右上角的**算法**。

![](img/f5bd06094eea3eb685cb1301e7fb6b7d.png)

然后输入算法的名称，例如，垃圾短信检测。在**源代码**部分，您可以决定您的算法的源代码将位于何处。

默认情况下，源代码将位于 Algorithmia 平台上。您可以选择将其保留在 GitHub 上，但是对于本文，我们将使用默认选项。

下一节指定了环境。Algorithmia 为您提供了不同的选项来选择不同的环境，如 Python、R、JavaScript、Java 和 Scala。默认选项是 Python 3。这里我们将继续这个选项。最后，点击“**创建新算法**按钮。

# 步骤 3:将预先训练好的模型和计数矢量器上传到 Algorithmia

您可以通过点击 Algorithmia 平台左侧面板上的**数据源**将您选择的模型上传到数据部分。然后点击**我的托管数据**目录，在那里你可以创建一个新的文件夹来保存你为这个特定算法上传的所有 pkl 文件。

在“我的托管数据”目录中，我创建了一个名为 **sms_spam_detection** 的新文件夹。然后，我上传了我们预先训练的模型和训练的 CountVectorizer，以将文本消息(sms)转换为术语/令牌计数的向量。

![](img/3ddda27339b4597a4b9c777252a8d737.png)

# 步骤 4:添加源代码

上传我们的预训练模型后，点击**源代码**选项卡。它将打开一个 IDE，您可以在其中添加源代码来运行我们创建的机器学习模型。下面是添加源代码的方法:

**(a)导入包**
我们首先导入重要的 Python 包，包括 Algorithmia，它将调用我们创建的算法。

```
import sys
import joblib
import pickle
import numpy as np
import Algorithmia
from sklearn.feature_extraction.text import TfidfVectorizer, CountVectorizer
from string import punctuation
import re 
import nltk
#download dependency
nltk.download('stopwords')
nltk.download('wordnet')
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer
```

注意:Algorithmia 的平台会自动导入文件中的 Algorithmia Python 包。

**(b)创建客户端**
然后我们从 Algorithmia 包中创建一个客户端，它提供了调用任何算法的标准化方法。

```
# we are creating the variable in global scope to use throughout our algorithm.
client = Algorithmia.client()
```

**( c)添加加载预训练模型和计数矢量器 pkl 文件的函数**
**load _ model()**函数将从数据源目录加载我们的预训练模型， **load_preprocessing()** 函数将加载计数矢量器文件。

```
def load_preprocessing():
    # Get file by name
    # Open file and load model
    file_path = 'data://Davis/sms_spam_detection/count-vectorizer.pkl'
    object_path = client.file(file_path).getFile().name
    # Open file and preprocessin object
    with open(object_path, 'rb') as f:
        object = joblib.load(f)
        return object def load_model():
    # Get file by name
    # Open file and load model
    file_path = 'data://Davis/sms_spam_detection/spam-detection-model.pkl'
    model_path = client.file(file_path).getFile().name
    # Open file and load model
    with open(model_path, 'rb') as f:
        model = joblib.load(f)
        return model# Load model outside of the apply function so it only gets loaded oncemodel = load_model()
vectorizer = load_preprocessing()
```

**(d)添加清理文本输入的函数**
这里我们将使用同样的 **text_clean()** 函数来清理短信。

```
#set stopwords
stop_words = stopwords.words('english')def text_cleaning(text, remove_stop_words=True, lemmatize_words=True):
    # Clean the text, with the option to remove stop_words and to lemmatize word # Clean the text
    text = re.sub(r"[^A-Za-z0-9]", " ", text)
    text = re.sub(r"\'s", " ", text)
    text = re.sub(r"n't", " not ", text)
    text = re.sub(r"I'm", "I am", text)
    text = re.sub(r"ur", " your ", text)
    text = re.sub(r" nd ", " and ", text)
    text = re.sub(r"\'d", " would ", text)
    text = re.sub(r"\'ll", " will ", text)
    text = re.sub(r" tkts ", " tickets ", text)
    text = re.sub(r" c ", " can ", text)
    text = re.sub(r" e g ", " eg ", text)
    text = re.sub(r'http\S+', ' link ', text)
    text = re.sub(r'\b\d+(?:\.\d+)?\s+', '', text)  # remove numbers
    text = re.sub(r" u ", " you ", text)
    text = text.lower()  # set in lowercase # Remove punctuation from text
    text = ''.join([c for c in text if c not in punctuation]) # Optionally, remove stop words
    if remove_stop_words:
        text = text.split()
        text = [w for w in text if not w in stop_words]
        text = " ".join(text) # Optionally, shorten words to their stems
    if lemmatize_words:
        text = text.split()
        lemmatizer = WordNetLemmatizer()
        lemmatized_words = [lemmatizer.lemmatize(word) for word in text]
        text = " ".join(lemmatized_words) # Return a list of words
    return (text)
```

**(e)添加对输入进行预处理的函数**
**process _ input()**方法将在进行预测之前对输入的短信进行预处理。

```
def process_input(input):
    # Preprocess and Create numpy array from the input

    message = str(input)
    clean_message = text_cleaning(message)

    #vectorize the message 
    vect_message = vectorizer.transform([clean_message])

    print(vect_message)

    return vect_message
```

**(f)添加应用模型进行预测的函数**
最后一个名为 **apply()** 的函数将负责执行来自预处理文本 sms 的预测。如果消息是合法的，它将返回*“正常消息*”,如果消息是垃圾消息，它将返回*“垃圾消息”*。

```
def apply(input):
    # pefrom prediction from the input. 

    message = process_input(input)
    prediction = model.predict(message)
    if prediction[0] == 0:
        return "normal message"
    else:
        return "spam message"
```

最后，我们保存添加到文件中的源代码。

![](img/7a8bac02e454cab680c6fdcec9e75c48.png)

# 步骤 5:向 Algorithmia 添加依赖项

从 UI 中点击 **dependencies 选项卡**,并添加我们的模型所依赖的以下包:

*   numpy
*   joblib
*   scikit-learn == 0.22.2.post1
*   统一代码
*   nltk == 3.5

然后点击右下角的**保存依赖关系**:

![](img/430cad949647cbb81d5a813d8df165cb.png)

注意:Algorithmia 中的依赖文件与 requirements.txt 文件相同，后者从 PyPi 中提取所列出的依赖文件。

在编辑器页面上，点击右上角的**构建选项卡**，安装依赖文件中列出的所有依赖项。如果成功安装了所有依赖项，您将会看到您的算法的特定版本现在处于联机状态，可以发布了。

![](img/3e74eca078acd3468b082647e0673806.png)

# 步骤 6:发布算法

我们的最后一步是公布算法。发布算法有 3 个步骤:记录所有更改、添加示例输入和输出，以及配置算法设置。

**(a)文档更改**
您将看到您的提交历史，并且您将能够添加一个发布说明。

![](img/19a2e50bceebf4a0651ccf5a106e2975.png)

**(b)添加一个示例**
在本节中，你创建你的示例输入和输出，以便用户可以尝试你的算法。

![](img/3be360e4cb6c8797d0873bfb75eb637b.png)

**配置算法设置**
最后，您选择您的算法是**公共**(这意味着任何人都可以调用它)还是**私有**(这意味着只有所有者可以调用它)。您还需要设置版税，然后单击页面底部的**发布**按钮。

![](img/010d02c037e82e3f3d219876a5fda2aa.png)

我们的 NLP 模型已经成功部署在 Algorithmia 平台上。让我们看看如何在 Python 应用程序(如 Flask 或 Django)中使用我们部署的模型。

# 如何安装 Algorithmia Python 客户端

我们首先使用 PIP 安装 Algorithmia Python 客户端。这将帮助我们调用运行 NLP 模型的代码。

```
pip install algorithmia
```

# 收集 API 密钥

单击算法面板上的“API 密钥”选项卡来收集 API 密钥，这将帮助您调用运行 NLP 模型的代码。

# 创建 Algorithmia 客户端

我们首先导入 Algorithmia Python 包，然后创建算法客户端对象

```
import Algorithmia

# Authenticate with your API key
apiKey = "YOUR_API_KEY"

# Create the Algorithmia client object
client = Algorithmia.client(apiKey)
```

# 调用算法

为了调用算法，我们需要将算法的名称及其版本添加到我们创建的客户端对象中。

名称是**“Davis/spam _ detection/0 . 2 . 0”，**包括您在 Algorithmia 上的帐户名称，后跟我们创建的算法名称。最后一位是算法的版本(0.2.0)。

```
# Create the algorithm object using the Summarizer algorithm
algo = client.algo('Davis/spam_detection/0.2.0')# Pass in input required by algorithm
input_sms = "Win a Â£1000 cash prize or a prize worth Â£5000"try:
    # Get the result
    print(algo.pipe(input_sms).result)
except Exception as error:
    # Algorithm error if, for example, the input is not correctly formatted
    print(error)
```

对于这个例子，模型预测 sms 是一个**“垃圾消息”**。酷，成功了！

# 包扎

恭喜你，你已经完成了这篇文章的结尾！

你可以在这里下载本文使用的数据集和笔记本:[https://github.com/Davisy/SMS-Spam-Text-Classification](https://github.com/Davisy/SMS-Spam-Text-Classification)

如果你学到了新的东西或者喜欢阅读这篇文章，请分享给其他人看。在那之前，下期帖子再见！也可以通过 Twitter [@Davis_McDavid](https://twitter.com/Davis_McDavid) 联系到我。

本文最初发表于[免费代码营](https://www.freecodecamp.org/news/deploy-ml-model-to-production-as-api/)。

***最后一件事:*** *在以下链接中阅读更多类似这样的文章。*

[](https://towardsdatascience.com/how-to-deploy-machine-learning-model-in-laravel-application-5e021494d316) [## 如何在 Laravel 应用中部署机器学习模型

### 从 Algorithmia 调用模型 API 并在 Laravel 中预测

towardsdatascience.com](https://towardsdatascience.com/how-to-deploy-machine-learning-model-in-laravel-application-5e021494d316) [](https://chatbotslife.com/how-to-use-texthero-to-prepare-a-text-based-dataset-for-your-nlp-project-734feea75a5a) [## 如何使用 Texthero 为您的 NLP 项目准备基于文本的数据集

### 一个简单的 python 工具包，可以快速、轻松地处理基于文本的数据集。

chatbotslife.com](https://chatbotslife.com/how-to-use-texthero-to-prepare-a-text-based-dataset-for-your-nlp-project-734feea75a5a) [](https://medium.com/analytics-vidhya/15-undiscovered-open-source-machine-learning-frameworks-you-need-to-know-in-2020-77ad6e6f109d) [## 2020 年你需要知道的 15 个未被发现的开源机器学习框架。

### 在你的下一个机器学习项目中有用的 ML 框架。

medium.com](https://medium.com/analytics-vidhya/15-undiscovered-open-source-machine-learning-frameworks-you-need-to-know-in-2020-77ad6e6f109d) 

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)