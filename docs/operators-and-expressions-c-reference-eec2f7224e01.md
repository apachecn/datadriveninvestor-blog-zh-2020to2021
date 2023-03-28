# 运算符和表达式(C#参考)

> 原文：<https://medium.datadriveninvestor.com/operators-and-expressions-c-reference-eec2f7224e01?source=collection_archive---------20----------------------->

## C#概念

## C#中不同的逻辑运算符

![](img/dc1bb90774943b5274f1af6c2da88266.png)

Photo by [Umberto](https://unsplash.com/@umby?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/electronic?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

本文演示了下面的运算符列表。

*   **按位求补运算符:** ~
*   **二进制左移运算符:** < <
*   **二进制右移运算符:** > >
*   **二进制与:** &
*   **逻辑或:** |
*   **逻辑异或运算符:** ^

它还包括优先级顺序，即操作符的执行顺序。

[](https://www.datadriveninvestor.com/2020/07/13/2020-development-choices-for-multi-platform-saas-application/) [## 多平台 SaaS 应用的 2020 年发展选择|数据驱动的投资者

### 我目前正在为公司做一个新项目。该项目包括一个移动应用程序，由一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/07/13/2020-development-choices-for-multi-platform-saas-application/) 

# 按位补码运算符~

“ **~** ”运算符通过反转每个位来生成其操作数的**位补码**:

```
uint a = 0b_0000_1111_0000_1111_0000_1111_0000_1100; 
uint b = ~a; 
Console.WriteLine(Convert.ToString(b, toBase: 2));// Output: 
// 11110000111100001111000011110011
```

# 左移运算符<<

The “ **< <** “运算符将其左侧操作数左移由其右侧操作数定义的位数。

左移运算丢弃结果类型范围之外的高位，并将低位空位位置设置为零，如下例所示:

```
uint x = 0b_1100_1001_0000_0000_0000_0000_1111_1111;
Console.WriteLine($"Before: {Convert.ToString(x, toBase: 2)}");uint y = x << 4;
Console.WriteLine($"After:  {Convert.ToString(y, toBase: 2)}");// Output:
//Before: 11001001000000000000000011111111
//After:  10010000000000000000111111110000
```

# 右移位运算符>>

“ **> >** ”运算符将左边的操作数右移右边操作数定义的位数。

右移操作会丢弃低位，如下例所示:

```
uint x1 = 0b_1111;
Console.WriteLine($"Before: {Convert.ToString(x1, toBase: 2),4}");uint y1 = x1 >> 2;
Console.WriteLine($"After:  {Convert.ToString(y1, toBase: 2),4}");// Output:
// Before: 1111
// After:    11
```

# 逻辑 AND 运算符&

“ **&** ”运算符计算其操作数的按位“**逻辑与“**”:

```
uint a = 0b_1111_1000;
uint b = 0b_1001_1101;
uint c = a & b;
Console.WriteLine(Convert.ToString(c, toBase: 2));// Output:
// 10011000
```

对于 bool 操作数，&运算符计算其操作数的逻辑与。一元运算符&是地址运算符。

# 逻辑异或运算符^

“ **^** 运算符计算其操作数的按位**逻辑异或**，也称为按位逻辑异或:

```
uint a = 0b_1111_1000;
uint b = 0b_0001_1100;
uint c = a ^ b;
Console.WriteLine(Convert.ToString(c, toBase: 2));// Output:
// 11100100
```

# 逻辑或运算符|

“ **|** ”运算符计算其操作数的按位**逻辑或**:

```
uint a = 0b_1010_0000;
uint b = 0b_1001_0001;
uint c = a | b;
Console.WriteLine(Convert.ToString(c, toBase: 2));// Output:
// 10110001
```

对于 bool 操作数，|运算符计算其操作数的逻辑或。

# 运算符优先级

下面的列表从最高优先级到最低优先级对按位运算符和移位运算符进行排序:

*   按位补码运算符~
*   移位操作符<< and >>
*   逻辑 AND 运算符&
*   逻辑异或运算符^
*   逻辑或运算符|

使用括号“()”来修改运算符优先级所命令的求值顺序。

请在下面找到输出随优先级变化的示例。**注:**情况 1 遵循默认的执行顺序，即&运算符首先被执行&OR 运算符。

而在第二种情况下，我们借助'()'手动指定订单执行，即先执行 OR 运算符，然后执行&运算符。

```
uint a = 0b_1101; 
uint b = 0b_1001; 
uint c = 0b_1010; **//Case 1**
uint d1 = a | b & c;
Display(d1);  // output: 1101 **//Case 2**
uint d2 = (a | b) & c; 
Display(d2);  // output: 1000  voidDisplay(uint x) => 
Console.WriteLine($"{Convert.ToString(x, toBase: 2), 4}");
```

## GitHub 回购

[](https://github.com/ssukhpinder/BitwiseAndShiftOperators) [## ssukhpinder/bitwiseandshift operators

### C#中的操作员指南。在 GitHub 上创建一个帐户，为 ssukhpinder/BitwiseAndShiftOperators 的发展做出贡献。

github.com](https://github.com/ssukhpinder/BitwiseAndShiftOperators) 

## 感谢您的阅读。请继续访问并在你的网络中分享。请把你的想法和反馈放在评论区。

在[LinkedIn](https://www.linkedin.com/in/sukhpinder-singh-532284a2/)[insta gram](https://www.instagram.com/sukhpindersukh/)[脸书](https://www.facebook.com/sukhpinder.singh.52/) [Twitter](https://twitter.com/sukhsukhpinder) 上关注我

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)