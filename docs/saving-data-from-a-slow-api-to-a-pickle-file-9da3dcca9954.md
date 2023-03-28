# 将数据从慢速 API 保存到 Pickle 文件

> 原文：<https://medium.datadriveninvestor.com/saving-data-from-a-slow-api-to-a-pickle-file-9da3dcca9954?source=collection_archive---------1----------------------->

## 一个创建的函数，用于在遍历 for 循环时保存 API 数据

从缓慢的 API 中绘制数据时的一个常见问题是，您可能会在截止日期前进行操作，并且您会发现从 API 中获取整个数据集需要几天时间。

最初，您可能会发现自己只是运行一个函数来提取数据，一旦您将数据放入 Jupyter 笔记本，您就可以对其进行处理。但是出现的另一个常见问题是，当您第二天早上回来工作时，在数据提取过程中突然出现一个错误。该错误将会导致您丢失从 API 中提取的任何数据。这可能是因为您从 JSON 文件中保存的字典的键或值中存储了数据。

[](https://www.datadriveninvestor.com/2019/02/25/6-alternatives-to-the-yahoo-finance-api/) [## 雅虎财经 API |数据驱动投资者的 6 种替代方案

### 长期以来，雅虎金融 API 一直是许多数据驱动型投资者的可靠工具。许多人依赖于他们的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/25/6-alternatives-to-the-yahoo-finance-api/) 

在快节奏的数据科学环境中，您必须在截止日期前提供结果，这些问题阻碍了进展。对于数据科学家来说，学会解决这些问题非常重要，这样他们才能为利益相关者提供有意义的产品。

![](img/3ebf5f0dc52f38d87cb9ad3e9fc7afb9.png)

Source: [https://www.smartfile.com/blog/python-pickle-security-problems-and-solutions/](https://www.smartfile.com/blog/python-pickle-security-problems-and-solutions/)

当我在熨斗学校进行我的数据科学期末项目时，我遇到了这个问题。所以经过一番努力，我想到了一个解决方案，创建一个 pickle 函数，它将打开一个预先保存的 pickle 文件，遍历一个 API，并将从 API 提取的数据转储到 pickle 文件中。

我将解释我的项目和我遵循的逻辑，并提供注释代码。

我正在完成的项目要求我使用 [pushshift.io](https://pushshift.io/) 工具从 subreddit 社区线程中获取 reddit 文本数据。我正在处理的数据的结构是{post_id : [comment_ids…]}.

但是在运行下面的功能之前，我必须将我的 post _ ids 和评论 id 加载到我的 Jupyter 笔记本中。你会在下面看到包含这个数据的变量的名字是 **comment_dict** 。此外，我需要创建一个 pickle 文件，其中保存了来自 **comment_dict** 的至少一个 post_id/comment_id 的文本数据。所以当我在我的函数中加载 pickle 文件时，它实际上是有内容可加载的。预先保存的 pickle 文件被标记为 **data_denier2.pickle** ，因为这个标签在我的项目中使用过。一旦所有这些都在您的笔记本中完成，pickle 文件存在，您就可以执行我提供的功能了。

从导入必要的库开始。

```
import pickle
import requests
import pandas as pd
import numpy as np
import time
import random
from tqdm import tqdm_notebook
```

现在您已经导入了所需的库，您可以跳转到数据选择器函数。

```
def comments_pickler(comment_dict):

    #load the existing pickle
    comment_data = pickle.load(open('data_denier2.pickle','rb')) 
    #keys to keep
    keys = ['author', 'body', 'created_utc', 'id', 'parent_id', 'score']

    #browser bug fix added, may be removed if deemed unnecessary
    headers = requests.utils.default_headers()
    headers['User-Agent'] = 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/56.0.2924.87 Safari/537.36'

    #tqdm_notebook tracks progress of the data extraction
    #comment_dict contains a post_id (key) and a list of comment_ids (value)  
    #we are grabbing the comments from the comment_ids
    for key in tqdm_notebook(comment_dict):
        #in case code breaks, this if statement will 'continue' until the last dictionary key
        if key in comment_data.keys():
            continue
        #container for future list of dictionaries
        x = []
        #pause this list over here
        sleep_counter = 0 # set counter back to zero once the key changes

        for value in comment_dict[key]:
            try:
                response = requests.get(f'[https://api.pushshift.io/reddit/comment/search?ids={value}'](https://api.pushshift.io/reddit/comment/search?ids={value}'), headers=headers) 
                #performing randomized sleep every 20 iterations to avoid maxing out api calls
                sleep_counter += 1
                if sleep_counter == 20:
                    sleep_counter = 0
                    seq = [i/10 for i in range(5,15)]
                    time.sleep(random.choice(seq))        
            except Exception as e:
                print(e)
                print('key:    ' + str(key))
                print('value:  ' + str(value))
                continue

            try:
                data = response.json()          
            except Exception as e:
                print(e)
                print('key:      ' + str(key))
                print('value:    ' + str(value))
                continue

            #dictionary comprehension extending the 'data' value from dictionary to list of dictionaries, x
            x.extend([dict((k, data['data'][0][k]) for k in keys if k in data['data'][0])])
        comment_data[key] = x
        #save the data obtained from this key, and jump to the next key
        pickle.dump(comment_data,open('data_denier2.pickle','wb'))
```

这个函数的逻辑是，我将遍历一个列表字典( **comment_dict** )，最终*扩展*一个字典列表( **data_denier2.pickle** )。本词典( **comment_dict** )包含 id。这些 id 一旦转换成 **data_denier2.pickle** 就会变成文本数据。

我加入了一些特性，比如一个随机化的计时器以避免 api 耗尽，try 和 except 语句读取和运行任何错误，tqdm_notebook 跟踪数据提取的进度，以及一些字典理解以将 api 中的数据整理成一种可用的形式，用于包含所有文本数据的最终 pickle 文件。

最终，我使用的步骤流程和逻辑应该作为数据科学家的指南，以便他们可以高效、及时地保存他们的数据。希望这有所帮助！