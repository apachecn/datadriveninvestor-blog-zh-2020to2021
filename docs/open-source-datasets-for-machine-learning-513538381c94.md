# 用于机器学习的开源数据集

> 原文：<https://medium.datadriveninvestor.com/open-source-datasets-for-machine-learning-513538381c94?source=collection_archive---------22----------------------->

![](img/f4efc94cc5cc2a210f1cfe3d4e1b8c18.png)

机器学习是人工智能的一种形式，它教会计算机系统根据过去的经验进行学习和改进。随着机器学习从收集的数据中揭示模式和规则，任务以类似于人类完成任务的方式自动化。机器学习允许公司通过利用客户服务，如产品、广告和其他以前手动执行的日常业务任务来转变他们的业务。用例可以扩展到多个行业和细节层次。目前的努力集中在复杂和关键的任务上，如自动驾驶、疾病检测和灾难预测。

机器学习算法只和训练集一样好——数据集对于预测质量是不可或缺的。很难找到特定的数据集来实验和解决机器学习问题。预算不允许选择最适合的数据集，或者所需的数据集可能根本不可用。有各种公开可用的数据集可以帮助您更专注于预测模型的创建，而不是数据基础的收集和标注。

# 开源数据

开源数据非常重要，因为这个世界依赖于数据和其中包含的信息。可能是用于商业洞察、机器控制或销售计划的数据—我们生活在一个数据驱动的商业模式的数字时代。开源数据是公开可用的数据，并开放供重用和共享。政府和组织的各种倡议提供了数据，作为现状演变的基础。总而言之，开放数据将帮助世界转变我们这一代人建立的流程和系统。

机器学习使用算法来随着时间的推移而改进，然而，其质量的指标是用于创建和采用这些模型的数据。以下四种数据类型主要用于机器学习:

*   **数字数据**:任何形式的定量的、可测量的数据，如速度或高度。数字数据包括离散和连续的数字，允许对数字进行数学运算。
*   **分类数据**:该类型由标签的类别定义，如性别和行业。分类数据是非数值型的，因此不能直接进行数学运算。
*   **时间序列数据**:时间序列数据按照定义的时间间隔在特定的时间点进行索引。可以基于基于时间的度量来比较数据。与数字数据的不同之处在于它的时间参考具有开始和结束数据点。
*   文本数据(Text data):文本数据包括可以使用字数统计或情感分析等方法进行分组和分析的单词和句子。

# 开源数据集

机器学习算法通常需要几个数据集来满足考虑各种指标的操作模型的要求。因此，训练和测试数据集用于确保模型的准确性。后续数据集在操作中用于验证和调整机器学习算法。由于下载的数量，一组公共数据集已经被确定为广泛用于机器学习算法。以下列表对机器学习的不同用例进行了分类，并列出可应用于每一类别的数据集的著名示例:

