# 让数据科学发挥作用的 10 个维度(第 8 部分)

> 原文：<https://medium.datadriveninvestor.com/10-dimensions-of-making-data-science-work-part-8-ff1d672b7571?source=collection_archive---------15----------------------->

## 可扩展性:维度#8

![](img/6f47e76a0a2422b0fce30edb08485f23.png)

Scalability by [Sumit Dutta](https://www.instagram.com/amatuer_chitrakar/)

这是让数据科学发挥作用的 10 个维度系列的第 8 部分。作为一个回顾，我们查看了[第一部分](https://medium.com/the-innovation/10-dimensions-of-making-data-science-work-2057183f0770)**战略**第二部分[第三部分](https://medium.com/the-innovation/10-dimensions-of-making-data-science-work-part-3-cd628818de8c)中的**角色****协作**第四部分中的[以及](https://medium.com/the-innovation/10-dimensions-of-making-data-science-work-part-4-6ae8a7a3823)[第五部分](https://medium.com/the-innovation/10-dimensions-of-making-data-science-work-79778a970498)中的**文化**的软维度，然后开始查看**发现和本系列的第 8 部分涉及一个被认为与数据科学同义的维度，因为它完全是关于利用大数据和人工智能，但在实践中却没有给予必要的重视— **可扩展性**。**

最基本的可伸缩性是系统适应和处理不断增长的需求的能力。在许多情况下，在原子水平上对小范围的世界表现最好的东西需要在真实的世界中以接近实时的速度工作。大多数数据科学函数都擅长在小样本上证明应用程序的概念，或者在玩具问题上复制前沿研究。当同样的人在提出下一个最好的事情之前应用以下问题的透镜时，在这样的功能中的可信度被建立。

> 这个模型在现实世界的生产中需要处理的规模是多少？
> 
> 随着业务的增长，该应用程序需要水平扩展还是垂直扩展？
> 
> 与我们为企业带来的收益相比，我们部署这种模式的成本是多少？

当我们刚刚开始扩展之旅时，我们看到多少数据科学家在创业生态系统中问这些问题？这是一种工作方式和思维方式，不是一朝一夕灌输的，但种子需要在正确的时间播种，以便在可伸缩性的成熟曲线上进行正确的过渡。

# 可伸缩性:这是一种心态

以下是初创公司可扩展性发展的 5 个阶段。这是一个维度，在这个维度中，你在哪里、何时以及是否需要它的问题比一丝不苟地遵循这个维度更重要。

**阶段 1:发现原子—** 在产品上市前的早期阶段，需要扩展的原子产品本身并不明确，可扩展性甚至不是目标。在这个不确定的阶段，尝试想法的原型版本是很常见的，甚至可能是必要的。在这个阶段，利用数据的科学还没有诞生，还谈不上可伸缩性。尽一切努力去理解什么是有效的是咒语。因此，这一阶段的最佳目标是找出需要扩大规模的原子单位。

**第 2 阶段:可扩展的后端—** 这主要是在需要扩展的原子产品有一定程度的清晰度，但数据科学功能尚未开始的阶段。在这一点上，可伸缩性维度对于公司后端系统的技术架构来说比数据科学更重要。充其量，数据的存储和检索需要是可伸缩的。现阶段每个人都应该考虑的关键问题是

*   这个组织的技术蓝图看起来像什么，说明了未来的战略大动作？形成技术蓝图的核心和外围服务基本清晰。
*   我们是否有可扩展的数据存储来捕获我们在扩展时***应该*** 的所有数据？

**阶段 3:访问和建模—** 随着业务的扩展，组织中数据消费者的数量也在增加。因此，在这个阶段，可伸缩性作为一个维度，在支持跨组织访问数据方面是最重要的。这适用于使用正确的架构和模式设计来构建可伸缩的数据存储，以便以可伸缩的方式提供最多查询的指标和事实。自助式仪表盘实际上应该消除了查询大量通用指标的需要。
这也是 v0 模型开始成为几个低挂水果的标准的阶段，这些水果可以用基本的机器学习模型收获。可伸缩性是一个维度，不仅要考虑模型“如何”构建，还要考虑“为什么”构建。问以下问题很重要

*   这个模型有助于实时决策还是批量决策？例如:发送促销电子邮件与展示产品的可用性
*   如果决策是实时的，那么影响模型输出的模型输入是否也在近实时地变化？例如，客户人口统计与客户当前位置
*   我们是需要许多粒度模型来迎合业务的不同部分，还是需要一个适合所有人的模型？

所有这些问题的答案决定了可伸缩性作为一个维度的重要性，以及数据科学家需要戴上的工程帽子的大小。每当上述问题的答案倾向于使用多个模型的近实时功能进行实时决策时，就一定需要考虑模型的计算复杂性、成本和服务架构。我甚至会建议数据科学家参加一个速成班，学习[算法分析、](https://towardsdatascience.com/time-complexity-for-data-scientists-664d00e57724)机器学习[模型部署选项](https://www.kdnuggets.com/2019/06/approaches-deploying-machine-learning-production.html)，以及[机器学习云计算的成本](https://builtin.com/artificial-intelligence/ai-computing-cost-reduction)。

**第 4 阶段:平台化—** 在这一阶段，大多数组织知道自己在可扩展性画布中的位置，并将高速生产机器学习模型，以满足不断增长的业务需求。在这个阶段开始出现的问题是重复和冗余。许多人使用几乎相同的特性为类似的业务问题构建模型，每个模型都消耗人力和机器资源。保持可伸缩性的重要因素是[平台](https://godaramkumar.medium.com/10-dimensions-of-making-data-science-work-part-7-7f1fc08a4477)的前一个维度，它支持创建功能存储、机器学习部署格式和流程的标准化，以及减少重复工作、废弃未使用的模型，并降低每个季度保持可伸缩性的成本。

**阶段 5:可扩展的 ML 即服务—** 在这个阶段，当数据科学模型和洞察分析被构建为一种服务，即即插即用的数据产品时，组织可以称赞自己将可扩展性作为一个维度。随着业务扩展到其他垂直行业，这些 ML 服务作为基础，从一开始就为其他垂直行业构建数据驱动的决策。例如，客户洞察平台提供全方位的客户视图，有助于为新的垂直业务获取客户。

考虑规模不是一种奢侈，而是一种必要，是管理良好的数据科学职能部门以及优秀数据科学家的核心要素。因此，一些组织在数据科学家的工作面试中进行了一轮工程测试。这是一种心态，需要应用到每个数据科学模型或解决方案中，以便在这个维度上成熟。

很快，我们将在本系列的第 9 部分中讨论方法和实践的第九个维度。

*内容与* [*阿南德·夏尔马*](https://medium.com/u/ce87d9792f4a?source=post_page-----2057183f0770--------------------------------) *和* [*马内什·米什拉*](https://medium.com/u/b25fb0a8be01?source=post_page-----2057183f0770--------------------------------) *而在* [*xto10x*](https://medium.com/u/61021e800281?source=post_page-----2057183f0770--------------------------------)