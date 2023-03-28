# 是什么让你成为现代 C++程序员

> 原文：<https://medium.datadriveninvestor.com/what-makes-you-a-modern-c-programmer-608fe80c61eb?source=collection_archive---------18----------------------->

*通过使用“现代”C++* ，让您的 C++技能更上一层楼

![](img/8ff41401afe21c9832c566dbd6de0492.png)

Photo by [Toa Heftiba](https://unsplash.com/@heftiba?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

Y 你知道 C++语言的语法和编码。但你知道是什么让你成为现代 C++程序员吗？您的代码是否使用了 C++ 11、14 或 17 中引入的特性？你在应用程序中使用了标准的库类吗？你知道 C++ *lambda* 函数、*智能指针*和用于循环的表达式*吗？*

如果你的答案是否定的，这里有一些技巧可以提升你的 C++技能，让你成为一名现代的 C++程序员。

# 1.标准库容器

*Vector* 、 *Array* 和 *List* 是 C++中使用的基本库容器。

*Vector* 在堆中分配内存，所以可以动态添加和删除元素。当容器的大小未知并且在运行时可以改变时，这是有用的。

如果容器的大小是固定的，例如。一年中的几个月(12)，继续使用一个 *std:array* 来代替。与*向量*不同，*数组*在堆栈中分配内存，对元素访问更快。

*列表*有助于顺序元素访问 ex。存储按日期排序的订单列表。在最坏的情况下，它需要遍历列表的末尾来访问元素。

除了这些，C++还提供了其他标准库容器如*栈*、*队列*、*出列*、*优先级 _ 队列*、*映射*、*无序 _ 映射。*

*Stack* 对于容器中元素的 push、pop、top 操作很有用。

*队列*仅用于对队列前面的元素进行推、弹出等操作。

*出列*类似于*一个队列*但是对队列前面和后面的元素执行操作。

*优先级队列*类似于*队列*，但是基于与它们相关的优先级在容器中插入一个元素。根据排名插入学生

*映射*用于存储按键值排序的键和值对。

*无序映射*用于没有排序的键和值对。

如果你是 C++的初学者，从使用 *vector* 开始。如果你觉得你需要一个*栈*或者*地图*，那么就开始使用这些容器吧。同样以这样一种方式编写你的代码，使得容器之间的切换更容易，例如使用关键字 *auto* 。将来，如果你想从*出列*切换到*队列*，那就简单多了。

# 2.兰姆达斯

在 C++的早期版本中，*函数指针*被用来在变量中存储函数行为。后来使用指针访问了该函数。函数指针的缺点是难以理解，可读性差。所以他们想出了 *lambdas* 来代替传统的函数指针。所有现代编程语言都像 Java，Kotlin 使用 *Lambdas* 。

下面是 C++中 lambda 的例子

```
[](){} // Empty Lambda function
```

其中[]表示用于捕获值的 capture 子句，()表示传递给函数的参数，{}包含 lambda 函数体。

```
*//Example Lambda function isOdd*
auto isOdd = [](int candidate){ return candidate % 2 != 0 }; bool is3Odd = isOdd(3); //Returns true as 3 is Odd
bool is4Odd = isOdd(4); //Returns false as 4 is Evenvector nums{2, 3, 4, -1, 1};
//Find the number of Odd Items in the Vector. Returns 3
int odds = std::count_if(begin(nums), end(nums), isOdd);
```

在上面的例子中， *isOdd* 是一个 lambda 函数，用于检查输入的数字是否为奇数。 *Lambdas* 可以和*一起使用，用于每个*、 *count_if* 和其他标准库函数，突然间这些库就变得有用了。

使用 lambdas 的优势在于——它们可以用于形成某些通用工作，有助于实现并发性并增加代码的可读性。

# 3.标准库算法

C++中的*算法*库定义了可以执行多种操作的函数，例如排序、计数、操作、在容器中查找元素等。开发人员不需要为它们编写任何代码，节省了关注代码其他部分的时间。

标准库算法*交换、排序和计数 _if* 示例如下

```
*//Example of Swap function for a and b
int a = 5;
int b = 8;
swap(&a, &b);*//*Example of sort function. Sort elements in ascending order
vector<int> v{5, 3, 4, 2, 1};
sort(v.begin(), v.end());*//Count the number of 3’s in the vector v
int num_items3 = std::count_if(v.begin(), v.end(), [](int i){return i == 3;});
```

有大量的标准库算法可以使用。使用它们的好处包括——它们使代码更具可读性和表达性，就像每个人都明白 *sort* 函数是做什么的。此外，不必从头开始编写它们可以节省您的时间、精力和处理边缘情况时的所有麻烦。这也使得开发者很容易切换容器，因为大多数算法使用*迭代器*来访问元素。由于迭代器可以用于任何容器，当开发者从*栈*改变到*队列时，*代码的改变将是最小的。

对开发者来说，最大的挑战是*为代码找到*正确的算法，并*学习*实现它们。

# 4.例外

程序在运行时抛出错误或导致失败是很自然的。虽然有些可能是可预测的，但有些可能不是。此外，不同类型的错误需要以不同的方式处理。在某些情况下，开发人员可能会忘记处理错误情况。为了处理异常和异常错误，使用*异常*。

*c++中的异常*包含 3 个主要部分

*   *Try —* 这个块需要尽可能的小，以检查抛出*异常*的代码
*   *抛出—* 可以抛出 *std::exception* 类的异常
*   *Catch —* 用于捕获异常的代码块。需要对异常进行排序，从最具体的异常在顶部，到一般的异常在底部。

一个*异常*的例子如下所示

```
//Example of Divide by Zero exception thrown
void func(int a, int b)
{
  try {
    if( b == 0 ) throw std::invalid_argument("b is zero");
    else a/b;
  }
  catch(std::exception& e){
    //Handle Exception here
  }
}
```

使用异常的优点是在 try 和 catch 块之间，通过调用它们的析构函数类，本地范围的对象被自动清除。所以与其他编程语言不同，C++中不需要 *finally* 块。另外 *std::exception* 类非常有用。大多数标准库代码抛出从这个类派生的对象。同样，当有一系列函数调用时，如 *a* 调用 *b* , *b* 调用 *c* …。 *y* 调用 *z* ，从 *z* 返回错误给 *a* 是相当令人沮丧的。这会花费大量时间并影响性能。在这种情况下，可以在 *z* 中使用异常来处理错误。

综上所述，*现代 C++* 表现力强，可读性强。它帮助开发人员使用语言的力量来表达意图，并最小化编码所需的工作。