*   **计算机视觉**:谷歌开放图像数据集([链接](https://storage.googleapis.com/openimages/web/index.html)
*   **自然语言处理**:烂番茄复习数据集([链接](https://drive.google.com/file/d/1w1TsJB-gmIkZ28d1j7sf1sqcPmHXw352/view))
*   **情感分析** : IMDB 评论数据集([链接](http://ai.stanford.edu/~amaas/data/sentiment/))
*   **自动驾驶** : Waymo 开放数据集([链接](https://waymo.com/open/))
*   **推荐系统** : MovieLens 评论数据集([链接](https://grouplens.org/datasets/movielens/))

如果著名的开源数据集不符合您项目的要求，您可以使用数据集搜索平台找到合适的数据集，如后面所述。

# Waymo 开放数据集

公开的 Waymo 开放数据集([链接](https://waymo.com/open))是由 Waymo 的自动驾驶汽车收集的传感器数据。该集合是用于训练自动驾驶机器学习模型的最大和最多样化的数据集之一。它包含了美国城市和郊区在不同光照和天气条件下的景观数据。目前的数据集计算了 1950 个片段，每个片段有 20 秒的传感器数据捕捉，这使研究人员可以预测汽车和其他交通参与者的行为。数据是从永久安装的五个激光雷达和五个正面和侧面摄像头收集的。

包含 2 TB 压缩数据的集分块在最大文件数中。25 GB 包含已标记的训练、已标记的验证和未标记的测试数据。训练数据集包括 1260 万个用于激光雷达帧的 3d 盒子，这些盒子带有用于车辆、行人、骑自行车者和交通标志的标签。此外，还提供了 1180 万个 2d 盒子，用于所有带有车辆、行人和骑自行车者标签的摄像机框架。激光雷达和相机标签是独立创建的，互不投影。下图是带有一个已识别车辆 3d 框的激光雷达帧示例([链接](https://github.com/waymo-research/waymo-open-dataset/blob/master/docs/images/vehicle-3D-labeling-example.png))。在图像的左下方，提供了一个合适的相机框架。

![](img/29c2a6b0144a01cedcb793fd8283cb99.png)

Camera frame (left) and lidar frame (right) of a vehicle

凭借其开放的方法，Waymo 积极地为自动驾驶的机器学习的公共研究做出贡献。

# 开源数据集平台

很难找到特定的数据集，在某些情况下，即使是著名的数据集也不适合应用领域。以下列表显示了一些平台，这些平台提供搜索功能来查找适合特定用途的数据集:

*   **谷歌数据集搜索引擎(** [**链接**](https://datasetsearch.research.google.com/) **)** :搜索引擎索引万维网上可用的机器学习数据集。
*   **亚马逊开放数据集(** [**链接**](https://registry.opendata.aws/) **)** :亚马逊的数据注册中心提供 200 个开放数据的数据集，由第三方维护，存储在 AWS 存储上。
*   **微软研究院开放数据(** [**链接**](https://msropendata.com/) **)** :这个数据仓库包含几个主要是自然科学领域的可用数据集。
*   **Kaggle 数据集(** [**链接**](https://www.kaggle.com/datasets) **)** :数据集商店是一个公开可用的平台，拥有超过 66，000 个各种领域的上传数据集。
*   **DATA.GOV 数据集(** [**链接**](https://www.data.gov/)**)**:DATA.GOV 是美国政府提供的超过 20 万数据集的唯一数据。

数据集平台在大小、覆盖的用例、复杂性和质量方面都有所不同。应考虑上述几个平台，以找到合适的数据集。

# Kaggle 数据平台

谷歌子公司 Kaggle 是一个在线平台，可以公开共享用于机器学习和数据分析的数据集。目标群体是来自不同行业的数据科学家、企业和组织，他们对发布数据集和与其他研究人员合作构建机器学习模型感兴趣。数据可以以不同的格式上传，如标记或数据库文件类型。作为核心，该平台提供了一个基于云的环境来计算数据和交换机器学习笔记本。Kaggle 拥有广泛的数据研究社区，允许通过公开讨论和参与数据挑战来交流知识。

# 结论和最终想法

机器学习严重依赖数据进行训练、测试和永久验证。合适数据的可用性对于预测模型的质量以及创建初始模型的工作都很重要。几个著名的数据集被用于创建这样的预测模型，而不需要收集和标记数据。如果著名的数据集不适合，广泛的数据集储存库如 DATA.GOV，数据集搜索引擎如谷歌的数据集引擎，或数据集平台如 Kaggle 可能会有所帮助。

机器学习的未来是一个由企业、公司和机构组成的开放社区，不仅共享数据，还共享知识，共同应对机器学习的挑战。例如，Kaggle 已经提供了一个共享和计算数据以及与其他专家交流知识的平台。

# 进一步阅读

为了更好地理解数据驱动的商业模式，值得考虑下面的阅读材料。

> **数字时代的商业模式(** [**链接**](https://medium.com/@marcelpaulboer/business-models-of-a-digital-era-5a530ccbd52f) **):**
> 不要错过这篇关于数字化转型和数字原生者如何改变商业的文章。随着新兴技术和客户行为的采用，公司表现出各种新的商业模式模式，这些模式面对数字时代的特征。

> **数字经济的数据驱动商业模式(** [**链接**](https://amzn.to/2XnmHll) **):**
> 这本书阐述了快速增长的公司不再依赖于实物资产，而是依赖于市场上公开提供的数字产品。数据是数字商业模式的核心，如何检索这些数据的新方法是竞争市场中的一项战略决策。