# 个人理财自动化的 4 种方式

> 原文：<https://medium.datadriveninvestor.com/4-ways-to-automate-personal-finance-b98549b37e50?source=collection_archive---------18----------------------->

使用通用自动化平台改善您的财务生活

![](img/76b9fd7eb702bc55be3347b044a47d2a.png)

Photo by [Joshua Earle](https://unsplash.com/@joshuaearle?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

在 [Tray.io](https://tray.io) 工作的最大好处之一是能够将该工具用于个人用例。这确实鼓励我们思考如何利用自动化来改善我们自己的生活。如果你从未听说过通用自动化平台，那么我会鼓励你阅读这篇文章:[https://tray . io/guide/初学者-指南-通用自动化-平台-下载](https://tray.io/guide/beginners-guide-to-general-automation-platforms-download)。如果你不够幸运，无法获得企业级 GAP 供应商，那么你可能希望使用免费服务，如 [Zapier](https://zapier.com/) 。

这一点变得越来越有用的一个领域是个人金融，尤其是在银行业开放的英国，因为 API 开始在这一领域激增。Starling Bank 就是一个最好的例子，它实际上超越了开放银行标准，拥有一个完全成熟的 API，甚至能够进行支付。这带来了许多使用案例:

1.  财务报表
2.  预算预警
3.  储蓄自动化
4.  即时支付通知

虽然这些听起来不像是令人兴奋的要解决的用例，但是差距提供了使这些任务不那么痛苦并且更容易跟踪的可能性。

# **1。财务报告**

进入你的银行应用程序，很容易看到你最近的交易列表。然而，对于更高级的报告，许多应用程序无法捕捉我们最感兴趣的内容。例如，我们可能想看看我们在食物或账单上的花费一年来是如何变化的。这就是访问原始交易信息派上用场的地方。在 Starling 的例子中，你可以建立一个工作流程，每天/每周/每月给你发电子邮件，告诉你你的分类支出，分析不同时期的趋势，告诉你你的账单支出是否在增加，或者你是否应该减少外出的支出。你可以这样做:列出你账户中某一特定类别的所有交易，将行写入 Google 工作表，并在你写入工作表的时间段内执行简单的趋势计算。填写完信息后，你可以通过电子邮件将谷歌表单的链接发送到你的收件箱，以确保你不会错过报告。你可以根据你是否达到、错过或超过目标来定制主题。

# 2.预算预警

你可能有几个账户，当你花费太多的时候，你会发现很难算出来。通过汇总你的所有支出，你可以设定目标，并在超出阈值时触发警报。这里有用的是将信用卡和经常账户支出放在一起给出一个完整的画面。甚至万事达卡现在也提供了通过其开放银行 API⁴进行卡交易的机会，尽管遗憾的是，连接到其 API 的路径并不那么清晰。

# 3.储蓄自动化

鉴于逐月支出可能会有变化，很难想象有一个固定的储蓄目标总是最佳的。相反，创建一个规则可能更好，比如“一旦我还清了信用卡和房租&账单，就把 *x* 的金额留在我的活期账户中，其余的存入储蓄/经纪账户”。传统应用不允许这种程度的灵活性。然而，这正是 GAP 可以帮助您实现的逻辑，它允许您设置一个每月运行的任务，查看您的剩余余额，并向您的储蓄帐户发送一笔付款，金额是在当时计算的。这将确保你有足够的钱用于日常开支，同时确保你每个月都有存款。

你甚至可以更进一步，设置一些与许多银行现在提供的“储蓄便士”功能非常相似的功能，即每笔交易支出都被四舍五入，差额被存入储蓄账户。通过定制储蓄的目的地，你可以确保优化你的储蓄回报。

至少，如果你的银行不支持通过 API 进行交易，大多数银行会支持读取交易，你可以每月给自己发一个提醒，提醒自己存钱。

# 4.即时支付通知

这是我最近为朋友和家人设置的，当他们给我付款时，我会收到通知。我们在这里解决的问题是，虽然我们现在可以在收到付款时得到通知，但我们不能总是确保我们已经成功地将付款发送给了正确的人。使用 Starling API，我设置了一个 webhook，每当我的帐户收到付款时，它都会向工作流发送一个事件。如果发件人存在于我的收款人列表中，我就可以将他们与收款人 ID 进行匹配。在工作流中，我设置了一个地址簿来匹配收款人 id 和电子邮件地址。现在，每当我的朋友或家人给我付款时，他们都会收到一封即时的个人电子邮件，确认他们的付款。

# 结束语

在通过自动化平台自由探索您的全部财务方面仍然存在许多挑战，这是由于金融机构的监管程度以及它们没有跟上 API 运动的步伐。然而，希望以上已经给你提供了使用你的数据来改善你的财务生活的灵感。

要获得银行及其 API 的列表，请查看这篇精彩的文章:[https://nordigen . medium . com/list-of-all-banking-API-updated-3bb 6029 a 0033](https://nordigen.medium.com/list-of-all-banking-apis-updated-3bb6029a0033)

开户行组织:【https://www.openbanking.org.uk/ 

斯特林银行 API:【https://developer.starlingbank.com/docs 

构建 Zap 工作流:[https://zapier . com/learn/getting-started-guide/build-Zap-workflow/](https://zapier.com/learn/getting-started-guide/build-zap-workflow/)

⁴万事达卡获取账户交易:[https://developer . master card . com/open-banking-connect/documentation/ais features/get-account-transactions/](https://developer.mastercard.com/open-banking-connect/documentation/aisfeatures/get-account-transactions/)