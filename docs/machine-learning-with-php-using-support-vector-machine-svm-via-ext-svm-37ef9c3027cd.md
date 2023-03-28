# PHP 机器学习:通过 ext-svm 使用支持向量机(SVM)

> 原文：<https://medium.datadriveninvestor.com/machine-learning-with-php-using-support-vector-machine-svm-via-ext-svm-37ef9c3027cd?source=collection_archive---------13----------------------->

![](img/21eebe037c5da6a99e63693dcc9650f8.png)

Photo by [Markus Winkler](https://unsplash.com/@markuswinkler?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

PHP 是一种非常受欢迎的语言，当某个东西变得非常受欢迎时，通常会有人出来说“这不酷”，没关系，这是事实。我读过很多文章说“PHP 对于机器学习来说并不酷”或者说“只要转移到语言 X 来执行它，它会工作得更好”(我不打算燃烧另一种语言，只是在互联网上谈论一些随机的东西)。

我是一个 PHP 爱好者，我不会否认这一点，我尝试了不同的语言，框架，开发了原生应用程序，我喜欢尝试新事物，但我也喜欢 PHP。但是有时我会因为 PHP 生态系统缺少一些非常有趣的特性而退缩，比如强大的机器学习库。

上一次发生这种情况是在我写博士论文的时候。我的论文是关于“室内定位”的:我必须研究各种技术，描绘出执行定位的可能方法，最后，我必须构建一个由处理定位的 web 界面和使用它的客户端组成的实验系统。

为了研究室内定位，由于我的大学身份，我从 IEEE Explore 获得了许多论文，研究了不同的方法，我最终选择了一种技术组合来实现我的定位，但这不是本文的目的。

**这跟 PHP 和机器学习有什么关系？**嗯，这有点奇怪，我进行的所有测试都是为了了解 SVM 如何在 python 中工作，因为帮助我开发的工程师精通 Python，但我必须编写一个 web 应用程序，而那个工程师并不实际编写后端，所以我有了一个想法，我在谷歌上搜索“PHP svm”，第一个结果是来自 PHP.net 文档的“ [SVM —手动— PHP](https://www.php.net/manual/en/book.svm.php) ”。

# Ext-svm:什么和为什么

批评者来了，PHP 刚刚接近机器学习，其他语言已经有很多年了，我为什么要选择它呢？这很简单，因为 [ext-svm](https://github.com/ianbarber/php-svm) 只是用 C++编写的 [libsvm 库](https://www.csie.ntu.edu.tw/~cjlin/libsvm/)([check libSVM on Github](https://github.com/cjlin1/libsvm))的包装器，这意味着每次你想使用 PHP 执行 SVM 操作时，这将在较低的级别执行，并且由于 ext-svm 接口，结果将传播到 PHP。

> LibSVM 是 SVM 分类和回归问题的高效求解器。svm 扩展将此封装在 PHP 接口中，以便在 PHP 脚本中轻松使用。从版本 0.2.0 开始，扩展需要 PHP 7.0 或更高版本。

对我来说，这太棒了！这就是我从我不太了解的 Python (python 开发者请不要恨我)转移到我更熟练的 PHP 所需要的一切。

# 安装 ext-svm

首先，该扩展在 [Pecl](https://pecl.php.net/package/svm) 上可用，这意味着如果你有管理员权限访问命令行，你就可以

```
pecl install svm
```

请注意，ext-svm 目前处于测试阶段，因此如果您对 pecl 有任何问题，要安装它，您只需:

```
pecl install svm-beta
```

输出将类似于:

```
downloading svm-0.2.3.tgz ...
Starting to download svm-0.2.3.tgz (130,776 bytes)
.............................done: 130,776 bytes
7 source files, building[... skipping the whole output ...]Build process completed successfully
Installing '/usr/lib/php/20190902/svm.so'
install ok: channel://pecl.php.net/svm-0.2.3
**Extension svm enabled in php.ini**
```

如果您想检查扩展是否已经正确安装，只需启动:

```
$ php -m | grep svm **svm**
```

扩展现在已经安装好了，您可以开始了！

[](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) [## 机器学习和人工智能如何改变电子商务的面貌？|数据驱动…

### 电子商务开发公司，现在，整合先进的客户体验到一个新的水平…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) 

# 构建您的第一个分类器

为了构建我们的第一个分类器，我们将坚持使用[文档示例](https://www.php.net/manual/en/svm.examples.php)并检查它是否工作。我们的分类器将从一个数组中训练，我们将检查它是否可以从训练数据集中预测一个值。

```
<?php
$data = array(
    array(-1, 1 => 0.43, 3 => 0.12, 9284 => 0.2),
    array(1, 1 => 0.22, 5 => 0.01, 94 => 0.11),
);

**$svm = new SVM();
$model = $svm->train($data);**

$data = array(1 => 0.43, 3 => 0.12, 9284 => 0.2);
**$result = $model->predict($data);**
echo $result;
```

如果您保存这个文件，然后通过控制台运行它，或者将它放在 web 服务器中并访问它，结果应该是`-1`。**为什么？**

让我们分解我们的代码来理解它是如何工作的。在前两行，我们找到了代表数据的数组

```
$data = array(
    array(-1, 1 => 0.43, 3 => 0.12, 9284 => 0.2),
    array(1, 1 => 0.22, 5 => 0.01, 94 => 0.11),
);
```

如果关注内部数组，每一行都可以分成两部分:结果和用于训练的特征。数组的第一个值(在索引 0 处)是分类结果，随后是特征，因此对于`array(-1, 1 => 0.43, 3 => 0.12, 9284 => 0.2)`,分类结果将是`-1`,随后被分组为键/值对的值是特征。

后来我们实例了 [SVM](https://www.php.net/manual/en/class.svm.php) :

```
$svm = new SVM();
```

可以通过调用`[setOptions](https://www.php.net/manual/en/svm.setoptions.php)`来调整 SVM 实例，例如，您可以在训练之前更改您的内核:

```
$svm->setOptions([ **SVM::OPT_KERNEL_TYPE** => **SVM::KERNEL_SIGMOID** ]);
```

调整选项的常量值可以在 php.net 的 [SVM 类文档中找到](https://www.php.net/manual/en/class.svm.php)。

现在我们已经准备好了 SVM，我们可以训练一个模型:

```
$model = $svm->train($data);
```

这一行输出一个 [SVMModel](https://www.php.net/manual/en/class.svmmodel.php) ，我们可以用它来进行预测。如果你有一个非常大的模型，你可以用`save(string $filename)`把它保存到一个文件中，然后用`load(string $filename)`从文件系统中重新加载，如下所示:

```
$model->save('model.svm');
// later... somewhere in the code
$model->load('model.svm');
```

**请注意** : `save`和`load`将返回一个布尔值，你可以检查它或者丢弃它，由你决定！

最近的三行是测试代码:

```
$data = array(1 => 0.43, 3 => 0.12, 9284 => 0.2);
$result = $model->predict($data);
echo $result;
```

你得到你测量的特征，想要对照模型进行检查，并把它们放入一个数组，在这段代码中，这个数组叫做`$data`。这些特征将通过使用训练集从 SVM 进行处理。

一旦我们的数据准备好了，我们就可以调用`predict`来对作为输入传递的数据进行分类，并得到一个对应于预测的浮点输出。最后，我们可以呼应它，或者在其他地方使用它。

# 建造，训练，预测

![](img/07ac349aefc5f3744e6122da77161580.png)

Photo by [Stephen Dawson](https://unsplash.com/@srd844?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

现在你的系统已经安装了 PHP SVM 扩展，你可以训练一个模型，保存它，重新加载它并进行预测，从现在开始，一切都取决于你！

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)