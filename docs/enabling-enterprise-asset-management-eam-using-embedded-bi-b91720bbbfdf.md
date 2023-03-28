# 使用嵌入式 BI 实现企业资产管理(EAM)

> 原文：<https://medium.datadriveninvestor.com/enabling-enterprise-asset-management-eam-using-embedded-bi-b91720bbbfdf?source=collection_archive---------2----------------------->

称之为嵌入式分析或嵌入式 BI，嵌入式技术将继续存在，并为我们提供更好的数据洞察力。随着 2020 年的到来，越来越多的企业开始采用嵌入式 BI 解决方案，以适应数字化转型的优势。

无论是对前端客户体验的影响，还是为后端运营提供动力，或者是与第三方企业级工具的集成，嵌入式分析都可以为企业带来很多好处。

![](img/5273c8aaa448ed02c844660426560b23.png)

由 Aberdeen Group 进行的一项研究显示，53%的 BI 解决方案提供商正在他们的定制解决方案中嵌入分析。这种能力对于非技术用户特别有用，因为他们不再需要切换到外部工具来提取 BI 驱动的洞察力或可视化。例如，支持嵌入式 BI 分析的全球活动管理公司 [EEG Events Group](https://www.sisense.com/case-studies/eeg/) 为其客户提供反映活动表现及其业务影响的活动后综合报告。

[](https://www.datadriveninvestor.com/2019/01/25/why-data-will-transform-investment-management/) [## 为什么数据将改变投资管理|数据驱动的投资者

### 有人称之为“新石油”虽然它与黑金没有什么相似之处，但它的不断商品化…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/25/why-data-will-transform-investment-management/) 

在余下的章节中，我们将了解嵌入式 BI 如何与企业资产管理(或 EAM)协同工作，以及如何着手**将嵌入式 BI 和分析与 EAM** 集成。

# 什么是嵌入式 BI？

根据 Gartner group 的说法，嵌入式分析或嵌入式商业智能是在交易应用程序中使用分析或 BI。虽然 BI 功能可以驻留在本地应用程序之外，但在嵌入式分析中真正重要的是可以从任何业务应用程序轻松访问它。

嵌入式 BI 分析对任何数据或业务分析师来说意味着什么？他们现在可以直接利用任何业务软件的 BI 功能或优势，而无需打开单独的用户界面。

![](img/5e0a9f6e7b6e71167f76f0c7abd6cdcb.png)

一个典型的例子是微软的 Power Bi 嵌入式工具。[嵌入式 Power BI](https://docs.microsoft.com/en-us/power-bi/developer/embedding) 使解决方案提供商或开发人员能够向甚至没有 Power BI 帐户的用户嵌入并提供对高质量 BI 报告和仪表板的访问。

那么，嵌入式 BI 有哪些业务优势呢？

*   降低业务成本，因为嵌入式商务智能解决方案比独立的商务智能解决方案更具成本效益。已经投资了其他业务解决方案的企业可以通过将它们与嵌入式分析相集成来利用它们的投资。
*   由于嵌入式 BI 工具与其他软件工具的无缝集成能力，数据处理速度更快。这可以在单个用户界面中简化与数据相关的任务。
*   提高数据分析师的整体工作效率，因为他们不必在多个应用程序和界面之间切换来完成任务。例如，通过将嵌入式分析与 CRM 系统结合使用，数据分析师可以在短时间内生成最新的销售报告。

在下一节中，我们将了解将嵌入式 BI 和分析与 EAM 系统集成的流程。

# 嵌入式商务智能如何与 EAM 协同工作

企业资产管理(Enterprise Asset Management)的简称，EAM 技术公司正在实现更好的跨地点和业务部门的组织控制和资源管理。这些资源包括:

*   机械、制造工厂和车辆等有形资产。
*   互联物联网或物联网设备、运营应用、供应链和维护管理系统等技术资产。
*   人力资源管理和员工生产力工具等人力资产。

像 IBM Maximo 这样的 EAM 工具和解决方案正在使用人工智能和嵌入式分析来延长资产的生命周期并降低维护成本。例如，使用联网的物联网设备，这种 EAM 工具可以实时收集数据，然后使用分析工具来衡量所有资产的可用性和使用情况。

虽然 EAM 工具可以最大限度地降低成本并提高业务价值，但嵌入式分析可用于识别业务运营中的新机遇(例如，设备重新分配)。

如何将嵌入式 BI 与 EAM 集成在一起？我们来讨论一下这个过程。

# 将嵌入式 BI 与 EAM 集成

像 maintenance 这样的 EAM 工具允许企业简化他们的维护流程。作为数据分析师，您可以在各种其他应用程序中使用 maintenance 的自定义数据报告功能。此外，通过将嵌入式 BI 和分析工具(如 [Power BI](https://powerbi.microsoft.com/en-us/) )与此 EAM 工具集成，您可以使用 Power BI 来创建大型数据仓库的可视化。

同样定位为计算机化维护管理系统(或 CMMS)，以下是如何将嵌入式 Power BI 工具与维护 EAM 工具相集成:

1.  登录您的维护帐户并获取会话令牌。
2.  登录到您的 Power BI 帐户，并使用会话令牌从 maintenance 配置 API 调用。
3.  在下一步中，使用 Power BI 工具获取维护收集的数据。
4.  根据从维护和其他应用中收集的数据，创建定制的 Power BI 仪表盘。
5.  使用 Power BI 中的[维护 API](http://developers.onupkeep.com/) ，连接软件工具和数据库之间的数据流。

通过这五个步骤，您已经将 Power BI 工具与 maintenance EAM 工具集成在一起。接下来，我们将看到将嵌入式 BI 和分析与 EAM 集成的价值和优势。

# 嵌入式商业智能和分析如何实现更好的 EAM？

嵌入式分析如何改进 EAM 流程？以下是嵌入式分析和商业智能的三个共同趋势，可以让任何企业受益:

## 将数据作为一项功能集成到任何应用程序中

无论是 EAM 还是任何其他流程，应用程序都越来越依赖于可用的业务数据。嵌入式分析将数据无缝集成到任何应用程序中，并在需要时交付给数据分析师。

除了更快的数据处理，数据可用性对于任何 EAM 工具的成功都至关重要，并致力于提供更好、更直观的用户体验。

## 利用数据科学模型提供的数据

构建有效的数据科学模型是一回事，但将这些模型的发现用于业务是另一个挑战。集成了数据科学模型的嵌入式分析可以顺利地向业务用户提供数据驱动的洞察。

嵌入式 BI 可以从数据科学模型中获取输出，并通过嵌入在单个应用程序界面中的 BI 报告和可视化来共享它们。

## 与云计算架构有效配合

企业越来越多地部署轻量级、可作为微服务执行的云架构。对于高效的[云分析](https://issuu.com/countants/docs/business_benefits_of_cross_domain_tracking_using_g)，将重量级 BI 应用集成到这样的架构中是不可行的。因此，BI 服务提供商正在部署使用嵌入式分析的小型 BI 微服务。

除了这些业务优势之外，商业企业还可以寻求多种策略来充分利用嵌入式分析的最大价值。这些战略包括:

*   跨数据库报告，围绕 BI 工具从多个数据源收集数据，包括像 Microsoft Azure、MySQL 和 Oracle 这样的数据库系统。
*   为更好的报告进行数据准备，利用分析来收集、清理和组织从不同系统检索的数据。这一策略确保业务用户从生成的 BI 报告中获得最多的洞察力。
*   确保数据质量，确保业务主管能够纯粹根据良好的数据做出决策。数据质量策略从分析流程中消除任何不良或非结构化数据。
*   基于用户角色提供数据可访问性，防止业务用户访问与其功能需求无关的数据。低效的数据可访问性会中断数据分析并导致合规性问题。
*   通过使用被认为是鼓励采用数据分析的最佳模式的嵌入式分析，在组织中创建数据驱动的文化。简而言之，嵌入式 BI & analytics 利用了 BI 的优势，同时将用户限制在他们的应用程序工作流中。

# 结论

由于业务数据很容易获得，任何企业都可以收集和分析这些数据，以获得洞察力和最大的竞争优势。嵌入式分析的出现使企业用户能够在使用包括 EAM 在内的第三方应用时无缝地获得洞察力。

凭借其在[云分析](https://www.countants.com/blogs/heres-how-you-can-configure-automatic-imputation-of-missing-data/?utm_medium=social&utm_source=Medium&utm_campaign=traffic)和[商业智能](https://www.countants.com/blogs/leveraging-business-intelligence-for-sales-and-marketing-initiatives/?utm_medium=social&utm_source=Medium&utm_campaign=traffic)方面的专业知识，Countants 正在为希望从[谷歌分析](https://www.countants.com/blogs/conversion-analysis-in-datalab-with-google-analytics-data/)和其他分析工具的投资中获得最大回报的客户提供价值。

[现在就联系我们](https://www.countants.com/contact-us/?utm_medium=social&utm_source=Medium&utm_campaign=traffic)定制商务智能解决方案，专门满足您的业务需求。