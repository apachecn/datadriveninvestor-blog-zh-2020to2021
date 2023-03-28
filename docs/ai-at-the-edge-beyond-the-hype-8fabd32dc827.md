# AI 在边缘，超越炒作！

> 原文：<https://medium.datadriveninvestor.com/ai-at-the-edge-beyond-the-hype-8fabd32dc827?source=collection_archive---------2----------------------->

![](img/bc5283397074479d95f0efe219b81db0.png)

## 边缘的人工智能利用了一种紧凑的架构，但它提供了一种令人难以置信的计算方法，试图推动曾经主要基于云的本地数据知情决策。

从 20 世纪 70 年代的第一台网络自动取款机，到 90 年代的万维网，再到 21 世纪初的智能电表，我们已经走过了漫长的道路。近年来，云计算得到了很多新闻，但随着物联网(IoT)池的不断扩大，这一边缘也变得越来越重要。据英特尔的[称，物联网设备已从 2006 年的 20 亿台增长到 2020 年的预计 2000 亿台。](https://www.intel.com/content/www/us/en/internet-of-things/infographics/guide-to-iot.html)

然后像任何其他领域一样，物联网也不会被排除在人工智能(AI)的用例之一之外，据 [Tratica](https://www.tractica.com/newsroom/press-releases/artificial-intelligence-edge-device-shipments-to-reach-2-6-billion-units-annually-by-2025/) 称，全球人工智能边缘设备的数量预计将从 2018 年的 1.614 亿台跃升至 2025 年的 26 亿台。

[](https://www.datadriveninvestor.com/2019/03/22/living-life-on-the-edge/) [## 生活在边缘|数据驱动的投资者

### 为边缘和混合计算而重新设计的旧思想这是一种数据抓取！感觉每个行业的每个人…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/03/22/living-life-on-the-edge/) 

*看完这些庞大的数字，相信你已经有兴趣了解更多这个话题了！:D*

在本帖中你会得到以下问题的答案:
*—什么是 AI 在边缘？
—为什么边缘的 AI 很重要？
—与云计算有何不同？
—已经在用的 AI 在边缘的应用都有哪些？
—何时选择基于边缘的应用而非基于云的应用？
—在边缘从事 AI 软硬件开发的都是些什么人？
—边缘计算会取代云计算吗？*

# 但是人工智能在边缘的真正含义是什么，为什么需要它？

许多使用云的应用程序在本地获取数据，将数据发送到云，处理数据，然后再发送回来。边缘意味着不需要发送到云；它通常更安全(取决于边缘设备的安全性),对网络的影响和依赖性更小。因此，**“边缘”意味着局部(或接近局部)加工**。这可以是实际的本地设备，如智能冰箱，或者尽可能靠近源的服务器(即位于附近区域而不是世界另一端的服务器:P)。

出于以下原因，需要边缘的 AI，

*   **网络影响** —网络通信可能非常昂贵(带宽、功耗等。)有时是不可能的(想想偏远地区或自然灾害期间)
*   **延迟考虑** —实时处理是应用程序所必需的，这些应用程序在做出重要决策时无法处理延迟
*   **安全问题**——边缘应用程序可能会使用个人数据(如健康数据),这些数据如果被发送到云端可能会很敏感
*   **针对本地接口的优化** —专为特定硬件定制的优化软件可以帮助 edge AI 模型实现更高的效率

谷歌的 Learn2Compress 等模型压缩技术的影响也有助于人工智能边缘处理的兴起，该技术能够将大型人工智能模型压缩到小型硬件外形中。

联合学习和基于区块链的分散式人工智能架构也是人工智能处理向边缘转移的一部分，部分训练也可能转移到边缘。

**那么，什么时候选择 edge 应用呢？**

![](img/ed1a156890d186cfe4eeaad147edb3a9.png)

*   **当需要实时决策时，以及**
*   **需要低延迟(最小延迟)的地方，以及**
*   **网络本身可能不总是可用的地方**

![](img/f81e4f8e4592883aec304260730d0ca5.png)

A self-driving car taking the complex decision on the edge

让我们以自动驾驶汽车或任何自动驾驶车辆为例，稍微详细地了解一下边缘应用。这种车辆需要像摄像头、雷达和激光这样的传感输入设备，以使车辆能够感知周围的世界，根据对收集的数据的分析，在飞行中做出复杂的决策。你怎么看，自动驾驶汽车最有可能使用云还是在边缘运行？

如果你的答案是，在边缘，就拍拍你的背！为什么？想一想，自动驾驶汽车是否有能力在行驶过程中等待发送数据和接收来自云端的分析报告？如果有几毫秒的网络延迟会怎样？

还有许多其他例子，我们在不知不觉中使用了 Edge AI。从谷歌地图提醒你糟糕的交通状况，到你的智能冰箱提醒你购买一些缺失的乳制品，到你的智能手机识别你的脸来解锁虚拟助手，如 Alexa、Siri、Cortana、谷歌助手，Edge-AI 在我们身边无处不在。

根据人工智能应用和设备类别，有几种硬件选项可用于执行人工智能边缘处理。这些选项包括 CPU、GPU、TPU、专用集成电路(ASICs)、现场可编程门阵列(FPGA)和片上系统(SoC)加速器。

请注意，**边缘人工智能算法仍然可以在云中训练，但在边缘运行。**

# 目前致力于 AI 在边缘的硬件和软件开发的玩家:

专注于物联网边缘硬件的大大小小的公司包括[](https://www.electronicproducts.com/Digital_ICs/SoCs_ASICs_ASSPs_MEMS/BrainChip_delivers_new_approach_to_machine_learning_with_neuromorphic_SoC.aspx)****(秋田神经形态片上系统)、CEVA([**neu pro 家族**](https://www.electronicproducts.com/Robotics/AI/Machine_learning_edging_closer_to_a_microcontroller_near_you.aspx) )、谷歌( [**Edge TPU**](https://www.electronicproducts.com/Robotics/AI/Engineer_s_guide_to_embedded_AI.aspx) )、绿波( [**AI 处理器 GAP8**](https://www.electronicproducts.com/News/Electronic_Products_announces_25_finalists_for_the_2018_Product_of_the_Year_Awards.aspx) )、华为(Ascend Chips)、英特尔(Xeon)、英伟达(Jetson TX2)、高通(视觉智能平台)****

****较小的公司倾向于专注于物联网边缘软件。有的像 Ekkono、FogHorn、Swim(一种基于云的 POS)一样专注于学习，有的像瑞萨( [**e-AI**](https://www.electronicproducts.com/Digital_ICs/Microprocessors_Microcontrollers_DSPs/Microprocessor_delivers_high_speed_e_AI_imaging_at_low_power_consumption.aspx) )一样以推理为目标。许多公司也开发具有这两种能力的软件，如亚马逊(AWS Greengrass ML 推理模型)、BrainChip (Studio 软件)、谷歌(Cloud IoT Edge)、华为(Atlas 平台)、IBM (Watson IoT 平台)。****

# ****边缘计算会取代云计算吗？****

****尽管边缘分析是一个令人兴奋的领域，但它不应被视为云/中央数据分析的潜在替代品。在提供数据洞察方面，两者能够并将相互补充，两种模式在组织中都有其一席之地。边缘分析的一个缺点是，只有一部分数据可以在边缘进行处理和分析，并且只有结果可以通过网络传输回中央办公室。这将导致原始数据的“丢失”,这些数据可能永远不会被存储或处理。因此，如果这种“数据丢失”是可接受的，那么边缘分析是好的。另一方面，如果决策的延迟(& analytics)在运行中的操作或关键的远程制造/能源方面不可接受，则应首选边缘分析。****

****edge 几乎有无限的可能性。但并不是每个应用程序都需要它——当你的语音应用程序向服务器提问时，或者当美国宇航局的工程师正在处理最新的黑洞数据时，你可能需要等待一秒钟！****

# ****最终决定权****

****早些时候，突破性的人工智能应用程序需要一个庞大而昂贵的数据中心才能运行，但支持人工智能的边缘计算设备几乎可以驻留在任何地方。这一现实并不意味着边缘计算将取代云计算。随着数字世界变得更加互联，无论如何，实时智能将转移到边缘。不可否认的是，人工智能在边缘提供了无尽的机会，可以帮助风险企业更有效地推动任务和提高效率。****

****敬请关注即将发布的关于利用预先训练好的模型来构建强大的 Edge 应用程序的博文，无需训练您自己的模型。****

*****快乐学习！:)*****