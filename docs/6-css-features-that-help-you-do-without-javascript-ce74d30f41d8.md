# 6 个 CSS 特性帮助你不用 JavaScript 就能做到

> 原文：<https://medium.datadriveninvestor.com/6-css-features-that-help-you-do-without-javascript-ce74d30f41d8?source=collection_archive---------16----------------------->

![](img/84135f5b10fe0cdae435bea5eb31a2b7.png)

最近，有很多关于 CSS 和 JavaScript 的比较，争论这些技术的应用来解决特定的问题。随着新的 CSS 特性的出现，争议变得越来越激烈，这些新特性使得解决大量问题变得更加容易，同时将 JavaScript 留在了身后。

CSS 和 JavaScript 配合得很好，这两种技术各有所长，但我们相信，越多的 CSS 用于控制界面的外观和行为，web 应用程序就越容错，越可靠。这是因为:

*   就其本质而言，CSS 是一种抗排斥的技术。这意味着当 CSS 解析器遇到它不理解的属性时，它会简单地忽略它并继续前进。换句话说，使用 CSS，程序员应用样式并期望它们工作。
*   JavaScript 不是一种容错技术。JS 代码中的一个语法错误就可能破坏整个应用程序。也就是说，当使用 JS 管理站点的样式时，检查相应结构的功能是绝对必要的。

在回答何时使用 CSS 而不是 JS 的问题时，还有许多其他的考虑要考虑。

CSS 为我们提供了设计奇妙解决方案的新方法，这些解决方案比相应的 JS 解决方案简单得多，也更容易创建。这指的是 CSS 的许多特性:过渡，自定义属性，动画，过滤器，数学。

在本帖中，我们将介绍 CSS 的一些很酷的特性(其中一些是最近才出现的)，你可能还不知道。也就是说，我们将讨论平滑滚动、position: sticky 属性，以及以前需要编写大量复杂的 JS 代码行的其他特性。

![](img/7124de1e7b29b40f742dbe8fd4b40b70.png)

# 1.平滑滚动

以前，要为页面配备平滑滚动功能，需要使用几行 JS 代码。而现在这个任务完全可以通过 CSS 的方式来解决。嗯，这不是很好吗？现在，您可以通过使用滚动行为 CSS 属性来利用平滑滚动。

看起来是这样的:

```
html {
scroll-behavior: smooth;
}
```

# 2.固定元素

锚定元素是我们最喜欢的 CSS 特性之一。关键是，当滚动页面时，相应的元素不会从视图中消失。现在，您不需要借助 JS 中的 offsetTo 和 window.scrollY 来将元素固定到页面。如今，您可以简单地使用 position: sticky CSS 属性:

```
header {
position: sticky;
top: 0;
}
```

为了正确使用该属性，您需要考虑它对元素的特定影响。当应用时，HTML 页面的结构起着一定的作用。顺便说一下，有时 position: sticky CSS 属性不起作用的原因在于没有考虑到这种影响

让我们来看看下面的 HTML 代码:

```
<main class="container">
<nav class="nav">
<ul>
<li>Home</li>
<li>About</li>
<li>Contact</li>
</ul>
</nav>
<div class="main-content">Main Content</div>
<footer class="footer">Footer</footer>
</main>
```

菜单(本例中的 nav 元素)只能固定到与其父元素(本例中的 main)重叠的区域。因此，当使用 position: sticky 属性时，有两个主要的元素类:

*   可停靠元素:这是我们应用了 position: sticky 属性(在我们的例子中是 nav)的元素。该元素将在父元素中移动，直到到达给定位置。比如可以是 top: 0px。
*   可停靠元素容器:这是包含可停靠元素的 HTML 元素。这是停靠项目可以移动的区域。这个“容器”定义了可停靠项目可以存在的边界。

使用该功能可以显著提高网站的可用性。对于那些用户必须频繁滚动页面的项目来说尤其如此。

这个特性几乎 100%支持浏览器。

# 3.裁剪文本

CSS 给了我们两个奇妙的特性:文本溢出和换行。它们允许您修剪文本，仔细处理单词，同时使我们不必使用 JavaScript 或其他一些复杂的方法来解决此类问题。这两个属性都不是新的，但是非常有用。

让我们仔细看看文本溢出和换行属性。

# 文本溢出属性

此属性控制文本在一行放不下时应被截断的情况下的显示方式。这种情况的一个例子如上图所示，在卡片的标题中。这里您可以使用构造 text-overflow: ellipsis，这将导致一个 Unicode 字符(…)被添加到被修剪文本的末尾。

要使 text-overflow: ellipsis 属性发挥作用，还必须使用 white-space: nowrap 和 overflow: hidden 属性。

```
.card-title {
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;
}
```

所有现代浏览器几乎都完全支持这一特性。

# 线夹特性

当我们需要处理多行文本而不是单行文本时，这个属性就派上了用场(上图中卡片的内容就是这种文本的一个例子)。虽然这是 CSS 溢出模块 3 级标准的一部分，现在它的状态是“工作草案”，这个特性已经被大约 95%的浏览器支持，尽管带有-webkit-前缀。在使用它之前，重要的是要考虑到它不能控制显示的字符数。但不管怎样，它非常有用。

