# 将对象从一个 S3 存储桶复制到另一个存储桶

> 原文：<https://medium.datadriveninvestor.com/copy-objects-from-one-s3-bucket-to-another-932936a739a9?source=collection_archive---------5----------------------->

![](img/1487895d33cbc1e354c8d318eba996a1.png)

亚马逊简单存储服务是互联网存储。它旨在使开发人员更容易进行网络规模的计算。

亚马逊 S3 有一个简单的网络服务界面，你可以用它在任何时间从网络上的任何地方存储和检索任何数量的数据。有时，根据我们的需要，必须将对象从一个桶复制到另一个桶，并通过副本将数据从一个区域切换到另一个区域。

[](https://www.datadriveninvestor.com/2018/09/22/infographic-journey-to-the-clouds/) [## 信息图:云之旅|数据驱动的投资者

### 聪明的企业领导者了解利用云的价值。随着数据存储需求的增长，他们已经…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2018/09/22/infographic-journey-to-the-clouds/) 

## **步骤 1:-使用命令行检查 AWS CLI 版本 2**

在安装 AWS CLI 版本 2 之前，您必须检查它是否已经安装。通过运行以下命令进行检查。如果你得到`aws2 not found` 意味着 **AWS CLI 版本 2** 还没有安装。

```
$ which aws2
  **OutPut:-**
  aws2 not found$ aws2 --version 
  **OutPut:-**
  aws2 not found
```

## **步骤 2:-在 macOS 上安装 AWS CLI 版本 2**

通过运行以下命令安装 AWS CLI 版本。

```
$ curl "[https://d1vvhvl2y92vvt.cloudfront.net/AWSCLIV2.pkg](https://d1vvhvl2y92vvt.cloudfront.net/AWSCLIV2.pkg)" -o "AWSCLIV2.pkg"
```

![](img/727cfbd0433fc322576e88eae73ca66d.png)

通过运行旧命令再次检查。但是，现在输出将会不同。表示安装了 aws2。

```
$ which aws2 
  **OutPut:-**
  /usr/local/bin/aws2$ aws2 --version 
  **OutPut:-**
  aws-cli/2.0.0dev4 Python/3.7.4 Darwin/17.7.0 botocore/2.0.0dev3
```

![](img/961bf2ce17b786955513df71da2da44a.png)

## **步骤 3:-通过运行以下命令**配置 AWS CLI

要配置 **AWS CLI** ，您必须使用`Access Key`和`Secret key`。如果您没有密钥，那么创建一个用于编程的 **IAM 用户**，并授予该用户完全的 S3 访问权限。

获取密钥后，通过运行以下命令进行配置。

```
$ aws2 configure
```

输入您的访问密钥 ID 和秘密访问密钥。按 Enter 键跳过默认区域和默认输出选项。有关区域参数的信息，请参见[亚马逊 S3 的 AWS 区域和端点](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region)。
**注意**:AWS CLI 输出为 JSON、text 或 table，但并非所有命令都支持每种类型的输出。如果命令输出不支持您选择的格式，它将默认为自己的格式。

```
AWS Access Key ID [****************2JWB]: AKIANKITPOOTQIRJ2JF3
AWS Secret Access Key [****************xZkN]: M/snFgx0/H/nEiIIiSmaJ34VAn195POOt787ghkHhgGGDKGHKnv1PptU
Default region name [None]:
Default output format [None]:
```

## 步骤 4:-在 S3 存储桶之间复制对象

通过运行下面的[同步命令](https://docs.aws.amazon.com/cli/latest/reference/s3/sync.html)，在源桶和目标桶之间复制对象:

```
$ aws2 s3 sync s3://SOURCE_BUCKET_NAME s3://NEW_BUCKET_NAME
$ aws2 s3 sync s3://learning-1234 s3://replica-test-new **OutPut:-**copy: s3://learning-1234/aa.txt to s3://replica-test-new/aa.txt
copy: s3://learning-1234/test/LinkedIn.jpg to s3://replica-test-new/test/LinkedIn.jpg
copy: s3://learning-1234/test_2.png to s3://replica-test-new/test_2.png
copy: s3://learning-1234/del.png to s3://replica-test-new/del.png
copy: s3://learning-1234/Screen Shot 2020-02-03 at 4.22.12 PM.png to s3://replica-test-new/Screen Shot 2020-02-03 at 4.22.12 PM.png
copy: s3://learning-1234/test_1.png to s3://replica-test-new/test_1.png
copy: s3://learning-1234/3.png to s3://replica-test-new/3.png
copy: s3://learning-1234/1.JPG to s3://replica-test-new/1.JPG
```

![](img/39e457f1aa3749ff114d6bd3a179ccf2.png)

**注意:-** 处理需要多少时间，取决于数据的大小。

## 步骤 5:-验证对象已复制

您可以验证对象是否被复制。通过运行以下命令。

```
$ aws2 s3 ls --recursive s3://replica-test-new --summarize**OutPut:-**2020-02-06 18:44:40     278363 1.JPG
2020-02-06 18:44:40     247555 3.png
2020-02-06 18:44:40     265132 49948283_319440778668592_1458464790849519616_o.jpg
2020-02-06 18:44:40     125622 Screen Shot 2020-02-03 at 4.17.18 PM.png
2020-02-06 18:44:40     110784 Screen Shot 2020-02-03 at 4.22.12 PM.png
2020-02-06 18:44:40         62 aa.txt
2020-02-06 18:44:40     108864 del.png
2020-02-06 18:44:40      29016 test/LinkedIn.jpg
2020-02-06 18:44:40      61607 test_1.png
2020-02-06 18:44:40      60994 test_2.png
2020-02-06 18:44:41      33238 test_3.pngTotal Objects: 11Total Size: 1321237
```

保护您的数据安全。🤓

欢迎在评论区提出任何问题或疑问，或者你可以在脸书上 ping 我。