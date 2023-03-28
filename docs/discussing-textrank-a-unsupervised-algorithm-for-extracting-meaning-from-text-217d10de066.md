# Text rank——用于关键词提取和文本摘要的无监督算法

> 原文：<https://medium.datadriveninvestor.com/discussing-textrank-a-unsupervised-algorithm-for-extracting-meaning-from-text-217d10de066?source=collection_archive---------2----------------------->

[Source](https://www.youtube.com/watch?v=2l6Fa767kEw)

[TextRank](https://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf) 是一种基于图的排名算法，用于根据文本片段在文本文档中的重要性对其进行排名。这项研究是由 Rada Mihalcea 和 Paul Tarau 在德克萨斯大学完成的，并证明了无监督关键词提取和无监督提取摘要的结果同样好，并且在某些情况下比以前的基准测试更好。

TextRank 围绕着以图形形式表示相关词汇单元的思想，后来使用著名的 PageRank 算法对这些组块进行排序。对于那些不知道 PageRank 是什么的人，请阅读下一段，其他人可以跳到下一段。

PageRank 是一种排名算法，用于对网页进行评分并相应地对其进行索引。它是以谷歌创始人之一拉里·佩奇的名字命名的。等式是这样的-

***PR(A)=(1-d)+d(PR(T1)/C(T1)+…+PR(Tn)/C(Tn))***

假设 A 是一个页面，T1 是 T2…Tn 是所有指向 a 的页面。

**PR(T1)** =页面 T1 的 PageRank

**C(T1)** =从页面 T1 发出的链接

**d** =阻尼因子(负责削减某些页面的过多影响，这可能会导致使用假机器人)

**1-d** =该因子处理任何没有链接指向它的新页面。这样的网页仍然会得到一些公关。

**d = 0.85(根据 PageRank 上的原始论文)**

[](https://www.datadriveninvestor.com/2020/12/01/how-to-build-a-twitter-scraping-app-with-python/) [## 如何用 Python |数据驱动投资者构建 Twitter 抓取应用

### 每秒发出约 6000 条推文，每天发布 5 亿条推文，普通人甚至不能…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/12/01/how-to-build-a-twitter-scraping-app-with-python/) 

***注意，PageRank 在网页上形成概率分布，所以所有网页的 page rank 之和将为一。***

作者主要谈解决两个问题——

1.  关键词提取
2.  摘要

**观看论文演练，深入了解**—[*https://www.youtube.com/watch?v=2l6Fa767kEw*](https://www.youtube.com/watch?v=2l6Fa767kEw)

Python 中有很多支持 TextRank 的包。我们将看到如何使用 gensim 为我们得到的。

```
>>> from gensim.summarization import keywords >>> text = '''Challenges in natural language processing frequently involve ... speech recognition, natural language understanding, natural language ... generation (frequently from formal, machine-readable logical forms), ... connecting language and machine perception, dialog systems, or some ... combination thereof.''' >>> print (keywords(text).split('\n')) [u'natural language', u'machine', u'frequently']>>> from gensim.summarization.summarizer import summarize >>> text = '''Challenges in natural language processing frequently involve ... speech recognition, natural language understanding, natural language ... generation (frequently from formal, machine-readable logical forms), ... connecting language and machine perception, dialog systems, or some ... combination thereof.''' >>> print (summarize(text, word_count=100) >>> print (summarize(text, ratio=0.1)
```

请随意分享你的想法——谢谢

*原载于*[*https://prakhartechviz.blogspot.com*](https://prakhartechviz.blogspot.com/2019/03/textrank-bringing-order-to-text.html)*。*

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)