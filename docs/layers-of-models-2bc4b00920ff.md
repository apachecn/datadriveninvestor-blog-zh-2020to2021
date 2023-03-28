# 模型的层次

> 原文：<https://medium.datadriveninvestor.com/layers-of-models-2bc4b00920ff?source=collection_archive---------27----------------------->

![](img/7b21787da9c97ad982526463f8005c24.png)

Photo by Miami Fashion Photographer James Santiago

在我第一次参加拉斯维加斯的亚马逊创新大会期间，我对一个讨论亚马逊如何在 Echo 和 Alexa 产品上处理语音识别的会议很感兴趣。本质上，这项服务将不同的演讲瓶分层。

[](https://www.datadriveninvestor.com/2020/10/08/voice-isnt-dead-how-ai-is-changing-the-call-tech-game/) [## 语音没有死亡——人工智能如何改变呼叫技术游戏|数据驱动的投资者

### 语音死了吗？这是一个公平的问题。关于流程数字化、新应用和增强型移动银行的讨论…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/10/08/voice-isnt-dead-how-ai-is-changing-the-call-tech-game/) 

在最高级别，有一个全球模型来处理特定方言的语音交互。告知该模型是考虑了用户已经订阅的不同技能的次要模型。最底层是一个根据用户的声音和他们如何措辞来训练的模型。语音识别模型分层的结果是提高了准确性和更好的用户体验。

虽然为语音模型的分层添加滤波器看起来很直观，但这种实现看起来更像一门艺术。对其中一层赋予过多的权重会导致有害的体验。对于我可能出现的某些情况，保持平衡是很重要的。

一种情况是当一个用户的口音非常明显地来自我们的母亲，用一套方言说话。另一个是当用户试图访问的应用程序、动作或技能提供了一组实体和意图，这是一个消除歧义的挑战。第三种可能的情况是，当用户群模型训练不当时，可能是用户感冒了，导致性能下降。

另一方面，分层可以带来更好的用户体验。即使语音识别没有显著提高，意图识别也会随着第一次尝试就获得正确请求的成功率而提高。然而，设计人员需要测试以确保持续的性能改进。

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)