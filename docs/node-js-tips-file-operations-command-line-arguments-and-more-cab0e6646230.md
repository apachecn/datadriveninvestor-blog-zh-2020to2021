# Node.js 提示—文件操作、命令行参数等等

> 原文：<https://medium.datadriveninvestor.com/node-js-tips-file-operations-command-line-arguments-and-more-cab0e6646230?source=collection_archive---------3----------------------->

![](img/0b30c292a3dfb656f4aa4907a2a90376.png)

Photo by [Jared Short](https://unsplash.com/@thejroc?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

像任何类型的应用程序一样，当我们编写节点应用程序时，有一些困难的问题需要解决。

在本文中，我们将研究一些编写节点应用程序时常见问题的解决方案。

# 将命令行参数传递给 Node.js 程序

我们通过使用`process.argv`属性获得命令行参数。

这是一个包含所有参数的数组，包括`node`和脚本名。

`'node'`总是第一个进入。

脚本名称是第二个条目。

其余的参数是剩余的条目。

例如，如果我们有:

```
node foo.js one two=three four
```

然后`node`是`process.argv`的第一个条目，`foo.js`是第二个，`one`是第三个，以此类推。

# 在 Node.js 中写入文件

我们可以使用`writeFile`方法在节点 app 中写一个文件。

例如，我们可以写:

```
const fs = require('fs');fs.writeFile("/foo.txt", "hello world!", (err) => {
  if (err) {
    return console.log(err);
  }
  console.log("file saved");
});
```

我们调用`writeFile`来写文件。

第一个参数是文件的路径。

第二个是文件的内容。

文件写入过程结束时调用回调。

`err`是错误对象，在遇到错误时定义。

还有一个同步版本叫`writeFileSync`。

我们可以通过书写来使用它:

```
fs.writeFileSync('/foo.txt', 'hello world');
```

第一个参数是文件路径。

第二是内容。

# 如何调试 Node.js 应用程序

我们可以使用`node-inspector`包来调试节点应用程序。

我们可以通过运行以下命令来安装它:

```
npm install -g node-inspector
```

全球安装。

然后我们用`node-inspector`运行`node-debug app.js`来运行它，这让我们可以用断点、剖析等来调试它。

我们也可以用调试器运行`node inspect app.js`来运行`app.js`。

# 读取 Node.js 中的环境变量

我们可以通过使用`process.env`对象来读取节点应用程序中的环境变量。

例如，如果我们有环境变量`FOO`，我们可以写:

```
process.env.FOO
```

# 在 Javascript 中移除数组中的空元素

要从 JavaScript 数组中移除 empty，我们可以使用`filter`方法。

例如，我们可以写:

```
const arr = [0, 1, null, undefined, 2,3,,,,6];
const filtered = arr.filter((el) => (el !== null || typeof el !== 'undefined'));
```

这将返回一个从`arr`创建的数组，所有的`null`和`undefined`都被移除了。

# 对 forEach 循环使用 async/await

我们可以将`async`和`await`用于 for-of 循环。

例如，我们可以写:

```
const printFiles = async (filePaths) => {
  for (const file of filePaths) {
    const contents = await fs.readFile(file, 'utf8');
    console.log(contents);
  }
}
```

我们使用承诺版本的`readFile`在 for-of 循环的每次迭代中读取文件。

要并行运行承诺，我们可以使用`Promise.all`方法。

例如，我们可以写:

```
const printFiles = async (filePaths) => {
  await Promise.all(filePaths.map(async (file) => {
    const contents = await fs.readFile(file, 'utf8')
    console.log(contents)
  }));
}
```

我们称`map`为`filePaths`来描绘通往承诺的道路。

然后我们在一系列的承诺中称`Promise.all`。

# 获取节点应用程序目录中所有文件的名称列表

我们可以通过使用`readdir`或`readdirSync`方法获得一个目录中所有文件的名称列表。

例如，我们可以写:

```
const fs = require('fs');

fs.readdir('/tesrDir', (err, files) => {
  files.forEach(file => {
    console.log(file);
  });
});
```

`files`拥有文件字符串、缓冲区或目录项的数组。

要同步读取目录，我们可以写:

```
const fs = require('fs');

fs.readdirSync('/testDir').forEach(file => {
  console.log(file);
});
```

我们同步读取一个目录。

# 用 Node.js 解析 JSON

我们可以要求 JSON 文件或者用`JSON.parse`解析它们。

例如，我们可以写:

```
const config = require('./config.json');
```

或者:

```
const config = require('./config');
```

扩展是可选的。

同样，我们可以使用`JSON.parse`来解析 JSON 字符串。

![](img/030b03b0a8d62ea7a44ef1a0f6318730.png)

Photo by [Matt Jones](https://unsplash.com/@mattrobinjones?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 结论

我们可以用`process.argv`获得命令行参数。

环境变量被读入`process.env`对象。

`require`可以用来导入 JSON 文件。

`fs`模块有读写文件的方法。

for-of 循环可以按顺序运行承诺。