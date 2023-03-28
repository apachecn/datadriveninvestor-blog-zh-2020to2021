# 用 Python 实现线性回归与多项式回归的完整指南

> 原文：<https://medium.datadriveninvestor.com/complete-guide-on-linear-regression-vs-polynomial-regression-with-implementation-in-python-964c64c28aa8?source=collection_archive---------0----------------------->

![](img/e604a56d8d891c9f73c77a629f7bb79e.png)

在我以前的文章中，我写了如何为我们的数据集绘制回归线。太酷了，对吧！但是还有一个问题，我们的模型越来越不精确。我们**的最终目标**始终是建立一个精确度最高、误差最小的模型。因此，在本文中，我们将了解如何通过使用曲线来实现最适合我们数据的多项式回归。

在此之前，这里有一些基本的多项式函数及其图形绘制。这将有助于您更好地理解对特定数据集使用哪个多项式。

**享受这篇文章吧！**

![](img/2a08700589415e2f0c11a4649fdffb40.png)

Comparison Between Models

## 多项式函数及其图形；

(1)曲线图为 **Y=X** :

![](img/4c2963a65e4bb525da12298ce911c3e1.png)

(2)曲线图为 **Y = X** :

![](img/394407289b8afd52270551b71c002f26.png)

(3)曲线图为 **Y = X** :

![](img/52551dde711591d99a757903e2acc74c.png)

(4)多项式多于一个的图: **Y = X +X +X** :

![](img/3366fccf235dfc9dfbaf2e805ca77fb4.png)

在该图中，您可以看到红点显示的是 Y=X +X +X 的图形，蓝点显示的是 Y=X 的图形。在这里，您可以清楚地看到，最大功率会影响我们的图形形状。

好了，让我们开始酷的部分吧！:)

好了，现在我们来看看为什么我们应该使用多项式(非线性)回归。这里我将举一个例子，对于第一部分，我将找到线性回归线并计算误差，对于第二部分，我将使用多项式回归，并找到最适合它的曲线并计算误差。然后，我们将比较这两个误差，看看哪个模型表现更好。

