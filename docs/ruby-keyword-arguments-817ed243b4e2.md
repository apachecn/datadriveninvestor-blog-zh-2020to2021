# Ruby 关键字参数

> 原文：<https://medium.datadriveninvestor.com/ruby-keyword-arguments-817ed243b4e2?source=collection_archive---------5----------------------->

## Ruby 方法:位置参数与关键字参数

在用 Ruby 编写方法时，我们经常使用位置参数，位置参数是指调用方法时传递参数的顺序必须与方法定义中设置参数的顺序相匹配。例如:

Example of working positional arguments in Ruby

换句话说:`subtotal`、`tax`和`senior_discount`在方法定义和方法调用中的顺序应该相同。如果我们在方法调用中传递参数的顺序与方法定义中的参数顺序不匹配，我们将得到以下错误:

Example of positional arguments failing in Ruby

呀！这个方法只有三个参数，但是如果我们有更多的参数呢？跟踪订单会变得很困难。幸运的是，Ruby 2.0 和更高版本给了我们一些非常有用的东西:关键字参数。

关键字参数是位置参数的替代方法，类似于哈希语法。对于关键字参数，我们传递参数的顺序完全没有关系！尽管我们的位置参数语法看起来像我们上面使用的例子，但是我们用于相同方法调用的关键字参数语法可以看起来像下面的任何一个(因为顺序无关紧要):

Example of keyword arguments in Ruby

换句话说:`subtotal:`、`tax:`和`senior_discount:`可以按照我们喜欢的任何顺序写在*的方法定义和方法调用中。我们直接在关键字后传递变量或值，瞧！*

*Ruby 社区的天才们通过消除参数依赖于顺序的需要，继续使我们的开发生活变得更加容易，这也将使我们未来的代码重构更加容易。例如，如果我们以后需要添加更多的参数，或者我们不小心移动了它们，我们可以这样做，而不用担心参数在所有现有或未来的方法调用中的传递顺序。尊重！*

## *附加信息和阅读*

*注意(在不太可能的情况下)你仍然使用带有关键字参数的 Ruby 2.0，你的参数*必须*有默认值。这个要求在 Ruby 2.1+中被否决了。最后，虽然可以在同一个方法中同时使用*和*位置参数和关键字参数，但是在即将到来的 Ruby 3.0 中，这一功能将被弃用，在撰写本文时，该版本将于 2020 年 12 月发布。你可以在这里阅读更多关于这个变化的信息[。](https://www.ruby-lang.org/en/news/2019/12/12/separation-of-positional-and-keyword-arguments-in-ruby-3-0/)*

*![](img/14949e0821ec482fd1fc8b75e967fe4e.png)*