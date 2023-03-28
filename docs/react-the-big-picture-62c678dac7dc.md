# 反应:大局-第一部分

> 原文：<https://medium.datadriveninvestor.com/react-the-big-picture-62c678dac7dc?source=collection_archive---------3----------------------->

你好，如果你正在阅读这篇文章，我假设你是 react 新手，你正在寻找 react 入门指南，它是什么，为什么它变得如此受欢迎，以便你可以决定 react 是否适合你和你的团队

该模块由三个简短的子模块组成。在第一个模块中，我们将探索 react 的特别之处，以及在竞争中值得选择的原因。在下一个模块 [*中，我们将讨论 react 的设计*](https://medium.com/@nsethi610/react-the-big-picture-part-ii-e9b2e1778753) 中固有的权衡，以便您可以了解通过选择 react，您将得到什么，放弃什么。此外，我 [*将通过考虑我听到的常见问题*](https://medium.com/@nsethi610/react-the-big-picture-part-iii-34780bf8452f) 来结束本模块，并提出缓解这些问题的方法。

# ***为什么会有反应？***

## 原因 1:灵活性

也许选择 React 的最有说服力的理由是，一旦你学会了它，你就可以为各种各样的平台和用例构建用户界面。

React 非常灵活。与竞争对手相比，React 嵌入的观点更少，因此它比 Angular 和 Ember 等固执己见的框架更灵活。

React 是一个库，而不是一个框架，正如您将要看到的，React 的库方法使它发展成为一个非常灵活的工具。最初创建 React 时，它只有一个单一的、集中的用例。它是用来为 web 应用程序创建组件的。

然而，随着 React 越来越受欢迎，它的生态系统已经覆盖了各种用例。

## 原因二:开发者体验

第二个原因是开发者体验。

相信我，一旦你试着学会反应，你很可能会坠入爱河。因为:

*   快速反馈开发体验与 React 的小型逻辑 API 相结合，创造了一种无与伦比的开发体验。
*   它提供了一个简单易学的 API。需要掌握的概念很少。React 的 API 是如此之小和简单，以至于开发者很少需要检查文档。整个 API 刚好能装进你的脑袋。还有比这更简单的吗？(我是《老友记》里钱德勒的超级粉丝😛)

使用 reach，您可以开发小的原子可重用代码，这就是所谓的组件。这基本上是一个返回类似 HTML 的函数。使用 React 组件，您可以使用标准 JavaScript import 语句在顶部导入 React，然后使用标准 JavaScript 函数声明组件。该函数通过一个名为 props 的对象接收变量。还可以使用标准的 JavaScript 类声明 React 组件。这些被称为功能组件。这种方法稍微需要更多的输入，但是给了你更多的能力。

现在，如果你看过一些 react 组件的例子，你可能会想知道这个 render 函数里面发生了什么。它看起来像 HTML，但是它位于 JavaScript 文件中，那么它是如何工作的呢？嗯，那叫 JSX。

JSX 和 HTML 之间有一些细微的区别，

*   JSX 向下编译成 JavaScript，变成了对 React.createElement 的调用
*   向该函数传递您创建的标记的名称，这是一个指定您想要设置的属性的对象。
*   最后，应该放在里面的标记。如果有嵌套标记，最后一个参数包含对其他元素的调用。更多详情可以去 react [docs](https://reactjs.org/docs/react-api.html) 。

像 Angular、Vue 和 Ember 这样的传统库试图通过发明它们自己的语法来增强 HTML 的能力，这些语法用于像循环这样的简单操作。举个例子，

*   在 Angular 中，你说*ngFor 让用户的用户。
*   在 Vue 中，你在 users 中说一个 v-代表用户
*   在 Ember 中，你在 users 中说#每个用户。

React 走了完全相反的路线。React 并没有试图让 HTML 变得更强大，只是用 JavaScript 处理 HTML。您不需要学习新的特定于框架的关键字、规则以及条件、循环等的语法。你只要用 JavaScript。JavaScript 已经有了一个内置的函数来迭代一个名为 map 的数组，所以在 React 中你只需要普通的 JavaScript。基本上，传统库在 HTML 中放了假的 JavaScript。而 React 做的恰恰相反。它在 JavaScript 中放了假的 HTML。我发现 React 的方法更可取，因为它创建了一个更简单的 API。React 鼓励你更好地使用 JavaScript，这样做，你也能更好地使用 React。

我使用 create-react-app，这是目前最流行的搭建 react 应用程序的方法。我只说 create-react-app，并给我的应用程序起一个想要的名字(*npx create-react-app my-app*)，它就在我的机器上创建了一个完全工作的开发环境。通过一个简单的命令， *npm start* ，它在我的机器上启动了一个 web 服务器，并为我的 React 应用程序提供服务。

在反应中，每个组分都是原子；它是独立的。这意味着您可以独立地使用每个组件，每次保存代码时，更改都会立即反映在浏览器中，这也称为**热重装**。

最棒的是。如果出现错误，您会在浏览器中收到一条详细的错误消息。如果我忘记在 JSX 中结束一个标记，我会得到一条编译时消息，指出我犯了错误的那一行。如果你需要调试你的代码，很容易设置一个断点，并在浏览器中查看原始代码。通过 source maps 的强大功能，您可以在浏览器中看到您在编辑器中编写的原始代码。

您可以使用在线 React 编辑器(如 CodeSandbox)轻松体验 React，共享您的工作，甚至构建您的整个应用程序。不需要任何配置。只需加载网站并开始编码。CodeSandbox 使 React 实验和分享您的工作变得容易。当我尝试一个想法的时候，我只是加载这个网站并开始编码。你可以创建多个文件，引用它们，使用现代 JavaScript，每次你击一个键，你就会看到你的改变反映在右边。

## 原因三:企业投资

第三个原因是，如今许多备受尊敬的公司都对 React 及其生态系统进行了深度投资。

React 是由脸书创建的，所以当然，React 是世界上流量最高的应用程序之一脸书的常用应用程序，也是脸书的其他应用程序，如 Instagram 和 WhatsApp。脸书坚定地致力于作出反应。尽管 React 是一个开源项目，但 React 项目的前六名提交者中有四名是脸书的全职员工。脸书开发团队维护着一个活跃的博客，不断概述每个版本的细节和未来的计划。由于脸书对 React 在生产中的深入承诺，当 React 中出现突破性变化时，脸书一直提供一个 codemod 来自动完成变化。

现在，codemod 是一个命令行工具，你可以指向你的代码库来自动修改。因此，使用 React codemod，您可以自动将较旧的 React 组件更新到最新的规范。这些年来，当突破性的变化发生时，脸书团队一直发布一个 codemod，以便自动更新到最新版本。

例如，当脸书发布 React 15 时。5，propTypes 特性作为一个单独的包发布，使用嵌入在 React 中的 propTypes 特性开始抛出警告，通知开发者这一变化。为了使更新变得容易，脸书发布了一个 codemod，通过更新导入来引用独立的 propTypes 包，从而自动完成更改。

美妙的是，我们今天可以对编写 React 组件充满信心，因为脸书在 React 代码的生产方面进行了大量投资，这意味着他们必须依靠自己创建的 codemods 来更新自己的代码。脸书生产超过 30，000 种元件。这是使用 React 的一个好处，因为它有助于确保将来不太可能出现重大的突破性变化。这样做将要求脸书对数以万计的他们自己的组件进行痛苦的突破性改变，因此这有助于确保项目的长期稳定性。

## 原因四:社区

考虑 React 的第四个原因是它拥有一个巨大的、活跃的社区。自 2013 年以来，React 在 GitHub 上的人气稳步增长，目前已超过 75，000 颗星。这使得 React 成为 GitHub 上最受欢迎的存储库之一。今天，它有超过 1000 个贡献者。事实上，在超过 200 万个存储库中，只有 3 个存储库在 GitHub 上的星级超过 React。堆栈溢出上有超过 55，000 个线程被标记为 reactjs，近 20，000 个被标记为 react-native，以及一长串与其他 react 相关技术的相关标记。

现在所有这些都很重要，因为这意味着一个简单的事实:如果你试图在 React 中做一些事情，你几乎可以在网上找到一个例子。嘿，哪个开发人员不喜欢偶尔复制粘贴一下呢？能够不断地从其他人那里得到答案是一件非常棒的事情，这些人遇到了和你试图解决的同样的挑战。这是因为 React 不仅仅被脸书所接受。今天，许多世界上最受尊敬的公司都在使用 React，包括苹果、网飞、亚马逊、Airbnb、PayPal，以及更多你在这里看到的公司。这些公司中的许多也定期开源他们与 React 相关的工作。因此，如果你选择做出反应，你肯定是在一个伟大的公司。而且你不需要创建你自己的组件，因为网上有大量的免费和成熟的组件库。微软开源了他们的 React 组件库，用于制作外观和感觉都像微软 office 的用户界面。Material-UI 提供了一组 React 组件，实现了 Google 的材料设计指南。React-Bootstrap 是一个流行的库，它包含 React 组件，使使用 Bootstrap 变得容易。

另外，GitHub 上有数百个有趣的独立 React 组件，您可能会觉得有用。查看 GitHub 上的 awesome React 列表，获得一长串附加组件。深入的社区投资带来了各种各样成熟的相关项目。需要路由吗？好吧，看看 React 路由器。你想使用一个库来处理复杂的数据流吗？好吧，Redux 和 Mobx 是今天可以考虑的两个热门选择。是否要设置自动测试？好吧，看看 Jest，它也来自脸书。想要一个 RESTful API 调用的替代方法，可以在客户端声明 API 调用吗？试试 GraphQL，它非常适合 React 应用程序。想要在 React with node 中快速设置服务器端渲染站点？那就试试下一个。js。当然，这只是触及了生态系统的表面。这个清单可以一直列下去。所以我想你可以说现在 React 是一件大事。

## 原因 5:性能

当 React 首次发布时，它的性能非常突出，帮助它在竞争中脱颖而出。React 团队认识到 JavaScript 很快，但是 DOM 让它感觉很慢。他们意识到更新 DOM 代价很高，因此他们发现以最有效的方式更新 DOM 将有助于提高性能。

因此，当您更改数据时，React 会在幕后智能地找出更新 DOM 的最有效方式。当 React 在几年前被创建时，这是一个新颖的设计，在许多情况下给了 React 显著的性能优势。在 React 之前，大多数库都会愚蠢地更新 DOM 来反映新的状态。这通常会导致重新绘制页面的重要部分，即使只发生了很小的变化。在 contract 中，React 监视每个组件的状态值。当组件的状态发生变化时，react 会将现有的 DOM 状态与新的 DOM 状态进行比较。然后，它确定更新 DOM 的最经济的方法。

这听起来很复杂，但这都是在幕后自动处理的。这种方法有多种好处。它有助于避免布局抖动，当 DOM 元素改变时，浏览器必须重新计算所有内容的位置。在一个许多人都在使用移动设备的世界里，高效变得越来越重要。移动设备的 CPU 能力差异很大，节省电池寿命也是一个问题。这也启用了 React 的简单编程模型。当数据发生变化时，React 会自动高效地更新 DOM。而且，您不需要做任何额外的事情就可以享受这种性能优势。当您更新组件的状态时，它会自动发生。比较是在内存中进行的，所以通常非常快

我希望这些原因能够解释为什么 react 比其他现有的库和框架更受欢迎。我 [*在下一个模块中，我们将讨论 react 的设计*](https://medium.com/@nsethi610/react-the-big-picture-part-ii-e9b2e1778753) 中固有的权衡，这样你就能明白选择 react 你会得到什么，放弃什么。

感谢阅读。一定要鼓掌表示感谢，不要忘记给你反馈。

来自[plur sight](https://medium.com/u/50a6c7ef7431?source=post_page-----62c678dac7dc--------------------------------)的文章动机和资源指南

编码快乐！！