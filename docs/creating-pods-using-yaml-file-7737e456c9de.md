# 使用 YAML 文件创建窗格

> 原文：<https://medium.datadriveninvestor.com/creating-pods-using-yaml-file-7737e456c9de?source=collection_archive---------10----------------------->

![](img/31c8679823d8ce88f8444939264e7658.png)

(Photo By Simon Migaj on Unsplsh)

在之前的博文[https://medium . com/@ adityamohanty/importance-of-pods-in-kubernetes-7ff 838 DC 1e 9 c](https://medium.com/@adityamohanty/importance-of-pods-in-kubernetes-7ff838dc1e9c)中，我们已经讨论了 kubernetes 中 pod 的重要性。在这篇文章中，我们将看到如何使用 YAML 文件创建一个 pod。

## YAML 文件:

*YAML* 代表专用于配置文件的“ **YAML 不是标记语言**”。它是一种数据序列化语言，用于将数据结构转换成可以存储的格式。YAML 在 kubernetes 中特别有用，它允许轻松地创建复杂的结构，而不是依赖命令行。

[](https://www.datadriveninvestor.com/2019/03/26/agile-management-the-good-the-bad-and-the-downright-ugly/) [## 敏捷管理:好的、坏的、丑陋的|数据驱动的投资者

### 公司不断重塑自己，以获得或保持竞争优势和市场份额。这是…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/03/26/agile-management-the-good-the-bad-and-the-downright-ugly/) 

## YAML 为一个 POD 文件:

让我们了解一下 yaml 文件的基本部分。一般来说，pod 可能由以下部分组成。

**apiVersion** :这描述了 yaml 文件中使用的 kubernetes api 版本。

**种类:**该字段显示 yaml 文件描述的资源类型。

**元数据:**这包括关于 pod 的各种信息，如名称、标签、名称空间等。

**规格:**显示 pod 内容的描述，如 pod 的容器、体积和其他数据。

**状态:**包含正在运行的 pod 的信息。比如每个集装箱的描述和状态。

我们将看到如何为 pod 创建 yaml 文件。让我们看看下面创建 pod 的文件。

```
apiVersion: v1
kind: Pod
metadata:
 name: mypod
spec:
 containers:
 — image: newpod
   name: firstpod
 ports:
 — containerPort: 8080
   protocol: TCP
```

上面的代码片段显示了一个非常简单的 yaml 文件。第一行显示了 kubernetes api 的版本 v1。同样，第二行显示了我们所指的资源类型，这里是 **Pod。**元数据的子节点*名称*表示 Pod 的名称。pod 有一个名为 *firstpod 的容器。*集装箱在 8080 港口运行。

## 使用 kubectl 创建 pod:

为了从 yaml 文件创建 pod，我们将使用 kubectl 命令。例如，可以在终端中使用以下命令从 yaml 文件创建 Pod。

```
$ kubectl create -f mypod.yaml
```

要了解 pod 列表，我们可以借助以下命令。

```
$ kubectl get pods
```

## 标签:

当创造圆荚体时，圆荚体的数量可能会增加很多。如果没有一个合适的机制，组织这些舱会非常困难。这将导致一个彻底的混乱。因此，我们需要一种机制来以适当的方式组织它们，以便我们可以知道哪个 pod 属于哪个组或类。因此，这种组织豆荚的任务是通过标签完成的。**标签**有助于组织各种 kubernetes 资源。我们将每个资源存储在一个键值对中，稍后使用 ***标签选择器*** 来选择资源。我们可以为每个资源设置多个标签，只要它们是唯一的。

```
apiVersion: v1
kind: Pod
metadata:
 name: label-demo
 labels:
   type: demo
   env: prod
spec:
 containers:
 — image: new
 name: label
 ports:
 — containerPort: 8080
 protocol: TCP
```

上面的代码片段显示了一个 yaml 文件的结构，该文件使用 label 来组织 pod。作为标签，我们有*类型*和*环境。为了了解创建的标签，我们将使用以下命令。*

```
$kubectl get po — show-labels
```

为了选择某些标签，我们可以利用标签选择器根据某些条件来选择资源，比如它是否包含带有某个键或某个键和值的标签等。

假设我们想要列出所有带有 *env=prod* 的 pod，我们将使用以下命令。

```
$kubectl get po -l env=prod
```

## 特定节点的调度窗格:

假设我们希望将 pod 调度到一个可以访问 GPU 的特定节点。为了做到这一点，我们将使用以下代码。

```
apiVersion: v1
kind: Pod
metadata:
 name: mypod
spec:
 nodeSelector:
   gpu: “true”
 containers:
 — image: newpod
   name: demo
```

此处**节点选择器**添加在*规格*部分下。这将使我们能够选择支持 gpu 的节点。

在这篇文章中，我们看到了使用 YAML 文件的各种方法。在下一篇博客中，我们将看到复制。