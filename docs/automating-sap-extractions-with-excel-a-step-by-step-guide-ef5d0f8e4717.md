# 自动化 SAP 的秘密武器——您的时间，别浪费了

> 原文：<https://medium.datadriveninvestor.com/automating-sap-extractions-with-excel-a-step-by-step-guide-ef5d0f8e4717?source=collection_archive---------0----------------------->

![](img/bc178daa4abcada670c15031e7ffa82c.png)

Photo by [Artur Tumasjan](https://unsplash.com/@arturtumasjan?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

## 如果您仍然手动使用 SAP 进行日常分析，那么您将会浪费大量时间，而且您可以自行实现自动化！

SAP 是最常用的企业资源规划系统(ERP)之一，它是一种管理和集成公司所有部门的活动和数据的软件，如财务、供应链、运营、报告等。

如果我没错的话，每天你或你团队中的某个人都必须登录 SAP，从五个、十个甚至更多不同的 SAP 事务中提取大量信息，对它们进行分析，并在最后返回进行你的计算显示为必要的更改，对吗？

那么，如果你不浪费时间手动提取它，你可以让它做所有需要的提取，而你和你的队友喝咖啡？

或者如果你不需要在一天结束的时候做所有的改变？为什么不两者都要呢？

看起来我试图出售一个非常复杂的开发解决方案，它将花费你每天使用的相同数量的交易，但转换成一袋袋的黄金，但它恰恰相反。

你所需要的就是 **Excel** ！

现在你可能正看着屏幕，头垂向左边，问“我到底要怎么让 Excel 做所有这些事情？”，对吧？

答案就是 **Visual Basic 应用程序(VBA)** 和 **SAP 脚本**的强大组合。

我想你可能从 Excel 的宏中知道 VBA，那正是我正在谈论的家伙。

这背后隐藏着一个难以理解的魔力，那就是 Excel 有一个记录宏按钮，可以记录用户在 Excel 中的每个动作和行为，SAP 也有一个。

基本上，你需要做的唯一的事情就是你已经做了的，但是记录下来并修改一些代码行，这样它就可以在以后单独做了。

# 预配置

首先，SAP 必须被设置为接受或能够与 VBA 交互。

为此，请转到自定义本地布局>选项。

![](img/20535aac9170a58a44da234e0c1e45dd.png)

Source: Writer

一个新的窗口将会打开，进入辅助功能&脚本>脚本，找到标签用户设置并标记“启用脚本”选项。

现在你可以用 VBA 来做你工作中无聊的部分了。

另一件重要的事情是:不要选中“启用脚本”下面的两个复选框，因为当它们被标记并且你运行你的代码时，会出现一个弹出窗口，等待你的批准让代码连接到 SAP。

![](img/fcd0a722fb73ebe6360988ee6dff3d9c.png)

Source: Writer

我们已经完成了预配置！

# SAP 记录

下一步是做你已经做过的过程，但是这次要记录下每一步。

要在 SAP 上记录您的操作，请单击 Customize Local Layout > Script Recording and Playback 选项，如下图所示。

![](img/bfaa9d3031e90c04c5a5d0e941d4520c.png)

Source: Writer

之后，会出现一个带有 4 个按钮的小窗口:

*   回放脚本(绿色)
*   记录脚本(红色)
*   停止录制(灰色)
*   更多(黄色)

![](img/85a11db23a09dfbf41366f25b34988a3.png)

Source: Writer

如果您点击“更多”按钮，窗口将展开两个新字段，您可以在其中定义保存设置。

![](img/afebdef94865c1009e3799f2ffa73c1b.png)

Source: Writer

![](img/c9138dffdc46de7b5f831f7ce9baf87e.png)

Source: Writer

定义好一切(文件名和保存脚本的文件夹)，只需点击 record 按钮即可开始。

![](img/4329ec602623dcba84d1309b0c9b9522.png)

Source: Writer

如果灰色的停止按钮变成黄色，播放和录制按钮变成灰色，您就可以知道它是否正在录制。

![](img/53719635afa81702887e11c53cf3388f.png)

Source: Writer

现在，您将执行您的日常流程。

举个简单的例子，我的任务是“提取一些采购文件信息”

为此，首先要访问 ME2N 事务。

![](img/068700f1612b4f37f6dd99dee760f3c8.png)

Source: Writer

一旦加载了事务，我必须执行两个操作:

*   插入我想获取数据的采购文件
*   删除选择参数

我从插入文档开始，在 Excel 上我有三个采购文档，我从那里复制它们，并在 SAP 上点击采购文档的多个选择。

![](img/c4af6cd82cd14dd6ca7218ed5b3538ca.png)

Source: Writer

在新窗口中，我单击剪贴板上的上传，粘贴我刚刚复制的文档。

![](img/d1801bb7791a82d646212436d7df6c06.png)

Source: Writer

之后，只需点击时钟按钮来执行条目。

![](img/f13dca71bc887918413587fcdfb5f76e.png)

Source: Writer

要检查多个输入是否已注册，请检查采购文件的多选按钮是否变为绿色。

![](img/45b0025da1413ba24898c40665069943.png)

Source: Writer

对于选择参数，我只需点击文本框并清除所有内容。

![](img/a38dca1049c56b9cd78eaacce55fc4c5.png)

Source: Writer

现在我已经配置好了一切，让我们开始执行吧！

![](img/18c5a66e75802fbcbbf44ac0365946eb.png)

Source: Writer

很好，正如你所看到的，SAP 已经将我文档中的数据返回给我，下一步是下载/导出它。所以我点击了一个导出本地文件的图标。

![](img/c4aa0534138a6de26423cccc52a04a0d.png)

Source: Writer

我选择了用制表符导出文本选项，这是我的个人偏好，因为用 Excel 效果更好。

![](img/70b7089f4461ac0452321419e085252d.png)

Source: Writer

我定义了所需的目录和文件名。

![](img/2833562ad5af62ed1738396519b99ff0.png)

Source: Writer

我查看了 SAP 底部的消息，以检查导出是否已完成。

![](img/354a75af967237b7f2cac3173a11a42d.png)

Source: Writer

最后，我点击黄色按钮停止了记录。

![](img/f86cd48b8b3fe98bb73fa8ef3f60e055.png)

Source: Writer

哒哒！您刚刚完成了您的第一个 SAP 记录！很简单，不是吗？

# 记录结果

要查看记录的输出，只需转到您在流程开始时定义的文件夹并打开文件。

乍一看，它似乎有很多代码行，你可能不明白他们在告诉你什么，没关系，保持冷静，因为我们将在下面的一些截图上工作。

![](img/a071509f9589a6ba570f97278a3d2d81.png)

Source: Writer

# 在 Excel 上启用开发人员选项卡

我们即将进入神奇的一步，但是在我们做任何事情之前，我们需要启用 Excel 上的 Developer 选项卡。如果您已经启用了它，请跳到下一个主题。

点击文件。

![](img/93421b1de5bfbbd277b521c24829edbe.png)

Source: Writer

点击选项。

![](img/99ca7d805345ebf38432a097077c59c1.png)

Source: Writer

将出现一个新窗口，然后单击自定义功能区。

您将看到两个列表，在左边的一个列表中，您将找到几个复选框，其中一个是开发者，只需选中它，然后单击左下角的 OK 按钮即可应用更改。

![](img/b50fa4ce1312c7025edde7935573e750.png)

Source: Writer

# 创建子程序

在“开发人员”选项卡上，单击 Visual Basic 按钮。

![](img/367524ace8b9878009a5d23dc424e429.png)

Source: Writer

要开始修改 SAP 记录，我们需要创建一个模块，所以继续插入>模块

![](img/aa35d3a1f44c8154dc67b1169545b0f4.png)

Source: Writer

创建的模块将出现在你左边的项目窗口中，如果它没有自己打开，双击模块即可。

打开模块，创建一个子程序，我称之为“测试”，现在粘贴 SAP 记录中的代码。

这里有一个技巧，VBA 认为“应用”这个词是一个保留字，这意味着这个词在 VBA 有一个特殊的应用，如果不按照它的设计用途使用，就会导致错误。

解释完之后，我们需要将出现在代码开头的四个“应用程序”更改为任何可用的变量名。我一般用“APP”来代替。

![](img/23c7109339ac3f20955ca0042996b13b.png)

Source: Writer

为了让您更好地了解 Excel 和 SAP 之间的匹配，我在 C 列和 D 列中添加了 SAP 文件导出所需的目录和文件名。

![](img/ab21e2f4c41539011bda51670ab51ef3.png)

Source: Writer

记住这个布局，我们可以继续编辑我们的子程序。

我在下面的截图中突出显示了代码的三个部分。

首先，**绿色的一个**，在这里我创建了一个“是否存在一个要提取的文档？”检查。为了做到这一点，我有一个名为 last_rows 的变量，其中存储了第一行的值/不为空，从 A 列的最后一行开始向上。

因为我的布局 I 在 A 列有一个标题，我知道如果我至少有一个文档，它应该从第二行开始，所以我添加了一个 if 语句来检查它，这样当 A 列没有文档时我就不会执行代码。

**黄色高亮**只是为了显示被替换的应用程序。

**红色高亮**显示了一件重要的事情。SAP 记录器，顾名思义，只记录 SAP 上发生的事情。

还记得我不得不从纸上复制采购文件，然后粘贴吗？记录器不会记住它，因为它发生在 Excel 上，所以如果你在记录器输出时执行它，你应该会有一个错误，因为代码会试图粘贴它没有复制的东西。

![](img/0626907b353904f30ba9a545475ebf3f.png)

Source: Writer

对于下一个截图，记得我删除了选择参数字段上的内容吗？在绿色突出显示的**中可以看到这种变化。SAP 将其解释为一个空字符串的输入。**

因此，如果您想将选择参数更改为另一个参数而不是删除它，您只需将**更改为**【您的参数】**。**

**除了编写字符串代码，你还可以做的另一件事是**从 Excel 单元格**中获取一个值，这就是发生在**紫色**和**灰色高亮**上的事情。**

**![](img/d330336e3630bb618c4f69d74360e560.png)**

# **将宏添加到按钮**

**为了完成并使它变得更容易，你可以添加一个按钮来开始执行你的例程。**

**为此，你需要进入插入>插图>形状，然后选择你最喜欢的形状。**

**![](img/9fc02b0266ecc29fbd0b027e0205d2cc.png)**

**Source: Writer**

**之后，你可以添加一些文本到你的按钮上，左键点击并选择“分配宏”选项**

**![](img/268d421ce8ac59dce67a3a70acdd8e70.png)**

**新窗口将显示您在此工作簿中的所有可用子程序，在我们的示例中，我们只有“测试”子程序。**

**点击它，然后依次点击确定**

**![](img/b8b3f4ce14f494ed79f9dcde1cdb2041.png)**

**Source: Writer**

**最后，您只需将文件保存为. xlsm 或. xlsb 格式，这样它就能保存您的 VBA 代码。**

**我更喜欢。xlsb，因为它的工作原理与。xlsm，但大小只有它的一半。**

# **这就是了！**

**有了这个，我想你可以开始创建你自己的 SAP 自动化了！**

**希望这篇文章对你有帮助！**

**你可以在这里看到这个项目的代码:**

**[](https://github.com/rfpcordeiro/vba-sap-automation-example) [## rfpcordeiro/VBA-sap-自动化-示例

### 一个简单的例子，展示了使用 Excel 和 VBA 自动化 SAP 交易是多么容易。GitHub 是超过 50 个…

github.com](https://github.com/rfpcordeiro/vba-sap-automation-example) 

> 特别感谢 Samanta Tomaz 帮助我为你选择了一个好榜样！**