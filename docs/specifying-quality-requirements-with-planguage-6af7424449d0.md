# 用计划语言指定非功能需求

> 原文：<https://medium.datadriveninvestor.com/specifying-quality-requirements-with-planguage-6af7424449d0?source=collection_archive---------1----------------------->

## 这里有一种方法可以精确地指定质量属性，如用户友好、健壮、可靠、快速和安全。

![](img/41402346023832ddd5701fc1522c69bc.png)

Business photo created by photoroyalty — [www.freepik.com](https://www.freepik.com/photos/business)

客户要求您编写用户友好、健壮、快速或安全的软件的频率有多高？每个人都会同意，这些都是我们希望在产品中体现的有价值的特性。然而，简单地说，它们是可怕的要求！这些模糊的词语让你不知道“用户友好”是什么意思，也不知道如何判断你是否达到了对某个特定客户来说“健壮”的特征。

听到来自用户的这种请求应该会刺激业务分析师去探索，比如说，对说话者来说什么是用户友好的。尽管如此，许多 ba 仍然编写模糊的质量属性需求，没有清楚地向开发人员和测试人员传达期望。像“系统应该是用户友好的”这样的陈述也是无法证实的。你不能通过评估一个产品来判断它是否满足这些模糊的质量要求。

[](https://www.datadriveninvestor.com/2019/01/17/the-technologies-poised-to-change-the-world-in-2019/) [## 2019 年即将改变世界的技术|数据驱动的投资者

### 很难想象一项技术会像去年的区块链一样受到如此多的关注，但是……

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/17/the-technologies-poised-to-change-the-world-in-2019/) 

为了解决不明确和不完整的非功能需求的问题，顾问和作者 Tom Gilb 开发了*计划语言*，这是一种具有丰富关键字集的符号，允许精确陈述质量属性和其他项目目标。关于全面的讨论，参见吉尔伯的书*《竞争工程:使用计划语言的系统工程、需求工程和软件工程手册》(巴特沃斯-海涅曼，1995)。*

事实上，您可以使用 Planguage 符号以一种精确、多维的方式来描述任何东西，而不仅仅是软件需求。每当需要明确的技术交流时，这是一种通用的技术。

# 关键词

Planguage 提供了许多关键字来表达不同类型的需求，但是您只需要其中的几个就可以开始了。用一种更传统的形式来写，一个性能需求可能是这样的:“至少在 95%的时间里，系统显示一个财务报告的时间不应该超过 7 秒。”下面是一个如何用 Planguage 表达同样需求的例子。

**标签:**性能。报告.响应时间

**雄心:**在基础用户平台上生成会计报告的快速响应时间。

**SCALE:** 按下 Enter 键或点击 OK 请求报告与开始显示报告之间经过的秒数。

**仪表:**对 30 份测试报告进行秒表测试，这些测试报告代表了为外地办事处会计定义的使用操作配置文件。

**目标:**95%的报告不超过 7 秒。←外地办事处经理

**拉伸:**预定义报告不超过 2 秒，所有报告不超过 5 秒。

**心愿:**所有报告不超过 1 秒。

基础用户平台**定义**:四核处理器，8GB 内存，Windows 10，运行 QueryGen 3.3，单用户，至少 50%的系统内存和 70%的系统 CPU 容量空闲，网络连接速度至少 50 Mbps。

您使用一个层次化的命名约定，用一个唯一且有意义的*标记、*或标签来标识每个需求。需求标签比如性能。Report . ResponseTime 时间很长，但不言自明。*目标*陈述了导致该需求的系统的目的或目标。*标尺*定义测量单位，而*仪表*描述如何进行测量。

所有利益相关者必须对“绩效”的含义有相同的理解。假设用户将测量解释为从他按下回车键的时间开始，直到完整的报告出现，而不是直到报告开始显示，如本例中所述。开发人员可能声称需求得到了满足，而用户坚持认为需求没有得到满足。明确的质量要求和度量可以防止这种争论。

# 灰色的阴影

Planguage 的一个优点是，您可以为正在测量的量指定多个目标值。这反映了实践中许多质量要求的灰色特征。与简单的黑白分明、是或否的结构相比，指定多个目标级别会产生更丰富的质量要求。

*目标*标准是最低可接受的成就水平。除非每个*目标*条件都完全满足，否则需求不会得到满足，因此要确保这些目标在实际业务需求方面是合理的。陈述*目标*需求的另一种方式是定义*失败*(另一个计划关键字)条件:“超过 5%的报告超过 7 秒。”*伸展*值描述了更理想的绩效目标，而*愿望*值代表了理想的结果。

考虑展示绩效目标的起源。*目标*标准后面的“←”符号表示该目标来自现场办公室经理。此外，Planguage 语句中的任何专业术语都用*定义*，以便读者理解。这个例子提供了一个叫做基本用户平台的东西的定义，测试将在这个平台上进行。

这种陌生的符号让一些人感到害怕。显然，如此精确地指定需求需要更多的工作。然而，其他人很快就意识到了它的优点。

当我在培训课上描述质量属性需求时，我总是会介绍计划语言。当我们做写作质量要求的练习时，我鼓励学生尝试一下。当我在一家制造电子显微镜的高科技公司教一个班时，整个班级当场决定采用平面语言。他们认识到这比他们当前编写这些非常重要的非功能性需求的方法要优越得多。

Planguage 包括许多额外的关键字，在指定明确的质量属性需求，甚至业务目标时提供灵活性和精确性。不过，你只需要几个关键词就可以开始了。

使用计划语言的主要缺点是产生的需求比简单的质量需求声明要庞大得多。然而，提供的丰富信息超过了这种不便。

即使你不使用完整的计划语言形式来编写质量需求，使用关键词来思考人们所说的“快”的确切含义，将会产生更加精确和共享的期望。这就是需求工程的全部内容。

=====================

本文改编自 Karl Wiegers 和 Joy Beatty 的 [*软件需求*](https://www.processimpact.com/pubs.html#SR3E) 。卡尔的最新著作是 [*软件需求精要:成功商业分析的核心实践*](https://www.softwarereqs.com/) (与坎达斯·霍康森合著)。他也是《软件开发珍珠[](https://www.processimpact.com/karls_books/SDP/index.html)*[*【日常事物的轻率设计】*](https://www.thoughtless-design.com/)[*成功的商业分析咨询*](https://www.processimpact.com/karls_books/SBAC/index.html) 等众多书籍的作者。*

*想要无限制阅读 Medium.com，可以考虑申请的会员资格。*