# 在线回溯测试中的数据问题

> 原文：<https://medium.datadriveninvestor.com/data-problems-in-online-backtesting-dc4cf54933dd?source=collection_archive---------19----------------------->

![](img/45f3f1aa29ab779346d757fdb4181772.png)

Market Data

我对 Quantopian 这样的在线回溯测试工具的最大问题是数据的不可见性。

你可以使用这些数据，但是必须在有限的环境下，在(对我来说)不合适的 IDE 或者在线 Jupyter 笔记本中。

你不被允许下载任何东西，更不用说数据了，所以你永远也不能按照你的意愿重新安排和检查数据。

当然，所有这些都是可以理解的，因为提供商不希望他们的数据被窃取。然而对于用户来说非常不方便。

当我在观察一个系统时，我经常想观察一只股票的一小部分数据。我想把它放在我自己的笔记本电脑上，并能随心所欲地操作它。我会经常将它导入 Excel，并在 Jupyter Lab 中经常使用它。

抛开在简单的在线 ide 中进行充分调试的几乎不可能不谈，我只是对数据限制感到盲目。

Hot Chili Analytics 背后的想法是拥有自己的云托管虚拟计算机，装载你需要的所有软件。更重要的是，您需要的数据，以您需要的格式。

再也不会因为无法在自己的电脑上按自己的要求查看和操作数据而感到沮丧。

目前设置为使用历史基础上的每日数据(以及实时交易的盘中数据)，我们将快速移动以适应更高分辨率的数据——很可能在适当的时候降至分笔成交点数据和出价数据。

HCA 使用 zip line——这对于很多很多花了几年时间学习 Quantopian 优秀开源代码的人来说是一个巨大的优势。

注册免费层，告诉我们你的想法。帮助我们开发您需要的产品。