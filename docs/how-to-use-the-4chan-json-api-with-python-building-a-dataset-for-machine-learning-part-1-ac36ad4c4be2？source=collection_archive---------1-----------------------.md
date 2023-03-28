# 如何在 Python 中使用 4chan Json API 为机器学习构建数据集第 1 部分

> 原文：<https://medium.datadriveninvestor.com/how-to-use-the-4chan-json-api-with-python-building-a-dataset-for-machine-learning-part-1-ac36ad4c4be2?source=collection_archive---------1----------------------->

## 4 带 Python 的 chan JSON API 第 1 部分

## 如何用 python 和 requests 从 4chan 的/pol 留言板提取评论？

![](img/c9bbbc23234fcb0a8c8335254d6fbb40.png)

Astronaut trying to escape planet 4chan.

# **简介**

对于所有围绕 4chan 的争议，嗯…我想是 4chan 的开始，我对他们的 **Javascript** **对象** **符号** ( **JSON** ) **应用** **编程** **接口** ( **API** )的博客帖子的缺乏感到惊讶。

是啊！没错，4chan 有一个只读的 JSON API，里面充满了各种去道德化、摧毁灵魂的可能性。

然而，不管出于什么原因，这个奇怪见解的金矿在互联网评论中几乎不存在。

如果我们在 duckduckgo 或 google 中搜索*‘4chan JSON API python’*，我们几乎找不到与博客文章相关的点击。

事实上，我们得到的点击率如此之低，人们可能会对此产生怀疑。

**声名狼藉/pol**

4chan 确实是一个有趣的地方。

在网站上花不超过 60 秒的时间就能理解为什么它如此有争议。

大概 4chan 上最有名最有煽动性的留言板就是 */pol* ，或者'*政治上* *不正确的*。

在过去的几年里，为了自然语言处理的目的，我一直在尝试各种社交媒体 API。

在这段时间里，我阅读了许多不同平台的评论，4chan 是迄今为止最有趣和最独特的。

4chan 有自己的术语和价值体系。

