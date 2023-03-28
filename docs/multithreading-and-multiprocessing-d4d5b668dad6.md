# 多线程和多重处理

> 原文：<https://medium.datadriveninvestor.com/multithreading-and-multiprocessing-d4d5b668dad6?source=collection_archive---------18----------------------->

## 了解什么是多线程和多处理，以及它们之间的区别

![](img/1de782b00cebfb265b36a1e219e5c82b.png)

Photo by [Arnold Francisca](https://unsplash.com/@clark_fransa?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

*   **多线程**是一种技术，其中由一个进程生成几个线程来同时、连续地执行单独的任务。这使您认为线程是并行运行的，然而它们实际上是以并排的方式运行的。Python 编程语言中的全局解释器锁(GIL)拦截同时运行的线程。
*   **多重处理**是一种实现并行的技术。多个进程在多个 CPU 上同时运行，它们之间不共享资源。每个进程可以有许多线程。这些线程在它们自己的内存空间中运行。

考虑以下计算一个数的平方和立方的程序:

首先，让我们看看通用代码和输出

我们得到的上述程序的输出如下

```
Squares of all the numbers 
square of 2 is 4 
square of 3 is 9 
square of 4 is 16 
square of 5 is 25 Cubes of all the numbers 
cube of 2 is 4 
cube of 3 is 9 
cube of 4 is 16 
cube of 5 is 25 **Time taken 1.6047849655151367**
```

现在，让我们用多线程为上述问题写一段代码

上述代码的输出如下:

```
square of 2 is 4 
cube of 2 is 4 
square of 3 is 9 
cube of 3 is 9 
square of 4 is 16 
cube of 4 is 16 
square of 5 is 25 
cube of 5 is 25 **Time taken 0.8078334331512451**
```

正如您所看到的，多线程技术花费了一半的时间来给出相同问题的输出。

我们可以使用多重处理得到相同的结果，如下所示

输出将如下

```
square of 2 is 4 
cube of 2 is 4 
square of 3 is 9 
cube of 3 is 9 
square of 4 is 16 
cube of 4 is 16 
square of 5 is 25 
cube of 5 is 25 **Time taken 0.82962965965271**
```

当这个程序执行时，总共有 3 个进程同时进行:我们的主父程序和 2 个进程，即 p1 和 p2。需要注意的重要一点是，每个进程都有自己的地址空间，称为虚拟内存。因此，程序变量不能在两个进程之间共享。如果您想在两个进程之间共享数据，您需要使用进程间通信(IPC)技术。

多线程和多重处理都是实现多任务的方法。然而，它们并不相同。以下是多线程和多处理之间的一些差异:

*   与创建线程相比，创建进程既耗时又耗费资源。
*   为了提高计算能力，多处理技术增加了 CPU，而多线程技术创建了多个线程。
*   如果您的一个流程出现错误，其他流程不会受到影响。然而，多线程并非如此，因为所有线程都属于一个进程。因此，如果一个线程遇到错误，整个进程就会停止。另一方面，如果一个进程被阻塞，其他进程将无法执行，除非被阻塞的进程被解除阻塞。如果一个线程被阻塞，同一进程中的其他线程可以继续运行它们的任务。
*   在多重处理中，多个进程同时执行。在多线程中，单个进程的多个线程是并发执行的。

我希望这篇文章是有帮助的。谢谢你阅读它！

> 你可以在这里联系我。