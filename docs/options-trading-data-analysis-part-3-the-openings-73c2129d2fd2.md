# 期权交易数据分析—第 3 部分—开盘

> 原文：<https://medium.datadriveninvestor.com/options-trading-data-analysis-part-3-the-openings-73c2129d2fd2?source=collection_archive---------11----------------------->

这一部分的兴趣在于查看开盘交易，并从我们可用的交易数据中提取信息。从这些信息中，我们将尝试收集交易行为，并可能讲述一个简短的故事。账户持有人采用什么交易策略？影响开仓交易的因素有哪些？交易一般是赊账还是借记？行为是否一致？这些是我们可以尝试找出的一些问题。

我们从[第 1 部分](https://phandinhlan.medium.com/options-trading-data-analysis-part-1-an-introduction-c6dcdc5d9a2f)和[第 2 部分](https://medium.com/analytics-vidhya/options-trading-data-analysis-part-2-visuals-36e659233f)开始，使用前面提到的技术将交易数据加载到`transactionDf` Pandas 数据帧中。我们进一步过滤数据，以放大特定于期权的交易。这可以通过过滤`TRADE`的`type`和`OPTION`的`transactionItem_instrument_assetType`来实现。这将给我们带来活跃的期权交易。我们还将通过在`description`字段中过滤`REMOVAL OF OPTION`来包含与非活动期权相关的交易。无效期权交易是行使或转让的结果。由于我们对开放交易感兴趣，我们将进一步过滤`OPENING`。

![](img/db79ea3eb8ede626faf692c9e7d45891.png)

Filter for opening option transactions

现在让我们做一些提炼，提取以下感兴趣的项目:

*   creditsPerTransaction
*   信贷资本
*   信贷本金
*   天数到期

![](img/2fa7e6f11a9fb72a33c790d5be687d46.png)

Refining

我们将信用总额合并为`transactionItem_credits`作为合同数量(`transactionItem_amount`)和每份合同价格(`transactionItem_price`)的乘积。我们还将`transactionItem_price`更名为`creditsPerContract`，将`transactionItem_amount`更名为`contracts`以适应我们的会话环境。我们将`transactionItem_instrument_optionExpirationDate`转换，与`transactionDate`相减，得到`daysToExpiration`。其他的都很容易计算。只需注意，我们需要将信用额乘以 100，便可获得实际的美元金额。使用`describe`方法可以为我们提供一些基本的统计信息。

![](img/36c0e796396c6abb280f7e46ed05a4dd.png)

Using describe() on opens

这里有一些有用的信息来讲述一个关于开放贸易行为的简单故事。首先，我们注意到平均信用是正的，这表明空缺由空头头寸组成。我们可以通过`transactionItem_instruction`字段来确认。

![](img/e646d7e3fa3d12a0d5234da477237dc6.png)

Count the number of sells and buy transactions

请注意，这里的类型选择是任意的，因为我们只想得到买卖数量的计数。我们可以看到，短裤比长开口多得多。

每笔交易的平均信用额度(`transactionItem_credits`)约为每份合同平均信用额度的 1.94 倍，这可能表明我们每笔交易的平均信用额度约为 2 份。我们可以推断，空缺通常由两份合同组成。考虑到我们的买入卖出比率，我们很可能会考虑交叉或交叉。

到期日统计数据表明，交易策略倾向于在到期日之后 30 至 60 天之间进行平仓交易，大多数平仓发生在到期前 45 天左右。

平均信贷占资本的百分比可以给我们一些头寸规模的线索，大约是 0.45%。但是，如果没有额外的信息，比如在任何给定的时间周期内未平仓的头寸数量，我们就不能很好地了解规模策略。

现在，我们可以探索某个时期的数据，看看它能为我们提供什么信息。让我们首先提取每周一次的以下项目:

*   交易数量
*   合同数量
*   信贷总额
*   每个合同的平均信用额
*   平均到期天数
*   平均资本
*   平均本金

我们可以通过重采样将它们连接成一个新的数据帧。使用`count()`方法检索事务的数量。合同数量和总信用是该时间段的总和，而其余是平均值。此外，由于数据的性质，我们可能会在重采样后对某些字段使用 NaN。对于资本和本金，我们将执行向前填充。

![](img/c492e5bd473c30dbfa0e967d2d3a538e.png)

openedStats snippet

我们将计算每笔交易的信用和每笔交易的合同。请注意，这些是针对每个时间段的。信贷占资本和本金的百分比也是为该期间计算的。

![](img/42040b9ee2a263a6b037ce050351bc7a.png)

openedStats table

![](img/65b53720bfc9b9bc14c1d0b2d6ded125.png)

openedStats.describe()

我们现在可以使用`describe()`类似地分析每周信息。

鉴于我们这里的数据，如果不尝试获得一些视觉效果，我会觉得不完整。我们可以使用[第二部分](https://medium.com/analytics-vidhya/options-trading-data-analysis-part-2-visuals-36e659233f)中讨论的一些技术，并获得一些视觉效果。

![](img/f4456c840c127a9a5b887405dcce6da1.png)

openedStats plot 1 snippet

注意这里我使用了`transform_fold`方法。这是为了达到与使用第 2 部分中描述的`melt`方法相似的效果。

![](img/2b6a7930b334a7511bafa49c639da308.png)

openedStats plot 1

在`plot 1`,我们可以看到每周的合同数量、信用额度、到期天数和交易量。现在可以更容易地看到开盘交易行为的一些细节。

*   有些星期根本没有开业活动。
*   低开盘价或 0 开盘价的周数似乎遵循从到期日算起 30 天的趋势。
*   从 10 月 11 日这一周开始，有 5 周时间几乎没有开业活动。一些假设可能表明普遍避免收益报告，因为这是 2020 年的数据，也许是在美国总统大选期间避免。
*   从 11 月 15 日那一周开始，开盘后立即回升，总信贷、合约和交易量在 11 月 22 日那一周创下历史新高。如果我们做一个回溯，这个时间框架也对应着一些主要事件的注入，提供更多的交易资金。
*   开盘交易的扩张和收缩模式似乎与到期日高度相关。

每笔交易的合同数、每笔合同的信用数和每笔交易的信用数的图表讲述了一个类似的故事。

![](img/3debb8a144abcec8b3a7fd02a19116f7.png)

openedStats plot 2

正如我们所看到的，通过一些基本的数据提炼和可视化技术，我们可以开始清除基于交易数据的期权交易行为的迷雾，并建立事件之间的相关性。在本系列的后半部分，我们将着眼于分析平仓交易，看看如何揭开更多的故事。

免责声明，请不要使用这里的任何信息作为财务建议。感谢阅读。

[第 4 部分——关闭](https://medium.com/datadriveninvestor/options-trading-data-analysis-part-4-the-closings-d31e6051f8b3)