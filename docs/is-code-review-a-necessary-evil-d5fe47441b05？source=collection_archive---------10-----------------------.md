# 代码审查是必要之恶吗？

> 原文：<https://medium.datadriveninvestor.com/is-code-review-a-necessary-evil-d5fe47441b05?source=collection_archive---------10----------------------->

![](img/8281473a6fa348124ea7a689d1fbd45d.png)

Photo by [Joshua Reddekopp](https://unsplash.com/@joshuaryanphoto?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

代码审查是一个有争议的问题。如果你询问移动应用程序开发公司，你会听到各种各样关于它的事情，从“不公平”和“不合理的昂贵”到“激励”，甚至是“有利于工作场所文化”。事实上，它可以是所有这些东西，甚至更多。和其他工具一样，只有在正确使用和微调之后，它才能发挥作用。

# 为什么要进行代码审查

有了像[无代码开发](https://techatlast.com/low-no-code-future-enterprise-mobile-app-development/)这样的好趋势，人们可能会认为代码评审已经成为过去。而且，考虑到它需要多少资源，对于预算紧张的[项目来说，代码审查可能成为一个真正的问题。](https://medium.com/datadriveninvestor/how-to-develop-a-mobile-app-on-a-tight-budget-5-major-cost-saving-tips-d394fed7ac20)

与此同时，跳过它会有可怕的后果。根据 NIST 的[报告，修复缺陷的成本在开发周期的每个后续阶段都会成倍增加。因此，举例来说，如果您在编码过程中未能捕捉到一个主要的错误，那么在验收测试过程中您将花费三倍以上的成本，在生产过程中您将花费六倍以上的成本。](https://www.nist.gov/document/report02-3pdf)

即使您准备通过向 bug 砸钱来处理它们，仍然有很好的理由来执行代码审查:

*   一致性:定期的评审有助于保持代码库的一致性，简化有迁移性开发人员的大型团队的任务。
*   **结构问题**:除了失误和意外错误，评审还能有效地发现死代码和内部团队成员没有注意到的类似问题。
*   **知识共享**:向开发团队传达评审结果将会提炼他们的专业知识，并作为有价值的见解来源。
*   **动力**:简单地知道有人会检查你的工作会让你保持专注和动力去做得更好。
*   **符合性**:代码审查对于完成[产品批准过程](https://cofounderstown.com/ios-vs-android-mobile-app-approval-ab958)是不可或缺的(通常是强制性的)。

# 何时不使用

公平地说，代码审查仍然不是万能的解决方案。在很多情况下，过度依赖 it 会导致效率低下甚至适得其反。例如，时间框架短的小规模项目不会从[开发过程](https://medium.com/datadriveninvestor/mobile-app-development-process-explained-by-professional-developers-in-singapore-4da47d0d6c0b)的整个额外阶段中受益，并且可能仅仅通过遵循良好的编码实践就可以做得很好。对于那些有明确目的的应用程序来说也是如此，这些应用程序并不意味着随着时间的推移而扩展或增长(只要项目的范围是现实地确定的)。

过度依赖代码审查是另一个问题。虽然它可以极大地提高产品的质量，[移动应用开发公司](https://swagsoft.com.sg/)不应该将它视为唯一的质量保证政策，甚至是主要的政策。换句话说，从一开始就写好代码同样重要。

最后，还有划清界限的挑战。一旦代码评审过程不受检查，它可能会成为一个目标，导致评审者仅仅为了它而要求变更。这不仅会延长已经非常耗时的过程，还会挫伤开发人员的积极性。毕竟，如果你无论如何都要重新开始，那么尝试是没有用的，所以在设定质量标准时要具体，并适度应用。

# 从代码评审中可以期待什么

代码审查是开发过程的一个特定方面。然而，当适当地整合到工作流程中时，它实际上可以对工作场所文化产生一系列有益的组织规模的影响。

1.  **提高质量标准**:上面提到的激励效应实际上可以传播到其他工作领域，培养对质量承诺的心态。
2.  **加强安全性**:公平的审查将促使开发人员超越[安全最佳实践](https://medium.com/the-research-nest/mobile-app-security-best-practices-you-cant-ignore-man-eef030cd32e5)，并通过创造性的方式解决漏洞，从而超越审查人员的期望。
3.  **促进团队合作**:组织良好的反馈是磨练解决冲突技能的好地方，可以用来改善整个工作场所的氛围。
4.  **促进开放性**:习惯于提供你的作品以供评论，有助于将这种想法应用到其他领域，而不是将其视为威胁。
5.  **提供满足感**:因出色的工作而获得应得的荣誉实际上是一种[强大的社会动力](https://positivepsychology.com/improving-motivation-at-work/)，从长远来看，可以在团队成果上创造奇迹。

# 如何做得更好

尽管有这么多好处，但代码审查肯定是冗长且耗费资源的。如果您注意到它在工作流中的负载与所做的努力不相称，仍然有方法来改进它。首先，尝试在评审者之间平均分配负载。一些 [](https://swagsoft.com.sg/) 开发公司甚至选择在整个团队中分担这个任务来消除瓶颈。

第二，确定关键阶段，如上游合并，并确保每个阶段都有相应的审查。最后，确保评估过程以激励而非恐吓的方式呈现，以利用同事压力的积极影响。

# 最后的想法

如你所见，代码审查不是最终的 QA 解决方案。事实上，它甚至不适合每一个项目。所以，和其他工具一样，它应该被小心而精确地使用。你不能简单地把它扔在项目上，然后等待结果，然而通过一些微调，你的努力将会得到回报。

*视觉演职员表:*[*https://giphy.com/*](https://giphy.com/)

最初发表于[https://prototypr.io/post/is-code-review-a-necessary-evil/](https://prototypr.io/post/is-code-review-a-necessary-evil/)