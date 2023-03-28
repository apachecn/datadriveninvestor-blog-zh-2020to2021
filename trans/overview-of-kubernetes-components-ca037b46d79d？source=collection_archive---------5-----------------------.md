# Kubernetes 组件概述

> 原文：<https://medium.datadriveninvestor.com/overview-of-kubernetes-components-ca037b46d79d?source=collection_archive---------5----------------------->

Kubernetes 组件概述

> 什么是 Kubernetes，它的组成部分是什么？嗯…

## 开始…

本文将简要概述 Kubernetes 及其不同的组件。

> 注意:本文的主要焦点是 Kubernetes 的组件。

![](img/1278a55bc9962223e6d0057d4af016f2.png)

Overview of Kubernetes Components

## 什么是 Kubernetes？

根据[官网](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/)

![](img/8e83fda35fbe3f4db4c9edd36494bdaa.png)

Overview of Kubernetes Components

> Kubernetes 是一个用于管理容器化工作负载和服务的开源平台。它的一些功能包括:

*   **服务发现和负载平衡:**它可以使用 DNS 名称或使用自己的 IP 地址来公开容器，如果容器的流量很高，Kubernetes 可以平衡和分配网络流量。
*   **存储协调:** It 允许您自动挂载自己选择的存储系统，比如本地存储、公共云提供商等等。
*   **自动化的推出和回滚:**自动化 Kubernetes 为您的部署创建新的容器，删除现有的容器，并将它们的所有资源应用到新的容器中
*   **自我修复:**重新启动失败的容器，替换容器，终止不响应用户定义的健康检查的容器
*   **秘密和配置管理:**允许您存储和管理敏感信息，比如密码、OAuth 令牌和 SSH 密钥

## 为什么受欢迎？

![](img/c67dc96702633fb676ca4cf923a89cbd.png)

Overview of Kubernetes

**传统部署**:早期，组织在物理服务器上运行应用程序。没有办法为物理服务器中的应用程序定义资源边界，这导致了资源分配问题

**容器部署**:容器被认为是轻量级的。与 VM 类似，容器有自己的文件系统，共享 CPU、内存、进程空间等等。因为它们与底层基础设施相分离，所以它们可以跨云和操作系统发行版进行移植。

其他因素:

*   在前一段时间，随着微服务趋势的增长，公司开始部署越来越多的微服务。
*   没有合适的方法来管理它们。

## DevOps 的崛起

![](img/1c89804a25f08220438a969f76779026.png)

Kubernetes 介绍了 DevOps。没有 Kubernetes，软件开发团队需要写下他们自己的软件部署，手动扩展，并更新工作流。在大型企业中，DevOps 处理这项任务。

## Kubernetes 组件

![](img/730133779d0f3bd80a5cffaa98cdb758.png)

Overview of Kubernetes

**Pod:**

*   库伯内特的最小单位(K8s)
*   它是容器的抽象
*   同一 pod 中的任何容器将共享相同的资源和本地网络。
*   容器可以很容易地与同一个 pod 中的其他容器通信。
*   每个 pod 都有自己的 IP 地址，当一个 pod 死亡时，会分配一个新的 IP 地址。
*   豆荚是 K8s 的复制单位。如果您的应用程序变得流行，并且单个 pod 实例不能承载负载，那么 Kubernetes 可以被配置为将您的 pod 的新副本部署到集群。

![](img/a8b0d7f0151e80e5959efd631b5356a6.png)

Overview of Kubernetes Components | Pods

**服务:**

*   Kubernetes 为一组 pod 提供它们自己的 IP 地址和一个 DNS 名称，并可以在它们之间进行负载平衡。
*   客户端向稳定的 IP 地址发送请求，请求被路由到服务中的一个 pod。
*   pod 和服务的生命周期没有联系。因此，如果一个 pod 死亡，它的服务不会受到影响。
*   该组件本身是一个负载平衡器。
*   一个服务用一个选择器来标识它的成员 pod。要使 Pod 成为服务的成员，它必须具有选择器中指定的所有标签。

![](img/17853d95a86cc7e976e3700f9783a04f.png)

Overview of Kubernetes Components| Service

**卷:**

容器中的磁盘上文件是短暂的(*持续很短的时间*)，这给在容器中运行的重要应用程序带来了一些问题。

问题:

1.  容器崩溃时文件丢失。kubelet 重新启动容器，但是是一个干净的石板。
2.  在一起运行的容器之间共享文件。

> 输入音量

