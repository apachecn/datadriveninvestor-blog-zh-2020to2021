# 计算 ETF 目标价格的简单方法

> 原文：<https://medium.datadriveninvestor.com/a-simple-way-to-calculate-the-target-price-of-an-etf-17917d30d2c0?source=collection_archive---------1----------------------->

## 更清楚地了解交易所交易基金的未来价格

![](img/9053698ea7aa540f1dda0c4ecb304501.png)

Photo by [Ricardo Arce](https://unsplash.com/@jrarce?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

目标价格是基于历史观察对证券未来价格的预测。当谈到获得交易所交易基金(ETF)的目标价格时，我们可以使用[市盈率(PE)方法](https://medium.com/@tunji.onigbanjo/a-simple-way-to-calculate-the-target-price-of-a-stock-9fd4d2e93e27?source=friends_link&sk=e4cb615fc25a465192006f8541085911)。问题是每股收益并不是 ETF 容易获得的基本指标。为了简单起见，我们可以只关注 ETF 的价格表现。

求解目标价格并不能取代你对证券的分析，尤其是 ETF。做你的研究和尽职调查，了解 ETF 的目标，它持有什么样的公司，以及提供 ETF 的公司如何运作，这些都比确定目标价更重要。

[](https://www.datadriveninvestor.com/2020/07/28/how-to-divorce-safely-and-sanely-without-sacrificing-your-children-or-your-finances/) [## 如何在不牺牲孩子或财务的情况下安全理智地离婚|数据驱动…

### 在美国，七月是以孩子为中心的离婚月。作为 cdfaⓡ的专业人士，我可以向你保证，从长远来看…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/07/28/how-to-divorce-safely-and-sanely-without-sacrificing-your-children-or-your-finances/) 

我喜欢 ETF，因为这是开始投资最简单的方式之一。ETF 不仅跟踪股票的表现。还有跟踪债券、房地产投资信托基金(REITs)和大宗商品等资产表现的 ETF。由于我们只关注 ETF 的价格表现来确定目标价格，这意味着以下方法适用于任何 ETF。

*注意:我分享这些信息只是为了教育目的。请在投资前做好调查和尽职调查。*

在求解 ETF 的目标价格时，我们可以求解当年和接下来 4 年的年末目标价格。这样一来，我们就可以对 ETF 的目标价格进行 5 年预测。

通过使用实际的 ETF，展示如何找到 ETF 的目标价格会容易得多。将使用的 ETF 是技术选择部门 SPDR 基金( [XLK](https://finance.yahoo.com/quote/XLK/performance?p=XLK) )。XLK 跟踪[技术选择部门指数](https://www.spglobal.com/spdji/en/indices/equity/technology-select-sector-index/#overview)的表现。

首先，我们需要 XLK 截至 2019 年 12 月 31 日的价格。在雅虎财经上查看其[图表](https://finance.yahoo.com/quote/XLK/chart?p=XLK#eyJpbnRlcnZhbCI6ImRheSIsInBlcmlvZGljaXR5IjoxLCJ0aW1lVW5pdCI6bnVsbCwiY2FuZGxlV2lkdGgiOjIuNzI0MjQyNDI0MjQyNDI0LCJ2b2x1bWVVbmRlcmxheSI6dHJ1ZSwiYWRqIjp0cnVlLCJjcm9zc2hhaXIiOnRydWUsImNoYXJ0VHlwZSI6ImxpbmUiLCJleHRlbmRlZCI6ZmFsc2UsIm1hcmtldFNlc3Npb25zIjp7fSwiYWdncmVnYXRpb25UeXBlIjoib2hsYyIsImNoYXJ0U2NhbGUiOiJsaW5lYXIiLCJwYW5lbHMiOnsiY2hhcnQiOnsicGVyY2VudCI6MSwiZGlzcGxheSI6IlhMSyIsImNoYXJ0TmFtZSI6ImNoYXJ0IiwiaW5kZXgiOjAsInlBeGlzIjp7Im5hbWUiOiJjaGFydCIsInBvc2l0aW9uIjpudWxsfSwieWF4aXNMSFMiOltdLCJ5YXhpc1JIUyI6WyJjaGFydCIsInZvbCB1bmRyIiwi4oCMdm9sIHVuZHLigIwiXX19LCJzZXRTcGFuIjpudWxsLCJsaW5lV2lkdGgiOjIsInN0cmlwZWRCYWNrZ3JvdW5kIjp0cnVlLCJldmVudHMiOnRydWUsImNvbG9yIjoiIzAwODFmMiIsInN0cmlwZWRCYWNrZ3JvdWQiOnRydWUsInJhbmdlIjpudWxsLCJldmVudE1hcCI6eyJjb3Jwb3JhdGUiOnsiZGl2cyI6dHJ1ZSwic3BsaXRzIjp0cnVlfSwic2lnRGV2Ijp7fX0sInN5bWJvbHMiOlt7InN5bWJvbCI6IlhMSyIsInN5bWJvbE9iamVjdCI6eyJzeW1ib2wiOiJYTEsiLCJxdW90ZVR5cGUiOiJFVEYiLCJleGNoYW5nZVRpbWVab25lIjoiQW1lcmljYS9OZXdfWW9yayJ9LCJwZXJpb2RpY2l0eSI6MSwiaW50ZXJ2YWwiOiJkYXkiLCJ0aW1lVW5pdCI6bnVsbCwic2V0U3BhbiI6bnVsbH1dLCJjdXN0b21SYW5nZSI6bnVsbCwid2lkdGgiOjIsInN0dWRpZXMiOnsidm9sIHVuZHIiOnsidHlwZSI6InZvbCB1bmRyIiwiaW5wdXRzIjp7ImlkIjoidm9sIHVuZHIiLCJkaXNwbGF5Ijoidm9sIHVuZHIifSwib3V0cHV0cyI6eyJVcCBWb2x1bWUiOiIjMDBiMDYxIiwiRG93biBWb2x1bWUiOiIjRkYzMzNBIn0sInBhbmVsIjoiY2hhcnQiLCJwYXJhbWV0ZXJzIjp7IndpZHRoRmFjdG9yIjowLjQ1LCJjaGFydE5hbWUiOiJjaGFydCIsInBhbmVsTmFtZSI6ImNoYXJ0In19LCLigIx2b2wgdW5kcuKAjCI6eyJ0eXBlIjoidm9sIHVuZHIiLCJpbnB1dHMiOnsiaWQiOiLigIx2b2wgdW5kcuKAjCIsImRpc3BsYXkiOiLigIx2b2wgdW5kcuKAjCJ9LCJvdXRwdXRzIjp7IlVwIFZvbHVtZSI6IiMwMGIwNjEiLCJEb3duIFZvbHVtZSI6IiNmZjMzM2EifSwicGFuZWwiOiJjaGFydCIsInBhcmFtZXRlcnMiOnsid2lkdGhGYWN0b3IiOjAuNDUsImNoYXJ0TmFtZSI6ImNoYXJ0IiwicGFuZWxOYW1lIjoiY2hhcnQifX19fQ--)页面，该股于 2019 年 12 月 31 日收于 91.67 美元。既然我们已经有了 XLK 的 2019 年底价格，现在让我们导航到雅虎财经上的[业绩](https://finance.yahoo.com/quote/XLK/performance?p=XLK)页面。在 Performance 页上，找到其 5 年的月度总回报值。是 26.11%。如果你使用的 ETF 没有 5 年的月总回报值，使用类别值。

我们现在有了我们需要的价值，可以得出 XLK 的 2020 年目标价格。下面是公式:*价格* (1 + 5 年月总回报)*其中*价格*为 ETF 价格， *5 年月总回报*为小数格式的总回报。XLK 的 2020 年目标价为 91.67 美元* 1.2611 = 115.61 美元。截至 2020 年 10 月 19 日收盘，XLK 为 125.52 美元。

为了求解 2021 年、2022 年、2023 年和 2024 年的目标价格，我们将使用前几年的目标价格。例如，我们将使用 2020 年的目标价格来求解 2021 年的目标价格，然后使用 2021 年的目标价格来求解 2022 年的目标价格。2021 年目标价 145.80 美元，2022 年 183.87 美元，2023 年 231.88 美元，2024 年 292.42 美元。

假设我们希望我们的目标价格保守一点。为了使每个目标价格更加保守，我们可以假设每年都会有一次单独的市场调整。市场调整是指主要指数，如标准普尔 500 指数下跌至少 10%。基于我们对 2020 年至 2024 年的目标价格，我们可以将每个价格乘以 0.9，以获得它们的目标价格，假设每年都会出现一次单独的市场调整。2020 年的新目标价是 104.05 美元，2021 年是 131.22 美元，2022 年是 165.48 美元，2023 年是 208.69 美元，2024 年是 263.178 美元。

如前所述，求解目标价格并不能取代你对 ETF 等证券的分析。在计算目标价格之前，你仍然需要对 ETF 有一个完整的了解。求解目标价格有助于你对 ETF 的潜在未来价格有一个更清晰的印象。求解目标价格可能很有趣，但不要让这妨碍你首先通过深入研究和尽职调查为自己选择最佳投资机会。

[查看屯积信保持联系](https://tunji.substack.com/)。

## 获得专家观点— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)