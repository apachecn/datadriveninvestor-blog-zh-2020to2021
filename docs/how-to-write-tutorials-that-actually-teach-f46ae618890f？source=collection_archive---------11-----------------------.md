# 如何编写实际教学的教程

> 原文：<https://medium.datadriveninvestor.com/how-to-write-tutorials-that-actually-teach-f46ae618890f?source=collection_archive---------11----------------------->

## 几乎所有的教程都很烂。我们可以做得更好。

![](img/3472274f530b9f8adaca00741c72d7f0.png)

Photo by [Sticker Mule](https://unsplash.com/@stickermule?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

“给一个人一条鱼，”我们说，“你可以喂他们一天；教一个人钓鱼，你就喂了他们一辈子。”

这句格言提醒我们，如果我们想真正教别人，让他们自给自足，我们不应该简单地给他们他们需要的东西。相反，我们应该引导他们，确保他们明白如何做我们教他们做的事情。

其中一部分不仅包括向他们展示完成某项任务需要做什么(用蟋蟀给鱼钩做诱饵)，还包括向他们展示为什么首先需要做什么(我们用蟋蟀做诱饵，因为我们在钓太阳鱼)。

它还包括后退一步，让这个人尝试——也许失败——自己完成任务的一部分。毕竟，正如[的个人轶事](https://www.businessinsider.com/thomas-edison-and-michael-jordan-were-failures-2010-9)和[的定量研究](https://www.waterford.org/education/why-failure-is-better-than-success-for-learning/)所显示的，通常最好的学习方法是[先失败](https://en.wikiversity.org/wiki/Learning_by_failing)。

那么，为什么我们还在继续写教程——声称是教学的文档——采取相反的方法呢？

# 大多数教程并没有真正教

想想你上一次学习的教程。如果这个教程和其他 99%的教程一样，看起来应该是这样的:

1.  首先，这样做。
2.  接下来，做这个。
3.  然后，做这个。
4.  看最后的结果。
5.  你完了。

当然，如果你完全按照他们告诉你的步骤去做，那么你就已经完成了手头的任务。但这真的是目标吗？

当然不是。目标是学习如何自己完成任务*，这样你最终可以在最少的帮助下完成任务。因为即使你记住了教程中的每一步(让我们面对现实吧，这很少发生),当你自己出发时，事情也不会为你整齐地排列好。事情会有所不同。会出现意想不到的事情。如果你不理解教程的意图，那么你将无法处理这种差异。*

*从这个意义上来说，在写教程时，我们应该把自己的角色看作是引导读者——给他们指明正确的方向——而不是像大多数教程那样，每一个细节都由读者来决定。*

# *教程不是参考资料*

*那么为什么我们倾向于写这么差的教程呢？我怀疑这是因为我们大多数人没有意识到实际上有不同类型的文档。*

*通常当我们开始写 ***教程***——写给*的文档教*其他人如何做一些新的事情——我们经常结束写 ***参考资料***——文档对那些已经知道如何做的人来说是一个简明的*提醒*。*

*可以理解。不同类型的文档很容易混淆。但事实是，当我们开始记录如何做某事时，我们需要了解我们的受众是谁，以及我们编写文档的目的是什么。*

*让我们想象自己在工作中，在一家我们已经工作了将近一年的公司里。我们还不是经验丰富的老手，但也不是全新的。我们知道如何在我们的组织中把事情做好，但我们仍然记得我们为解决这些问题所经历的斗争。*

*所以我们决定记录下我们学到的东西，这样下一个可怜的人就不会遭受和我们一样的挣扎。但问题是，我们要写什么？推而广之，我们的文档最适合谁？*

*此时，花点时间停下来思考两件事:*

1.  *我们的文档会是什么样的，以及*
2.  *最终，谁最有可能使用我们的文档？*

*(*看到我在那里做了什么吗？我不再给你提供信息，而是提出一个小问题让你自己解决。*😀)*

*最有可能的是，我们会写下一个一步一步的指南，准确地说明如何完成手头的任务。如果我们特别勤奋，我们会确保不遗漏任何细节，这样读者就没有出错的机会。*

*十有八九，这是一份很好的文件……给我们未来的自己。对于我们现在的同事来说，他们有时需要复习细节。不幸的是，一旦完成编写，这些文档通常会作为新员工的入职学习材料交给他们。*

*这正是不应该发生的。因为参考资料很少能成为好的教程。*

*让我们举一个来自软件工程世界的简短但具体的例子(不要担心，基本原则适用于其他学科)。我可能会决定写一篇关于如何使用公司代码库的新员工教程。通常，一个新的工程人员需要做的第一件事就是下载应用程序的代码，然后运行这个应用程序。*

*天真地说，我可能会这样写:*

```
*1.
Go to the Applications/Utilities folder on your Mac and open the Terminal application.
Type the following commands:
 *cd ~*
 *mkdir codebase
* *cd codebase
* *git clone* [*https://git.mycompany.com/corp/user-orch-svc*](https://git.mycompany.com/corp/user-orch-svc)2.
Once the cloning process has finished, type the following commands: *mvn package -P assets
 export ASSETS="~/codebase/user-orch-svc/assets"*
Now run:
 *mvn exec:java -Dexec.mainClass="com.ourcompany.userorch.Main"*
You'll be able to see the running application by launching a web browser and entering *localhost:8080** 
```

*我们的读者已经完成了检查代码和运行应用程序的任务。但是他们不会记住所有的步骤，也不理解它们的重要性。而且他们肯定没有准备好开始使用其他类似的应用程序。*

*让我们剖析一下这个教程和其他大多数教程的问题所在。*

*[](https://www.datadriveninvestor.com/2020/07/29/how-working-from-home-increased-my-productivity/) [## 在家工作如何提高我的工作效率|数据驱动型投资者

### 在家工作确实激发了我最大的潜能，让我更有效率。因为在家工作给了我…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/07/29/how-working-from-home-increased-my-productivity/) 

## 我们的读者不会记住他们做过的事情

本教程向我们的读者介绍了完成手头任务所需的每个细节。只要他们按照教程的每一个字，他们就能完成手头的任务。

但这根本不需要他们思考。

相反，这让他们在整个过程中有效地梦游。除非他们花费额外的精力去尝试内化他们正在做的事情，否则他们将很难回忆起他们做了什么来让一个应用程序被检查并运行。

那么，与直觉相反，我们实际上应该在这里或那里留出一个步骤，让我们的读者去理解。这将使他们的大脑参与到这个过程中，并防止他们盲目地跟随。

> 这里有一个经验法则:如果有人可以复制粘贴我们的教程，那么它就不是真正的教程。

## 他们不会明白他们为什么这么做

教程为我们的读者展示了每一步。但是它没有解释为什么这些步骤是重要的。例如，即使他们意识到他们正在创建一个*代码库*文件夹来签出代码，他们为什么需要这样做呢？“资产”是怎么回事？

这一点很重要，尤其是当我们的读者转向其他类似的任务时。最终，他们会遇到与这些资产相关的应用程序启动问题。或者他们需要使用完全不同的应用程序。在任何情况下，他们对所涉及的步骤有了坚实的理解，就能更好地独立解决问题。

## 这并没有挑战他们

也许最重要的是，教程没有给他们失败的机会。他们不需要自己想办法。鉴于失败是最好的学习方式，这意味着教程错过了一个黄金机会。

强迫我们的读者停下来，尝试一些东西，可能会失败并再次尝试，实际上有助于解决前两个问题；它让读者思考*他们在做什么*，并且帮助他们理解*他们为什么*这么做。

所以让我们考虑一下如何重写教程。* 

*首先，让我们关注第一部分，检查代码。再看一下上面的例子，考虑一下如何修改这个教程。然后看看下面的修改。*

```
*All of our company resources are listed here: [*https://resources*](https://resources)
Use that page to find the URL to our git repository.(Can't find it? Look under the “Engineering” tab)You should have found the link to [*https://git.mycompany.com*](https://git.mycompany.com) 
Go there now, and find the repository for the User Orchestration microservice.(Not finding it? Note that you’ll need to switch into the “corp” project first).(Still can’t find it? Note that we routinely use the “orch” abbreviation for orchestration, and the “-svc” suffix for microservices.)(If you still can’t find the repository, enter *user-orch-svc* into the searchbar. Click on the first search result.)Now, create a folder on your Mac to clone the repository into. You'll likely be cloning other repositories later into this folder. Note that most engineers create a folder called *codebase/* within their home directory, but it's really up to you.Finally, clone the *user-orch-svc* repository to the folder you've just created, using https.(If you haven't used git before, or you can't remember how to clone a repository using https, you can find instructions here: [https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/cloning-a-repository)](https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/cloning-a-repository))By the time you're done, you should a folder called *user-orch-svc/* within that *codebase/* folder (or whatever you'd decided to name it) that you'd created earlier.*
```

*第二个版本肯定没有第一个版本简洁。但是遵循第一个版本的读者除了在他们的计算机上得到一些代码的拷贝之外什么也没有得到。相比之下，第二本书的读者会有所收获:*

*   *在他们的组织中寻找资源的经验*
*   *熟悉如何搜索代码库*
*   *一些人想到了他们将在电脑上存储代码的地方*
*   *了解如何将存储库克隆到他们的本地计算机上，如果他们还不知道的话。*

*现在让我们看看第二部分，让应用程序运行起来。再看一下上面的例子，然后继续下面建议的修改:*

```
*Once the cloning process has finished, you'll want to run the application.First, you'll need to build a set of assets that the service needs to launch and run properly. We've created a Maven profile called "assets" that builds the assets. Note: if you want to see what it's doing, open the *pom.xml* file and look for this section: <profiles>
        <profile>
            <id>*assets*</id>From the command line, run this profile with this command:
 *mvn package -P assets*This starts the standard Maven *package* goal, running as the *assets* profile.Building assets is a common pattern here, that you'll need to do with pretty much any orchestration service. Once Maven is done running, you'll notice a new *assets/* folder created in the project directory. Take look through that folder to see the sorts of things that were generated.Now try running the application. First, you'll need to find the entry point into the application, to provide as the *mainClass* value to Maven. See if you can search the codebase to find it.One tip: search the codebase for *public static void main*Hopefully you found it: *com.ourcompany.userorch.Main*  That's our pattern, to place the main method in a *Main* class in the service's top-level package.Use the *exec:java* command to launch the application:
 mvn exec:java -Dexec.mainClass="com.ourcompany.userorch.Main"Whoops... it failed, right? Look at the error message, and see if you can figure out why.It looks like it can't find the assets you'd just created, right? See if you can fix the problem and get the application running yourself.--The problem was that the application was looking for an *ASSETS* environment variable, pointing towards that *assets/* folder that you'd created earlier. See if you can fix the problem and get the application running.--The easiest way to do this is to simply set the environment variable like so:
 *export ASSETS="~/codebase/user-orch-svc/assets"*Now when you run:
 *mvn exec:java -Dexec.mainClass="com.ourcompany.userorch.Main"*The application should launch fine. Note that you could create your own startup script that always sets the environment variable. However, you'll learn later that sometimes, for testing, you'll want to point to another location.Finally, try to hit application in a browser. Look through the startup logs for clues on how to do that, if you need to.Having issues? You'll be able to see the running application by launching a web browser and entering *localhost:8080**
```

*同样，我们在这里写的比原来的版本多得多。但是我们的读者对他们正在做的事情有了更多的了解。例如，他们将来可能会遇到与那个 *assets/* 文件夹相关的问题。本教程为他们解决这些问题提供了坚实的理解。他们自己也发现了第一手的模式，如*主类*值。*

# *这是一种承诺*

*当然，编写好的教程需要时间。*

*这当然不仅仅是简单地列出一些步骤让人们去遵循。它不仅包括决定哪些信息给*包括*，还包括哪些信息给*省略*。它还包括解释每个步骤背后的目的。它包括为我们的读者自己解决问题或挑战。*

*我们可能会发现自己不止一次地记录类似的主题。例如，如上所述，我们可能会提供关于如何执行某些任务的简明参考文档，同时还会编写涵盖相同任务的深入教程。*

*虽然写好的学习材料是一种承诺，但这是一种值得做出的承诺。*

*太多时候，文档被认为是一种事后的想法，如果我们有时间的话，我们就会去做。但是如果我们真的想帮助我们的读者真正学到我们要教的东西，那么我们需要把我们的文档当作一等公民来对待。随之而来的是认识到我们的观众，并为他们写作。*

*所以他们不仅仅只有一条隐喻意义上的鱼，而是能够去捕捉更多的鱼。*

**觉得这个故事有用？想多读点？只需* [*在这里订阅*](https://dt-23597.medium.com/subscribe) *就能把我的最新故事直接发到你的收件箱里。**

**你也可以通过* [*成为今天*](https://dt-23597.medium.com/membership) *的灵媒会员来支持我和我的写作——并获得无限量的故事。**

## *访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)*