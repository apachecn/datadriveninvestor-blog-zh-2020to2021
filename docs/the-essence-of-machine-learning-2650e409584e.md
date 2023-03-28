# 机器学习的本质

> 原文：<https://medium.datadriveninvestor.com/the-essence-of-machine-learning-2650e409584e?source=collection_archive---------10----------------------->

## 一元线性回归分析&梯度下降法

![](img/667b318cc71d87b150d06a88f43903f4.png)

机器学习已经彻底改变了我们的世界，展示了它在无数领域的应用。简而言之，这是一门让计算机在没有被明确编程的情况下完成特定任务或实现特定目标的科学。这种范式改变了我们的世界，彻底改变了我们看待问题和设计解决方案的方式。本文的重点是线性回归，更具体地说，**一元线性回归**。线性回归中使用的概念抓住了机器学习的核心，是一种可以轻松理解和实现的算法。

**回归**，简单地说，就是通过确定数据集中输入和输出之间的关系来制定准确的预测。回归允许通过使用过去的数据来预测连续值。线性回归是一种用于**监督** **学习**的算法，这是机器学习的一个子集，我们在其中为数据提供“答案”:每个数据集都有一个输入(x-自变量)和相应的输出(y-因变量)。我们向机器提供输入和输出，算法找到最佳可能的映射函数，使得 *y = f(x)* 。这个函数可以用来预测未来的结果。在监督学习中，我们知道正确的答案，我们的工作是监督机器能够正确预测新的数据输入。**相比之下，无监督学习**没有输出，算法在输入中寻找模式。**线性回归**在输出连续时使用，即数值:{*f(*x*)*|*f(*x*)*∈ℚ}，最好用直线建模。同样，还有多项式回归(用于非线性 x 和 y 关系)和逻辑回归(用于二进制输出)。单变量简单的说就是只有一个自变量；如果有多个 x 值(输入)，多元回归将在输入的一个*向量*上执行。因此，我们看到，线性回归，在其核心，没有什么过于复杂或抽象，而是一个非常强大的工具。线性回归形成了预测分析的基础，并且是机器学习的关键部分。

[](https://www.datadriveninvestor.com/2020/02/19/cognitive-computing-a-skill-set-widely-considered-to-be-the-most-vital-manifestation-of-artificial-intelligence/) [## 认知计算——一套被广泛认为是……

### 作为它的用户，我们已经习惯了科技。这些天几乎没有什么是司空见惯的…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/19/cognitive-computing-a-skill-set-widely-considered-to-be-the-most-vital-manifestation-of-artificial-intelligence/) 

线性回归通常建模如下:训练集→学习算法→假设。然后，可以通过假设运行新的输入，以便产生预测。需要注意的是，在使用数据集时，遵守**70–30 规则**是很常见的:70%的数据用于训练；30%用于测试和验证模型的准确性。该假设表示为:

![](img/323f3b4ae8657ef3f30989e1afbdc814.png)

这与 b↔θ₀和 m↔θ₁.的直线方程 y = b + mx 相同这正是假设所在——数据集的最佳拟合线，从中可以推断出预测。不同之处在于，机器正在计算生产线并不断改进，尽可能提供最低的误差幅度。线性回归的任务是找到θ₀和θ₁的最佳可能值，以便创建最准确的模型。

![](img/ee9e767e51cdb257420d786530378132.png)

The error of the model can be seen with the residuals. The average error of the current model is determined with MSE.

线性回归的力量在于程序评估错误并自我改进，而不需要任何显式代码(模型“学习”)。这通过最小化**成本函数**来完成。成本函数(也称为损失函数)的目的是评估当前预测模型的准确性；它说明了机器在确定 x 和 y 之间的关系时的错误程度。最常用的成本函数是**均方误差(MSE)** 。MSE 通过查看模型预测与实际输出的接近程度来确定模型预测的平均误差量。成本函数表示如下:

![](img/78dda5d34fa42a78e28b91da1c5f278c.png)

通过用实际输出减去模型的假设就可以找到误差。我们看到，通过对每个训练集{(x，y)，(x，y)，…，(xᵐ，yᵐ)})的误差的平方求和，并除以训练集的数量(m)，我们得到模型的平均误差。为什么要平方差异？有两个主要原因:这确保了 a)误差为正，b)较大的误差被放大，而较小的误差被忽略。它还是一个*连续可微的* *函数*，这一点非常有用，我们将会看到:如果一个函数 *f(* x *)* 也是一个连续函数，则称它是连续可微的。我们除以 2，以便更容易和更快地计算**梯度下降** — 2 被称为比例因子。成本函数所做的只是通过确定平均误差来计算当前模型的准确性。成本函数越小，精确度越高。目标是使成本函数尽可能接近 0，即减少当前模型中的误差。这是通过梯度下降实现的。

![](img/9769b730c7a386eb6889eb721ea74d8d.png)

The diagram on the left shows the line produced by a specific hypothesis and the diagram on the right shows the contour plot of a specific cost function. The goal is to determine values for θⱼ such that the cost function is in the ‘center’ of the contour plot, as illustrated. These images are from Andrew Ng’s Machine Learning course.