要使用它，我们需要通过应用显示:-webkit-box 和-WebKit-box-orient:vertical properties 来使用旧的 flexbox 实现。看起来是这样的:

```
.card-title {
overflow: hidden;
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 3;
}
```

![](img/c39835ecd2dfd986b9fccf454f18e833.png)

# 4.自定义 CSS 属性:CSS 变量

在 JavaScript 领域，CSS 预处理程序(如 Sass、Less 和 Stylus)是非常有用和流行的技术。预处理程序扩展了 CSS 的功能，例如，允许你使用变量和函数。但是现代网页设计者可以使用强大的标准 CSS 功能，即自定义 CSS 属性或 CSS 变量。

CSS 变量有助于保持应用程序的一致性，并有助于实现 DRY。它们促进了应用程序主题的开发和维护。这些能力是预处理器成功的主要原因之一。

使用标准 CSS 特性意味着您不再需要预处理程序来创建变量。变量，就像我们喜欢的其他标准 CSS 特性一样，以层叠的方式工作。

创建 CSS 变量非常容易。也就是说，要声明一个变量，在它的名字前面加两个破折号(-)就足够了。之后，在需要变量值的地方，调用函数 var()，将之前创建的变量作为参数传递给它。如你所见，一切都很简单。

```
:root {
--base: #ffc600;
--spacing: 10px;
--blur: 10px;
}
img {
padding: var(--spacing);
background: var(--base);
webkit-filter: blur(var(--blur));
filter: blur(var(--blur));
}
.hl {
color: var(--base);
}
```

CSS 变量可以通过 JavaScript 操作。

# 5.为黑暗模式提供支持

自从苹果去年为 macOS 引入了黑暗模式，并且因为 CSS 让我们能够使用媒体查询来检测这个主题的使用，许多大型网络项目(如 Twitter 和 Google Maps)都采用了这个主题。

黑暗模式不仅仅是装饰网页的一种方式。它确实能帮助一些人上网。

这里有一些说明其有用性的引语。

还有一些人，由于客观原因，需要黑暗模式。他们使用这种模式作为残疾人的工具之一。比如我们说的是视力低下的人。

Thomas Steiner，德国谷歌客户解决方案工程师。

莫莉有亚瑟综合症。因此，她什么也听不见，并且她的一只眼睛的视野被限制在 5 度。(……)在黑暗模式下查看页面将是她的权力范围。这种模式对其他人也很有用，为那些头疼的人或那些不得不在光线不好的房间里坐在电脑前的人扩大了使用互联网的可能性。如果在开发某个东西的时候，只把重点放在一些特殊的用户身上，不仅对他们有用。

查尔斯·雷诺兹，英国政府设计师。

此外，从 Thomas Steiner 的材料中，您可以了解到使用黑暗模式有助于节省能源:“(……)正如您所知，在 AMOLED 显示器上使用黑暗模式可以节省大量能源。针对 YouTube 等热门谷歌应用的安卓研究表明，在某些情况下，节能率可高达 60%。

一个新的 CSS 特性是 prefers-color-scheme media 函数，它让我们知道用户是否启用了黑暗模式。它已经兼容 Chrome、Firefox、Safari 和 Opera。

将这一点与 CSS 变量结合起来，意味着 web 开发人员可以很容易地让访问者利用动态明暗模式。

```
:root {
--color: #222;
--background: #eee;
--text: 'default';
}
body {
color: var(--color);
background: var(--background);
}
body:after {
content: var(--text);
display: block;
text-align: center;
font-size: 3rem;
}
@media (prefers-color-scheme: light) {
:root {
--color: #222;
--background: #eee;
--text: 'light';
}
}
@media (prefers-color-scheme: dark) {
:root {
--color: #eee;
--background: #222;
--text: 'dark';
}
}
```

# 6.@supports 指令

长期以来，web 开发人员不得不求助于第三方解决方案(如 Modernizr JS 工具)来了解当前浏览器是否支持某些 CSS 功能。例如，通过配置-webkit-line-clamp 元素属性，您可以检查该属性在浏览器中是否受支持，如果不受支持，您可以使用一些回退。

在 CSS 中出现@supports 指令后，直接从 CSS 代码中检查浏览器的功能成为可能。

@supports 指令非常类似于媒体查询。它支持用条件运算符 AND、OR 和 NOT 构建的表达式的各种组合:

```
@supports (-webkit-line-clamp: 2) {
.el {
...
}
}
```

这将检查浏览器是否支持-webkit-line-clamp 属性。如果是这样，也就是说，如果条件为真，将应用@supports 指令中声明的样式。

所有现代浏览器都支持这一功能。

![](img/c46ee82f3aa6681a1975dc4c5af222de.png)

# 结论

在本文中，我们介绍了 CSS 的一些有用特性。如果你可以不使用 JS 而只使用 CSS 来做一些事情，那么就这样做吧。

前端的现代世界正在快速变化，我们不断有新的机会可供我们支配，帮助我们更快更好地开展业务。尝试 CSS 和学习新事物不仅很有收获，而且非常有趣。为什么不尝试一下你今天学到的新东西呢？

享受成功发展！:)

*原载于 2020 年 8 月 18 日*[*【https://geniusee.com】*](https://geniusee.com/single-blog/6-css-features-that-help-you-do-without-javascript)*。*