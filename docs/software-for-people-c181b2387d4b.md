# 面向大众的软件

> 原文：<https://medium.datadriveninvestor.com/software-for-people-c181b2387d4b?source=collection_archive---------6----------------------->

我们为什么要构建软件？因为软件可以彻底改变人们的生活。因为我们可以改善人类的生存条件。如果你的代码没有任何作用，那么它就是无用的。只要我们愿意，我们可以谈论我们的函数有多花哨，我们的算法有多快，但如果这项技术对任何人都没有帮助，它就没有任何价值。

在这篇博文中，我将讲述我是如何通过倾听人们的想法来认识问题，并提出和实施解决方案的。

# **听**

有一天，我们和我的搭档吉莉安去了书店。吉莉安想买一本书。她很挣扎，因为她的家庭图书馆有相当多的书，购买你已经有的书没有任何意义。她说了类似这样的话:

> 如果我有这本书，我希望我能在我的手机上检查一下。

![](img/eac9e96910d2448f6eba1d3264810b07.png)

那时，我刚刚完成了 Flatiron Bootcamp，准备在学校围墙外建造一些东西。所以，吉莉安和我开始讨论一个应用程序的细节。

我们决定调用应用程序货架帮助！

[](https://www.datadriveninvestor.com/2020/01/16/software-development-process-how-to-pick-the-right-process/) [## 软件开发过程:如何选择正确的过程？数据驱动的投资者

### 软件是任何企业组织成功的生命线。没有软件的帮助，一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/01/16/software-development-process-how-to-pick-the-right-process/) 

# **对话框**

与应用程序的潜在用户进行对话，以确定我们如何帮助用户，这非常重要。这是我在开始开发之前问 Gillian 的问题，也是她再次访问这个博客时的大致反应:

![](img/c282ddce119253ed57a4d6de49d4aa24.png)

Source: [https://pixabay.com/illustrations/conversation-dialogue-interview-1262311/](https://pixabay.com/illustrations/conversation-dialogue-interview-1262311/)

*   货架帮助将如何帮助你？

> 首先，我不想无意中购买同一本书的多个副本！但是，不幸的是，每当我去书店的时候，我不能把我的整个实体图书馆带在身边。虚拟图书馆解决了这个问题。第二，我的公寓里不同的地方都有书，其他的在我父亲在威斯康辛州的房子里。我偶尔会把书借给别人。如果有一个系统可以让我简单地查看我所拥有的一本书的物理位置，那就太好了。第三，我只能按照单一的顺序整理书架上的书籍，尽管它们中的许多可以归入多个类别。例如,《不屈:旺加里·马塔伊的回忆录》可以放在一个关于肯尼亚、环保主义、女权主义或其他自传的部分。但在物理货架上，基于其物理放置，它只能是一个类别的一部分。书架帮助允许我在多个类别中包含一本书。第四，在商店看到一本书，有时候没钱买，就用手机拍下来，留着以后看。我可以把这些书归类到“某一天”的类别中，而不是在下次发薪日去书店的时候再去找那张照片。

*   为什么在你的库中拥有不同的类别(标签)很重要？

> *原因有很多。一个是我已经提到的问题——标签允许一本书成为众多主题类别的一部分。另一个原因是，就像在图书馆或书店一样，我几乎可以找到我拥有的关于某一主题的所有书籍。在图书馆或书店，我最喜欢的事情之一就是看我正在找的书周围的书——有时，如果我看到相同主题的其他书，我甚至会开始以一种新的方式思考一个想法。我已经见过至少一个具有这种功能的虚拟图书馆，所以我知道我不是唯一享受这种体验的人！如果我意识到我有足够的或没有足够的对我来说重要的特定主题的材料，分类也帮助我注意到这一点。*

*   你觉得你会只在电话上用还是有你能想到的其他平台？

> *如果我在电脑上写作和研究，我也会用它。我目前没有智能板，但如果我在寻找一本特定的书，我也会在公寓的智能板上或电视上使用它。我也没有平板电脑，但如果我有，也可以在那里使用。我喜欢随身携带我的书，所以可能希望能够在任何便携式电子设备上使用它。*

*   你认为 Shelf Help 还能帮助其他人吗？

> *是的！！我有家人和朋友，他们有太多的书，需要更好的方法来整理它们！我还认为，在未来的版本中，人们可以用它来分享他们正在阅读的书籍和/或互相借阅。我喜欢实体书，但我想在某个时候，版权允许的情况下，人们也可能通过应用程序借阅电子书。*

**MVP**

最小可行产品看起来像这样:

![](img/caa80bbad0c2af232d5bac5763c7e54c.png)

Source: [https://www.flickr.com/photos/psd/7489475370](https://www.flickr.com/photos/psd/7489475370)

1.  用户可以看到他们图书馆中的所有书籍
2.  用户可以看到库中存在的所有标签
3.  用户可以选择特定的标签，并查看与该标签相关的所有书籍
4.  用户可以创建新标签
5.  用户可以向图书馆添加图书
6.  用户可以给图书馆里的每本书添加一张图片
7.  用户可以向图书添加多个标签
8.  用户可以编辑图书的详细信息
9.  用户可以删除图书
10.  用户可以按书名搜索书籍

# **打造**

当我们结束谈话并决定一个 MVP 时，我开始开发这个应用程序。

![](img/5dac633e541eb592fd7a41f4caa81699.png)

Source: [https://giphy.com/gifs/coding-5ntdy5Ban1dIY](https://giphy.com/gifs/coding-5ntdy5Ban1dIY)

首先，我用 React 和 redux 开发了一个基本的前端。我用虚拟数据创建了所有组件，以确保一切都在它的位置上。我设置了 redux 操作，以便于管理不同组件中的状态。

当基本的前端完成后，我开始用 Ruby on Rails 和 postgresql 数据库进行后端工作。我生成了模型、控制器和迁移。我添加了序列化器来清理服务器响应。此外，我们使用 Gillian 图书馆的真实书籍创建了一个小数据集。

接下来，我将前端的动作定向到 rails API RESTful 路径，并在 DOM 上呈现后端的数据。

当 MVP 的 pre-alpha 版本完成后，我在 Heroku 和 Netlify 上部署了所有东西，并发了一个链接给 Gillian。

货架帮助的工作还在继续，我们离可以投入生产的应用还很远。但是当她第一次打开 Shelf Help 并开始与它互动时，这是一种非常有益的感觉。吉莉安非常高兴，她说:

> “这太神奇了，太感谢你了！！架子队来帮忙了，万岁！!"

![](img/869515e470bc53094e5bab39c680aab2.png)

Source: [https://giphy.com/gifs/reactiongifs-yes-success-BoBOKNtlR8rTi](https://giphy.com/gifs/reactiongifs-yes-success-BoBOKNtlR8rTi)

为了取得成功(不仅是在技术领域)，我们还必须积极倾听并认识到需求。我们需要参与对话，以便理解通过编写下一行代码我们可以增加什么价值。

感谢阅读，并查看 Github 的[货架帮助！](https://github.com/pavel-ilin/shelf-help)

在 [LinkedIn](https://www.linkedin.com/in/pavel-ilin) 上连接。