# 关于顶级 CEO，IEX 云 API 能告诉我们什么？

> 原文：<https://medium.datadriveninvestor.com/what-can-the-iex-cloud-api-tell-us-about-top-ceos-e388d365580e?source=collection_archive---------10----------------------->

![](img/2c7fe57175f2e9d7aa1e06820a93629c.png)

最近，我一直在 Python 中尝试不同的财务数据 API(试图在 COVID lockdown 中提高工作效率)。如果你有兴趣了解不同的金融应用编程接口，这里有其他比较它们的文章[这里](https://towardsdatascience.com/comparing-the-best-free-financial-market-data-apis-158ae73c16ba)和[这里](https://towardsdatascience.com/best-5-free-stock-market-apis-in-2019-ad91dddec984)。

但是我意识到有一个 API (IEX 云)可以给你每个被查询公司的 CEO 的全名。所以，我想知道，首席执行官们最常见的名字是什么？

为此，首先我从维基百科下载了标准普尔 500 所有股票报价机的列表。[格拉汉姆·格思里](https://medium.com/@grahamguthrie_14946)在这里写了一篇如何做到这一点的描述[。Graham 还写了一篇完整的描述，介绍如何从 IEX 下载特定公司的财务数据。我跟着那些教程去获取公司数据。](https://medium.com/wealthy-bytes/5-lines-of-python-to-automate-getting-the-s-p-500-95a632e5e567)

[](https://www.datadriveninvestor.com/2020/03/25/using-google-search-trends-to-predict-initial-jobless-claims/) [## 使用谷歌搜索趋势预测首次申请失业救济人数|数据驱动的投资者

### 几年来，我的重点一直是使用多种替代数据来预测宏观经济统计数据…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/03/25/using-google-search-trends-to-predict-initial-jobless-claims/) 

从 IEX 一次可以查询的 tickers 数量是有限的，所以你必须批量下载标准普尔 500。我批量做了 50 个，这是 API 免费版的极限。

一旦你有了所有公司的数据框架，你会看到有一列叫做“CEO”。那是首席执行官的名字。您可以使用以下方式获得 CEO 的名字:

```
dfCom['firstName'] = dfCom['CEO'].str.split().str[0].str.strip()
```

然后，您可以使用以下命令删除任何奇怪的字符:

```
dfCom['firstName'] = dfCom['firstName'].str.replace(r"[\"\',]", '')
```

然后，您可以使用以下方式对 11 个最常见的 CEO 姓名进行排名:

```
dfCom.groupby(['firstName']).count().sort_values(['companyName'], ascending=False)["companyName"].head(11)
```

你会看到最热门的名字是:

1.  迈克尔
2.  大卫
3.  詹姆斯
4.  约翰
5.  托马斯
6.  威廉
7.  杰弗里(男子名ˌ等于 Geoffrey)
8.  罗伯特
9.  理查德
10.  史蒂文(男子名)
11.  标记

这可能不是一个完全不令人惊讶的列表。更令人担忧的是，仅这 11 个名字就描述了整个指数(165 家公司)近三分之一的领导者。下面你就知道我为什么选 11 了。

您可以使用以下代码创建单词云:

```
names = dfCom['firstName'].values
names = str(names).replace("'","")
names = names.replace("\n","")
names = names.replace("'[","")
wordcloud = WordCloud(width=800, height=400).generate(names)
```

然后使用 matplotlib 绘制它，使用:

```
fig, ax = plt.subplots(figsize=(25, 10))
plt.imshow(wordcloud)
plt.axis("off")
plt.savefig('CEONamesWordCloud.png',bbox_inches = 'tight',pad_inches = 0)
```

![](img/3ca25aeba4996b43c8e2bac3859a3a78.png)

如果你认为这份名单看起来像 50 多岁男性最常见的名字，那你就完全正确了。根据美国社会安全局的数据，美国 1960 年代出生的男孩的前 11 个名字是:

1.  迈克尔
2.  大卫
3.  约翰
4.  詹姆斯
5.  罗伯特
6.  标记
7.  威廉
8.  理查德
9.  托马斯
10.  杰弗里(男子名ˌ等于 Geoffrey)
11.  史蒂文(男子名)

在这里看到完整的代码和我使用的数据[。](https://github.com/SteveHedden/CEONames)