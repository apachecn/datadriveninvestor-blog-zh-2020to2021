# 消除机器学习个性化的三个常见误区

> 原文：<https://medium.datadriveninvestor.com/three-myths-surrounding-machine-learning-personalization-9b1a7133e6db?source=collection_archive---------11----------------------->

![](img/d04f429cc9a3edc59196671ab8b84d63.png)

Photo by [Glenn Carstens-Peters](https://unsplash.com/@glenncarstenspeters?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

在我们对人工智能的未来和不可避免的奇点感到激动之前，我们应该清楚机器学习个性化(MLP)到底是什么。原来它*做的是*而它*做的是*很可能不是你想的那样。在接下来的文章中，我将尝试解释和消除我在阅读和与学者和实践者讨论 MLP 时看到的三个最常见的误区。

请记住，这些神话适用于协同过滤和个性化推荐的混合方法，它们依赖于[行为大数据](https://www.ncbi.nlm.nih.gov/pubmed/28632441)，构成了我们今天在行业中看到的大部分部署。

**误解 1: MLP 通过预测你的需求、偏好和欲望来工作**

这种误解是可以理解的，因为我们通常认为人既有内在的欲望、需求和偏好，也有外在的行为。如果我们使用*人*化这个词，那么我们可能会假设我们指的是一个人的内心世界的需求和偏好——那种独特的、个人历史、价值观、目标、欲望和需求的叙事汤，它让你成为 ***你*** 。但我们不是也不能。许多学术文章和谷歌、IBM 等公司的推荐系统专利都犯了这个错误。例如， [Basu 等人(1998)](https://www.aaai.org/Papers/AAAI/1998/AAAI98-101.pdf) 的一篇被大量引用的论文指出:

> 本文提出了一种推荐的归纳学习方法，该方法能够使用评级信息和其他形式的关于每个产品的信息来预测**用户偏好。**

或者另一个更近的例子，来自[约曼斯等人(2019)](https://onlinelibrary.wiley.com/doi/full/10.1002/bdm.2118?casa_token=C47RUc1WZykAAAAA%3AbOudGhEzXLbjSuTs6JwqKLMJu3Rau06Kld-AaVpMuZQZf6oUPpfvnFZYpBw2L3fej0GoYfp_r2zz9A) 的第一句:

> 计算机算法越来越多地被用来预测人们的偏好并提出建议。

[](https://www.datadriveninvestor.com/2020/03/24/encoder-decoder-sequences-how-long-is-too-long/) [## 编码器解码器序列:多长是太长？数据驱动的投资者

### 在机器学习中，很多时候我们处理的输入是序列，输出也是序列。我们称这样的一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/03/24/encoder-decoder-sequences-how-long-is-too-long/) 

我可以很快告诉你为什么这不可能是 MLP 的工作方式。*喜好*不买东西。*需求*不要点击广告。*欲望*不要搅动。人们*做*这些事情，这些事情以可观察到的行为形式被记录下来。在 MLP 使用的训练数据实际上只是你*观察到的*行为的一小部分，这些行为是由应用程序或设备的设计*提供*的，并且碰巧被测量到。然而，聪明的设计师和数据科学家可以收集正确的测量数据，从观察到的行为到心理状态做出相当准确的推断。

MLP 无法预测你的偏好的另一个原因是，我们没有办法知道你真正的偏好是什么。我们指的是你深思熟虑的、有意识的、口头报告的偏好，还是我们与进化祖先共有的那些无意识的目标导向的偏好？没有*基本事实*，我们无法计算损失函数，因此我们无法优化预测模型的参数以最小化该成本函数。

> 尽管存在这种差异，许多工业界和学术界的人似乎已经落入了激进行为主义的陷阱，不管他们是否意识到了这一点。

这里有一个更具体的例子。当你训练一个机器学习模型时，没有标有“需求”或“兴趣”的结果列，也没有这样一个变量可能具有的可能离散值的列表，例如“卫生纸”或“意大利之旅”相反，结果列将简单地显示“购买”或“增加”或“流失”,这些列的值通常为 1/0。这些都是非常狭义的行为，是之前精神状态的无限性的结果。但是，严格地说，精神状态并不等同于行为。(参见丹尼尔·丹尼特的[倒谱](https://en.wikipedia.org/wiki/Inverted_spectrum)思维实验，这是一个为什么行为的“意义”被过度决定的好例子。)

将一种行为与一种精神状态混为一谈是草率的想法，最糟糕的是，会让外行人相信机器可以预测他们的想法。MLP 不应该被误认为是心理预测理论。

神话 2:个性化推荐是你独有的

这个流言可能需要更多的解释，有几个角度，但我在这里只关注几个。在许多情况下，预测和建议是基于根据*聚合*数据训练(优化)的模型，这些数据甚至可能不包括任何*你的*个人数据。如果你可以说收到了一个“个性化”的建议或预测，那么这只是因为建议不是使用一个预先设定的列表，并一次给所有人。在互联网出现之前，广告大概就是这样做的，当时每个人都看到同样的广告牌和报纸广告。我们姑且称之为 MLP 的“天真观点”。

许多人似乎认为，如果数据表中的每一行都被分配了一个预测(而不是全局分配给每个人，比如说基于全局平均值)，那么该预测就是个性化的。但这是对个性化极其单薄的理解。个性化的概念值得更深入的研究。

## 评价个性化的新分类法

我建议我们考虑使用 1)数据或 2)模型，或者两者的某种组合的双重属性分类法来进行个性化。MLP 中使用的数据可以分为输入和输出属性。比如一个个性化推荐使用 X%的行为输入特征，或者是***GDPR***下归类为个人数据的输入特征比例。显而易见，个性化需要*个人数据*，个人数据根据特定的法律制度有不同的定义(例如， [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) 或 [CCPA](https://en.wikipedia.org/wiki/California_Consumer_Privacy_Act) 或 [FTC](https://en.wikipedia.org/wiki/FTC_fair_information_practice) 的公平信息实践原则)。

相反，我们可以通过参考**输出数据属性**来量化个性化程度，比如值的唯一性。更个性化的预测意味着更少的人分享相同的推荐。当然，一个让每个人都得到相同推荐的系统并不是真正个性化的(或者是吗？).这当然取决于排名列表的大小、库存大小以及你推荐的用户数量。

## 实质性与程序性个性化

观察个性化的另一个有趣的方式是考虑它是实质性的 T21 还是程序性的。我从政治哲学中借用了这个观点，在政治哲学中，学者们争论是程序正义还是实体正义更好。我将暂时回避那些棘手的问题。

实质性个性化是指**输出**的属性(例如，所有独特的输出)，而不考虑导致该输出的过程。过程个性化指的是**过程**(例如，所有的行都被输入到同一个过程中)，而不考虑这样一个过程可能产生的特定输出。这种区分很有用，因为可能会有这样的情况，我们有一组高度同质的数据主体，即使我们已经对每个唯一的数据主体的数据训练了一个模型，但我们最终得到的是相同(或非常相似)的输出建议。从局外人的角度来看，我们似乎没有个性化我们的推荐，因为几乎每个数据主体都得到了相同的推荐。

> 但是我们可以回答说我们的建议是*程序上个性化的*。

## 我们可能概念化的各种其他方式*个性化*

下面的列表既不是详尽的，也不是相互排斥的。我们可能会认为我们的个性化推荐是个性化的，因为它们结合了个人数据(根据 GDPR 定义),例如，每个用户都会收到一个*唯一的*推荐。

考虑到这一点，我们还可以根据用于生成预测或推荐的模型的**属性，将预测或推荐归类为个性化的。在最基本的层面上，仅仅使用用户自己的数据来为每个用户学习一个单独的模型似乎是非常个性化的，尽管对大多数组织来说并不实际。大多数数据控制者根本不会收集这么多的行为数据(…到目前为止)。这种观点的一个结果是，具有完全相同简档的用户将得到完全相同的模型。同样，这是一个基于*输入的* *程序性*而非实质性个性化的例子。**

我们可以采取的另一种方法是将个性化量化为模型参数值的唯一性。因此，如果我们的模型有不同的参数值，那么产生的预测是个性化的，即使*结果*是相同的。这将代表*基于输入的实质性*个性化。目前，大多数基于聚合数据训练的行业模型都不满足这一标准。

或者我们可以将个性化量化为用于生成预测的模型的*类型*:也许一些人会得到一个神经网络，而另一些人会得到一个随机森林。也许一些用户不太关心“最佳可能预测”，线性回归比深度神经网络更可取(它也更容易解释……)。只要数据主体被输入到分配特定模型的独特程序中，我们就可以称之为基于*模型的程序性*个性化，即使最终的推荐都是相似的(也许因为我们只能推荐一小部分项目)。

最后，也许个性化预测意味着为你生成个性化推荐的模型有一组*独特的输入特征*。随着 GDPR 下的数据主体选择退出特定形式的数据收集(例如，某些类型的跟踪 cookies 或 GPS 定位)，这种情况将会越来越多。您允许数据控制器收集的行为数据可能意味着您需要基于不同特征集的不同模型，这由监管压力决定。我们可以将这种情况归类为基于输入的实质性个性化的实例。

误解 3: MLP 比你自己(或你的朋友)更了解你

当研究人员和行业声称他们的 MLP 系统“优于人类”时，要保持警惕在某些情况下，研究人员可能人为地缩小了预测上下文的范围，使其更易于机器处理。这样做可以让 MLP 看起来比实际上更强大、更准确，尤其是在评估预测性能的时候。例如， [Yeomans 等人](https://onlinelibrary.wiley.com/doi/full/10.1002/bdm.2118?casa_token=C47RUc1WZykAAAAA%3AbOudGhEzXLbjSuTs6JwqKLMJu3Rau06Kld-AaVpMuZQZf6oUPpfvnFZYpBw2L3fej0GoYfp_r2zz9A) (2019)将朋友和配偶的预测与简单的协同过滤(CF)系统的预测进行了比较，以预测焦点用户对笑话的评级。研究发现，一个基本的 CF 系统比朋友或配偶能够更准确地预测。

然而，这个实验包括了由研究人员预先选择的 12 个笑话。从几乎无限的所有文化和语言的笑话集中选择 12 个笑话的困难得多的问题留给了人类。本质上，研究人员已经为研究中的每个受试者定制了一个笑话列表，给出了他们的语言背景、原籍国和当前位置。一旦缩小到如此小的推荐空间，该算法的性能似乎相当令人印象深刻，但仍然隐藏了最困难的任务已经由人类完成的事实。对于电子商务网站上的个性化，也可以提出类似的论点:通过访问一个网站，一个人已经自我选择加入了一个对该网站提供的产品感兴趣的群体。因此，当我们听到令人印象深刻的准确性或回忆分数时，我们需要记住预测上下文是多么具体和狭窄。

所以下次你看到吹捧一些新的个性化算法的论文或新闻稿时，问问自己到底是什么让这个*人*成为现实？这些预测在多大程度上考虑了一个人的社会和道德认同感以及自我叙述？他们声称它可以预测用户的兴趣吗？他们是否解释了它会根据输入数据、输出数据或模型的某些方面生成个性化预测？他们是否解释了围绕他们报告的准确性或回忆分数的预测背景？