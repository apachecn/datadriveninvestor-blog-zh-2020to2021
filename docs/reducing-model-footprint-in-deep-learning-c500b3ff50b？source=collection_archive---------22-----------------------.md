# 去膨胀你的神经网络

> 原文：<https://medium.datadriveninvestor.com/reducing-model-footprint-in-deep-learning-c500b3ff50b?source=collection_archive---------22----------------------->

![](img/c146134339bcb680a7a06cae77f7ff56.png)

[https://thumbs.dreamstime.com/b/cutting-grass-pair-scissors-16225110.jpg](https://thumbs.dreamstime.com/b/cutting-grass-pair-scissors-16225110.jpg)

修剪是我很久以来一直感兴趣的事情，但不知何故，我从来没有实现它。我对它感兴趣有很多原因。主要是能够减少我的模型的大小、成本和计算需求，同时保持准确性(至少是某种程度上)。

TL；通常，这是通过以某种形式或方式删除参数来实现的。

如果需要，我们可以通过将网络的某些部分设置为 0 或删除它们来删除它们，而不是使用掩码。(又名权重和偏差)

在大多数情况下，网络首先被训练一段时间。然后修剪。这降低了它的准确性，因此被再次训练(微调)。这个循环一直重复，直到我们得到我们需要的结果。

# 修剪方法的主要类型

这种方法有很多种，但它们是根据它们对最初想法的改变来分类的。请注意，最终，主要思想是相同的，只是如何做是不同的。

## 结构

*   关于结构选择，一些作者选择删减单个参数，产生稀疏网络(大量 0)。这对于高效存储来说可能不是很理想。
*   其他一些人考虑将某些参数分组并作为组删除它们的方法。这样更优化。

## 得分

*   像所有网络一样，当我们试图选择去掉哪个参数时，评分变得至关重要。
*   一些作者建议基于绝对值移除，其他人决定基于该参数对整个网络的贡献进行修剪。
*   其他人根据给定的分数删除。
*   有些在本地执行修剪，而有些则在整个网络中全局执行。

## 行程安排

*   一些一次修剪所有的重量
*   其他的使用循环或其他条件反复修剪

## 微调

*   一些在修剪之前存储权重，并使用它来继续训练。
*   其他人试图回到以前的状态，重新初始化整个网络

[](https://www.datadriveninvestor.com/2020/01/13/the-future-of-humanity-is-genetic-engineering-and-neural-implants/) [## 人类的未来是基因工程和神经移植|数据驱动投资者

### 领先的技术、音乐和电影节将于 2020 年 3 月 13 日至 22 日举行。它将以前沿的谈话为特色…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/01/13/the-future-of-humanity-is-genetic-engineering-and-neural-implants/) 

# 修剪试探法+代码

从上一个主题扩展这个并尝试编码一点。(这些都在朱莉娅·朗)

**注意**这些代码是理解主要思想的玩具示例。正确的代码请参考我的知识库。[链接](https://github.com/SubhadityaMukherjee/pytorchTutorialRepo/tree/master/Pruning)

让我们在嵌套数组中获取一些随机值。在所有情况下，假设这些是网络的权重。比方说，每个子阵列代表网络的一层。

```
weights = [rand(10) for _ in 1:10]
```

我们还考虑要丢弃的值的百分比/数量作为输入。

## 全球震级

*   取整个网络中的最低值。扔掉它们。

好的，我们首先展平嵌套数组。然后我们可以很容易地找到 n 个最小值，因为现在它是一个长数组。我们可以写一个小函数来识别值是否大于值，否则返回 0 或原始值。

```
function setval(val, cmpval, setter)
    if val<cmpval
        return setter
    else
        return val
    end
end
```

然后我们可以对这个扁平列表进行排序。之后，我们运行一个基于元素的 map 函数(在每一层上)并将每个元素传递给我们之前的函数。如果当前值小于我们选择的值，这将允许我们将所有必需的元素设置为 0(或我们自己的值)。这将有效地降低价值。

```
"""
weights = array
n = lowest nth smallest value to prune below ( aka take the nth smallest value and prune below it ) (eg: 3)
"""
function global_mag_prune(weights, n = 3, setter = 0)
    temp = collect(Iterators.flatten(weights))
    sort!(temp)
    map.( x-> setval(x,temp[n], setter) ,  weights  )

end
```

我们还编写了一个函数来确定网络变得有多稀疏。(又名多少个零)。

```
return temp2, sum(x->x==0, collect(Iterators.flatten(temp2)) , dims=1)/(size(temp)[1]*size(temp)[1])*100
```

## 分层星等

*   取网络中每层的最低值并进行修剪。

修改全局层的方式，并将其应用于每个层。为此，我们首先复制重量。然后，对于数组中的每一层，我们找到最少的 n 个值，取第 n 个值，并将所有其他值设置为 0。作为边缘情况，如果输入的元素数量大于层的总长度，则整个层被设置为 0。

```
"""
weights = array
n = lowest nth smallest value to prune below ( aka take the nth smallest value and prune below it ) (eg: 3)
"""
function layer_mag_prune(weights, n = 3, setter = 0)
    backup = deepcopy(weights)
    for layer in 1:length(weights)
        sort!(backup[layer])
        if n>length(weights[layer])
            n = length(weights[layer])
        end
        backup[layer] = map.( x-> setval(x,weights[layer][n], setter) ,  weights[layer]  )
    end
    return backup, sum(x->x==0, collect(Iterators.flatten(backup)) , dims=1)/(size(weights)[1]*size(weights)[1])*100        
end
```

## 全球梯度幅度

*   识别整个网络中的最低绝对值(权重*梯度)并移除它们

为此，我们需要计算到目前为止权重的梯度。好吧，我可以用一个随机数组来证明这个概念。所以我们基本上采用之前的代码，将初始部分改为权重和梯度的乘积。

```
function global_grad_prune(weights, n = 3, setter = 0)
    temp = weights*rand(size(weights))
    temp = collect(Iterators.flatten(weights))
    sort!(temp)
    temp2 = map.( x-> setval(x,temp[n], setter) ,  weights  )
    return temp2, sum(x->x==0, collect(Iterators.flatten(temp2)) , dims=1)/(size(temp)[1]*size(temp)[1])*100
end
```

## 层状梯度大小

*   最低的绝对值每层，并删除他们类似的，我们再次修改这一点，以适应我们的需要

```
"""
weights = array
n = lowest nth smallest value to prune below ( aka take the nth smallest value and prune below it ) (eg: 3)
"""
function layer_grad_prune(weightsnew, n = 3, setter = 0)
    weights = deepcopy(weightsnew)*rand(size(weightsnew))
    backup = deepcopy(weights)
    for layer in 1:length(weights)
        sort!(backup[layer])
        if n>length(weights[layer])
            n = length(weights[layer])
        end
        backup[layer] = map.( x-> setval(x,weights[layer][n], setter) ,  weights[layer]  )
    end

    return backup, sum(x->x==0, collect(Iterators.flatten(backup)) , dims=1)/(size(weights)[1]*size(weights)[1])*100

end
```

## 随意

*   每个权重被独立考虑，并以所需网络的一部分被丢弃

为此，我们首先通过确定权重的总大小来确定要删除的值的数量，然后将其乘以要删除的值的分数。然后，我们展平数组，将不需要的值设置为 0，然后重新成形为原始形状。

```
"""
frac = percentage of values to remove
"""
function random_prune(weights, frac = .3, setter = 0)
    num_prune = Int(round(frac*(size(weights)[1]*size(weights)[1])))
    @info num_prune
    backup = collect(Iterators.flatten(deepcopy(weights)))
    backup[rand(1:length(backup), num_prune)] .= 0
    @info size(weights)
    return reshape(backup, size(weights))
end
```

# 我们能从论文中学到什么(感谢 Blalock 等人)

*   修剪方法不能由单个数据集决定，而必须使用标准化测试对各种数据集进行测试来决定
*   如果需要少量压缩，在某些情况下，修剪实际上可能会提高我们的准确性
*   随机修剪可能并不总是最好的选择
*   全局修剪更好
*   根据图层类型分配不同的修剪百分比会有所帮助
*   稀疏模型通常优于密集模型
*   修剪后的模型有时可以获得比初始架构更高的精度
*   对于一开始就很差的架构更有效
*   也许能够改善时间/空间与精确度的权衡

# 太棒了，但是…

*   有时你会选择一个更好、更高效的架构
*   这完全取决于你的目标是什么

# ~完成

我们的修剪之旅到此结束。

如果你喜欢你所读的，请随时订阅/问我以下任何问题。

> 注意，本文大部分内容基于 Davis Blalock 等人的一篇优秀论文[神经网络修剪的状态是什么？](https://arxiv.org/pdf/2003.03033.pdf)

【引用】:Blalock，d .，Ortiz，J. J. G .，Frankle，j .，& Guttag，J. (2020)。神经网络剪枝是什么状态？。arXiv 预印本:2003.03033。

## 获得专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)