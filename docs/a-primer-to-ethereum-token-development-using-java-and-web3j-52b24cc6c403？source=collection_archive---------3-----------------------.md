# 使用 Java 和 web3j 开发以太坊令牌的初级读本

> 原文：<https://medium.datadriveninvestor.com/a-primer-to-ethereum-token-development-using-java-and-web3j-52b24cc6c403?source=collection_archive---------3----------------------->

![](img/3b83c2e1c3e533483355c6cb6fca1201.png)

我最近写了一篇关于使用 Android 开始[以太坊开发的文章，其中我演示了如何在 Android 中设置 web3j 以及如何传输以太。在文章发表后，我收到了一个请求，要求我写一篇关于使用 web3j 与定制 ERC20 令牌进行交互的文章，这导致了本文的创作。尽情享受吧！](https://medium.com/datadriveninvestor/an-introduction-to-ethereum-development-on-android-using-web3j-and-infura-763940719997)

为此，我们将使用我创建的名为 JavaToken 的基本 ERC20 智能契约，您可以在这里找到。出于演示目的，我们将使用它和它所在的存储库，所以请随意克隆它并跟随它！我们将要部署和运行的网络将是一个使用 Truffle 的本地 Ganache Testnet。

# 步骤 0.9:生成智能契约 java 包装器

第 0.9 步是为我们的智能契约获取一个 java 包装器。这是第 0.9 步，因为从技术上来说*如果你的合同已经部署，这不是强制性的，但它会使以后与合同交互时事情变得容易得多。首先使用 solidity 编译器编译你的 solidity 契约。如果您使用的是 Truffle，那么只需在 JavaToken 存储库的 Truffle 目录中运行以下命令就可以做到这一点:*

```
truffle compile
```

接下来，安装 web3j 命令行界面。

Mac/Linux:

```
curl -L get.web3j.io | sh
```

窗口:

```
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/web3j/web3j-installer/master/installer.ps1'))
```

现在我们已经安装了所有这些，只需运行

```
web3j truffle generate Truffle/build/contracts/JavaToken.json -o src -p com.javaToken
```

从 JavaToken 目录中。这将为 JavaToken 智能契约生成一个包装器，使它在以太坊中的交互更加容易。

# 步骤 1:部署您的合同

为了部署我们的令牌，我们设置了一些凭证，并简单地用它们调用 deploy()方法。

这就对了，你刚刚部署了一个全新的以太坊令牌！

或者，如果您的合同已经部署，并且您只是想与它进行交互，您可以简单地使用以下命令加载它:

# 第二步:保持平衡

合同被配置为向其部署者提供全部初始供应。让我们检查一下我们是否真的得到了一切。如果我们有步骤 0.9 中的包装器，这就像:

否则，事情会更复杂一些:首先，我们需要在事务中手动输入我们希望在合同中调用的函数的详细信息，在这种情况下，它的名称是 balanceOf，我们提供的参数是一个地址，我们希望该函数返回一个 uint256。然后，我们对这些数据进行编码，并将其与我们希望发送给呼叫方(我们的地址)的合同一起放入交易中。最后，我们将十六进制结果解码成一个大整数。

现在我们有 100，000 个爪哇人。让我们送一些给朋友吧！

# 步骤 3:转移一些令牌

同样，有包装器和没有包装器之间的区别相当明显:

这次没有包装有点不同，因为我们需要实际证明该交易来自我们的帐户，因为我们通过传输令牌而不是像以前那样只读取数据来改变区块链的状态。我们以同样的方式创建一个函数对象。虽然智能合约函数返回一个布尔值，但我们并不在这里指定它，因为我们不需要它，因为我们通过交易收据检查交易是否成功，所以我们将返回指定为一个空列表。接下来，我们创建一个事务管理器。这种区别很重要，因为 said manager 将我们的凭证作为参数，这意味着通过它发送的事务属于我们(与上面的 balanceOf 调用不同)。最后，我们发送交易，并通过检查收据来验证交易是否成功。

# 结论

仅此而已！您刚刚学习了如何使用 web3j 部署自己的 ERC20 令牌。恭喜你！这一切的代码可以在[这里](https://github.com/nschapeler/JavaToken)找到。

感谢您的关注！

尼古拉斯

*如果你喜欢这个，请为这个故事鼓掌，让更多的人看到它！*

*如果你喜欢这个，请给我买杯咖啡:)*

以太坊:0x 190d 71 ba 3738 f 43 DC 6075 f 5561 e 58 AC 9d 4 e 3 DFC 2

比特币:1 brucwzs 2 vnrkfmbfs 14 zqerw 74 a1 h1 ke

lite coin:lbnfojftfvcj 7 gfaautwqhithjcj 3m 8y 3v