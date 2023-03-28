# 区分普通工程师和书呆子的挑战

> 原文：<https://medium.datadriveninvestor.com/the-fizzbuzz-challenge-to-differentiate-a-normal-engineer-from-a-nerd-8362b6488b9c?source=collection_archive---------2----------------------->

## 我们都有一个同事

![](img/6f2b8e336fb3ec0596c74416608d8658.png)

Photo by [Christina @ wocintechchat.com](https://unsplash.com/@wocintechchat?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/software-engineer?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

软件工程师是一群独特的人。虽然他们大多数都是正常人，但有些人喜欢以不同的方式做事。如果你给这些稀有物种一个要解决的问题，它们会绞尽脑汁寻找最优解。你会发现他们不是以随机的方式从 A 点到 B 点，而是通过使用 [Dijkstra 的算法](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)沿着最短的路径行走。

> 你心目中的完美约会是什么样的？
> 
> 日/月/年。其他格式有点混乱。

这就是我们中的一些人看待事物的方式。

虽然有多种方法来识别工程师的类型，无论他们是普通工程师还是书呆子，但 FizzBuzz 测试是区分他们的最简单的方法之一。FizzBuzz 测试也是许多软件面试中给出的常见算法。

在我们开始之前，让我给你一个 FizzBuzz 算法的简单概念。

给定从 1 到 100 的数字，要求打印所有数字，以便

*→如果这个数能被 3 整除，你会打印出嘶嘶的声音*

*→如果这个数能被 5 整除，你就打印 Buzz*

*→如果数字能被 15 整除，则打印 FizzBuzz*

*→否则，打印号码*

因此，您的最终输出将类似于

```
1
2
Fizz
4
Buzz
Fizz
7
...
14
FizzBuzz
16
...
```

现在让我们看看不同类型的工程师将如何解决这个问题。

# 普通工程师

一个普通的工程师会把这看作一个简单的问题，并试图用最简单的方法来解决这个问题。这是他们的源代码的样子:

```
def basicSolution():Unit = {
  for (num <- 1 to 100) {
    if (num % 15 == 0) *println*("FizzBuzz")
    else if (num % 3 == 0) *println*("Fizz")
    else if (num % 5 == 0) *println*("Buzz")
    else *println*(num)
  }
}
```

一个简单问题的简单解决方案。他们不太关心错综复杂的事物等等。他们发现问题，解决问题。

此时，一个普通的工程师会收拾行李回家。干得好。

# **专职工程师**

这些类型的工程师更有经验和奉献精神，他们会研究这个问题并考虑优化它。他们将致力于普通工程师的解决方案，并尝试将其调整到下一个水平。不过他们的想法不会走得太远。

对于上述情况，他们会想是否需要 15 的额外模运算？事实证明，并不需要。这里有一个更好的解决方案:

```
def AdvancedSolution():Unit = {
  for (num <- 1 to 100) {
    var status = false
    if (num % 3 == 0) {
      *print*("Fizz")
      status = true
    }
    if (num % 5 == 0) {
      *print*("Buzz")
      status = true
    }
    if (status==false) *println*(num)
    else *println*("")
  }
}
```

**请注意 3 次和 5 次检查的 print 语句，而不是 println。*

有了这个，一个专门的工程师就能够去除额外的模运算。通过多一点代码行，它们被成功地限制到只有几个模运算。他们比一般人更专注，但不会花太多时间——他们会尝试优化清晰可见的问题。

但对于这个小小的变化，他们确实希望得到经理们的一点赞赏。

# 极客

极客根本不喜欢模运算。他们知道模运算的复杂度很高，而且 T2 根本不喜欢它。他们想办法把它从代码中完全删除。作为一个注重细节的人，他们有很多时间花在像这样的小问题上。

这是他们的代码看起来的样子:

```
def NerdSolution() = {
  var tempNumber3=0
  var tempNumber5=0
  for (num <- 1 to 100) {
    var status = false
    tempNumber3=tempNumber3+1
    tempNumber5=tempNumber5+1
    if (tempNumber3==3){
      *print*("Fizz")
      status = true
      tempNumber3=0
    }
    if (tempNumber5==5){
      *print*("Buzz")
      status = true
      tempNumber5=0
    }
    if (status==false) *println*(num)
    else *println*("")
  }
}
```

如您所见，该解决方案完全消除了高时间复杂度的模运算，并完成了预期的工作。

极客们力求完美。他们会花费大量时间寻找最佳解决方案——不管问题是大是小。他们不希望自己的工作得到太多的赞扬。他们只是需要更多可以优化的问题。

# 递归粉丝

他们不喜欢循环！句号。在他们的宗教中，循环就像魔鬼，应该不惜一切代价避免。他们的软件字典从递归开始。

这是他们解决问题的方法:

```
def GeniusFizzBuzz(start: Int, end: Int): Unit = {
  if (start <= end) {
    val mod3 = (start % 3) == 0
    val mod5 = (start % 5) == 0
    if (mod3 && mod5) *println*("FizzBuzz")
    else if (mod3) *println*("Fizz")
    else if (mod5) *println*("Buzz")
    else *println*(start)
    *GeniusFizzBuzz*({
      start+1
    }, end)
  }
}
```

他们会想办法把每一个代码都变成递归。如果它不需要循环任何东西，他们就不会碰那些代码——反正也没什么意思。

这是一个如何用四种不同方法解决同一个简单问题的演示。以及解决问题的过程如何让我们了解工程师的类型。

如果你属于第四类，那么恭喜你；你有独特的品味。

如果你找到解决这个问题的其他方法，请告诉我。你把自己归为哪一类？