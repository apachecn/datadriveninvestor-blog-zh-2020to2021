# 反应:大局-第二部分

> 原文：<https://medium.datadriveninvestor.com/react-the-big-picture-part-ii-e9b2e1778753?source=collection_archive---------10----------------------->

你好，如果你正在阅读这篇文章，我假设你已经阅读了我之前的文章，这篇文章告诉你是什么让 react 与众不同，值得你选择而不是竞争对手 ，现在你正在寻找一个权衡的简短概述，这样你就可以决定 react 是否适合你和你的团队

# *权衡取舍*

## 权衡 1:框架还是库

第一个权衡是框架还是库。像 Angular 和 Ember 这样的竞争对手都是框架。相反，React 通常被认为是一个库，因为它是精简的，专注于组件，并且没有观点。

现在，一个框架并不比一个库好多少；这是一种权衡。选择框架方法有几个优点，比如

*   一个框架包含更多的观点，所以你可以避免花时间在许多选项中进行选择，这减少了决策疲劳，并且通常有更少的设置开销。
*   框架有助于加强一致性，因为大多数框架更加固执己见。

然而，React 的库方法也有一些明显的优势。React 大约只有 35K gzipped，比大多数框架小得多。这意味着它足够小，您可以将其分散在现有的应用程序上，以便您可以慢慢地迁移现有的应用程序来做出反应，甚至是服务器端渲染的应用程序。

假设你有一个内置的应用程序。net、Java、Ruby、PHP、Python——随便什么。因为 react 小而灵活，所以您可以用 React 组件替换页面上的单个组件。而且，您可以在任何地方使用 React 组件，因为它们是轻量级和原子级的。这正是脸书如何从服务器端渲染 PHP 慢慢渲染其应用程序的反应。React 不会强迫你做任何决定。它允许您只引入保留应用程序所需的功能。您可以自由选择项目所需的精确技术，也可以自由选择最适合您的用例的技术。

## 权衡 2:简洁与明确

要考虑的第二个权衡是简洁还是显式。

React 用简洁换取可预测性和明确性。你花了更多的时间来明确地把东西连接在一起，但是这有助于它们不分开，并且它也有助于人们更好地理解代码在做什么。这里有一个具体的例子，

*   像 Knockout 和 Angular 这样的框架普及了双向绑定，通过自动保持表单输入与底层数据同步来避免键入。
*   在 React 出现之前，这种方法非常流行。它之所以受欢迎，是因为它需要较少的编码。通过双向绑定，JavaScript 值和输入会自动保持同步。
*   相比之下， *React 包含单向绑定，而不是*。它需要更多一点的代码。使用 React，您可以声明一个显式的更改处理程序，并在您的输入中引用它。

这项额外的工作有一些好处，如

*   你有更多的控制权，因为你可以准确地宣布在每一个事件中应该发生什么。
*   您可以在更新状态之前转换和验证输入，并根据需要执行性能优化。
*   您的代码更加明确，因为您清楚地说明了事件发生时您希望发生什么，这使得在发生错误时易于理解和调试。

尽管 React 帮助单向绑定重新流行起来，但出于这些原因，其他流行的库，如 Angular，今天也改变了方向，接受了它。现在，如果您的团队强烈倾向于双向绑定，您可以使用添加它的库来进行反应，但出于我刚才提到的原因，很少有人这样做，我也没有真正使用它。此外，您不需要为每个输入声明单独的更改处理程序。在 React 中有一些简单的模式来集中您的变更处理程序，您可以在这里找到更多的。

总之，这里是权衡。与传统的双向绑定方法相比，React 需要更多的类型来实现，但是具有更容易维护、更清晰、更可靠和更高性能的优点。

## 权衡 3:以模板为中心还是以 JavaScript 为中心

第三个权衡是以模板为中心还是以 JavaScript 为中心。

Angular，Vue 和 Ember 试图通过发明他们自己独特的在 HTM 写代码的语法来使 HTML 更强大。React 采用了完全相反的方法，而是利用 JavaScript 的能力来处理 HTML。这一根本区别是 React 如此优雅的原因。

让我们考虑在每个技术中写一个循环。

*   *对于 Angular，你说*ngFor，然后使用一个看起来有点像 JS 的语法，但是是在字符串内部声明的。*
*   *Vue 类似，但是打字少一点。同样，您在字符串中编写循环代码。*
*   在 Ember 中，你使用 Ember 的#each helper，与上面的其他助手相比，这个助手有点罗嗦。
*   *最后，使用 React，您使用 JavaScript 的内置 map 函数和一个普通的 JavaScript arrow 函数来显示每个用户名。因此，唯一特定于 React 的语法是花括号，这不仅仅是因为它的代码更少，还因为它是普通的 JavaScript。*

最后，让我们来看看它们是如何处理点击按钮的。

*   *使用 Angular，您可以在事件周围添加括号，并且与传统的事件处理程序不同，您还可以在事件处理程序名称旁边添加括号，就好像您正在调用它一样。如果是真正的 JavaScript，这种语法就不会起作用。*
*   *在 Vue 中，您可以使用带有冒号和事件名称的 v-on，也可以在 click 前面加上 at 符号。同样，这两个都是特定于 Vue 的语法。*
*   使用 Ember，你可以指定一个普通的 onclick，这很好，但是在内部，你使用一个特定于 Ember 的约定将点击与一个特定的动作联系起来，这个动作是通过一个字符串声明的。
*   *最后，用 React 声明一个 onClick 处理程序。*因此，在 React 中，您使用本地点击处理程序名称，但这是驼色的，因为 React 的 JSX 使用 JavaScript 大小写规则；否则，唯一独特的语法是在花括号内而不是在引号中指定函数名。如果您了解 JavaScript，那么您就知道如何在 React 中处理条件、循环和事件。这也是 React 的 API 这么小的原因。

