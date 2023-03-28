# 数据科学的网络搜集——合法吗？

> 原文：<https://medium.datadriveninvestor.com/web-scraping-for-data-science-is-it-legal-266fb51171ec?source=collection_archive---------0----------------------->

## 为您的数据科学项目抓取网站时，请记住这一点。

![](img/c0463146c0ded7dfb8794e9c3a370362.png)

Photo by [Tingey Injury Law Firm](https://unsplash.com/@tingeyinjurylawfirm?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

作为一名数据科学家，你不会总是有一个干净的数据集准备用于新项目。在大多数情况下，数据科学项目的第一步是使用模仿人类上网行为的抓取工具从网站中提取数据。

然而，这些网络抓取工具可能会被视为对大多数网站的威胁。事实上，像脸书这样的公司似乎反对网络抓取，即使是为了研究目的。

为了让您的数据科学项目有一个良好的开端，我们将分析在哪些场景下采集数据被认为是合法或非法的。

# 研究项目的网络搜集

虽然以研究为目的的项目，如涉及情绪分析、假新闻检测或模型预测的项目，可能看起来无害，但如果你未经许可从一些公司的网站上获取这些数据，可能会引起它们的警觉。

让我们以脸书和纽约大学之间发生的事情为例。

10 月 16 日，脸书写了一封信，要求 NYU 大学的一个研究项目停止未经许可收集数据。NYU 项目包括通过收集用户的广告定位数据来跟踪政治广告是如何定位的。脸书[写了](https://thehill.com/policy/technology/522551-facebook-fights-nyu-political-ad-research-project-argues-it-violates-the):

> “搜集工具，无论多么善意，都不是从我们这里收集信息的许可手段。我们理解你工具背后的意图。然而，浏览器插件抓取信息违反了我们的条款，这些条款旨在保护人们的隐私。”

虽然像脸书这样的公司不允许网络抓取，但在研究中，**抓取并不被认为是一个大问题。事实上，[网络抓取对英国研究人员来说是合法的](https://aballatore.space/2020/04/01/web-scraping-is-legal/)，在 2014 年引入了[明确的立法](http://eprints.lse.ac.uk/71399/1/blogs.lse.ac.uk-The%20right%20to%20read%20is%20the%20right%20to%20mine%20Text%20and%20data%20mining%20copyright%20exceptions%20introduced%20in%20the%20UK.pdf)来定义非营利研究的版权例外。**

话虽如此，脸书对纽约大学项目的反应可能只是剑桥分析公司丑闻后不可避免的过度反应。事实上，在受到公众批评后，脸书似乎放弃了关闭该项目的威胁。

[](/5-things-you-should-know-to-easily-learn-web-scraping-6577bd8ebb08) [## 你应该知道的 5 件事来轻松学习网络抓取

### 降低学习网络抓取的难度。

medium.datadriveninvestor.com](/5-things-you-should-know-to-easily-learn-web-scraping-6577bd8ebb08) 

# 用于商业目的的网页抓取

当你从网站上抓取数据时，你正在访问可能受版权保护的数据。如果你抓取网站并把获得的数据用于商业目的，你可能会陷入麻烦。

让我们以 HiQ 和 LinkedIn 的案例为例。

HiQ 是一家数据分析公司，根据从 LinkedIn 收集的公开数据提供商业智能。出于这个原因，LinkedIn 在给 HiQ 的停止信中援引了计算机欺诈和滥用法案(CFAA)。

尽管美国上诉法院[驳回了](https://parsers.me/us-court-fully-legalized-website-scraping-and-technically-prohibited-it/) LinkedIn 的请求，称对公共网站进行网络抓取并不违反《CFAA 》,但应该指出的是，该决定并未授予 HiQ 出于商业目的使用通过抓取获得的数据的自由。

HiQ 用于抓取 LinkedIn 和避免知识产权禁令的一些技术将在下面的文章中解释。

[](https://medium.com/datadriveninvestor/3-simple-ways-for-web-scraping-without-getting-blocked-34f3b1f885d1) [## 3 个简单的方法来抓取网页而不被阻塞

### 防刮擦机构操作指南。

medium.com](https://medium.com/datadriveninvestor/3-simple-ways-for-web-scraping-without-getting-blocked-34f3b1f885d1) 

所以带有商业目的的项目，比如出售收集的数据，是不安全的。**相反，你可以通过下面的选项**在不出售数据的情况下让你的项目盈利。

# 交易项目的网页抓取

交易包括买卖东西。目标是从任何买卖活动中获利。

网上搜集交易通常以下列方式进行。

有些人构建了一个 scraper，它返回特定产品的价格，因此当价格下降时，程序会在产品售完之前自动购买该产品。一旦对该产品的需求增长，价格上涨，他们转售该产品以获取利润。

然而，最好的交易类型之一是套利，因为你只利用两个或更多市场之间的价格差异，所以你在一个市场买入，同时在另一个市场以更高的价格卖出。

套利发生在汇率、体育博彩、加密货币等领域。最重要的是，套利交易在美国是合法的，而且受到鼓励，因为它有助于提高市场效率。

如果你喜欢用套利交易赚外快，看看下面的文章:

[](https://medium.com/swlh/how-to-make-money-from-web-scraping-without-selling-data-92c1f961b25) [## 如何在不出售数据的情况下从网络抓取中赚钱

### 你只需要几行代码来赚点外快

medium.com](https://medium.com/swlh/how-to-make-money-from-web-scraping-without-selling-data-92c1f961b25) 

# 结论

在本文中，我们分析了网络抓取的合法性。我们发现研究项目不应该有法律问题，特别是在像英国这样的国家，英国明确规定网络抓取对研究人员来说是合法的。然而，具有商业目的的项目可能会侵犯版权。也就是说，仍然有可能从套利交易获得的数据中获利。

最重要的是，看起来“你要用这些数据做什么”将决定抓取网站的合法性。

[**如果你想用西班牙语学习 Python，可以订阅我的 YouTube 频道。每周我都会发布类似下面这样的视频。**](https://www.youtube.com/channel/UCGKngc82bux4NIDar572E5Q/featured?sub_confirmation=1)

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)