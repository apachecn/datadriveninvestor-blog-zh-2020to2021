# 使用 AWS Lambda+AWS API gateway+AWS Elastic 文件系统在 AWS 中部署深度学习模型。(第二部分)

> 原文：<https://medium.datadriveninvestor.com/deployment-of-deep-learning-models-in-aws-using-aws-lambda-aws-api-gateway-aws-elastic-file-2b7102b3ff39?source=collection_archive---------4----------------------->

大家好，

在这 3 篇文章系列中，我们将了解如何部署深度学习模型，该模型在 AWS 中执行图像分类，并向世界公开其 API，因此其他人可以与您的 API 进行交互。

**前往岗位 1:** [**链接**](https://medium.com/@balakrishnakumar.v/deployment-of-deep-learning-models-in-aws-using-aws-lambda-aws-api-gateway-aws-elastic-file-a48fdeb2c140)

**转到帖子 2:你正好在那里，在你应该在的地方。**

**转到帖子 3:** [**链接**](https://medium.com/@balakrishnakumar.v/deployment-of-deep-learning-models-in-aws-using-aws-lambda-aws-api-gateway-aws-elastic-file-c423139fa858?sk=c781d42e92cab18e797f2b5e58b7068c)

# 自动气象站 Lambda(第二部分)

![](img/717f42b327f577ae27d7d4e1e924e622.png)

在我们的第一篇文章中，我们提到了 AWS Lambda 的局限性，即为什么它**不能**处理大小为> 250 MB 的未压缩部署包，因此我们附加了 EFS，它就像 AWS 的 Google Drive，您可以在那里水平扩展并加载您的部署包。

所以在这篇文章中，我们将使用 AWS Lambda 层和 AWS EFS 将部署包添加到 AWS Lambda 中。

让我们开始吧。

1.IAM 角色的创建:

IAM 角色类似于为一个 AWS 服务提供访问其他服务的权限。在我们的例子中，Lambda 函数将访问 EFS(用于部署包)和 S3(用于存储模型工件和最终输出结果)。

导航到 IAM 控制台，点击**创建角色**，选择一个用例作为 **Lambda** ，点击**下一步:权限**

![](img/ccb3ffe6f80d13777ae22212f25499b2.png)![](img/a8b90a4ad167c0436f63199a9f1bc72d.png)

现在附上下面列出的政策，然后添加您选择的标签。

![](img/621349fa0ee37e375323de2e76d06b04.png)

最后，您的控制台应该如下所示，然后单击 CreateRole。

![](img/2036cfd76c9d25cb0ad4e8e2dc9985fc.png)![](img/81297e8f878fcb0b9b258318d85a60ed.png)

2.现在让我们导航到 AWS Lambda。现在单击创建函数。

![](img/a70407b42a6f483e59681cf7db3753fe.png)

2.从头开始选择 template -> Author，提供您选择的函数名，为了方便起见，我选择运行时为 Python 3.6。(你可以根据你训练深度学习模型的方式，选择任何类似 python 3.7/3.8 的运行时)

![](img/1fb44cc3fcaa9398c5f333882893370a.png)

3.在 Permission 选项卡下，您需要选择在 IAM 策略下创建的执行角色，这是我们在上一步中创建的。

然后单击创建函数。

![](img/43722faf6c5b95c6c26b463232a9b572.png)

现在我们在新创建的函数的主页上。在这里，我们将逐步调整一些参数。

# 使用 Lambda 层导入包

![](img/afaa031f121e930f48ba8c2b28dcfeb1.png)

4.首先，我们将创建一个 Lambda 层来演示如何将一些轻量级的包加载到我们的函数代码中。所以在这个例子中，我将展示如何使用 lambda 层将 Scikit-Learn 包加载到 Lambda 函数中。层就像函数的后端，我们可以在其中放置一些依赖项。

为了让 lambda 层工作，我们需要以下面的格式压缩我们的包。

您可以选择任何其他感兴趣的包。

**scikit-image . zip**→**python \ lib \ python 3.6 \ site-packages**

![](img/0e23dd99f808f5e8af0a3ad27e5895a7.png)

5.创建您选择的 zip 文件后，将 zip 文件上传到您拥有的一个 S3 存储桶中，或者创建一个新的 S3 存储桶并上传 zip 文件。在我的例子中，我有两个包，一个包含 scikit-image，另一个包含其他依赖项，然后复制对象 URL。

![](img/693d0e029b1792fa2ae567ed740c3126.png)

6.转到 Lambda 主页，单击图层选项卡，然后单击创建图层按钮。然后提供名称和描述，在 S3 链接 URL 下附加包含 zip 文件的 S3 存储桶的链接，并选择适当的运行时。

![](img/08bd65f1e88a27ad514c4f6e3560d82d.png)![](img/34c22b3aea5722c0d396fb4029a763b8.png)![](img/8abac0d1aa1532250e6ea210ef564549.png)

7.创建图层后，使用 lambda 函数添加图层。

![](img/f0ad2b9558d1e36413aed6f1a19427cc.png)![](img/c05ec66893674ccab941c36717deb776.png)![](img/e769de6205495859a482b7c46ed08268.png)

现在，我们可以看到一个与我们的功能相关的层。我们将尝试把这个模块导入到我们的函数中。

![](img/e0e35aeeaed1fd08397ce9145e94591a.png)

当我们单击测试按钮时，它会提示配置测试事件。只需提供一个事件名称，然后单击保存。

8.相应地修改您的 lambda 函数，然后单击 save 并单击 Test 运行您的 lambda 函数。这里的输出将 skimage 版本打印为 0.16.2。这就是我们如何使用 lambda 层导入包。

![](img/55d418a747bed80cb37694315debbbdf.png)

# 使用 EFS 导入包

因此，如果我们有更多的包要导入，那么 lambda 层无法处理它，所以我们将 EFS 配置为 python 后端。

让我们开始吧。

在您的 Lambda 函数下，如果您滚动，您将看到 VPC 和文件系统的部分，现在让我们通过单击编辑来配置这些选项卡。

![](img/9e726eef46f72514126950a507cf841d.png)

1.  在 vpc 下，选择默认的 VPC(你可以创建自定义的 VPC，但当你添加互联网网关等时，它是昂贵的。)
2.  选择所有 3 个子网，这样 lambda 函数在所有子网中都可用。
3.  选择我们在本系列的第 1 篇文章中创建的安全组，然后单击 save。

![](img/23d931ced5d6daaeef84a0e51abf49b3.png)![](img/67de5418f7eb7ea21aa4ae34aa84f51a.png)

4.现在让我们配置弹性文件系统。

![](img/ff78293ecf955b088524a601196f6e48.png)

5.对于 EFS 文件系统，选择我们在文章 1 中创建的 EFS，并选择 EFS 的访问点，在我们的例子中，我们创建了 **/demo** 。选择适当的接入点。

最后，添加本地挂载路径，这是我们存储包并通过 lambda 函数访问它们的路径。

根据 AWS 标准，它必须以“**/mnt/demo”**开始，然后单击保存。

![](img/c97ed18fcabfc36a6b18cb2d671ec7c7.png)![](img/a646b9ed56d8097db0b437a8b3936921.png)![](img/6480a85e735c11ef90e0db07b8b2fff2.png)

现在，我们已经成功配置了 VPC 和 EFS 装载点。注意我们有一个本地挂载点:**“/mnt/demo”。**

所以我们在这个路径下加载我们的部署包(heavy ),并在 lambda 函数中导入它们。

6.因此，要加载一些包，我们可以遵循两种方法。

I .如果您的本地计算机上已经有了所有的包，那么只需使用 WinSCP 将其复制并粘贴到挂载位置。

二。通过 EC2 实例连接到 EFS，然后简单地按照命令→**pip 3 install<package name>-t/EFS/demo/—system**

现在我们可以通过 putty 和 WinSCP 看到我们的 EFS 文件系统，我们已经挂载了 **demo** 文件夹。

![](img/201b498fc5b56bb9b39ac7d75a8bc0b8.png)

7.现在让我们将 PyTorch 包添加到我们的 EFS 中，并尝试通过 lambda 函数导入它。

命令:**pip 3 install torch = = 1 . 5 . 1+CPU torch vision = = 0 . 6 . 1+CPU-f**[https://download.pytorch.org/whl/torch_stable.html](https://download.pytorch.org/whl/torch_stable.html)**-t/EFS/demo/—系统**

![](img/61115a53b53896dd79dd6ecdb02209d4.png)![](img/247e3b9c903013cc9e3b50c524837063.png)

此外，我们通过 WinSCP 确认所有基于 torch 的包都已加载。现在让我们尝试将它们导入 lambda 函数中。

![](img/58e34dae3b76e5cb27acadf3b6c5baeb.png)

同样在基本设置下，根据您的要求增加超时时间。最大时间是 15 分钟，这是硬限制，您可以将内存限制增加到 3GB (RAM)以加快处理速度。因为 AWS Lambda 定价是基于执行时间和 API 调用计数的，所以您可以根据需要配置它们。

通常超时和内存是协同作用的，它们之间有一个平衡。

8.很好，现在我们需要在 lambda 函数上将 EFS 中挂载的 torch 目录的路径添加到我们的 python 文件系统中。因此，当 python 执行时，它会将目录添加到帐户中，并加载 torch 包。

**C1:进口系统**

**C2: sys.path.insert(0，'/mnt/demo/') # For python 3.6**

在这里的输出中，我们实际上可以看到加载的 torch 包的版本，挂载路径也被添加到系统中。

![](img/65125f7ec2143e40dbcae10d295c6638.png)

9.到目前为止，我演示了 torch 包，稍后您可以添加其他必要的包，如 six、requests、pillow、OpenCV、open3d、NumPy、matplotlib、fastai、cv2、statistics、requests 等，通过 **EC2** 在同一个目录" **/efs/demo** 中使用 pip3 命令，并在 **AWS LAMBDA 中使用挂载点" **/mnt/demo** 调用它们。**

![](img/9aae8bc1336baafa56408fd89442efe5.png)

此外，这是一个很好的措施，注意到我们的 EFS 计量大小，因为 EFS 比 S3 昂贵，请确保您正确使用它。

EFS 通常收费 **(0.33 美元/GB)。**

# **端点创建**

10.现在，由于我们通过安全 VPC 将 EFS 连接到我们的 Lambda，在 AWS 中，默认情况下，您的功能无法访问互联网(您可以创建一个新的 VPC，并为互联网添加 NAT 网关，但这需要成本(每 NAT 网关小时 0.056 美元)，而且您无法使用 boto3 库与其他 AWS 服务建立任何连接。这里再解释一下。

但幸运的是，我们可以通过端点将 lambda 函数只连接到两个服务，然后通过 boto3 库访问它们。

1.  连接到 S3(通过端点)
2.  连接到 DynamoDb(通过端点)

为了连接到 S3 铲斗进行数据传输，进行以下配置。

在 VPC 选项卡下，导航到端点并创建端点。

然后在 AWS 服务下搜索 S3，检查子网组，最后单击创建端点，然后等待直到状态变为可用。

![](img/b88db21cf63f4739884fa3eb684653c7.png)![](img/980ffe0866224a2906c6272ab376e044.png)![](img/ab23ca2ed7bf0116fb280ad9dc018098.png)![](img/dc53c89b633cc4ac76accaaf2b14c725.png)![](img/055b40fb5072a550b5ea426f98194dcc.png)

如果您希望将 dynamodb 数据库连接到您的 lambda 函数，请执行相同的操作并搜索 dynamodb。

现在我们已经成功地完成了如何将沉重的包部署到 AWS Lambda 中。

现在继续阅读帖子 3，部署我们的深度学习模型，并通过 API Gateway 调用它。

最佳做法是检查 AWS Lambda:[https://aws.amazon.com/lambda/pricing/](https://aws.amazon.com/lambda/pricing/)的定价

我将发布与机器和深度学习相关的文章，以及它们与 AWS 服务的交集。

如果你认为这是你应得的，请投票并关注。

在那之前，下次见。

**文章作者:**

**BALAKRISHNAKUMAR V**