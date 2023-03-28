# 什么是 Kubernetes

> 原文：<https://medium.datadriveninvestor.com/what-is-kubernetes-1db87220f4ba?source=collection_archive---------17----------------------->

## 为什么科技界会为之疯狂？

![](img/fec27b63212d8b28cd5ae821c8345f3e.png)

Kubernetes 不再是一个新奇的事物，但不知何故，它的潜力还远未被开发。直到最近它才开始被大规模采用，并且在云本地计算基金会(CNCF)调查的 78%的企业中已经投入生产。然而在此之前，Kubernetes 并没有真正得到应有的关注。

如果你出于某种原因仍然对 Kubernetes 持怀疑态度，那么现在可能是改变你的想法并加入这些变革者的时候了，而不是努力理解这个平台到底是什么。为了让你更容易理解:下面是 Kubernetes 是什么，以及为什么技术世界对它如此着迷(以及为什么你也应该这样做)。

# Kubernetes 首先是什么？

第一次提到 Kubernetes 可以追溯到 2014 年，Google 的内部容器集群管理器 Borg 和 Omega。从那以后，成千上万的资料都涉及了这个主题——包括 Linux 的历史、容器和许多技术术语。事情是这样的:Kubernetes 相当复杂，但不一定要复杂。

但是，在理解 Kubernetes 之前，您必须熟悉容器。这些是简单的标准软件单元，它们打包了代码及其所有的依赖项、库和配置文件。这样，应用程序可以快速可靠地从一个计算环境运行到另一个计算环境。

虽然容器相对容易掌握和部署，但大规模管理它们却完全是另一回事。如果你必须控制很多容器，那么最好的方法是自动化整个过程，至少在某种程度上是这样。例如，如果没有它，每次有新特性发布时，您都必须手动更新所有这些容器。手工操作不仅耗时，而且容易出错。

在这种情况下，编排工具变得非常受欢迎。**这正是 Kubernetes 派上用场的地方。**这是一个始于谷歌的开源项目，它自动化了容器操作，并使其大规模运行成为可能。有了它，再也不需要执行围绕着手动部署和扩展容器化应用程序的所有过程——有了 Kubernetes，您可以将运行 Linux 容器的主机集群在一起，并轻松高效地管理这些集群。

# 为什么是 Kubernetes？

起初可能看起来不是这样，但 Kubernetes 可能是满足您需求的正确选择——无论您是想要尝试新事物的开发人员还是正在寻找新投资的企业主。原因如下。

*   它可以轻松地配置、自动化和管理容器的调度、创建、删除和移动，结果，一个管理员就可以处理数千个同时运行的容器，
*   它利用了容器的力量，同时简化了集群中服务和机器的管理。另外，Kubernetes 集群允许将工作负载部署到整个集群，而不是特定的服务器，
*   集群还跨越本地、公共、私有或混合云的主机，这就是为什么 Kubernetes 被称为托管需要快速扩展的云原生应用程序的理想平台。
*   与此同时，Kubernetes 为开发人员提供了更高的效率——devo PS 团队可以轻松地将应用打包到一个容器中，并在不同的平台上一致地部署它，因此不需要等待很长时间来进行机器供应，
*   此外，Kubernetes 可以节省大量的基础设施和维护成本，有助于更好地利用硬件和运行应用程序所需的所有资源，
*   更不用说 Kubernetes 还有监控和自愈能力——比如当一个容器崩溃时，会自动创建一个新的。

这些好处足以让科技界对 Kubernetes 感到兴奋吗？绝对的。

当企业在寻找改进应用程序开发方式的方法时，他们必然会发现 Kubernetes。这源于这样一个事实:越来越多的企业开始接受容器——这是理所当然的。然而，在某种程度上，他们需要强大的方法来适当地扩展和管理它们。【Kubernetes 让这一切成为可能。

事实上，完全自动化容器化应用编排的能力是 [83%接受调查的技术专家](https://www.cncf.io/blog/2018/08/29/cncf-survey-use-of-cloud-native-technologies-in-production-has-grown-over-200-percent/)选择 Kubernetes 的原因。在早期，这可能只是一种宣传——但毫无疑问，它现在已经被广泛采用。多年来，它不仅变得更加“严肃”和稳定，而且还可用于各种商业模式。

然而，与此同时，企业已经意识到利用 Kubernetes 需要特定的技能。这可能是为什么短短几年内 Kubernetes 的求职份额增加了 2125%的原因之一。对该平台的更高需求和兴趣也促进了 Kubernetes 周围社区的增长，一年一度的 KubeCon 会议从一个相对较小的活动发展成为一个有数千人参加的全球聚会。

毫无疑问，科技界正在为 Kubernetes 而疯狂——这可能也是你为之兴奋的恰当时机。

# Kubernetes 与公共云平台

准备好利用 Kubernetes 吗？从技术上讲，您可以自己安装和管理一切，但此时，选择托管解决方案会更容易、更快。尤其是因为 Kubernetes 的托管服务现在由最大的公共云平台(如 AWS、Google Cloud 和 Azure)提供。自己看吧:

1.  [**亚马逊弹性集装箱服务(EKS)为 Kubernetes**。如果您已经将 AWS 用于其他用途，那么您应该选择此选项。事实上，许多企业已经信任 EKS 来运行他们最敏感和最关键的应用程序，主要是因为它的安全性、可靠性和可扩展性。](https://aws.amazon.com/eks/)
2.  [**Azure Kubernetes 服务(AKS)**](https://azure.microsoft.com/en-gb/services/kubernetes-service/#features) 则是在 Azure 上使用 Kubernetes 的最快方式。它使得定义、部署、调试和升级最复杂的 Kubernetes 应用程序成为可能，加速了世界上许多团队的容器化应用程序开发。
3.  [**Google Kubernetes**](https://cloud.google.com/kubernetes-engine)**Engine**也是一个受欢迎的选择，有助于开发各种支持有状态、无服务器和应用加速器的应用，允许使用 Kubernetes-native CI/CD 工具来保护和加速构建和部署生命周期的每个阶段。

这还不是全部。很明显，云市场的主要参与者都以这样或那样的方式支持 Kubernetes，这应该是一个足够好的尝试理由。

# 尝试 Kubernetes 的正确时间是现在

Kubernetes 在 Google 有十多年运行容器化应用程序的经验。然而，更重要的是，它一直在进化。

在这个过程中，最大的公共云供应商、技术提供商以及许多软件供应商和企业已经接受了它，或者正在计划这样做。你也准备好加入他们了吗？

# 你可能也会喜欢

[如何使用 AWS、IaaS、IaaC 和 CICD 创建自动化流程](https://scalac.io/automation-process-using-aws-iaas-iaac-and-cicd-orchestration/)
[如何管理远程员工](https://medium.com/scalac/how-to-manage-remote-employees-7644703991cb)

*原载于 2020 年 4 月 22 日*[*https://scalac . io*](https://scalac.io/what-is-kubernetes/)*。*