![](img/93357333837558b1d55561f35ae737ae.png)

梯度下降*最小化成本函数*。梯度下降是一种寻找函数的局部或全局最小值的优化算法。让我们想象一个只有一个变量θ₀.的成本函数我们可以看到，我们的成本函数， *J(θ* ₀ *)* ，在笛卡尔平面上绘制时呈现抛物线的形式。因此，最低值将在顶点。当函数处于最小值时，函数的导数为 0，因为切线是一条直线。梯度下降允许模型学习正确的方向以减少其误差。经过多次迭代后，模型收敛到最小值，进一步的调整几乎没有效果。梯度下降表示为偏微分方程:

![](img/ea19c2b986bee07a36f692518bbd475b.png)

我们来剖析一下这个等式。θⱼ是我们希望用来计算梯度下降的值。 **:=** 是*赋值运算符*，它将新计算的值赋给θⱼ； **=** 是一个*真值断言运算符— x=x* 。由于这是一个偏微分方程，成本函数的微分将针对θⱼ:进行，我们对θ₀或θ₁进行微分，并保持另一个值不变。这是为θ₀和θ₁同时完成的，因此它们的值都被准确地更新。α是一个**超参数**，意味着它是在执行梯度下降之前建立的。它代表*学习率*——它控制更新θⱼ.时所采取的步长(以及迭代次数)如果α过大，可能会超最小值而不收敛，甚至可能发散；如果它太小，可能需要很长时间才能收敛。找到α的正确值需要一些试验；我们通常从 0.001 开始，如果发现太慢，我们将α增加 10 倍，从 0.001 到 0.01 到 0.1，等等。这个方程的主要思想是梯度本身。梯度和导数一样，告诉我们一点的斜率，但梯度是一个*矢量*；它告诉我们斜率的大小和方向。因此，梯度下降通知模型要移动的方向，以及要采取的移动的大小，以便降低成本函数。

![](img/7b777aa37836ed9df4a56dce1382d9cc.png)

You can look at the number of steps taken for various learning rates with [**this lab**](https://developers.google.com/machine-learning/crash-course/fitter/graph) from Google Developers. With α = 0.10, it took 81 steps.

我们实际上如何确定θ₀和θ₁的值？我们为这两个值都设置了一个默认值，通常是 0(尽管从理论上讲，您可以选择任何有理数)。然后，我们对成本函数(MSE)执行梯度下降。将 *J(* θ₀,θ₁ *)* 代入我们的成本函数，我们得到方程:

![](img/5d4d9eca75b6d9c035e678de128284a8.png)

Until the value of the cost function is a minimum, gradient descent will continuously be performed. This is the same equation as before, with the partial differential computed for θ₀ and θ₁.

直到梯度收敛到 0，或者一个非常小的值( *J(* θ₀,θ₁ *)* →ε)，程序将继续调整和调整自己，而无需程序员的任何明确指示。该模型将评估其准确性并继续改进，直到θⱼ的任何进一步变化对结果几乎没有影响。这种形式的梯度下降被称为**批量梯度下降**，因为我们使用的是*整个数据集*的平均误差。另一种计算开销较小的形式是**随机梯度下降**，它仅使用数据集中 1 个随机示例的成本梯度。随机梯度下降法比分批法噪音更大(理解为更随机),但消耗的时间和资源明显更少。这两种形式可以结合在**小批量随机梯度下降**中，这是两者之间的一个很好的折衷，也是实践中最常用的算法。不管是哪种风格，主要思想是模型从错误中学习并不断改进自己，而不需要程序员的任何显式输入或代码。这些是令人难以置信的通用统计技术，通过调整它们使算法自我学习，真正的潜力可以得到展示。

![](img/73358bdfe58d50164d634f200a91e636.png)

A comparison of the iterations taken for Stochastic, Batch, and Mini-batch gradient descent. We can see how the Stochastic plot resembles a 1-D Markov chain, while Batch is much cleaner but potentially more expensive.

![](img/f13d0b06e9829498b01bfa4b7f116790.png)

The pièce de résistance. Here is a plot for gradient descent visualized in higher dimensions. This is a demonstration of what each iteration of gradient descent could look like for a cost function *J(*θ₀, θ₁). We have achieved the highest possible accuracy for the model, and can now employ it for forecasting.

线性回归是一种基本的预测算法，它展示了机器学习的能力和潜力。数据用于改进和改变模型；不是代码。它的应用是无限的，从金融到医疗保健。本文试图展示线性回归和梯度下降的基本数学原理，回答是什么让它起作用的问题？试图在不理解这些原则的情况下通过机器学习导航，就等同于在没有灯光的森林中漫步。理解算法的核心是至关重要的，因为知道*如何*和*为什么*比仅仅知道*什么*要重要得多。数学是机器学习的驱动力，理解底层概念提供了解构“黑箱”概念的具体理解。机器学习正在从根本上改变每个行业，打造一个由数据驱动的未来。你可以成为其中的一员。