# 物体检测教程和书里没有教的是什么？

> 原文：<https://medium.datadriveninvestor.com/what-is-not-taught-in-object-detection-tutorials-and-books-dc33ab4c3063?source=collection_archive---------3----------------------->

## *假阳性/阴性，真阳性/阴性！如何标注背景图片？背景图片的力量。*

![](img/9c79459c479d70a2d842b3588f044045.png)

> *我花了几天时间寻找关于背景图像的材料，背景图像的注释，背景图像的效果，我决定写一篇文章，把我所有的发现总结在一篇文章里，这样其他从业者就可以了解背景图像的所有力量*

R 最近，我在一个自由职业项目中使用不同的算法进行物体检测，比如 YoloV3、YoloV4、MobileNet SSD。我自己收集了图像数据集，用手机拍照，用 LabelImg 注释工具注释。在我开始做这个对象检测项目之前，我认为这将是一项简单的工作，但是当我开始手动注释 6000 多张图像时，我意识到使用自定义数据集进行对象检测并不是一项简单的工作。网上有很多自动化的标注工具，但是我想亲自体验一下这个过程，了解一下图像标注的过程有多难，有哪些水下的岩石存在。由于这个项目是我的第一个严肃的大型机器学习项目，我经常会看不同的书籍和教程来教授类似的项目。我在这些书和教程中注意到的是，几乎所有的书和教程都没有教授或至少告知存在假阳性/阴性和真阳性/阴性的事实。当我开始在我的电脑上测试我训练过的物体检测模型的权重时，这个问题就出现了。当我测试模型时，最初我开始在视频帧中看到不同的假阳性输出。我对这个结果感到惊讶，因为我在教程和书籍中没有看到任何这类问题。我开始研究这个问题，并找到了一些解决这个问题的有用技巧。

# **更多背景图片**

是啊！你需要收集更多的背景图片。当我发现这个解决方案时，我不明白为什么我们需要背景图片，它们是什么。从进一步的研究中，我明白这是需要“教导”模型什么是**真正的目标对象(一个你想要检测/分类的对象)和什么是**不是**真正的目标对象——据我理解这类似于一般化方法。因此背景图像不包含任何形式的目标对象。对于背景图像，您可以收集不包含任何目标对象的随机图像，当您注释背景图像时，您只需跳过它们而不添加任何注释，这样您的图像在像 XML 这样的注释文件中就没有任何 X，Y 坐标。在我对这个主题进行研究之后，我将我在网上找到的所有有用的步骤应用到我的对象检测模型中。结果正如所料——误报永远消失了！我希望它能起作用，它真的起作用了！我将在这篇文章的底部分享一些有用的链接，关于背景图像和减少你的物体检测项目中的 FP 度量。现在，让我给你一些我在我的项目中学到的背景图像注释提示。**

# **注释背景图像**

**确保你为每一类物体收集了足够多的图像:根据你的物体检测算法，它会有所不同。在我的例子中，对于 MobileNet SSD v2 算法，每个类所需的最低映像数量是 300–400。但是在我的项目中，我收集了大约 6000 多张图片，并使用 LabelImg 注释工具手工注释它们。当我发现收集背景图片可以帮助你减少 FPs 的提示时，我不知道如何注释背景图片。在对这个主题进行了一些额外的研究后，我发现在 LabelImg 工具中可以很容易地完成，当你想在“LabelImg”中注释一个背景图像时，只需单击“Space”按钮。**

***注:您不必保存图像，当您按下“空格”按钮*时，图像会自动保存**

**背景图像的注释文件(XML)如下所示:**

```
<folder>My Folder</folder>
<filename>image.jpg</filename>
<path>/home/usuario/Escritorio/PR/My Folder/image.jpg</path>
<source>
	<database>Unknown</database>
</source>
<size>
	<width>1812</width>
	<height>2416</height>
	<depth>3</depth>
</size>
<segmented>0</segmented>
```

**完成图像数据集的收集和标记后，可以开始下一步:将其转换为 TFRecords 文件(如果使用 Tensorflow 进行训练)。为此，你可以看看这些例子:**

**[](https://github.com/tensorflow/models/issues/3365#issuecomment-661326737) [## 仅背景图像支持问题# 3365 tensor flow/模型

### 嗨，物体检测模型支持训练中的“仅背景”图像吗？

github.com](https://github.com/tensorflow/models/issues/3365#issuecomment-661326737) [](https://github.com/tensorflow/models/issues/3578#issuecomment-375267920) [## 使用对象检测 API 创建 tf 记录时，添加纯负面图像会出错？问题…

### 我在测试我的由对象检测 API 训练的 SSD 模型时遇到了这个问题。该模型执行良好，直到它满足…

github.com](https://github.com/tensorflow/models/issues/3578#issuecomment-375267920) 

关于 Tensorflow 中背景图像支持的一些问题:

[](https://github.com/tensorflow/models/issues/3365#issuecomment-366750341) [## 仅背景图像支持问题# 3365 tensor flow/模型

### 嗨，物体检测模型支持训练中的“仅背景”图像吗？

github.com](https://github.com/tensorflow/models/issues/3365#issuecomment-366750341) 

**有时候*你会从 GitHub 回购发行页面*的评论中了解到很多东西。关于背景图片的一些有价值的评论:**

[](https://github.com/tensorflow/models/issues/3365#issuecomment-367927611) [## 仅背景图像支持问题# 3365 tensor flow/模型

### 嗨，物体检测模型支持训练中的“仅背景”图像吗？

github.com](https://github.com/tensorflow/models/issues/3365#issuecomment-367927611) [](https://stackoverflow.com/a/59266084) [## 背景图像中的一类目标检测

### 感谢贡献一个堆栈溢出的答案！请务必回答问题。提供详细信息并分享…

stackoverflow.com](https://stackoverflow.com/a/59266084) [](https://stackoverflow.com/a/53247641) [## 如何训练不含物体的 Tensorflow 物体检测图像？

### 感谢贡献一个堆栈溢出的答案！请务必回答问题。提供详细信息并分享…

stackoverflow.com](https://stackoverflow.com/a/53247641) 

B 在你的目标检测/分类项目中，背景图像可以减少你的 FPs 和 FNs。如果你是深度学习、计算机视觉或机器学习的新手，不要把自己局限于教程、书籍、文章。如果你在你的项目中遇到问题，谷歌一下，试着在 Github 上的项目问题页面上找到解决方案。最有可能的不是你，第一个遇到这种问题的人，可能人们已经在 Stackoverflow 上发布问题，提出问题。很有可能你会找到答案。

# 结论:

# 如果你找到了某个罕见问题的答案或解决方案，如果你写一篇文章解释你在一篇文章中找到的答案，你可以帮助别人更快地找到答案。

# 感谢阅读！如果你喜欢这篇文章，请点击拍手按钮👏尽可能多的次数。这将意味着很多，并鼓励我继续写这样的故事。我们在[推特](http://twitter.com/@iamjelal)上连线吧！🐦干杯！**