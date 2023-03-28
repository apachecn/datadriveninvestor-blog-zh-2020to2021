# 如何在 Python 中使对象不可变

> 原文：<https://medium.datadriveninvestor.com/immutability-in-python-d57a3b23f336?source=collection_archive---------0----------------------->

![](img/8a50f8bf01eb5b25c1a9f22536e86510.png)

Sands of change? Or immutability?

*变化之沙* 就在我们身边。。。或者他们是？让我们研究一下 Python 中的**不变性**。

[](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) [## 2019 年最值得学习的编码语言|数据驱动的投资者

### 在我读大学的那几年，我跳过了很多次夜游去学习 Java，希望有一天它能帮助我在…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) 

你听说过 Python 中的一些对象类是**不可变的**，比如`string`、`tuple`和`int`。但是，如果您希望自己的类是不可变的呢？你找对地方了！

假设我有一个程序，在数据库中记录汽车。一旦汽车生产出来，我不希望汽车的属性有任何改变。一辆*斯巴鲁 Crosstrek* 不可能一夜之间变成*特斯拉 Model X* ，现在可以了吧(可惜)？让我们看看如何实现这一点。

# 方法 1:__ 槽 _ _

![](img/4f2d1a89cdf01709674ed45357979f2c.png)

Not that kind of slots!

您可能听说过 Python 对象的`__slots__`属性。这精确地指定了对象可能包含的属性列表。它还具有一些性能优势。下面是它的用法示例:

```
class Car:
    '''Contains information about a car such as make, model, etc.
    '''
    __slots__ = ['make', 'model', 'year', 'color'] def __init__(self, make, model, year, color):
        self.make = make
        self.model = model
        self.year = year
        self.color = color
```

现在，你可以看到没有办法添加新的属性！

```
car = Car('Subaru', 'Crosstrek', '2018', 'Blue')print(car.make)
# output: 'Subaru'print(car.year)
# output: '2018'# --> try to set a new attribute, I dare you!
car.all_wheel_drive = True
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
<ipython-input-216-f3fe1ffbcb21> in <module>
----> 1 car.all_wheel_drive = TrueAttributeError: 'Car' object has no attribute 'all_wheel_drive'
```

然而，你可能已经注意到了这里的一些东西。。。该对象不是不可变的。**您仍然可以更改** `__slots__` **中设置的所有值！！**

```
car = Car('Subaru', 'Crosstrek', '2018', 'Blue')print(car.make)
# output: 'Subaru'# change existent value
car.make = 'Ferrari'print(car.make)
# output: 'Ferrari'
```

啊哦。让我们试试另一种方法，好吗？

# 方法 2:“冷冻机”的子类

![](img/37c463eeeb082a1f098709d683e80b1e.png)

Not that kind of frozen!

在这种方法中，我创建了一个名为`Freezer`的父类。你要做的就是从`Freezer`开始子类化。

在 Python 初始化之后，我通过覆盖对象上的`__delattr__`和`__setattr__`方法来“冻结”对象。我设置了`_frozen = True`,表示实例现在已经“冻结”了。

```
class Freezer:
    '''Freeze any class, such that instantiated
    objects become immutable.
    '''
    _frozen = False def __init__(self):
        self._frozen = True def __delattr__(self, *args, **kwargs):
        if self._frozen:
            raise AttributeError('This object is frozen!')
        object.__delattr__(self, *args, **kwargs) def __setattr__(self, *args, **kwargs):
        if self._frozen:
            raise AttributeError('This object is frozen!')
        object.__setattr__(self, *args, **kwargs)
```

这是我重新定义的`FreezerCar`类，它是`Freezer`的子类。

```
class FreezerCar(Freezer):
    '''Contains information about a car such as make, model, etc.
    '''
    def __init__(self, make, model, year, color):
        self.make = make
        self.model = model
        self.year = year
        self.color = color # initialize parent class "Freezer"
        super().__init__()
```

现在，让我们确保这个工作！

```
freezer_car = FreezerCar('Subaru', 'Crosstrek', '2018', 'Blue')print(freezer_car.make)
# output: 'Subaru'print(freezer_car.year)
# output: '2018'# --> try to set a new attribute, I dare you!
freezer_car.all_wheel_drive = True# you'll get an ERROR: AttributeError: This object is frozen!# --> try to change an existent attribute, I dare you!
freezer_car.make = 'Ferrari'# you'll get an ERROR: AttributeError: This object is frozen!
```

现在**这就是**我说的！

# 方法 3:为什么不两者都用？

![](img/51e37a4aa9690450d989f6850ccff598.png)

Not that kind of combine!

“方法 2”对于不变性是足够的。然而，如果我们同时使用`__slots__`和`Freezer`实现会怎么样呢？如果我们结合我们的方法呢？嗯。。。只有一个办法可以知道！让我们来调查一下:

```
class SlotsFreezer:
    '''Freeze any class such that instantiated
    objects become immutable. Also use __slots__ for speed.
    '''
    __slots__ = []
    _frozen = False def __init__(self):
        # generate __slots__ list dynamically
        for attr_name in dir(self):
            self.__slots__.append(attr_name) self._frozen = True def __delattr__(self, *args, **kwargs):
        if self._frozen:
            raise AttributeError('This object is frozen!')
        object.__delattr__(self, *args, **kwargs) def __setattr__(self, *args, **kwargs):
        if self._frozen:
            raise AttributeError('This object is frozen!')
        object.__setattr__(self, *args, **kwargs)
```

这里是重新定义的`SlotsFreezerCar`类，它是`SlotsFreezer`的子类

```
class SlotsFreezerCar(SlotsFreezer):
    '''Contains information about a car such as make, model, etc.
    '''
    def __init__(self, make, model, year, color):
        self.make = make
        self.model = model
        self.year = year
        self.color = color # initialize parent class "SlotsFreezer"
        super().__init__()
```

以下是时间表！注意:为了比较，我包含了一个基本的 car 类实现，没有插槽。

```
# SETUP
class NormalCar:
    def __init__(self, make, model, year, color):
        self.make = make
        self.model = model
        self.year = year
        self.color = colorslots_freezer_car = SlotsFreezerCar('Subaru', 'Crosstrek', '2018', 'Blue')freezer_car = SlotsFreezerCar('Subaru', 'Crosstrek', '2018', 'Blue')car = SlotsFreezerCar('Subaru', 'Crosstrek', '2018', 'Blue')normal_car = NormalCar('Subaru', 'Crosstrek', '2018', 'Blue')# TIMING%timeit getattr(freezer_car, 'make')# 106 ns ± 0.457 ns per loop (mean ± std. dev. of 7 runs, 10000000 loops each)%timeit getattr(slots_freezer_car, 'make')# 106 ns ± 0.706 ns per loop (mean ± std. dev. of 7 runs, 10000000 loops each)%timeit getattr(car, 'make')# 106 ns ± 2.66 ns per loop (mean ± std. dev. of 7 runs, 10000000 loops each)%timeit getattr(normal_car, 'make') # WINNER !!!!# 97 ns ± 0.321 ns per loop (mean ± std. dev. of 7 runs, 10000000 loops each)
```

韦尔普，这很有趣。**我猜在 Python 中聪明并不总是有回报的！** *有时候简单其实更好。:)*

对此有一些警告，它们是:

1.  Python 的`dict`有其他方法`__delitem__`和`__setitem__`用来改变对象。如果您从`dict`继承并且需要不变性，那么对于这两个方法，请遵循上面的模式
2.  更复杂的类在性能方面可能有不同的行为。请记住，更复杂的实现可能对您的情况有所帮助。
3.  不变性可能会在以后伤害你，尤其是在复杂的类层次结构中。Python 作者没有包含内置的`make_immutable`函数是有原因的。:)

你走之前还有一件事。以下是一些有用的链接:

*   [Python 中难以置信的快速随机采样](https://medium.com/ibm-watson/incredibly-fast-random-sampling-in-python-baf154bd836a)
*   [用沃森机器学习训练机器学习模型](https://www.ibm.com/cloud/machine-learning)
*   [使用沃森自然语言理解从文本中提取见解](https://www.ibm.com/watson/services/natural-language-understanding/)
*   [了解如何成为 NLP 专家](https://blog.goodaudience.com/https-medium-com-ethankoch-how-to-become-an-nlp-expert-81cb94989612)