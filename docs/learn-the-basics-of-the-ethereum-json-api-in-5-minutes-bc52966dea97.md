# 在 5 分钟内学习以太坊 JSON API 的基础知识

> 原文：<https://medium.datadriveninvestor.com/learn-the-basics-of-the-ethereum-json-api-in-5-minutes-bc52966dea97?source=collection_archive---------3----------------------->

![](img/17e34acfb18ec129e0681de0802b1ca9.png)

Photo by [Shahadat Rahman](https://unsplash.com/@hishahadat?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

有一天，我发现自己需要使用 python 与以太坊网络进行通信，而在这种环境下，让 web3.py 工作似乎是不可能的。因为我仍然需要与网络对话，所以我求助于使用以太坊提供的 JSON-RPC API，所有的 web3 库都是建立在这个 API 之上的。原来，还挺有意思的！所以，让我们开始吧！

# 基本设置

首先，让我们声明几个在以后发送请求时会有帮助的变量:

为了简单起见，我们使用一个 Infura 节点来连接以太坊 Ropsten Testnet。你可以在这里得到一个 API 密匙。

**你的第一个要求**

让我们通过获取网络的当前天然气价格来尝试一下。我们可以通过简单地做以下事情来做到这一点:

我怎么知道使用什么方法和发送什么参数？都可以在官方以太坊文档中找到。

# **获取最新区块**

让我们尝试一些更有趣的东西——让我们获取最新的块，看看我们可以从那里读取什么！

让我们仔细看看其中一个交易:

您可能已经开始了解这些调用是如何工作的了，所以让我们尝试一些更高级的方法:

# 发送交易

首先，让我们使用 web3.py 库创建一个新帐户，并加载一些 Ropsten ether。我喜欢用[这个水龙头](https://faucet.ropsten.be/)。

要发送事务，我们需要 nonce。我们也可以使用与上面相同的模式通过 RPC JSON API 获取:

接下来，我们创建并签署我们的事务，并再次使用 JSON RPC API 发送它:

如果你在不同的以太网(测试)上测试，确保相应地设置链 Id。

请注意我们是如何重复使用开始时获取的汽油价格的。

# 结论

仅此而已！您刚刚学习了使用 [JSON RPC 以太坊 API](https://github.com/ethereum/wiki/wiki/JSON-RPC) 与世界上最有影响力的区块链互动的基础知识！你可以在这里找到所有这些[的代码。](https://github.com/nschapeler/ethereum-rpcjson)

感谢您的关注！

尼古拉斯

如果你喜欢这个故事，请为它鼓掌，让更多的人看到它！

*如果你喜欢这个，请给我买杯咖啡:)*

以太坊:0x 190d 71 ba 3738 f 43 DC 6075 f 5561 e 58 AC 9d 4 e 3 DFC 2

比特币:1 brucwzs 2 vnrkfmbfs 14 zqerw 74 a1 h1 ke

lite coin:lbnfojftfvcj 7 gfaautwqhithjcj 3m 8y 3v