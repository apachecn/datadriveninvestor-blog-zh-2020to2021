# 多填充物

> 原文：<https://medium.datadriveninvestor.com/polyfills-a6a458c60b38?source=collection_archive---------22----------------------->

![](img/3830f8966fea71153ac1e6424db482e9.png)

Photo by [Luke Chesser](https://unsplash.com/@lukechesser?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

几周前，[我写了一篇关于网页设计简单性的文章。](https://medium.com/@nicholasechevarria/a-junior-devs-musing-on-simplicity-in-coding-506a254b28e5)在这篇文章中，我谈到了全球网络接入的不平等。过度设计网站加剧了这个问题。

在那篇文章中，我介绍了一些程序员解决互联网接入和使用问题的有趣方法。不久之后，我了解了 polyfills。

## **一瞥 Polyfills**

> [poly fill，或 polyfiller，是一段代码(或插件),它提供了开发者希望浏览器本身提供的技术。-雷米夏普](https://remysharp.com/2010/10/08/what-is-a-polyfill)

使用 polyfills，用户可以向浏览器添加实用程序，以使其功能更加全面，能够运行我们想要运行的代码，而无需预处理器、命令行工具或要下载的库/包。

任何本机方法、属性或浏览器 API 都可以被聚合填充，因此，例如，可以向 Internet Explorer 这样的浏览器添加一个 **fetch()** 方法。(虽然我承认使用 Internet Explorer 的人是罕见的、困惑的一群，但他们仍然应该和我们其他人一样拥有相同的网络。)这是可能的，因为 Javascript 中的一切都是对象，所以我们可以添加另一个对象，并赋予它属性来重新创建获取行为。

也就是说，表达式和运算符不能被聚合填充，因为它们不是对象。相反，它们被嵌入到 Javascript 的解析引擎中，使得不可能添加 ES5/ES6 语法。

尽管如此，多孔填料在打破网络壁垒方面还是非常有用的。通过有选择地将标准化代码注入旧的浏览器，竞争环境变得更加公平。

## 生产聚合填料

在我们编写 polyfill 之前，让我们确保检查所讨论的浏览器是否具有执行(比如说)的本机功能。replaceAll()字符串方法:

```
// Make sure there's no native method available first
if (!String.prototype.replaceAll) {
	// Add some polyfill code...
}
```

下一步是为我们填充的方法创建一个函数。方法接受两个参数:要搜索的子字符串和替换它的字符串，所以让我们设置一下。

```
if (!String.prototype.replaceAll) {
	String.prototype.replaceAll = function (str, newStr){
		// Recreate the native method here...
	};
}
```

# 假装恐惧

现在我们可以尝试重新创建。replaceAll()字符串方法。解决这个问题的一个简单方法是思考:“*如果……我会怎么做。replaceAll()不可用？*”

在这种情况下，我们将让我们的函数根据用户输入生成一个新的 regex 模式。但是因为我们的函数是在原型上，在我们的函数内部，`this`是调用`replaceAll()`方法的字符串。我们可以调用`this.replace()`，使用`new RegExp()`创建一个新的正则表达式模式，并使用[全局(](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/global) `[g](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/global)` [)标志](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/global)传递我们的`str`参数。然后，传入`newStr`参数作为替换它的对象，然后返回结果。

```
if (!String.prototype.replaceAll) {
	String.prototype.replaceAll = function (str, newStr){ // If a string
		return this.replace(new RegExp(str, 'g'), newStr); };
}
```

我们快完成了。我们需要做的最后一件事是为我们*没有*接收到函数的正则表达式模式的情况创建一个异常。如果提供了一个，我们不想创建新的模式，而是检查`str`是否是正则表达式，如果是，就传递它。[否则，我们需要检查输入的类型。](https://gomakethings.com/true-type-checking-with-vanilla-js/)

```
if (!String.prototype.replaceAll) {
	String.prototype.replaceAll = function (str, newStr){ // If a regex pattern
		if (Object.prototype.toString.call(str).toLowerCase() === '[object regexp]') {
			return this.replace(str, newStr);
		} // If a string
		return this.replace(new RegExp(str, 'g'), newStr); };
}
```

聚脂填料很好玩！