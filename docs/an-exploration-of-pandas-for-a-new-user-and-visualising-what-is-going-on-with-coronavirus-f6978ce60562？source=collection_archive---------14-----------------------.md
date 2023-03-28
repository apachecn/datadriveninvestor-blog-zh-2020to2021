# 为新用户探索熊猫，并可视化冠状病毒正在发生什么

> 原文：<https://medium.datadriveninvestor.com/an-exploration-of-pandas-for-a-new-user-and-visualising-what-is-going-on-with-coronavirus-f6978ce60562?source=collection_archive---------14----------------------->

![](img/eb6234243bbf93f410419e0906571208.png)

Photo by [Sid Balachandran](https://unsplash.com/@itookthose?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

我已经学了几个星期的 Python，最近对熊猫有了更多的了解。

> 在计算机编程中， **pandas** 是为 **Python** 编程语言编写的软件库，用于数据操作和分析。特别是，它提供了数据结构和操作来操作数字表和时间序列。它是在三条款 BSD 许可下发布的自由软件。

由于冠状病毒是所有的新闻，我认为这将是很好的尝试和可视化的一些数据。

[](https://www.datadriveninvestor.com/2019/02/07/8-skills-you-need-to-become-a-data-scientist/) [## 成为数据科学家所需的 8 项技能|数据驱动型投资者

### 数字吓不倒你？没有什么比一张漂亮的 excel 表更令人满意的了？你会说几种语言…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/07/8-skills-you-need-to-become-a-data-scientist/) 

我从安装 jupyter 笔记本和创建一个新项目开始。然后我寻找一个可以收集数据的来源。我选定了这个来源:[https://raw . githubusercontent . com/datasets/新冠肺炎/master/time-series-19-covid-combined . CSV](https://raw.githubusercontent.com/datasets/covid-19/master/time-series-19-covid-combined.csv)，它列出了我感兴趣的字段:

*   国家
*   日期
*   确认的
*   恢复
*   死亡

![](img/6e3e431e2db7fbc03e62e96814aaaf24.png)

Photo by [CDC](https://unsplash.com/@cdc?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

我一直在 jupyter 和 pandas 文档之间来回切换，我确实设法得到了一些有趣的信息，其中一些有点奇怪，但我想我需要更多地使用它。

```
import pandas as pd
import matplotlib.pyplot as plt
import io
import requests
url="[https://raw.githubusercontent.com/datasets/covid-19/master/time-series-19-covid-combined.csv](https://raw.githubusercontent.com/datasets/covid-19/master/time-series-19-covid-combined.csv)"
s=requests.get(url).content
dataset=pd.read_csv(io.StringIO(s.decode('utf-8')))dataset.columns
```

这将输出数据帧的列列表

```
['Province/State', 'Country/Region', 'Lat', 'Long', 'Date', 'Confirmed', 'Recovered', 'Deaths']
```

然后我想看看数据框中的国家，只是为了检查我正在处理的信息

```
dataset['Country/Region'].unique()
```

这导致了

```
['Mainland China', 'Thailand', 'Japan', 'South Korea', 'Taiwan', 'US', 'Macau', 'Hong Kong', 'Singapore', 'Vietnam', 'France', 'Nepal', 'Malaysia', 'Canada', 'Australia', 'Cambodia', 'Sri Lanka', 'Germany', 'Finland', 'United Arab Emirates', 'Philippines', 'India', 'Italy', 'UK', 'Russia', 'Sweden', 'Spain', 'Belgium', 'Others', 'Egypt', 'Iran', 'Lebanon', 'Iraq', 'Oman', 'Afghanistan', 'Bahrain', 'Kuwait', 'Algeria', 'Croatia', 'Switzerland', 'Austria', 'Israel', 'Pakistan', 'Brazil', 'Georgia', 'Greece', 'North Macedonia', 'Norway', 'Romania', 'Denmark', 'Estonia', 'Netherlands', 'San Marino', 'Belarus', 'Iceland', 'Lithuania', 'Mexico', 'New Zealand', 'Nigeria', 'Ireland', 'Luxembourg', 'Monaco', 'Qatar', 'Ecuador', 'Azerbaijan', 'Czech Republic', 'Armenia', 'Dominican Republic', 'Indonesia', 'Portugal', 'Andorra', 'Latvia', 'Morocco', 'Saudi Arabia', 'Senegal', 'Argentina', 'Chile', 'Jordan', 'Ukraine', 'Saint Barthelemy', 'Hungary', 'Faroe Islands', 'Gibraltar', 'Liechtenstein', 'Poland', 'Tunisia', 'Palestine', 'Bosnia and Herzegovina', 'Slovenia', 'South Africa', 'Bhutan', 'Cameroon', 'Colombia', 'Costa Rica', 'Peru', 'Serbia', 'Slovakia', 'Togo', 'Vatican City', 'French Guiana', 'Malta', 'Martinique', 'Bulgaria', 'Maldives', 'Bangladesh', 'Moldova', 'Paraguay', 'Albania', 'Cyprus', 'St. Martin', 'Brunei']
```

![](img/4179fddac7832259b33cb7e84e306d4e.png)

Photo by [T.H. Chia](https://unsplash.com/@teckhonc?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

太棒了，所以我想把列限制在我想要的范围内，所以我运行了这个:

```
a = dataset[['Country/Region','Date','Confirmed','Recovered','Deaths']]
a.head().to_csv()
```

这导致了

```
,Country/Region,Date,Confirmed,Recovered,Deaths
0,Mainland China,2020-01-22,1,0,0
1,Mainland China,2020-01-23,9,0,0
2,Mainland China,2020-01-24,15,0,0
3,Mainland China,2020-01-25,39,0,0
4,Mainland China,2020-01-26,60,0,0
```

现在我需要将指数改为日期，然后在数据框中为每个国家绘制一个图表，显示确诊、恢复和死亡人数

```
b=a.set_index('Date')
for country in b['Country/Region'].unique():
    c=b[b['Country/Region']==country]
    c.plot(title=country)
    plt.savefig(country+'.png')
```

我发现我第一次跳到熊猫身上很酷，不管怎样，这是我制作的图表！

![](img/0a6731e9fbb754df7fec93e872284564.png)![](img/fdb287e9ea04f79886f38fd10d845358.png)![](img/113450635dd3e9d49d4b811e8426d77a.png)![](img/089cb7254c5a8451835199d6befeb939.png)![](img/61521cc95b5911244709ae88f9956605.png)![](img/a1fb319edecc66507d84aadbf3d70354.png)![](img/2006b2697dbda45e7160ddea556c309d.png)![](img/7a6f54c3245201663fb3fece437abd20.png)![](img/8da562d99a903262f25ba62b4279b2d9.png)![](img/81fc65d32c6d6c92466d998d1c76e6c8.png)![](img/a8ff11fc3d20bde2eb69910f2e653ebf.png)![](img/27d44f152b4032c5a253d0efc320256e.png)![](img/9682f82d93f778b0fb7437de4a5961f6.png)![](img/18c5ace5930f94d1c43fbfca7d2b47ea.png)![](img/dae3b288f62775c703ec62a810bb4ca7.png)![](img/d0c26f02705661ba4dccfbe1767f8ca1.png)![](img/37c7ac0384db116190b28d374d0833ec.png)![](img/278073558568383e60bc94757a84f4b0.png)![](img/8f73381fbc78fef4b9a263b30ccc254e.png)![](img/f189f05cb2c7f74985d7335a56f07800.png)![](img/2bd04b9cd8bb9180c7160555f4f787e1.png)![](img/995ee5e2510b86b29b4f1e0d82bf3063.png)![](img/617b4908c90699d55a6c90f4bfea67f6.png)![](img/a95354d0c5d4123e569c26bf0ed61c1b.png)![](img/8ed7436136bdf07eebc7c25e6660e8c1.png)![](img/209b4988658d4fae89e80673ce9073a7.png)![](img/e806e9906e133ee4f8e271f5bb48a0bd.png)![](img/cc2d598bae8ba1f09d68ebc4f98e37cd.png)![](img/a0c2af618d5f415a8a268a6766076423.png)![](img/a88afbb96284a8e20b47080951b40cfe.png)![](img/f26efe0397f1ae8f6e98fefef9ec6371.png)![](img/6b991511253ad22df48fd0ca37a29b71.png)![](img/08faeea8a13c342b6d747afa4af0730f.png)![](img/a8b0c156df382c69b1e13419e3446d52.png)![](img/c28f22691d96ea0be41753f8a94ba86f.png)![](img/b993a2cd45237b89aba924f4326180eb.png)![](img/d6f32b97306fbafdf3db1175c2bbf949.png)![](img/a59066ebd2a5bc8f7792c77bf0bed2cd.png)![](img/bfcb576a5eda6372998147fa7df08394.png)![](img/097411bad3fd5354ddc84a3f3fe9dd7d.png)![](img/dd3d3a75e9b2f307a363c33a09331e9e.png)![](img/3b55caf9b1b615c0c065329857438ad9.png)![](img/277c8d37e616fa90e74fd88caa305bbd.png)![](img/000c8360f1568c3c05fb0bd4c0627ba3.png)![](img/6f756f15c62ca16e5dc53a4e6e23d08d.png)![](img/f481bd8fceda42631051055b89742df1.png)![](img/aed6543bdda3f5a25f413926df70f5f8.png)![](img/b9d2da8eee31b2c445e4a4a0eb63eb69.png)![](img/5310efe1bb487ef16cf95ff0e7bd22fa.png)![](img/84bb606167722e2ad1f757b176713e35.png)![](img/90a0ef57239bbbede902da8d7be7b427.png)![](img/815e272ac0927182ea29aec28bb36b8e.png)![](img/834e86e229d32fc89e12e56a64f53878.png)![](img/30840ab99669c2650a50b444efcf6d80.png)![](img/4cd4cf3c6b8c61d283364a78c2aabcf4.png)![](img/28a383f7bf2662b7b497dbc36da8198b.png)![](img/2acbbf6ada2a059a20e8ca6b7059ee56.png)![](img/73bd8e2ee209d21ac9146e44f9ce3fd1.png)![](img/955b864d9cb7c3a31f4224613b70c18f.png)![](img/394eccc16c9aeb1d26c9988780a7a24d.png)![](img/6dae07e6d8f3ac8e0cb7d10b07be45d7.png)![](img/a08810931931e31b0e600e1cad15e30f.png)![](img/108174bd6dbf78d3b881e12c471ec5a4.png)![](img/d42da612bc75433a543c76755c46f72b.png)![](img/1c7e43d898f2e1d25b3beb95618cded2.png)![](img/9f6e26d8f807d886cae6f9a8ee529f6e.png)![](img/0f7fd1b593ab84be7cd1862aa95a5108.png)![](img/7c3036f82c9599e05dff15cc26ef5eaa.png)![](img/f93930948149eaf509c396d9a38aaa65.png)![](img/fa781e5e0a520a335fbb05092a2dfff1.png)![](img/545693a0a1745b20e8483b64cfefc6b0.png)![](img/4b6f49509aa133b2e3a8756a47bd9556.png)![](img/b38969f6e3d198b28847c3c2a50a2095.png)![](img/81dc5c8a19ad9a334e1b98233a535d07.png)![](img/27847416c7e2073abfd38b2e2d291124.png)![](img/12d37e4e248ea454e528d26de64413c7.png)![](img/c15439e4627b44a3e474f154903c17e5.png)![](img/4b89f48b8fa5a303dad83ff50a5cf7b8.png)![](img/2704811dac3539024fece639f07418ba.png)![](img/afab08aabeb588924a11458149040595.png)![](img/6e353a77ee24f0bf6c36a397b5b04d8d.png)![](img/a549e095408fbcdaf2f98a73dc7c8aec.png)![](img/f7618b646234dfe5c7db158d27c12ab9.png)![](img/87a531c351720dab2db2de0c74d6a7ca.png)![](img/f173f2170f0041f74fe4ed1427439b1a.png)![](img/4127f49bc21e91f23e98a176d0c0d601.png)![](img/898cc3fd6240958570cb430abd47b617.png)![](img/3f54751978778840036699f34f51d336.png)![](img/1c518174ad3a3551891b32adc4016123.png)![](img/8ad7f58ccbad6473e04114a6a031853a.png)![](img/ef81c8d5b88c87a0cf1bdb2f3ecbb0eb.png)![](img/cfa01318c66210d2b6d6e3a5bf48e2f5.png)![](img/0aacd8fe5852cb0fdcf97df2d4736982.png)![](img/de9d08de53503a2f4e136bf8907ae43b.png)![](img/ed6355c339ef895f55df782cc1425726.png)![](img/f68e428231b0814a3f4801d8592dbe13.png)![](img/146e252f7ae9ca3e48a2877d7e76c039.png)![](img/29bee233681c2bac7d98f8362d800931.png)![](img/95a39210ecbc36f52cba3881822fbfc5.png)![](img/db6f954dadce0596c7b255c5643e4738.png)![](img/f36033db35e0f2cc9254af3643da8abf.png)![](img/e65f62dc464d9cebfd8274c8ebc65d23.png)![](img/eac7425b60592c8e0898ac56601bd70c.png)![](img/939816dfc71cff85d7b1a6ee389d4995.png)![](img/d46865d03c9ae3318265c6faa9f3c14c.png)![](img/7e65dc5ca384f2ee40a8ce662b43709b.png)![](img/f2da5eb9c5bc9cb67e12ad436c485a01.png)![](img/809efe928c6f545f737140b245bf9b7f.png)![](img/23f160d67433771f8695d9ac9ebf93b0.png)![](img/bbeaaf958399a54937c414aeacaa7682.png)![](img/b80654191c750b32a1c592d6a965c6f8.png)

然后我尝试了一些不同的东西