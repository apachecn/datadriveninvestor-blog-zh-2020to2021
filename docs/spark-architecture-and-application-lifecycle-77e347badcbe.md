# Spark 架构和应用生命周期

> 原文：<https://medium.datadriveninvestor.com/spark-architecture-and-application-lifecycle-77e347badcbe?source=collection_archive---------0----------------------->

![](img/b6d24b424f22b40fe2fad6ce6693a2c0.png)

Photo by [amirali mirhashemian](https://unsplash.com/@amir_v_ali?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

这是 Apache Spark 准备系列的 Databricks 认证助理开发人员的第二部分。在[第一部分](https://medium.com/datadriveninvestor/databricks-certified-associate-developer-for-apache-spark-preparation-series-41e66dc4165b?sk=295a1092b9a76bb387fac28d2daa84ce)中，我们讨论了考试细节、先决条件和建议的准备工作。

我们遵循 Databricks 推荐的准备材料(包含在[第一部分](https://medium.com/datadriveninvestor/databricks-certified-associate-developer-for-apache-spark-preparation-series-41e66dc4165b?sk=295a1092b9a76bb387fac28d2daa84ce))。因此，在本文中，我们将从 Spark 的架构开始，并尝试从认证的角度来介绍它。我也会尽可能地添加有用的资源。

**基础架构**

Apache Spark 是一个分布式处理引擎。由于其内存中的并行计算框架，它非常快。请记住，Spark 只是处理引擎，它需要一个单独的存储(如 HDFS)来永久写入数据。典型的 Spark 应用程序运行在一个机器集群(也称为节点)上。它将一个较大的任务分解成多个较小的任务，并在这些机器之间分配。然而，这给协调和管理这些机器上的工作带来了挑战。Spark 内置了这一功能，其架构旨在处理大型分布式应用程序。有几个核心组件和角色被分配给这些组件和角色来帮助执行这种分布式工作。

![](img/59d2b45d379da5bc4de19759a0f357ea.png)

Figure 1: A Spark Cluster

**驱动**

驱动程序(或驱动程序)是在一台机器上运行的进程，负责整个应用程序的生命周期。它维护关于 Spark 应用程序的信息。它在执行器(工作机)上分析、分配和调度任务(要完成的处理)。它还在应用程序成功/失败后对用户做出响应。驱动器类似于管弦乐队。像管弦乐队一样，驱动程序不执行任何计算，它只是管理整个应用程序生命周期(图 1)。

**遗嘱执行人**

执行器是运行在集群中其他机器上的工作进程。同一台机器上可以运行多个执行器。每个执行器都有一个数据集合，也称为分区，由驱动程序分配给它们执行代码。他们还向驾驶员报告分配工作的状态(成功/失败)(图 1)。

**插槽**

根据用户为 Spark 应用程序指定的内核，每个执行器可以有多个插槽用于一个任务(由驱动程序分配)。这意味着有两个级别的并行性:首先，工作在执行器之间分配，然后一个执行器可能有多个插槽来进一步分配工作(图 1)。

**任务**

任务是要在分区(行的集合)上完成的工作。这些由驱动程序分配给执行者。这些将在 executor 机器上可用的插槽中运行(图 1)。

**乔布斯**

作业是 Spark 中的并行操作。由驱动程序维护的 spark 应用程序可以包含多个作业。

**火花会**

SparkSession 是控制 Spark 应用程序的驱动程序进程。它是 Spark 所有功能的入口点。对于 Databricks 笔记本和 REPL 环境，它已经在变量“spark”下创建了(图 2)。然而，当编写应用程序时，你必须自己创建它，如下所示。

![](img/4d80ecaa095a35fbc587602a36976a63.png)

Figure 2: SparkSession found as spark in Databricks’ notebook

```
## Create a SparkSession when building applicationsfrom pyspark.sql import SparkSessionspark = SparkSession.builder.master("local")\
                            .appName("My First App")\
                            .config("config.name","config.value")\
                            .getOrCreate()
```

创建 SparkSession 后，您将能够运行 pyspark 代码。SparkSession 是在 Spark 2.x 版本中添加的。在早期版本中，我们有两个独立的上下文:SparkContext 和 sqlContext，它们分别提供了与 rdd 和 Dataframes/Hive 交互的功能。这两个功能现在已经合并到 SparkSession 中，但是 SparkContext 和 sqlContext 还没有被弃用，仍然可以单独访问(图 3)。

![](img/1b17a9f325d054a473de121f1d1fe6fc.png)

Figure 3: SparkContext and sqlContext

**转换、动作和执行**

转换是帮助您实现逻辑的功能。人们可以使用这些来修改底层数据。转换的例子有**选择、过滤、分组、排序、限制**等。转换在本质上是*惰性的*，这意味着直到一个动作被调用时处理才被执行。Spark 只是构建一个谱系，并等待调用一个动作来执行该谱系中的转换(图 4)。惰性求值使得并行执行操作变得容易，并允许各种优化。

![](img/b8ba65f8c55d425ba17aac78b1d2d6ce.png)

Figure 4: Spark lineage

转换本质上可以是狭义的或广义的。窄转换不会导致混洗(数据在网络上的机器间移动)，即计算结果所需的数据最多驻留在一个分区上。另一方面，大范围转换会导致混乱，因为底层数据驻留在许多分区中，并且需要跨机器重新分布。

**动作**

动作是当遇到时触发来自沿袭的计算的语句。虽然变革本质上是懒惰的，但行动是热切的。操作的例子有 show()、count()、collect()等。例如

```
1\. Data_file = spark.read.csv(“/home/users/some_random_data.csv”)2\. Selection_df = data_file.select(“first column”, “second column”)3\. Filter_df = selection_df.where(“second column is not NULL”)4\. Group_df = filter_df.groupBy(“first column”)5\. Count_df = Group_df.count()
```

上面的代码示例展示了一个典型的 spark 应用程序。对于步骤 1-4，我们从 csv 文件中读取数据并应用一系列转换。Spark 只是在内存中为这些步骤构建一个谱系，并不执行实际的处理。步骤 5 是一个计数动作，当 Spark 到达时，它将追溯到步骤 1，执行所有处理并输出计数。

**流水线作业**

每当 Spark 应用程序遇到洗牌时，数据就会被写入执行器磁盘。但是，洗牌操作之前的所有步骤都可以放在一起，并且一次执行。这就是所谓的流水线技术，结合 Spark 在内存中进行处理而不会立即溢出到磁盘的事实，它可以使查询更快。

**催化剂优化器**

Spark 数据框架——构建在 Spark SQL 之上——使用底层 catalyst optimizer 获得性能速度。Catalyst optimizer 找到最有效的方法来应用您的转换和操作。Catalyst optimizer 是数据帧性能优于 rdd 的原因。

注意:rdd 不包括在 Databricks Spark 认证中，所以我们在这里不讨论它。

每当我们使用 Spark SQL(也可以是 pySpark 中的 dataframe 代码)运行一个查询时，在转换成物理计划并执行之前，它都要经历几个计划阶段。使用 Dataframes 和 Spark SQL 意味着您依赖 catalyst optimizer 来优化您的查询计划，而不是使用 rdd 并自己完成。例如，

```
### Example By: [Sumit M](https://www.linkedin.com/in/bigdatabysumit) 
### For example, you are trying to calculate average salary of employees by age### using RDDs
fileRdd = sc.textFile(“/employeeData.csv”)
fileRdd.map( x => {val fields = x.split(",");\
       (fields(1), fields(2)) }) \ 
       .map(x => (x._1, (x._2, 1))) \ 
       .reduceByKey((x,y) => (x._1 + y._1, x._2 + y._2))\
       .map( x => (x._1, x._2._1 / x._2._2))### using Dataframes
data_df = fileRdd.toDF(“username”, “age”, “salary”)
data_df.groupBy($”age”).agg(avg(“salary”))
```

**在 RDD 进场:**

我们使用 Lambda 函数准确地告诉 Spark“如何做”, Spark 不能优化它。它直接将这些函数发送给执行器来处理数据。如果有任何可能的优化，我们必须自己做。

**在数据帧方法中:**

我们使用声明的方式告诉 Spark“做什么”,而将“如何做”的部分留给 Spark 的优化器。这使得通过 Catalyst optimizer 优化数据帧成为可能。

**催化剂优化器工作**

当我们使用 Spark SQL 提交查询时，它会经历以下步骤。

![](img/eee6d1ce1beef4d338245164f964f8c7.png)

Figure 5: Catalyst Optimizer working (Image courtesy: [Databricks blog](https://databricks.com/glossary/catalyst-optimizer))

*   它创建一个未解析的逻辑计划，并检查列名和表名等的有效性。
*   之后，创建一个已解析的逻辑计划。在这一步，命令可能会被重新组织以优化性能。
*   Catalyst optimizer 可能在此阶段生成至少一个物理计划来执行查询。这个阶段代表了 Spark 在应用优化后实际要做的事情。
*   如果有多个物理计划，则使用成本模型评估每个计划的成本。选择具有最佳性能的计划，编译成 java 字节码，然后执行。

**缓存**

Spark 可以在计算期间将数据存储在内存中。这是进一步加快查询速度的好方法。我们知道 Spark 是一个内存处理引擎，但是在开始处理之前，它必须从磁盘读取一次数据。例如

```
Data_file = spark.read.csv(“/home/users/some_random_data.csv”)
```

这是第一次从磁盘读取，并且该读取所属的每个沿袭都必须从磁盘读取。但是您可以使用缓存将它存储在内存中以加快处理速度。

```
df_cached = Data_file.cache()
df_persisted = Data_file.persist()
```

cache()和 persist()是用于内存存储的内置 Spark 函数。cache()仅存储默认值(仅限内存),然而，persist 有几个选项，例如内存和磁盘持久性。更多细节可以在[这里](https://spark.apache.org/docs/latest/rdd-programming-guide.html)找到。

您可以对应用程序逻辑中经常访问的任何数据进行同样的操作。在反复使用相同数据集的应用程序中，缓存是最强大的优化技术之一。当您缓存一个数据帧时，它的每个分区都将临时存储在它的执行器的内存中，这将使即将到来的读取更快。

**Spark 应用的生命周期**

我们已经讨论了 Spark 应用程序的核心组件。让我们看看应用程序本身的生命周期。假设您创建了一个 pyspark 应用程序`my_first_app.py`并提交给集群。

```
spark-submit \
--master <url> \ 
--deploy-mode cluster \ 
--conf <some_key> = <some_value> \ 
my_first_app.py \
```

首先，这个应用程序将与资源管理器通信，并请求运行资源。如果请求成功，在其中一个节点上启动驱动程序(图 6)。由于这是一个打包的应用程序，代码中的第一件事应该是在 SparkSession 上创建。

![](img/9be158f7a3093fb100078503cde45d61.png)

Figure 6: Driver Launch

创建 SparkSession 后，它将与集群管理器通信，请求在集群中启动 Spark executor 进程。请记住，执行器数量和相关配置(内核、RAM 等)是由用户在提交应用程序时设置的。集群管理器通过启动执行器进程来响应请求，并将相关信息发送给驱动程序进程。之后，驱动程序和执行器进行通信，移动数据，驱动程序将任务调度到每个执行器上(图 7)。每个执行者用状态(成功或失败)和结果来响应。在图 7 中，我们总共有三个节点。在节点 01 上，驱动程序进程正在运行。在 Worker 01 上，两个执行器正在运行，而 Worker 02 上只有一个执行器进程在运行。

![](img/6b4b3cb2b5ad9e786e4ed3bd6284a662.png)

Figure 7: Drivers and Executors in action

完成后，驱动程序以成功或失败退出，集群管理器关闭集群中的执行器。

您在`my_first_app.py`中编写的实际代码定义了您的 Spark 应用程序，每个应用程序可以有一个或多个作业。

一般来说，一个动作有一个火花工作。Spark 作业被分解为一系列阶段。阶段表示可以一起执行的一组任务，例如 Select 后跟 Where 等。每当数据需要在执行器之间转移时(例如在连接查询中)，Spark 就会创建一个新的阶段。每个阶段由几个任务组成，这些任务在执行器的可用槽中运行。

**总结:**

驱动程序是一个向多个执行者发送任务的程序。Spark 性能的秘密在于并行性，即将工作分配给多个虚拟机的能力。

回想一下，Spark 不会在读取操作后立即执行操作(惰性评估)。相反，它建立了一个将应用于源数据的数据转换计划。只有当你调用一个动作时，这个计划才会被执行。

Catalyst Optimizer 旨在为应用您在代码中调用的转换和操作找到最有效的计划。

恭喜你！您已经了解了 Spark 架构的基础知识。还有一些事情，特别是关于 Spark UI 的，我将在以后的某个时间讨论。在本系列接下来的文章中，我将重点介绍使用数据框架的 Spark 编程，因为它是认证的最大部分。

最后，我鼓励你在 LinkedIn 上关注[just suffith Spark(顺便说一句，这不是我的页面:p ),了解关于 Spark 和数据块的日常 mcq。](https://www.linkedin.com/company/justenough-spark/)

快乐学习:)