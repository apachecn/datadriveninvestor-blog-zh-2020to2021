# 构建对话流聊天机器人 Lilis 1:聊天机器人服务员最基本的产品功能是什么

> 原文：<https://medium.datadriveninvestor.com/build-dialogflow-chatbot-lilis-1-what-are-the-top-seven-minimum-viable-product-features-of-a-998d6bfb60e7?source=collection_archive---------10----------------------->

## 如何使用 Dialogflow 构建和部署咖啡订单聊天机器人 Lilis

![](img/e7fce178839630401cd24ddfa2035fb9.png)

Build and Deploy Coffee Order Chatbot Lilis

想象一下，你走进一家星巴克，没有人，只有一个聊天机器人女服务员 Lilis 忙着为你点餐。这种最低可行产品(MVP)的七大必备特征是什么:一个聊天机器人服务员/女服务员？

在我们进入技术细节之前，让我们快速演示一下 chatbot Lilis。Lilis 是用 Dialogflow 构建的，部署在 Google Assistant 上。用户可以通过说出“与咖啡点餐聊天机器人 Lilis 交谈”来激活它

a quick demo of coffee order chatbot Lilis

# 聊天机器人服务员的七大 MVP 特征

如演示中所示，在咖啡店或餐厅工作、接受客户订单的聊天机器人服务员必须具备以下七个特征，才能被视为最基本的可行产品:

1.  意图检测和空位填充来解释来自客户的订单。
2.  处理一个订单中的多个项目，并向客户提供订单列表。
3.  更改商品或取消订单，允许客户更换商品或取消订单。
4.  常见问题解答/知识库，用于回答与业务相关的客户问题。
5.  多种语言的语音输出，以利用文本到语音(TTS)技术。
6.  结束对话以完成订单并避免循环。
7.  部署到 Google Assistant、Slack、网站或其他平台。

比如“两杯大杯冰咖啡，不加糖。”将触发 Dialogflow agent 中定义的的 intent *order.start* ，参数将被解码为

*   *咖啡-数量= 2*
*   *coffee-size = 'large'*
*   *coffee-type =‘冰咖啡’*
*   *咖啡-说明=‘无糖’*

# 莉莉斯的建筑

![](img/217123e82197ed9ea84b8923e6553253.png)

*   绿色圆角矩形代表对话流中的 ***意图***
*   黄色圆角矩形代表 Dialogflow 中的 ***参数***
*   红色圆角矩形代表 Dialogflow 中的 ***响应***
*   虚线边框表示这是一个可选步骤

# 如何使用 Dialogflow 构建和部署咖啡订购聊天机器人 Lilis

语音助手/聊天机器人是未来。人口老龄化、劳动力萎缩，以及聊天机器人在计算、记忆、免疫等方面的优势，正在引导世界走向机器人与人类合作改造行业的未来。作为一名开发人员或 NLP 技术爱好者，我们能做的就是在预见到趋势后尽快采取行动。

如何使用 Dialogflow 搭建咖啡点餐聊天机器人，并部署到 Google Assistant？以下实践课程将介绍聊天机器人 Lilis 的架构和对话流技能，包括:

*   如何设计和训练意图
*   如何使用上下文在意图之间传递变量
*   用 javascript 实现编码来处理复杂的意图和响应
*   使用知识库回答客户的常见问题(FAQ)
*   测试并部署到具有选定语音功能的谷歌助手

Build Dialogflow Chatbot Lilis

本课程中的相同技能集可以应用并扩展到为餐馆和零售建立聊天机器人。关注我的媒体以获取未来的更新，如果您有任何问题，请在下面发表评论，并将链接分享给对构建语音助手感兴趣的朋友。下一篇文章再见🤖：

![](img/c4dea6d79ee9148851692b77cb46c9e4.png)

[https://www.youtube.com/playlist?list=PLbd_cZnEWl9BNQEq29DHZAJ-84oMOCGaW](https://www.youtube.com/playlist?list=PLbd_cZnEWl9BNQEq29DHZAJ-84oMOCGaW)

# 构建对话流聊天机器人 Lilis 2:如何构建和培养接受客户订单的意向

**进入专家视角—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)