*   用于保存数据。Kubernetes 保证数据在容器重启时得到保存。
*   这是一个包含一些数据的目录，可由 pod 中的容器访问。
*   有不同类型的卷[可用](https://kubernetes.io/docs/concepts/storage/volumes/#awselasticblockstore)
*   一个 [](https://kubernetes.io/docs/concepts/workloads/pods/) pod 可以同时使用任意数量的卷类型。临时卷类型具有 pod 的生存期，但永久卷的生存期会超过 pod 的生存期。

**配置图:**

![](img/cfbdccc13247e525ce80482ab082443b.png)

Overview of Kubernetes Components | ConfigMap

*   配置映射使您能够将配置从 pod 和组件中分离出来。
*   这使得 pod 配置更易于更改和管理，并防止将配置数据硬编码到 Pod 规格。
*   让我们将配置数据与应用程序代码分开设置。
*   将非机密数据存储在键值对中。
*   pod 从这个配置图中读取数据。

> 注意:要在集群中使用敏感信息，必须使用 Secrets。

**秘密:**

![](img/54f6c8d01dea34f28f4874edbd753e5e.png)

Overview of Kubernetes Components | Secrets

*   **秘密**是存储敏感数据的安全对象，比如密码、OAuth 令牌和 SSH 密钥。
*   使用机密降低了将数据暴露给未授权用户的风险。
*   存储的值是 base64 编码的。

> 注意:在 K8s 中，默认情况下不启用内置安全机制

**部署:**

*   虽然 pods 是 k8s 中的基本计算单位，但是它们是由一个抽象层来管理的:[部署](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)。
*   指定 pod 蓝图的组件。
*   用于创建无状态应用程序。
*   大多数情况下，您将不会使用 pod，而是使用部署。
*   部署的主要目的是声明一次应该运行多少个 pod 副本。
*   如果一个 pod 失效，部署将自动重新创建它。

**入口**:

您可以创建一个节点集群，并在集群上启动 pod 部署。但是，我们需要允许外部流量进入您的应用程序。

> 进入入口

![](img/d147ed22aec8b32d490798836e638ee8.png)

Overview of Kubernetes Components| Ingress

*   将 HTTP 和 HTTPS 路由从群集外部公开给群集中的服务。
*   来自外部世界的请求首先到达入口。
*   入口定义了流量路由规则，并将请求转发给适当的服务。

有多种方法可以向集群添加入口。最常见的方法是添加一个[入口](https://kubernetes.io/docs/concepts/services-networking/ingress/)控制器或一个[负载平衡器](https://kubernetes.io/docs/tasks/access-application-cluster/create-external-load-balancer/)。

> 注意:客户端可以是网络浏览器、移动设备等。

**有状态集合:**

如果您在 Kubernetes 上部署任何有状态的应用程序，您将需要确保 pods 可以通过不变的唯一身份(主机名、IP…等等)相互联系。).

> 输入有状态集合

*   它负责创建有状态的应用程序，例如 MySQL clusters、Redis、Kafka、MongoDB 等。
*   为它的每一个豆荚保持一个粘性的身份。每个 pod 都有一个永久标识符。

![](img/e998dd8853ed25154edc176e973293e7.png)

Overview of Kubernetes Components | Stateful Set

*   像 Nginx 这样的无头服务控制着网络域。

**持续音量:**

在群集上运行的程序不能保证在特定的节点上运行。如果一个程序试图将数据保存到一个文件中以备后用，但随后被重新定位到一个新的节点上，那么该文件将不再位于程序期望的位置。

> 输入持久卷

![](img/c5ec886a9d0d707a2540bd116eb0a05c.png)

Overview of Kubernetes Components | PersistentVolume

*   为了永久存储数据，Kubernetes 使用了[持久卷](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)。
*   *持久卷* (PV)是集群中的一块存储。
*   PV 独立于 pod 生命周期。
*   它们提供了一个可以挂载到集群的文件系统，无需与任何特定的节点相关联。

**持续量声明**:

*   PVC 是为永久存储提供特定类型和配置的请求。
*   应用程序要求 PV 使用 PVC

**存储类**:

*   要指定您想要的持久存储风格，您可以使用 [Kubernetes 存储类](https://cloud.ibm.com/docs/containers?topic=containers-kube_concepts#storageclasses)。
*   当您创建 PVC 时，请求会发送到存储提供商。
*   根据存储类中定义的配置，在您的应用程序中订购和配置物理存储设备。
*   如果请求的配置不存在，则不会创建存储。

![](img/eaa3af6a8fab6494e77aef58f45df626.png)

Overview of Kubernetes Components | Storage

有趣的阅读:

[](https://medium.com/google-cloud/kubernetes-110-your-first-deployment-bf123c1d3f8) [## Kubernetes 110:您的首次部署

### 如果你读过我对 Kubernetes 的介绍，你应该对基本的部分有一个很好的基础理解…

medium.com](https://medium.com/google-cloud/kubernetes-110-your-first-deployment-bf123c1d3f8) [](https://medium.com/better-programming/3-years-of-kubernetes-in-production-heres-what-we-learned-44e77e1749c8) [## 3 年的 Kubernetes 生产——以下是我们学到的东西

### 从我们的 Kubernetes 期刊中获得的关键信息

medium.com](https://medium.com/better-programming/3-years-of-kubernetes-in-production-heres-what-we-learned-44e77e1749c8)