如果您查看确切的代码，这将会更加清楚，但是您并不真正需要担心所有的框架和库。我试图对比这两种方法，以阐明为什么 react 更好。

所以，让我们实际上进入要点，对比每种方法的好处。模板方法的好处是

*   它需要较少的 JavaScript 知识。模板语言为执行核心功能提供了简化的 API。
*   您主要关注用特定于框架的语法来增强模板。
*   这些独特的语法有一些优点，比如避免了 JavaScript 的 this keyword 行为经常引起的混乱。

这使得不熟悉 JavaScript 的开发人员更容易使用模板。从理论上来说，模板语言是更好的，因为有一个原则叫做最小权力原则。这是反直觉的，但是功能较弱的语言理论上可能更好，因为它们可以通过只允许用户执行一小组规定的操作来防止误用。

但是当然，有一个明显的缺点，那就是以模板为中心的方法导致了特定于框架的语法。要想精通 Angular 和 Vue 这样的以模板为中心的库，你必须花时间学习它们特定的语法和规则，来做 JavaScript 已经可以处理的事情。

相比之下，React 几乎没有什么独特的语法需要学习，因为 React 包含 JavaScript，所以您不必学习新的词汇来描述其他以模板为中心的库(如 Angular)添加到 HTML 中的新功能。您在 React 中编写的大部分内容实际上只是普通的 JavaScript。这导致更少的输入和代码，我发现这产生了更容易阅读和调试的结果。

最后，React 以 JavaScript 为中心的方法鼓励提高您的 JavaScript 技能。诚然，你可以认为这是一个缺点，因为 ES 2015 中的新功能列表非常重要。但是，一旦你这样做了，你不仅会更好地反应，你会更好地在 JavaScript

总之，为了更好地使用 React，您主要需要学习现代 JavaScript。这很好，因为这意味着你的技能将转移到你编写的所有其他 JavaScript 代码中，即使你将来不再使用 React。

## 权衡 4:独立文件还是单个文件

第四个权衡是每个组件一个单独的模板和一个文件。

像 MVC 这样的模式普遍将模型、视图和控制器分成三个独立的文件。传统上，对于 web 应用程序，这意味着视图是 HTML。模型用 JavaScript 为视图声明数据，控制器控制与模型的交互。

相比之下，使用 React，每个组件都是一个独立的关注点。每个组件都独立存在，并且可以由其他组件组成，以构建丰富、复杂的 ui。这意味着标记和逻辑位于同一个文件中。当 React 在 2013 年推出时，人们对 React 的设计非常怀疑，因为它与当前将 HTML 模板和 JavaScript 逻辑放在单独文件中的最佳实践背道而驰。

在 React 中，每个组件在同一个文件中既包含逻辑又包含标记，所以从表面上看，这似乎违反了关注点分离的原则。然而，在 React 中，您以不同的方式考虑关注点的分离。

传统的关注点分离通常专注于将每项技术放在一个单独的文件中。所以在 web 开发中，这意味着将 HTML、CSS 和 JS 放在单独的文件中。但是 React 认识到，虽然这些确实是独立的技术，但是必须小心地将它们组合在一起才能做任何有用的事情。因此，在 React 中，每个组件都是一个单独的关注点。*例子包括*

*   *一个按钮*
*   *一个约会对象*
*   一架手风琴
*   *或文本输入。*

*这些组件中的每一个都是一个单独的问题。因为 JavaScript、CSS 和 JSX 共同创建了一个有用的组件，所以它通常会嵌入逻辑、样式和标记问题。根据我的经验，将这种相互交织的问题放在单独的文件中实际上会妨碍调试并减慢反馈，因为您必须在思想上保持这些单独的文件同步。当然，通过将小而简单的组件组合在一起，您可以创建更复杂的组件。所以，我觉得组件是一个值得分离的常见问题。将 HTML、JavaScript 和 CSS 分离到单独的文件中的旧思维模式，仅仅是分离的技术，但它们的关注点和交互实际上从根本上是交织在一起的。如果您更改一个文件，通常需要对其他文件进行相应的更改。哦，你不必在同一个文件中处理样式。使用 React，如果您愿意，您可以在传统的单独 CSS 文件中自由处理 CSS。*

想想像俄罗斯娃娃一样的组件构成。俄罗斯娃娃很有趣，因为每个娃娃都可以容纳一个更小的娃娃(我喜欢俄罗斯娃娃的类比，但这是我的原创)。React 的组件模型也是这样工作的。简单的、可重用的组件可以组合在一起构建丰富的、复杂的用户界面。React 的组件方法非常适合于构建复杂的 ui，它将页面分解成独立的小块，可以独立地进行推理和测试。

因此，在为您的项目选择框架或库时，这些是我们应该理解并记住的一些权衡

[*在下一个也是最后一个模块中，我将通过考虑我听到的常见问题*](https://medium.com/@nsethi610/react-the-big-picture-part-iii-34780bf8452f) 以及缓解这些问题的方法来结束本系列。

文章动机和资源指南来自[plur sight](https://medium.com/u/50a6c7ef7431?source=post_page-----e9b2e1778753--------------------------------)

感谢阅读。一定要鼓掌表示感谢，不要忘记给你反馈。

编码快乐！！