# 肘方法—帮助确定 K 均值聚类算法中 K 值的指标|数据驱动的投资者

> 原文：<https://medium.datadriveninvestor.com/elbow-method-metric-which-helps-in-deciding-the-value-of-k-in-k-means-clustering-algorithm-data-d67271cdbe87?source=collection_archive---------5----------------------->

![](img/7247ee55a77d7459f87177efc344d551.png)

在本文中，我将解释有关该方法的信息，它有助于决定 K 的值，您可以使用该值使用 [K 均值聚类](https://www.datadriveninvestor.com/glossary/k-means-clustering/)算法对数据进行[聚类](https://www.datadriveninvestor.com/glossary/clustering/)。

过去，我们没有任何技术可以通过某种方式对数据进行聚类。我们必须在旅途中通过在该领域的良好知识来单独标记它。如果你不了解你正在处理的领域，你就不能区分它们。假设你有很多关于公司的内容，但你对公司一无所知。比如哪个公司属于哪个领域。那么要把它们做成一个集群几乎是不可能的任务。因为公司的数量太多了，而且要花很多时间来对其进行聚类。

[](https://www.datadriveninvestor.com/2019/01/23/which-is-more-promising-data-science-or-software-engineering/) [## 数据科学和软件工程哪个更有前途？数据驱动的投资者

### 大约一个月前，当我坐在咖啡馆里为一个客户开发网站时，我发现了这个女人…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/23/which-is-more-promising-data-science-or-software-engineering/) 

但如今，由于[机器学习](https://www.datadriveninvestor.com/glossary/machine-learning/)技术的发展，使用其一点点描述内容分析来区分公司并对类似公司进行聚类是一件非常容易的事情。

# 无监督学习

[聚类](https://www.datadriveninvestor.com/glossary/clustering/)是一种无监督的机器学习技术，用于[分类](https://www.datadriveninvestor.com/glossary/classification/)。

[无监督学习](https://www.datadriveninvestor.com/glossary/unsupervised-learning/)意味着没有特定的输出可用于指导学习过程。数据通过算法自我探索，以找到模式并相应地给出一些输出。

# k-均值聚类算法

[K-Means 聚类](https://www.datadriveninvestor.com/glossary/k-means-clustering/)方法/算法在[数据挖掘](https://www.datadriveninvestor.com/glossary/data-mining/)和分析领域广泛用于聚类分析。K-means 用于将 n 个观察值划分为 k 个聚类，其中每个观察值都属于具有最近平均值的聚类。

使用 K-Means 聚类算法，我们可以得到一些聚类。我们不需要告诉算法如何像它自己做的那样产生聚类。结果是属于同一组/群的每个数据点或观察值比其他群/群中的观察值更相似。

K-Means 使用迭代细化方法，根据用户给定的要查找的聚类数生成最终的聚类。无论用户定义了什么样的 k 值，它都会将数据分布到 k 个簇中。

# 评价 K-均值聚类的肘方法

正如我们所知，我们必须确定 k 的值。但是为了确定 k 的值，肘法可以帮助我们找到 k 的最佳值。

它使用数据点与其各自分配的聚类质心之间的**距离平方和(SSE)** 或称平均值。我们在 SSE 点开始变平并形成一个弯头的地方取值。

这就是该方法如何帮助找到 k(数据集的聚类数)的良好值，并帮助为给定数据集建立良好的聚类。

下面，我在 K-Means 聚类算法中加入了用于查找 K 的最佳值的 Elbow 方法的代码文件。

链接到 Gist 文件(肘方法的代码)->

Gist code for Elbow Method

> *#代码为肘法，为 K-Means 聚类算法找出 K 的最佳值。*
> 
> *从 sklearn.cluster 导入 pyplot 作为 PLT*
> 
> *导入方式*
> 
> *#运行 Kmeans 算法，得到数据点簇的索引*
> 
> *# sse 是距离列表的平方和*
> 
> *sse = []*
> 
> *X = "作为列表的文档集"*
> 
> *# k_list 是我们要为*查找聚类的范围列表
> 
> *k_list = list(range(1，10))*
> 
> *对于 list_k 中的 k:*
> 
> *# km_model 是我们定义模型以拟合数据的 KMeans。km _ model = k means(n _ clusters = k)*
> 
> *#将数据(X 为数据集)拟合到 km _ model km _ model . fit(X)SSE . append(km _ model . inertia _)*
> 
> *#将 sse 对 k 作图，求 k 开始变平并做成肘状的角度处的值。*
> 
> plt.figure(figsize=(6，6))
> 
> plt.plot(k_list，sse，'-o ')
> 
> plt.xlabel(r '聚类数*k* ')
> 
> plt.ylabel('距离平方和')

这将给出 k 的最佳值，您可以获得数据的最佳聚类，其中它将生成良好的聚类，每个观察值或数据点都被分配到最佳聚类。我们不必担心随机分配 k 的值。

尝试使用这种方法找到 k 的值，并检查它如何提高分类的准确性。

![](img/22b28850f2fc4647db66fe4c11f76005.png)

Jayesh Manani 毕业于计算机工程专业。他曾在 Allevents.in 和 Torrent Pharmaceuticals Ltd .等公司担任数据科学工程师。目前在 IIM 艾哈迈达巴德担任副研究员，与印度管理学院教授一起从事文本分析和社交媒体分析等分析项目。他还擅长网页抓取和机器学习。他制作了一些可用于分析社交媒体数据的刮刀，公司可以根据分析结果做出许多决策。他还写关于 Medium.com 的技术，如何使用技术和算法来处理普通人在日常生活中面临的问题。Jayesh 对技术和生活充满热情。他对自动化、人工智能、区块链、物联网、数据科学以及技术可以给我们的社会和生活带来的影响非常感兴趣。

*原载于 2020 年 1 月 21 日*[*【https://www.datadriveninvestor.com】*](https://www.datadriveninvestor.com/2020/01/21/elbow-method-metric-which-helps-in-deciding-the-value-of-k-in-k-means-clustering-algorithm/)*。*