[](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) [## 2019 年最值得学习的编码语言|数据驱动的投资者

### 在我读大学的那几年，我跳过了很多次夜游去学习 Java，希望有一天它能帮助我在…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) 

没有进入具体的条款，(你知道我的意思，对不对？)从机器学习的角度来看，这很有意思。

由于这些原因，存在于互联网这个非常特殊角落的自然语言是独一无二的。

> ***‘用 4chan 线程训练出来的聊天机器人会是什么样子？’***

我们大概可以想象出上述问题的答案。

有一个关于 **Tay** 的精彩故事，这是一个由微软创造的聊天机器人，用户用 Twitter 数据进行训练。

不到 24 小时，它就开始在推特上发布一些相当冒犯的内容。

无论推特上的推文有多极端，与 4chan 相比都是苍白无力的，人们只能想象其可能性。

# 概述:

大约在 2019 年 10 月 1 日，4chan API 团队更新了他们在 Github 上的文档，为他们的 JSON 端点提供了一些很棒的文档。

我们将使用的端点是目录:[https://a.4cdn.org/pol/catalog.json](https://a.4cdn.org/pol/catalog.json)

学习解析任何 JSON API 的棘手部分不一定是您必须编写的代码的复杂性，而是理解不同字段和端点之间的结构和关系。

# 参考资料:

## **Python 库**

*   [日期时间](https://docs.python.org/3.8/library/datetime.html)
*   [pprint](https://docs.python.org/3.8/library/pprint.html)
*   [请求:r.json()](https://2.python-requests.org/en/master/user/quickstart/#response-content)
*   [json](https://docs.python.org/3.8/library/json.html)

## **Python 内置函数**

*   [枚举()](https://www.python.org/dev/peps/pep-0279)
*   [范围()](https://www.python.org/dev/peps/pep-0281)
*   [产量](https://www.python.org/dev/peps/pep-0255)
*   [。获取()](https://docs.python.org/3.7/library/stdtypes.html#mapping-types-dict)

## **Python 异常**

*   [按键错误](https://docs.python.org/3/library/exceptions.html)

## **Python 生成器函数**

*   [发电机](https://docs.python.org/3/reference/expressions.html#yield-expressions)
*   [发电机功能](https://wiki.python.org/moin/Generators)

## **4chan API 文档**

*   [4chan API 文档](https://github.com/4chan/4chan-API)
*   [4chan API 目录端点](https://github.com/4chan/4chan-API/blob/master/pages/Catalog.md)

# 第一步:

进口我们的进口产品。

```
import requests
import json
from pprint import pprint
from datetime import datetime as dt
```

# 第二步:

使用[请求](https://2.python-requests.org/en/master/)库建立到 4chan 目录端点的连接。

```
r = requests.get('https://a.4cdn.org/pol/catalog.json')
```

# 第三步:

有几种不同的方法来转换来自服务器的响应。

**方法一:**

```
import json 
import requests
from pprint import pprint r = requests.get('https://a.4cdn.org/pol/catalog.json') 
r = json.loads(r.text) pprint(r)
```

**方法二:**

```
import requests 
from pprint import pprint r = requests.get('https://a.4cdn.org/pol/catalog.json') 
r = r.json() pprint(r)
```

**出局:**

```
{'page': 11,'threads': [{'bumplimit': 0,'com': 'Thread OP''country': 'US','country_name': 'United States','ext': '.png','filename': 'picture.png','fsize': 287315,'h': 1000,'imagelimit': 0,'images': 1,'last_modified': 1575651990,'last_replies': [{'com': 'Comment to Thread OP'country': 'US','country_name': 'United States','name': 'Anonymous',{'com': '<a href="#p235356550" ''class="quotelink">&gt;&gt;235356550</a><br><span ''class="quote">&gtn</span>','country': 'US','country_name': 'United States','ext': '.jpg','filename': 'AnotherPic.jpg','fsize': 65516,'h': 600,'id': '9PriyurA','md5': 'UmA62vBYEKcDREnJDL+FCw==','name': 'Anonymous','tim': 1575651990509,'time': 1575651990,'tn_h': 125,'tn_w': 125,'w': 600}],'md5': 'rSv4H+6jrvu7zenf3gQ6DQ==','name': 'Anonymous','now': '12/06/19(Fri)11:25:54','replies': 2,'resto': 0,'tn_h': 250,'tn_w': 225,'w': 900}]}]
```

正如您所看到的，方法 2 利用了内置的请求功能，而不是必须导入 JSON 标准库。我用的是方法 2。

# 步骤 4:访问键/值对

下一步是“解析”我们的数据，这意味着以一种易于处理的方式重新排列数据。

有几种方法可以做到这一点，使用 pandas 是我的第一直觉，但是我发现使用标准库工具对于这方面的**Extract Transform Load(ETL)**过程更加实用。

来自 [r.json()](https://2.python-requests.org/en/master/user/quickstart/#response-content) 的 response 对象给了我们一个字典列表，也称为**嵌套 JSON** ，有时候整理起来真的很痛苦。

**出局:**

```
import requestsr = requests.get('https://a.4cdn.org/pol/catalog.json')
r = r.json()for items in r:
   print(items.keys())
   print(items['page'])
   print(items['threads'])
```

**出局:**

```
#print(items.keys())dict_keys(['page', 'threads'])
dict_keys(['page', 'threads'])
dict_keys(['page', 'threads'])
dict_keys(['page', 'threads'])
dict_keys(['page', 'threads'])
dict_keys(['page', 'threads'])
dict_keys(['page', 'threads'])
dict_keys(['page', 'threads'])
dict_keys(['page', 'threads'])
dict_keys(['page', 'threads'])
dict_keys(['page', 'threads'])
```

**出局:**

```
#print(items['page'])1
2
3
4
5
6
7
8
9
10
11
```

**出局:**

```
#print(items['threads'])
{'page': 11, 'threads': [{'bumplimit': 0, 
                          'com': 'Thread OP Comment', 
                          'country': 'US', 
                          'country_name': 'United States', 
                          'ext': '.png', 
                          'filename': 'pic.png', 
                          'fsize': 287315, 
                          'h': 1000, 
                          'imagelimit': 0, 
                          'images': 1, 
                          'last_modified': 1575651990, 
```

好了，现在我们来看些好东西。

我们已经成功剥离了 JSON 的外层，现在我们可以访问核心的 JSON API 数据。

但是只有一个问题，我们只得到第一页的线程。我们想要的是用一个 get 请求访问所有 11 个页面的所有帖子。

**出局:**

```
import requestsr = requests.get('https://a.4cdn.org/pol/catalog.json')
r = r.json()for items in r:
    for thread in items['threads']
        print(thread.keys())
```

# **步骤 5:用一个 get 请求访问所有页面和键/值字段。**

让我们回顾一下我在第四步中所做的事情，并制定一个行动计划。

*   对于整个/pol 板，我们在任何给定时间都有**10-11 页的线程**。
*   我们每页有**~ 18-20 篇文章**。
*   每个页面都有自己的**页面/线程键对**，必须同时访问它们才能访问数据。

所以我们的问题如下:

我们如何用一个 get 请求访问所有的页面和线程？

通过使用**[**枚举()**](https://www.python.org/dev/peps/pep-0279/) **和一个** [**生成器**](https://docs.python.org/3/reference/expressions.html#yield-expressions) **功能当然！！****

```
import requestsr = requests.get('https://a.4cdn.org/pol/catalog.json')
r = r.json()def gen_chan():
    for idx, page in enumerate(r):
        for thread in r[idx]['threads']:
            yield thread
```

**生成器本身就是一个完整的讨论，但是正如你所看到的，使用 yield 语句，而不是 return，给了我们一个[生成器函数](https://wiki.python.org/moin/Generators)。**

**在不跑题的情况下，这是一个谈论常见 python“反模式”的好机会。**

**有两种方法可以做到这一点，这两种方法都达到了同样的目的。**

****方法一(不那么伟大的方式):****

```
import requestsr = requests.get('https://a.4cdn.org/pol/catalog.json')
r = r.json()for pages in range(0, len(r)):
    for threads in r[pages]['threads']:
        print(threads)
```

****出局:****

```
0
1
2
3
4
5
6
7
8
9
10
```

**通过使用嵌套的 for 循环，我们的第一个循环索引了 **['pages']** 键的长度。**

**然后，我们可以使用该索引作为 pages 字典的关键字，并访问每个页面上的所有帖子。**

**在这种情况下，使用 [range()](https://www.python.org/dev/peps/pep-0281/) 就可以了，但是更好的方法是在生成器函数中使用 [enumerate()](https://www.python.org/dev/peps/pep-0279/) 。**

****方法二(更好的方法):****

```
import requestsr = requests.get('https://a.4cdn.org/pol/catalog.json')
r = r.json()def gen_chan():
    for idx, page in enumerate(r):
        for thread in r[idx]['threads']:
            yield thread
```

****出局:****

```
0
1
2
3
4
5
6
7
8
9
10
```

**同样，如果我们在第一个 for 循环中 **print(idx)** ，我们将同时接收所有页面。**

**我们可以使用该输出来迭代地索引每个页面，并提取所有内容，使用第二个 for 循环来访问线程键。**

# **第六步:从每个帖子中提取评论。**

**现在让我们来看看每个帖子的评论。**

**它们存储在名为 **['last_replies']** 的密钥中。**

**这很棘手，因为不是所有的帖子都有评论，如果有的话，从帖子被创建到存档，它们总是在更新。**

**为此，我选择了[。get()](https://docs.python.org/3.7/library/stdtypes.html#mapping-types-dict) 内置的 dictionary 方法，这样我们就不会在键不存在的情况下收到任何 [KeyErrors](https://docs.python.org/3/library/exceptions.html) ，因为线程上还没有注释。**

**这是我做的一个小辅助函数，以防以后我想改变我们的提取方法。**

```
def get_threads(key: str, default='NaN'):
    return threads.get(key, default)
```

**现在我们终于有了完整的代码。**

```
import requests
from datetime import datetime as dtr = requests.get('https://a.4cdn.org/pol/catalog.json')
r = r.json()def gen_chan():
    for idx, page in enumerate(r):
        for thread in r[idx]['threads']:
            yield threaddef get_threads(key: str, default='NaN'):
    return threads.get(key, default)for threads in gen_chan():
    no = get_threads('no')
    now = get_threads('now')
    time = get_threads('time')
    my_time = dt.today()
    com = TextMaster.strip_html(get_threads('com'))
    name = get_threads('name')
    trip = get_threads('trip')
    ids = get_threads('id')
    capcode = get_threads('capcode')
    filename = get_threads('filename') + get_threads('ext')
    resto = get_threads('resto')
    semantic_url = get_threads('semantic_url')
    replies = get_threads('replies')
    images = get_threads('images')
    url = TextMaster.extract_url(get_threads('com'))
    sent = TextMaster.textblob_sentiment(get_threads('com'))
    if 'last_replies' in threads:
        for comment in threads['last_replies']:
            com_com = comment.get('com', 'NaN')
            resto_com = comment.get('resto', 'NaN')
            now_com = comment.get('now', 'NaN')
            time_com = comment.get('time', 'NaN')
            fname_com = comment.get('filename', 'NaN')url_com = comment.get('com')
            sent_com = comment.get('com')
```

**如果你想知道 TextMaster 类是什么，请继续关注第二部分。**

**这篇文章基本上总结了这一点。**

**我们现在可以构建一个 NLP 预处理管道，并将数据插入数据库。**

***原载于【https://alexjslessor.com】[](https://alexjslessor.com/blog/4chan_p1)**。*****