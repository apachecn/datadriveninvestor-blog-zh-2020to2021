# 我连续 5 天每天创建一个数据集

> 原文：<https://medium.datadriveninvestor.com/i-created-a-dataset-each-day-for-5-days-624bcb74bc31?source=collection_archive---------20----------------------->

以下是我到目前为止学到的…

![](img/b2e1872b610e1489863213926063a78e.png)

Source: Pixabay, Pexels.com

如今，我看到了许多挑战，如#66DaysOfData 和#90DaysOfCoding，人们挑战自己在如此短的时间内从头开始学习任何东西的成功故事。有了这么多的选择，选择正确的挑战或创造自己会变得更有挑战性。我决定创造我所能想象的**最难的挑战**:连续 5 天每天使用纯网络抓取创建一个数据集。规则是这样的:

*   **不允许导入**ka ggle 数据集。
*   API 访问也被禁止。
*   没有**花哨的** Python 包，不应该有允许你在一行或任何地方访问内容的函数。
*   同样，没有**内核或者笔记本**，只有纯脚本。
*   你需要决定白天做什么，**没有明天的计划。**
*   你必须选择一个比昨天更难的挑战，每天**。**

**这对我来说简直是一个不可能的挑战。这就是我选择它的原因。这些都是我真实的经历，没有夸张，没有欺骗。**

**我的偏好:**

*   ****脚本语言:** Python**
*   ****刮削工具:**硒(如有必要，请求)**
*   **编码环境: PyCharm**

**注意:我创建数据集只是为了教育目的。如果您有关于数据政策的问题或顾虑，请在此留下私人留言。**

**![](img/e3ee266fde896c8c55b6bf6b82598c46.png)**

**Source: Matt Howard, Unsplash**

**让我们继续我的 5 天旅程吧。**

# ****第 1 天——一个平稳的开端****