[](https://www.datadriveninvestor.com/2020/02/19/cognitive-computing-a-skill-set-widely-considered-to-be-the-most-vital-manifestation-of-artificial-intelligence/) [## 认知计算——一套被广泛认为是……

### 作为它的用户，我们已经习惯了科技。这些天几乎没有什么是司空见惯的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/19/cognitive-computing-a-skill-set-widely-considered-to-be-the-most-vital-manifestation-of-artificial-intelligence/) 

在这里，我采用这个多项式函数来生成数据集，因为这是一个示例，我将向您展示何时使用多项式回归。我要加一些噪点，这样看起来更真实！

这里我们要用 [**正规方程**](https://medium.com/@shuklapratik22/multivariable-linear-regression-using-normal-equation-707d19f1c325) 实现线性回归和多项式回归。你可以 [**点击这里**](https://www.youtube.com/channel/UCpRJj1vjQsjCTB3S5ANvNvg) 查看各种机器学习算法的详细讲解视频。

让我们向前看，

正常方程如下:

![](img/8d024ad226fc80eee1dff1b52fc731a9.png)

在上面的等式中:

θ:最佳定义的假设参数。

x:输入每个实例的特征值

y:每个实例的输出值

# 简单线性回归:

**简单线性回归的假设函数:**

**y =β_ 0+β_ 1 * x**

**我们来编码:**

(1)导入所需的库:

![](img/5fe477d0a95ee3dd3d5e6786d0691dd7.png)

(2)数据集生成:

![](img/aef03c0bb3a44cec2e4103db179fbec6.png)

(3)x 的形状:

![](img/98305cf7142eb86541ff7472f35f9cdd.png)

(4)主矩阵的第 1 列:

这里，列-1 将始终是β_ 0 系数的值，该值将始终为 1。但是要创建一个矩阵，我们需要把它看作一列。为了更好的理解 [**，点击这里**](https://youtu.be/wmmUJnmwQho)

![](img/0580534fd406985410e953f2e5810894.png)

(5)x _ bias 的形状:

![](img/cdc897b04c35e5dfe6aa9f5862a8c7b2.png)

(6)因为我们需要用 x_bias 附加 x，所以它必须具有相同的形状:

![](img/4997526b8c4fbb347402bdc47c1104a8.png)

(7)最终矩阵 x:

![](img/5d1bb7f34251186edf5312e9f8d61ead.png)![](img/4369c1d3a572fa8b6d612e4b0d81f653.png)

(8)矩阵转置:

![](img/7663eadbad8681abfe87ea375f663c57.png)

(9)矩阵乘法:

![](img/b9d62badc989102421ca11d8b61e628a.png)

(10)矩阵的逆矩阵:

![](img/23d9543e9d6b8cd07aa3bd124e227db1.png)

(11)矩阵乘法:

![](img/5fac7cc10a5207cd3097cfae05552134.png)

(12)求系数:

![](img/41fe0faefe0a6bc6aab39278c6a72cf6.png)

(13)绘制回归线:

![](img/18b46f32d9181a046be1ea165e15d56a.png)

(14)预测功能:

![](img/92e6e73eb96e161e502137ad1b9508fe.png)

(15)计算均方误差:

![](img/2b4abc02ee25498474a327a9078e1bbf.png)

所以这里我们可以看到误差很高。让我们看看如果使用多项式方程会发生什么。

正常方程如下:

![](img/8d024ad226fc80eee1dff1b52fc731a9.png)

# 多项式回归:

## 多项式回归的假设函数:

![](img/fa9b05cd5dc4446703ce2598a6e2bc8d.png)

在哪里，

贝塔 _0，贝塔 _1，…是我们需要找到的系数。

x，x，x 是我们数据集的特征。

![](img/6550e9e3733c33c4fd894caf45cc091e.png)

**咱们来码:**

(1)导入所需的库:

![](img/5615ed92e42f2a0a15ee17d776a591a0.png)

(2)生成数据点:

![](img/4a27ad9a5e7c81b3fff44f5710f4bb1f.png)

(3)初始化 x，x，x 向量:

![](img/055ca8522da22c322d8a50f4a2bbb618.png)

(4)X 矩阵的第 1 列:

![](img/00bf3bad7dd5a090d9c4ec0ea301562a.png)

(5)形成完整的 x 矩阵:

![](img/a478a7a14f532038096df29bb2fb9f48.png)

(6)矩阵的转置:

![](img/adc84612146ece1f4a1dab88408a6301.png)

(7)矩阵乘法:

![](img/f38555c7d9efe900d199a2b9d7033859.png)

(8)矩阵的逆矩阵:

![](img/96b10f524c3a89012f7af62703a2ef60.png)

(9)矩阵乘法:

![](img/78bd17f981744f35defd9e289bbee748.png)

(10)系数值:

![](img/1b355bdf8d316838007e033af5b10626.png)

(11)将系数存储在变量中:

![](img/86bb8df94ca366a60a984b8fa83875de.png)

(12)用曲线绘制数据:

![](img/4569d7ee8a0681dd7380b9836c396e64.png)

(13)预测功能:

![](img/ea5009547f4ef8f9da89b6c424408cf4.png)

(14)误差函数:

![](img/fd6450193ec6d5da53ea4fa31ad800a5.png)

(15)计算误差:

![](img/04230d70109df987843727c1ccf00b38.png)

这里你可以看到误差**明显低于线性回归中的误差**。

所以我们可以说它做了一件相当好的工作。因此，总之，我们可以说，如果我们的数据集遵循曲线趋势，那么我们可以使用多项式回归获得更好的结果和准确性。

我希望你们喜欢这篇文章。如果你喜欢，请点击拍手图标。

## 向前看，

在下一篇文章中，我将展示如何用 python 实现其他多项式回归。

我所有的文章都在我的博客上:
[**patrickstar0110.blogspot.com**](http://patrickstar0110.blogspot.com)

**在我的 youtube 频道观看带有解释和推导的详细视频:**

【https://www.youtube.com/channel/UCpRJj1vjQsjCTB3S5ANvNvg**T21**

**(1)简单线性回归解释及其推导:**
[https://youtu.be/1M2-Fq6wl4M](https://youtu.be/1M2-Fq6wl4M)

**(2)如何从零开始计算线性回归中模型的精度:**
[https://youtu.be/bM3KmaghclY](https://youtu.be/bM3KmaghclY)

**(3)使用 Sklearn 的简单线性回归:**
[https://youtu.be/_VGjHF1X9oU](https://youtu.be/_VGjHF1X9oU)

**(4)机器学习数学(矩阵)讲解:**
[https://youtu.be/1MASyeyAydw](https://youtu.be/1MASyeyAydw)

**(5)正规方程的完整数学推导:**
[https://youtu.be/E7Q4UP6bNmc](https://youtu.be/E7Q4UP6bNmc)

**(6)利用正规方程实现简单线性回归:【https://youtu.be/wmmUJnmwQho】** 

## 阅读我的其他文章:

(1)从零开始线性回归:
[https://medium . com/@ shuklapratik 22/Linear-Regression-从零开始-a3d21eff4e7c](https://medium.com/@shuklapratik22/linear-regression-from-scratch-a3d21eff4e7c)

(2)暴力线性回归:
[https://medium . com/@ shuklapratik 22/Linear-Regression-line-Through-Brute-Force-1 bb6d 8514712](https://medium.com/@shuklapratik22/linear-regression-line-through-brute-force-1bb6d8514712)

(3)线性回归完全推导:
[https://medium . com/@ shuklapratik 22/Linear-Regression-Complete-Derivation-406 f 2859 a09a](https://medium.com/@shuklapratik22/linear-regression-complete-derivation-406f2859a09a)

(4)简单线性回归实现从头开始:
[https://medium . com/@ shuklapratik 22/Simple-Linear-Regression-Implementation-从头开始-cb4a478c42bc](https://medium.com/@shuklapratik22/simple-linear-regression-implementation-from-scratch-cb4a478c42bc)

(5)从零开始简单线性回归:
[https://medium . com/@ shuklapratik 22/Simple-Linear-Regression-implementation-2fa 88 CD 03 e 67](https://medium.com/@shuklapratik22/simple-linear-regression-implementation-2fa88cd03e67)

(6)梯度下降及其数学:
[https://medium . com/@ shuklapratik 22/what-is-Gradient-Descent-7eb 078 FD 4c DD](https://medium.com/@shuklapratik22/what-is-gradient-descent-7eb078fd4cdd)

(7)从无到有梯度下降的线性回归:
[https://medium . com/@ shuklapratik 22/Linear-Regression-With-Gradient-Descent-From-Scratch-d 03 DFA 90d 04 c](https://medium.com/@shuklapratik22/linear-regression-with-gradient-descent-from-scratch-d03dfa90d04c)

(8)线性回归误差计算技巧:
[https://medium . com/@ shuklapratik 22/Error-Calculation-Techniques-For-Linear-Regression-AE 436 b 682 f 90](https://medium.com/@shuklapratik22/error-calculation-techniques-for-linear-regression-ae436b682f90)

(9)机器学习用矩阵介绍:
[https://medium . com/@ shuklapratik 22/机器学习用矩阵介绍-8aa0ce456975](https://medium.com/@shuklapratik22/introduction-to-matrices-for-machine-learning-8aa0ce456975)

(10)了解线性回归中正规方程背后的数学(完全推导)
[https://medium . com/@ shuklapratik 22/Understanding-Mathematics-Behind-Normal-Equation-In-Linear-Regression-aa 20 dc5 a 0961](https://medium.com/@shuklapratik22/understanding-mathematics-behind-normal-equation-in-linear-regression-aa20dc5a0961)

(11)使用正规方程(矩阵)实现简单线性回归
[https://medium . com/@ shuklapratik 22/Implementation-Of-Simple-Linear-Regression-Using-Normal-Equation-matrix-f 9021 c 3590 da](https://medium.com/@shuklapratik22/implementation-of-simple-linear-regression-using-normal-equation-matrices-f9021c3590da)

(12)多变量线性回归实现:
[https://medium . com/@ shuklapratik 22/Multivariable-Linear-Regression-using-normal-equation-707d 19 f1c 325](https://medium.com/@shuklapratik22/multivariable-linear-regression-using-normal-equation-707d19f1c325)

![](img/9c3d4e80ad5f35bf332885ac145b5075.png)

Thank You!!