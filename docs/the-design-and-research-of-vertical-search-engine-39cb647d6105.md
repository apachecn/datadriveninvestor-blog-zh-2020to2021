# 垂直搜索引擎的设计与研究

> 原文：<https://medium.datadriveninvestor.com/the-design-and-research-of-vertical-search-engine-39cb647d6105?source=collection_archive---------5----------------------->

## 垂直搜索引擎系统旨在收集关于大数据的架构、信息收集和索引建立的信息

![](img/561b3a68642301352f7ec10008c8d40a.png)

Photo by [Markus Spiske](https://www.pexels.com/@markusspiske?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels) from [Pexels](https://www.pexels.com/photo/screen-web-design-developing-codes-1936299/?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels)

# 这篇文章主要是关于什么的？

本文重点研究如何从数百亿的海量网页和文档中准确定位所需内容，以满足用户对专业和深入知识的需求，并具体到通信行业的招标信息，研究如何实现全面的数据收集，核心是搜索引擎对分类客户进行清洗、聚类和快速反馈。

本文通过研究垂直搜索引擎的关键技术，实现了通信行业招标领域的网页信息采集，将非结构化内容与结构化数据分析技术相结合，实现了准确全面的全文索引和联合检索技术，帮助用户快速定位到想要的搜索结果。

# **让我们从介绍开始**

随着社会进步和大数据时代的到来，各个行业都迎来了新的机遇和挑战。其中，如何利用新一代信息技术来提高行业的工作水平已经成为迫切需要。

> **以通信行业招标为例**

目前合法适用项目的中标率超过 90%。然而，随着招标范围和规模的扩大，招标效率低、周期长的问题越来越明显。

而传统的“招投标方式”是由专人查询各省级政府、公共资源交易中心、泛运营商官方网站上发布的招投标信息。

它正在等待多种类型的投标。很难从海量信息中准确定位并获取适应性强的相关信息。

在等待招标信息公告和有效过滤垃圾信息的过程中，造成人力、时间、财力的巨大浪费。

总的来说，存在“科学确定采购需求难、信息搜索成本高、数据价值开发率低等问题”。

> 大数据技术在招投标行业的应用可以快速打破相关限制

结合搜索引擎技术，可以将分散在各地、运营商网站的所有招标信息、中标查询信息整合到数据库中。

并且根据地域、行业、金额、时间等各种关键词进行分类，用户无需逐一守护多个网站信息，即可获得全国各地的各种旗帜，还可以通过关键词主动获取分类查询和订阅信息推送。

# 什么是搜索引擎？让我们从搜索引擎的历史开始

通用搜索引擎的出现大大提高了互联网信息搜索的便利性，但通用搜索引擎已经不能满足行业用户对个性化信息检索服务的需求，于是出现了面向特定领域的垂直搜索引擎。

> **搜索引擎技术经历了三代重大技术发展**

1。第一代是以雅虎为代表的人工目录分类和导航技术，但在实际搜索结果的相关性和排序的合理性上存在严重的劣势。

2。第二代是 Google 作为代表性的文本处理技术，在检索呈现层面引入了排名优化方法，准确率、检索率、检索率都比第一代有了很大的提升。

3。第三代是基于百度、搜狗、Wolfram Alpha 的智能搜索引擎，通过综合运用人工智能、数据挖掘、模糊匹配、神经网络、数学分析等技术，更精准地满足了目标用户的实际使用需求，取得了良好的综合效益。

*垂直搜索引擎技术是第三代技术的核心。*

[http://gph.is/2EgXmz5](http://gph.is/2EgXmz5)

# **垂直搜索引擎的发展**

垂直搜索引擎(vertical search engine，VSE)是针对某个行业的专业搜索引擎。它是搜索引擎的细分和延伸。

它是网页库中某一类专门信息的集成。数据经过处理，然后以某种形式返回给用户。它也被称为专业搜索引擎或主题搜索引擎。

与通用搜索引擎相比，垂直搜索为特定领域、特定人群或特定需求提供有价值的信息和服务。

其特点是“专、精、深”，具有行业色彩。垂直搜索引擎涉及信息索引、机器学习、数据挖掘和自然语言处理等各个领域的知识和技术。

它们是高度综合和高度专业化的。然而，他们广泛应用于界面管理数据，一个优秀的垂直搜索引擎不仅需要专业的技术背景，还需要相关的行业经验。

垂直搜索引擎技术未来的发展方向集中在如何提高信息检索结果的准确性、基于智能代理的信息过滤和个性化服务、全面的相关信息搜索、与分布式架构的结合使用以及面向民族和国家研究的本地化、多语言搜索应用等方面。

[](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) [## 机器学习和人工智能如何改变电子商务的面貌？|数据驱动…

### 电子商务开发公司，现在，整合先进的客户体验到一个新的水平…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/11/19/how-machine-learning-and-artificial-intelligence-changing-the-face-of-ecommerce/) 

# **垂直搜索引擎系统设计思路**

将项目管理知识系统应用于通信行业招投标领域，提出了招投标开放引擎系统(BOES)开放式知识组织引擎。

BOES 的总体框架包括存储和索引层、查询和推理功能层、BOES API 层和开放查询和推理接口层。

它利用语义存储、索引、查询、推理和接口技术，构建了存储索引系统、语义查询和推理内核，支持实现招投标行业各种要素的检索、浏览、关联、导航等功能。

基于 BOES，基于 BOES 数据特点，开发 APP 应用服务平台，构建高性能、可靠的知识存储索引系统和 BOES 搜索查询、语义推理内核引擎，支持信息推送服务，提供封装的 API 接口供第三方系统使用。

[https://gph.is/g/E0xyKjy](https://gph.is/g/E0xyKjy)

# **垂直搜索引擎系统的架构设计**

垂直搜索引擎系统架构分为表示层、逻辑业务层和数据访问层。各层之间的数据信息传输由接口完成。

1。表示层位于最外层，直接与用户交互，负责接收用户输入的“搜索”信息，并显示搜索结果。

2。业务逻辑层是整个系统的核心部分，实现过滤数据、抓取 web 信息、索引、管理系统等功能。它位于数据访问层和表示层之间。数据信息的交换具有上承上启下的联系。

3。数据访问层访问主题网页信息数据库、用户和管理员信息数据库等。，并为逻辑层业务和表示层提供数据支持。

# **信息采集模块设计**

该模块完成网页信息的采集，是整个系统的基础和重点，包括 **9 个**子模块共同实现整体功能:

1。叙词表子模块:负责行业和领域叙词表的选择，建立并形成叙词表。

2。链接种子采集子模块:负责获取多个与主题相匹配的链接，作为数据抓取的开始。

3。网页下载子模块:负责完成网页的下载工作。

4。网页解析子模块:负责完成爬虫配置、网页内容提取、链接定位。

5。内容相关性判断子模块:负责完成分类器的训练，然后使用训练好的分类器对抓取的网页内容进行过滤，过滤掉与人工智能主题无关的网页。

6。主题相关性评估子模块:负责使用 PageRank 算法计算链接的 PR(链接的高低值)值，将 PR 值高的保留为网页链接继续爬行，使爬虫工具每次都能爬行到有价值的网页信息。

7。链接管理子模块:负责抓取链接的管理和去重。

8。数据存储子模块:负责将提取的符合主题要求的信息保存到数据库中。

9。爬虫启动模块:负责创建蜘蛛对象，启动爬虫。

[https://gph.is/2C49Jym](https://gph.is/2C49Jym)

# **指标构建模块设计**

该模块主要负责分词和标引，并能根据需要提供智能处理功能，如自动分类、自动聚类、自动标引、自动排序、文本挖掘等。

作为 Apache 下的顶级开源项目，Solr 是基于 Lucene 的全文搜索服务器，提供了比 Lucene 更丰富的查询语言。它可以在 Jetty 和 Tomcat 等 Servlet 容器中独立运行。

该模块的具体流程分为客户端使用 POST 方法向 Solr 服务器发送描述字段及其内容的 XML 文档。

Solr 服务器基于 XML 文档添加、删除、更新索引创建索引过程，客户端使用 GET，该方法向 Solr 服务器发送请求，然后解析 Solr 服务器返回的 XML、JSON 等格式的查询结果的搜索索引过程。

该系统在 Solr 中增加了分词项目，集成了 IK Analyzer 分词器，实现了数据表信息的分词，并将 Solr 与数据库连接，创建了数据表的倒排索引。

索引建立完成后，通过发送包含查询关键字、语法版本和返回结果数量等参数的 HTTP 请求进行查询。Solr 收到请求后，以 XML 的形式响应结果。

# **在招投标领域的应用**

本文结合垂直引擎系统的关键技术、查询优化和推理策略的关键技术，以及招投标行业综合服务平台的研发技术，研发一个融合行业特色、定位企业精准需求、服务企业金融的综合移动服务平台。

招标大数据平台系统对招标采购过程中的各种数据进行记录和分析，建立数据分类模型，对数据进行深入计算，形成数据集。

在此基础上，构建招投标大数据资源，让招投标采购行业的数据从封闭的系统中迁移到开放的平台上，实现自动化推送服务。

# **总结**

解决有效招标领域采购需求难以科学确定、信息搜索成本高、数据价值开发率低等问题。

基于 BOES 的垂直引擎系统，基于 Solr 的全文检索索引，基于这样的关键技术的通信行业综合招投标服务平台。

我们开发了一个集行业特色、全面覆盖、企业需求精准定位、企业金融服务于一体的综合移动服务平台。

平台系统对招标采购过程中的各种数据进行记录和分析，建立数据分类模型，对数据进行深度计算，形成数据集。

在此基础上，构建招标采购大数据资源库，使招标采购行业数据从封闭系统走向开放系统。该平台实现了自动推送服务，取得了良好的效果。

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)