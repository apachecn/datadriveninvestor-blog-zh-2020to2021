# JavaScript 算法:之间是什么？

> 原文：<https://medium.datadriveninvestor.com/javascript-algorithm-what-is-between-246e27e90dac?source=collection_archive---------9----------------------->

## 我们将创建一个数组，输出从 a 到 b 的所有数字(我们的两个参数)。

![](img/78e6d923528cf2ec49a69b4f030b6cf8.png)

今天，我们将编写一个名为`between`的函数，它将接受两个整数输入，`a`和`b`。

使用这两个数字作为我们的参数，该函数的目标是输出一个包含从`a`到`b`的所有数字的数组。这里有一个例子:

```
let a = 1;
let b = 4;// output: [1,2,3,4];
```

我们如何着手将它转化为代码呢？跟着走。

[](https://www.datadriveninvestor.com/2019/03/22/the-seductive-business-logic-of-algorithms/) [## 算法诱人的商业逻辑|数据驱动的投资者

### 某些机器行为总是让我感到惊讶。我对他们从自己的成就中学习的能力感到惊讶…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/03/22/the-seductive-business-logic-of-algorithms/) 

我们首先创建一个空数组，并将其赋给一个名为`arr`的变量。

```
let arr = [];
```

接下来，我们使用我们钟爱的 for 循环和从`a`到(包括)`b`的循环。每个数字进入`arr`数组。

```
for(let i = a; i <= b; i++){
   arr.push(i);
}
```

当我们完成时，我们返回我们的数组。

```
return arr;
```

以下是剩余的代码:

```
function between(a, b) {
  let arr = [];
  for(let i = a; i <= b; i++){
    arr.push(i);
  }
  return arr;
}
```

如果你觉得这个算法有帮助，可以看看我最近的其他 JavaScript 算法解决方案:

[](https://levelup.gitconnected.com/javascript-algorithm-simple-comparison-ca408f24b353) [## JavaScript 算法:简单比较

### 对于今天的短算法，我们要写一个函数，涉及比较两个不同数据类型的整数。

levelup.gitconnected.com](https://levelup.gitconnected.com/javascript-algorithm-simple-comparison-ca408f24b353) [](https://medium.com/javascript-in-plain-english/javascript-algorithm-shopping-list-a0e89442b8b9) [## JavaScript 算法:购物清单

### 我们将编写一个算法，将所有食物相加。这种算法着眼于基础数学…

medium.com](https://medium.com/javascript-in-plain-english/javascript-algorithm-shopping-list-a0e89442b8b9) [](https://medium.com/javascript-in-plain-english/javascript-algorithm-generate-range-of-integers-73f739b4871) [## JavaScript 算法:生成整数范围

### 我们要写一个函数，它会在每隔一段时间后产生一个在给定的最小值和最大值之间的整数范围…

medium.com](https://medium.com/javascript-in-plain-english/javascript-algorithm-generate-range-of-integers-73f739b4871)