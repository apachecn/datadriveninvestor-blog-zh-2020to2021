# 以太坊是什么，为什么会有气的问题？

> 原文：<https://medium.datadriveninvestor.com/what-is-ethereum-and-why-does-it-have-a-gas-problem-2c9d8142e160?source=collection_archive---------1----------------------->

![](img/886f535bbcc53916606501dc39d20d0e.png)

The Price of Ethereum

以太坊，大多数人都知道它是按市值排名位于比特币之后的加密货币，但它不仅仅是另一种硬币。

在本帖中，我们将解释以太坊是什么，天然气是如何工作的，当前的问题以及如何解决这些问题，并巩固以太坊作为领先的区块链网络的地位。

# 以太坊是什么？

以太坊网络是一个开源的、可编程的 T2 区块链 T3，它允许创建 T4 智能合同 T5 或迷你软件程序，用固定的规则来管理用户互动。例子可能是每周固定日期的付款、完成任务的奖励或赢得游戏的支出。

区块链以太坊的维护和安全是由赚取加密货币的激励推动的，加密货币也被称为以太坊(又名 [ETH](https://www.coingecko.com/en/coins/ethereum) 或以太)。

# 以太坊不仅仅是以太坊

![](img/6168a8acdc0bbc78305db5dd95e6ff33.png)

The Ethereum Network

以太坊不仅仅是以太坊网络和 ETH。它还允许用户创建自己的加密货币，即代币，每种货币都有自己的规则和用途(智能合约)。

以太坊上创造的大多数代币都遵循一个被称为[ERC-20](https://www.investopedia.com/news/what-erc20-and-what-does-it-mean-ethereum/)(“ERC-20 代币”)的特定标准。他们必须遵守以太坊区块链制定的基本规则，这样才能提供更好的互操作性。除此之外，规则和用途由创作者决定。

任何人都可以做一个 ERC-20 代币，很多人都这样做了；事实上，在撰写本文时，有超过 200，000 种不同的 ERC-20 代币。

在撰写本文时，排名前 10 位的 ERC-20 代币是:

1.  美元系绳( [USDT](https://tether.to/) )
2.  链环([链环](https://chain.link/)
3.  美元硬币( [USDC](https://www.circle.com/en/usdc) )
4.  AAVE ( [AAVE](https://aave.com/) )
5.  Uniswap ( [UNI](https://uniswap.org/)
6.  包装比特币( [WBTC](https://wbtc.network/) )
7.  Theta 令牌( [THETA](https://www.thetatoken.org/) )
8.  制造者( [MKR](https://makerdao.com/en/) )
9.  合成酶( [SNX](https://www.synthetix.io/)
10.  复合( [COMP](https://compound.finance/) )

ERC-20 令牌的完整列表可以在以太网扫描块浏览器中找到

[https://etherscan.io/tokens](https://etherscan.io/tokens)

# 以太坊交易

虽然以太坊允许创建复杂的规则集，但简单的交易，或从一个人到另一个人的财富转移，是核心用例。

来自[比特币基地](https://www.coinbase.com/)、[币安](http://binance.com)、[现金 App](https://cash.app/) 等公司的集中服务是托管服务。它们使购买和交易加密货币变得容易。你只需给他们你的身份证件，附上一个银行账户，然后就可以走了。

这种易用性是有代价的。你不仅要向提供商支付多层费用，而且持有你账户密钥的服务拥有完全控制权。他们可以转移、冻结和损失你的钱，而你对此无能为力。正如一句古老的密码谚语所说——不是你的钥匙，不是你的密码。

当然，这些集中式服务有它们的位置，但它们并不真正符合加密货币的原始精神，正如 Satoshi 在创造比特币时所设想的那样。

> *[*比特币，一种全新的完全点对点的电子现金系统，没有可信的第三方。*](https://bitcoin.org/bitcoin.pdf)*”—中本聪**

*随着所谓的去中心化金融的兴起，我们现在又回到了 Satoshis 的愿景，即将权力交还给个人，目标是帮助金融应用民主化。*

*DeFi 的核心是非保管钱包，简单地说，就是你放私人钥匙的钱包。非保管钱包的例子包括 [MetaMask](https://metamask.io/) 、 [Numio](http://numio.one/) 和 [Ledger](https://www.ledger.com/) 。*

*有了非保管钱包，您可以完全控制您的加密货币。*

# *那么什么是气体呢？*

*简而言之，这就是以太坊，但什么是气体呢？*

*![](img/be3852691d193d13db5eaf2f28a9bbfe.png)*

*Not that type of Gas (Photo by [Markus Spiske](https://unsplash.com/@markusspiske?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/gas-pump?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText))*

> **Gas 是“……在以太坊区块链平台上成功进行交易或执行合同所需的费用或定价值”——*[*Investopedia*](https://www.investopedia.com/terms/g/gas-ethereum.asp#:~:text=What%20Is%20Gas%20(Ethereum)%3F,on%20the%20Ethereum%20blockchain%20platform.)*

*在进行以太坊交易时，总会有一项费用，称为汽油费，必须以以太坊支付。不能用你发的加密货币支付。*

*这不是一个集中服务的问题，因为他们会为你解决问题，并从你拥有的任何令牌中收取费用-当然是溢价。非保管钱包带来的问题是，你总是需要足够的 ETH 来支付油费。*

*最重要是，如果你想发送一个 ERC 20 代币，你必须在同一个钱包里有 ETH 来支付费用。*

***流程***

*当你想从你的非托管钱包发送一笔交易，而这个钱包只持有一个 ERC-20 令牌而没有 ETH 时，这是如何工作的？*

*简单地说，你需要把 ETH 转到你的钱包里才能取出令牌。*

*如果你的另一个钱包里没有 ETH，那么你可能需要开通一个集中服务，购买足够的 ETH 来支付费用以及他们收取的任何费用，然后将这些费用发送到你的钱包里。*

*你还必须考虑以太坊网络转账费用不断波动的因素，因此，当它到达你的钱包时，仍有足够的以太坊进行原始交易。*

*另一方面，你也可能会发送太多，并在你的帐户中留下一些你可能永远不会使用的少量 ETH 或者因为汽油费而无法发送。*

*这不是一个简单的过程。*

# *所以以太坊又慢又贵？*

*最近的 DeFi 爆炸凸显了以太网作为日常支付系统的主要弱点。也就是说，它又慢又贵——但是为什么呢？*

*![](img/c2cf2407f8de4dc14c291a38b38bcdd2.png)*

*Ethereum Gas Prices Are Rising*

*以太坊目前基于所谓的[工作证明](https://en.wikipedia.org/wiki/Proof_of_work#:~:text=Proof%20of%20work%20(PoW)%20is,minimal%20effort%20on%20their%20part.) (PoW)共识机制*。在以太坊的例子中，这是一个由分散的节点(计算机)组成的巨大网络(约 11，000 台)，这些节点单独验证每一笔交易。任何运营一个节点的人都会得到一笔费用(天然气)。*

*所以，很简单，你想做交易，想优先于其他人，所以你支付更高的费用。任务完成。*

*嗯……比那要复杂一点。*

*以太坊的结算层只能处理每秒 15 笔交易(tps ),而且没有固定的费用结构，而是根据以太坊网络在任何时候的繁忙程度而定的可变价格。*

*当以太坊网络安静时，15tps 的限制不是问题，汽油费也很便宜。当每个人都想使用网络时，问题就出现了。它变得繁忙，网络出现瓶颈，所以你可以为优先权支付更高的煤气费，但每个人都想要优先权，所以每个人都竞相出价，煤气费继续上涨。*

*目前，每笔钱包对钱包交易的汽油费约为 5-20 美元，无论你发送的金额是多少。而在与智能合约交互时，比如在 [Uniswap](https://uniswap.org/) 上，收费可以达到十倍以上。*

***这是变更为* [*股权证明*](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/) *但至少还需要 24 个月。**

# *那么，我们如何才能让它更快、更便宜、更友好呢？*

*汽油费并不是一个新问题。在 2017 年牛市的时候是个问题，现在也是个问题。事实是，在它得到解决之前，我们不会看到以太坊作为支付系统的全面采用。它需要所谓的[缩放](https://ethereum.org/en/developers/docs/layer-2-scaling/)。*

*[以太坊 2.0](https://consensys.net/knowledge-base/ethereum-2/faq/) 的推出将是以太坊迄今为止最大的一次升级。以太坊 2.0 提供的可伸缩性改进应该会导致更快的交易速度和更低的用户费用——然而有一个大问题…它还没有准备好。*

*这就是第 2 层的用武之地，将交易移出以太坊区块链(第 1 层)。*

*幸运的是，现在有许多第 2 层可伸缩性解决方案可用。*

*   *[状态通道](https://docs.ethhub.io/ethereum-roadmap/layer-2-scaling/state-channels/)*
*   *[侧链](https://docs.ethhub.io/ethereum-roadmap/layer-2-scaling/sidechains/)*
*   *[血浆](https://docs.ethhub.io/ethereum-roadmap/layer-2-scaling/plasma/)*
*   *[乐观累计](https://docs.ethhub.io/ethereum-roadmap/layer-2-scaling/optimistic_rollups/)*
*   *Validium ( [zkSTARKS](https://docs.ethhub.io/ethereum-roadmap/layer-2-scaling/zk-starks/)*
*   *[zkRollups](https://docs.ethhub.io/ethereum-roadmap/layer-2-scaling/zk-rollups/)*

*你可以阅读上面链接中的每个解决方案，或者在[物质实验室博客](https://medium.com/matter-labs/evaluating-ethereum-l2-scaling-solutions-a-comparison-framework-b6b2f410f955)上获得完整的比较。*

*总之，这些解决方案带来了什么；*

*   *每秒交易量(TPS)的增加*
*   *费用的降低*
*   *使用您发送的令牌支付汽油费用的能力**

*这些第 2 层解决方案各有利弊，但目前真正引起轰动的是 zkRollups。以太坊的创造者[维塔利克·布特林](https://vitalik.ca/general/2021/01/05/rollup.html)一直直言不讳地支持 zkRollups，似乎它们会一直存在下去。*

*目前[建设 zkRollup 基础设施的主要玩家](https://medium.com/datadriveninvestor/a-brief-guide-to-zkrollup-projects-and-products-january-2021-ebf857a8165b)有， [zkSync](http://zksync.io/) 和 [Loopring](https://loopring.org/) ，还有一些很棒的产品正在由 [Numio](https://numio.one/) 、 [Gitcoin](https://gitcoin.co/) 、 [Curve](https://curve.fi/) 和 [Argent](https://www.argent.xyz/) 等公司打造。*

***并非在所有情况下都是如此，但该功能内置于各种第 2 层解决方案中。**

*![](img/937fbd7a5386a1438e2515dee8406c2f.png)*

*Ethereum Layer 2 — zkRollups*

# ***结论***

*总之，以太坊是一个巨大的、不断增长的生态系统，它可以改变世界，但它不会，因为气体仍然是一个问题。因此，为了大规模采用，第 2 层技术是必不可少的。*

*如果你想更深入地了解以太坊，有无数的关于以太坊的文档，以及各种项目、产品和扩展解决方案——如果你想有所突破，你最好现在就开始阅读。*

*约珥*

*推特:[https://twitter.com/joelkite](https://twitter.com/joelkite)*