**我随便选了一个话题:“MBTI 类型”。幸运的是，我发现了一个没有任何活动迹象的老派约会论坛:Project Evo love([http://www.projectevolove.com/](http://www.projectevolove.com/))。从一个程序员的角度来看，这是一个无价的礼物。没有复杂性，只是纯粹的 CSS 和 HTML 操作，一致的类和名称。这是一个很好的初级练习:**

```
from selenium import webdriver
driver = webdriver.Chrome(executable_path=<path>) # opens a new chrome driver 
# <path>: path to the chrome driver appdriver.get(<url>) # opens the given web pagedriver.quit() # closes the current driverdriver.find_elements_by_css_selectors(<selector>)# returns a list of element objects# "#<id>": id selector
# ".<class>": class selector
# "<element>": element selector 
# "<parent> > <child>" direct child of parentelement.get_attribute(<attr>) # returns the attribute

# "innerHTML": HTML code of elements inside of the element
# "innerText": The content of element as string
# "href" (if element is of "a"-type): returns link of "a"-element
# "outerHTML": HTML code of element
```

**我一次就刮了论坛的每 500 页。数据收集需要 2-3 个小时，在 Kaggle 上发布一个小时。很简单。**

**第 1/5 天**

*   ****时间段:**3-4 小时**
*   ****改进:** Selenium 基础和 Chrome 开发工具**

**[](https://www.kaggle.com/yamaerenay/mbtitypes) [## MBTI 类型和九格图文本

### 按类型/主题分类的真实人物的文本

www.kaggle.com](https://www.kaggle.com/yamaerenay/mbtitypes) ![](img/d548aae5d027f0ed1fa34981eb5c988d.png)

Source: Patrick Tomasso, Unsplash** 

# ****第二天——我们又来了****

**我认为我发布的数据太小，不够充分，这就是为什么我决定建立一个补充数据集。我选了一个看似规模很大的网站叫做 16 个性([https://www.16personalities.com/](https://www.16personalities.com/))，把昨天的游戏升级。搜集各种性格类型的资料并不难，我只用了 30 分钟就做到了。我得加点料。当时我觉得完全迷失了，我注意到网站的统计部分。刮全球性格类型分布:完美！但是等等，选哪个？**

**![](img/9be5df8622f13cc84c1dad8d9df2900a.png)****![](img/33408c04339fa5fc355c0eb170480c3c.png)**

**Question: Global Or Country?**

**如果你只是对全球发行感兴趣，那么不要犹豫，选择左边的选项。否则，选择总是正确的选项，因为**数据越大，数据集**越有价值。我从其他网站上抓取了国家列表，反复搜索国家，最终在一个小时内抓取了它们的分布。数据准备花了一个小时，最后我在 Kaggle 上发布了数据集。**

**第 2/5 天**

*   ****时间段:** 3 小时**
*   ****改进:**Python 中 I/O 操作的技巧和窍门，JSON 操作技巧**

**[](https://www.kaggle.com/yamaerenay/mbtitypes-full) [## MBTI 类型数据

### 包括世界统计，每种类型的信息和更多疯狂的东西...

www.kaggle.com](https://www.kaggle.com/yamaerenay/mbtitypes-full) ![](img/45af2e2ddfa25595b2deb905e75d3d4b.png)

Source: Javier Allegue, Unsplash** 

# ****第 3 天——从这里开始****

**这一天，我有很多与 uni 有关的作业和工作，所以我只有 2 到 3 个小时。经过 2 天纯粹而轻松的成功，我决定**改变观念**。够了个性的东西。我选了“网站统计”。这有点挑战性，因为很难找到合适的免费在线发布的信息。我发现亚马逊 Alexa([https://www.alexa.com/topsites/countries](https://www.alexa.com/topsites/countries))上发布的一份结构良好的表格数据显示了全球范围内最受欢迎的网站。同样的问题，又来了:**

**![](img/e2988e4113c766fcc8b626994b5c55eb.png)****![](img/481f97e7f3f819db11c0075bf56724d0.png)**

**Question: Global or Country?**

**你知道答案。花了 2 个小时才搜集到全部数据。数据争论和发布到 Kaggle 花费了 1-2 个小时。一天结束时，感觉就像一、二、三，嘣:我所做的就是找到相似的元素，保存到列表中，并将其转换为更结构化的格式，如 CSV。**

**第 3/5 天:**

*   ****时间段:**3-4 小时**
*   ****改进:**处理更动态的网站，更关注 Robots.txt 文件**

**[](https://www.kaggle.com/yamaerenay/top50websites) [## 各国最受欢迎的 50 个网站

### 2021 年 2 月]:关于最受欢迎的网站、国家排名等信息...

www.kaggle.com](https://www.kaggle.com/yamaerenay/top50websites) ![](img/dc7acd881a388cc2d96353a2f6f1d60d.png)

Source: Xhoni Mykaj, Unsplash

一天后，我想经历一些真正的挑战，这将我们带到第四天。** 

# ****第 4 天—另一个关卡****

**过去的 3 天只是文本，文本，文本…获取文本内容是没有大脑的，抓取图像很酷。是时候给它加点料了。决定哪个比**如何**难多了。我可以选择刮一个自由的股票网站，如 Unsplash 的任意类别-它可以是任何东西，从动物到人，从自然到时尚-。还有一个更难的选择:谷歌图片(【https://images.google.com/】)我毫不犹豫地选择了它。很难刮的几个原因:**

*   ****过度嵌套结构:**元素中的元素…在 HTML 级别开始**
*   **元素的机器生成的**id**:很难找到一般的用例**
*   ****无滚动，无数据:**需要实现向下滚动功能，以加载更多结果**
*   ****杂乱的**图像容器(大小不同)**
*   ****广告**显示为图像**

**我对汽车的浓厚兴趣促使我从 Carlogos.org([https://www.carlogos.org/popular-car-brands/](https://www.carlogos.org/popular-car-brands/))收集了美国最受欢迎的 50 个汽车品牌。通过快速搜索，我找到了保存图片的方法:我反复搜索了每个品牌的 100 张照片，抓取了图片的链接，并下载了图片，如下所示:**

```
from selenium import webdriver
import requests
from PIL import Image
import io
driver = webdriver.Chrome(executable_path=<path>)
driver.execute_script('window.scrollTo(0, document.scrollHeight)') # scrolls to the bottom of the page (document.scrollHeight: full height of shown part of the website)driver.find_elements_by_css_selectors(<path_to_img> > img) # returns list of images
img.get_attribute("src") # returns the list of links of images (different from "href" attribute of "a"-elementpage = requests.get(link) # returns the image on a new tab
image_bytes = io.BytesIO(page) # returns page in bytes
image = Image.open(image_bytes).convert('RGB') # converts bytes to images
with open(<fpath>, "w") as file:
  image.save(file, "JPEG") # saves image as JPEG file
```

**编码用不了多长时间:总共 2 个小时。当向下滚动直到找到 100 张图片时，程序需要很长时间来获得整个网页中所有图片的链接。**

**第 4/5 天**

*   ****时间段:** 4 小时**
*   ****改进:**滚动、下载图片**

**[](https://www.kaggle.com/yamaerenay/100-images-of-top-50-car-brands) [## 汽车品牌图片

### 50 大汽车品牌的 100 张图片(美国排名)及更多...

www.kaggle.com](https://www.kaggle.com/yamaerenay/100-images-of-top-50-car-brands) ![](img/400d43b77dc0aefa083887dba8b8a701.png)

Source: Joshua Earle, Unsplash** 

# ****第 5 天——再难不过了****

**第五天。我敢对自己说，不再有简单的东西，不再有简单的网站。Youtube:**

*   **不接受 **cookies** 不允许**
*   ****全新的**Youtube 自己发明的 HTML 元素(以 yt-开头)**
*   **(可能)高级机器人**追踪器****
*   **HTML **更深层次的开始****

**我挑战自己收集最受欢迎广告的**抄本**。感谢 Think With Google([https://www . thinkwith Google . com/marketing-strategies/video/leaderboards/](https://www.thinkwithgoogle.com/marketing-strategies/video/leaderboards/))排行榜，我可以很容易地找到广告，但是我无法找到与 Youtube 视频的外部链接进行交互的方法。**

**![](img/564be0bb20040290435e5e00f498516e.png)**

**Videos Playing Internally, Think With Google**

**我不得不使用 URL 查询在 Youtube 上进行搜索，如下所示:**

```
import urllib
urllib.parse.quote_plus("no more scraping")
=>"no+more+scraping"# and concatenate it with the base url
"https://www.youtube.com/results?q=no+more+scraping"
```

**在每个搜索结果中，我选择了第一个，这与它是否正确无关。然后我试图抓取自动生成的英文字幕，但 cookie 策略不允许我正确地这样做。以下是我尝试用更高级的方式来刮的技巧:**

*   **编码**时间间隔** `driver.implicitly_wait(<seconds>) or time.sleep(<seconds>)`(没用)**
*   **使用“http-request-randomizer”包访问来自不同国家的随机**代理**IP(由于一个我无法修复的驱动程序问题而无法工作)**
*   **从堆栈溢出复制粘贴高级代码(也失败了)**

**规则打破:然后我遇到了“youtube-dl”，一个漂亮的 Python 包，它允许你抓取 youtube 视频的内容，而无需处理 cookie 策略、僵尸检测问题、yt 元素。就这样。花了将近 30 分钟才找到大约。550 个视频。**

**第五天**

*   ****时间段:**7-8 小时**
*   ****改进:**使用“http-request-randomizer”的代理，selenium 和 time.sleep()的等待函数，youtube-dl 进行 youtube 抓取**

**[](https://www.kaggle.com/yamaerenay/most-popular-youtube-ads-20172020) [## 最受欢迎的 Youtube 广告

### 2017-2020 年 Youtube 热门广告信息(带字幕)

www.kaggle.com](https://www.kaggle.com/yamaerenay/most-popular-youtube-ads-20172020)** 

****旅程结束****

**![](img/d0866eaee3f7d7faeb552dbd672747cf.png)**

**My Datasets on Kaggle**

**5 天前，我还没有网络抓取的心态，**可能还没有**。这是一次无价的经历——从简单的表格数据开始，到更高级的主题。**

**值得注意的是，您只需要在特殊场合进行网络抓取。如果没有必要，**不要浪费你的时间**搜集，使用最实用的工具，例如，你可以下载公共数据集或访问免费的 API。**

**然而，如果你知道如何去做，它会派上用场，特别是当一个非常具体的任务被给出时，比如**

*   **“在哪里可以找到印度最受欢迎的前 50 个网站？”**
*   **或“说出耐克广告的前 5 个关键词”等。**

**它还能帮助你练习:**

*   **如何最有效地进行 I/O 操作**
*   **如何正确地与服务器交互**
*   **如何转换和构造数据类型**

**今天，我想从你这里得到的是**挑战你自己**，不管是哪种挑战。给自己设定一个目标，写下你的经历。如果你选择了我的挑战，你也可以试试:**

*   **暗网刮除**
*   **处理验证码**
*   **自动网络爬行**

**你可以自己尝试一下。祝# 5 刮痧日快乐！**

**![](img/4b2bf5a49fbc1348caac0d8ee8e3e857.png)**

**Source: Markus Spiske, Pexels.com**