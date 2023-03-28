# ArgParse 作为跟踪机器学习超参数的工具？

> 原文：<https://medium.datadriveninvestor.com/argparse-as-a-tool-for-tracking-machine-learning-hyperparameters-fe594b9788ef?source=collection_archive---------5----------------------->

![](img/974aec6e9f156afff2485d3b1fbf16d3.png)

机器学习超参数是在学习过程开始之前设置的参数。它用于控制学习过程。这些参数是可调的，可以直接影响模型的训练效果。

超参数可以被分类为模型超参数，当[将机器适配到训练集](https://en.wikipedia.org/wiki/Model_fitting)时不能被推断，因为它们涉及[模型选择](https://en.wikipedia.org/wiki/Model_selection)任务，或者算法超参数，其原则上对模型的性能没有影响，但是影响学习过程的速度和质量。模型超参数的一个例子是神经网络的拓扑和大小。

> **超参数调整的重要性是什么？**超参数至关重要，因为它们控制着机器学习模型的整体行为。最终目标是找到超参数的最佳组合，使预定义的损失函数最小化，以给出更好的结果。
> 
> 不这样做将给出次优的结果，因为模型不收敛并且不能有效地最小化损失函数。
> 
> 这就像探索一系列的可能性，并试图找到给你最好结果的最佳组合。
> 
> — [李杏儿](https://towardsdatascience.com/why-you-should-do-feature-engineering-first-hyperparameter-tuning-second-as-a-data-scientist-334be5eb276c#:~:text=What%20is%20the%20importance%20of%20hyperparameter%20tuning%3F,function%20to%20give%20better%20results.)

Hilde J.P. Weerts 和康奈尔大学的另外两人提交了一份[**研究**](https://arxiv.org/abs/2007.07588) 以确定调整超参数是否重要，或者是否可以安全地将其设置为默认值。但是一般来说，调整超参数的原因是为了达到模型的最高性能。

[ArgParse](https://docs.python.org/3/howto/argparse.html#id1) 是“Python 标准库中推荐的命令行解析模块”。该模块使得编写用户友好的命令行界面变得容易。有时候，在机器学习中，你会经历多次实验，以便你可以理解分数和超参数之间的关系，并找到获得最佳性能模型或算法的方法。从命令行开始新的试验并在 CLI 中指定参数值是有意义的。

下面是一个简单的 Python 程序，展示了如何使用 argparse。

```
**import** argparse

argparser = argparse.ArgumentParser(description='Process hyper-parameters')

argparser.add_argument('--tr',       type=float, default=0.41, help='training rate')
argparser.add_argument('--fallout',  type=float, default=0.01,   help='fallout mean')
argparser.add_argument('--data', type=str,   default='/this/is/a/test/data/', help='data directory for training')

args = argparser.parse_args()

*# then you can access passed values*
print(args.tr)
print(args.fallout)
print(args.data)
```

然后就可以运行代码了。如果不带任何参数运行它，将使用默认值..

```
python main.py
```

那么您应该期待输出:

```
0.41
0.01
/thi/**is**/a/test/data/
```

您也可以使用参数运行代码。将解析您指定的参数，以便您可以在培训脚本中使用它们:

```
python main.py --tr 0.0213 --fallout 0.5
```

然后您会得到输出:

```
0.0213
0.5
/thi/**is**/a/test/data/
```

Argparse 是一种跟踪机器学习超参数的好方法，但是它有一些缺点。如果您的项目快速增长，您会发现很难维护 CLI 参数。这是因为 argparse 不保存或记录命令行中传递的参数，所以您必须自己保存参数值。它还需要额外的努力来跟踪长期基于实验的项目中超参数的值。

使用 ArgParse，您可以轻松地添加新的参数，方便地开始新的试验，还可以随时决定超参数的值。

在机器学习中，还有其他几种方法来跟踪超参数。您还可以尝试其他的:Click、AttrDict、Hydra 和其他一些。

干杯！