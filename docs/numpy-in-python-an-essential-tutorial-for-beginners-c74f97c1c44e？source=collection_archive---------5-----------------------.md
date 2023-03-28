# Python 中的 NumPy:初学者必备教程

> 原文：<https://medium.datadriveninvestor.com/numpy-in-python-an-essential-tutorial-for-beginners-c74f97c1c44e?source=collection_archive---------5----------------------->

![](img/4fff1978ba74899ae90fd564c22fe7f6.png)

Photo by [Kelly Sikkema](https://unsplash.com/@kellysikkema?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

Python 在机器学习和人工智能中被广泛使用的主要原因之一是它有很多库可供选择。这些库为数据科学家和开发人员提供了基础，他们不必从头开始编写项目代码，事实上，他们可以更专注于复杂的算法和大型数据集。

一个这样的库是“ **NumPy** ”库。它是数值 Python 的缩写，是使用 Python 进行科学计算的基础包。与 python 标准库相比，NumPy 保证了很高的执行速度。它带有大量的内置功能。它提供了一个高性能的多维数组对象和工具来处理这些数组。这些数组称为 NumPy 数组。

在本文中，我将向您展示一些使用 NumPy 数组的方法。

# 什么是 NumPy 数组？

NumPy 数组是数字数据值(整数或浮点数)的多维矩阵。NumPy 数组只允许数字数据值。NumPy 数组不同于 Python 中允许任意数据类型的列表。它甚至比只关注数字数据值更具限制性。它还必须是**同类**数据值。这意味着 NumPy 数组包含整数值或浮点值，但不能同时包含两者。

# NumPy 的安装

要开始使用 NumPy 数组，我们必须首先安装 NumPy 包，因为默认情况下，它不包含在基本 Python 中。使用 pip 在命令提示符下安装 NumPy 包。

```
pip install numpy
```

要开始，我们必须首先导入 NumPy 库，以便开始在我们的程序中使用。

```
import numpy as np
```

这条语句将把 NumPy 包中所有可用的模块和函数加载到内存中，我们开始使用它们。这里，我们给 NumPy 一个缩写名“np”，使我们的代码更容易阅读和使用。每次我们使用' NumPy.function '时，我们可以写' np.function '

# 入门指南

让我们开始使用 NumPy 数组。

NumPy Arrays 是一个元素(通常是数字)表，所有元素都是相同的类型，由一个非负整数元组索引。在 NumPy 中，尺寸被称为*轴*。

例如，3D 空间[1，2，1]中的点的坐标有一个轴。这个轴有 3 个元素，所以我们说它的长度是 3。在下面的示例中，阵列有 2 个轴。第一个轴的长度为 2，第二个轴的长度为 3。

```
[[1 , 0 , 2],
 [3 , 2 , 1]]
```

NumPy 的数组类叫做 *ndarray* 。它也被称为别名数组。

**创建 NumPy 数组的不同方式:**

创建一维数组

```
import numpy as np
nump_arr = np.array([1,2,3])
```

这将从现有的 python 数组创建一个一维数组:

```
import numpy as np
py_arr = [1,2,3]
nump_arr = np.array(py_arr)
```

创建 2D 阵列:

```
import numpy as np
nump_arr = np.array([[1,2,3,4,5],
                    [6,7,8,9,10]])
```

在 NumPy 中创建数组的另一种方法是使用 0、1 或空函数:

```
arr_zeros = np.zeros(3)
print(arr_zeros)

arr_ones = np.ones((3,2))
print(arr_ones)

arr_empty = np.empty(5)
print(arr_empty)

arr_full = np.full((2,3),4)
print(arr_full)
```

函数**0**创建一个充满 0 的数组，函数**1**创建一个充满 1 的数组，函数**空**创建一个数组，其初始内容是随机的，并取决于内存的状态。默认情况下，创建的数组的 dtype 是 float64。函数 full 会创建一个 2 * 3 的数组，里面全是 4。

```
Output:
[0\. 0\. 0.]
[[1\. 1.]
 [1\. 1.]
 [1\. 1.]]
[0\.   0.25 0.5  0.75 1\.  ]
[[4 4 4]
 [4 4 4]]
```

另一个很酷的功能是能够创建不同的阵列，如随机阵列:

```
np.random.rand(2,3)
```

它将创建一个介于 0 和 1 之间的 2 * 3 随机数数组

```
array([[0.32482924, 0.51608091, 0.21548059],
       [0.6142247 , 0.2120958 , 0.39264305]])
```

在…期间

```
np.random.rand(2,3)* 100
```

将创建 0 到 100 之间的随机数的 2 * 3 数组。

```
Output:
array([[94.20171774, 19.99361621, 90.99119916],
       [60.80955174, 48.8203693 , 84.60342955]])
```

您也可以用不同的方式定义数组的大小:

```
np.random.randint(10,size=(2,3))
```

它创建一个大小为 2 * 3 的数组，数组中的随机数在 0 到 9 之间，这里的 10 不包括在内。

```
Output:
array([[5, 3, 3],
       [5, 5, 5]])
```

为了创建数字序列，NumPy 提供了 **arange** 函数，它类似于 Python 内置的 **range** ，但是返回一个数组。

```
np.arange(0,200,10)
Output:
array([  0,  10,  20,  30,  40,  50,  60,  70,  80,  90, 100, 110, 120,
       130, 140, 150, 160, 170, 180, 190])
```

该函数将返回一个一维数组，其值介于 0 和 200 之间，中间相隔 10 个数字。这里再次需要注意的是，200 并不包含在内。

有一个函数 **linspace** 如果您想指定返回的元素数量，而不是像 **arange、**那样指定步骤，那么由于有限的浮点精度，几乎不可能预测使用浮点参数时获得的元素数量。

```
np.linspace(0,2,9)
Output:
array([0\.  , 0.25, 0.5 , 0.75, 1\.  , 1.25, 1.5 , 1.75, 2\.  ])
```

# 检查阵列

ndarray 对象更重要的属性是:

**ndarray.ndim:** 数组的轴数(维度)。

**ndarray.shape:** 数组的维度。这是一个整数元组，表示每个维度中数组的大小。对于一个有 *n* 行和 *m* 列的矩阵，形状将是(n，m)。因此，形状元组的长度是轴的数量 ndim。

**ndarray.size:** 数组的元素总数。这等于形状元素的乘积。

**ndarray.dtype:** 描述数组中元素类型的对象。可以使用标准 Python 类型创建或指定 dtype。此外，NumPy 提供了自己的类型。numpy.int32、numpy.int16 和 numpy.float64 就是一些例子。

**ndarray.itemsize:** 数组中每个元素的字节大小。例如，float64 类型的元素数组的 itemsize 为 8 (=64/8)，而 complex32 类型的元素数组的 itemsize 为 4 (=32/8)。它等效于 ndarray.dtype.itemsize。

**ndarray.data:** 包含数组实际元素的缓冲区。通常，我们不需要使用这个属性，因为我们将使用索引工具访问数组中的元素。

现在您已经创建并加载了数组，您可以通过上述属性检查它的大小、形状和数据类型。

```
import numpy as np
a = np.arange(15).reshape(3, 5) 
a 
*Output*:
array([[ 0,  1,  2,  3,  4],        [ 5,  6,  7,  8,  9],        [10, 11, 12, 13, 14]]) 

**a.shape** 
*Output*:
(3, 5)

**a.ndim** *Output:*
2

**a.dtype.name** *Output:*
'int64'

**a.itemsize** *Output:*
8

**a.size** *Output:*
15 

**type(a)** *Output:*
<class 'numpy.ndarray'> 

b = np.array([6, 7, 8]) 
b 
*Output:*
array([6, 7, 8])

**type(b)** *Output:*
<class 'numpy.ndarray'> 

b = np.array([1.2, 3.5, 5.1])
**b.dtype** *Output:*
dtype('float64')
```

如果您需要转换数据类型，您可以使用 **array.astype(dtype ),如果**您需要将 NumPy 数组转换为 Python 列表，也有一个命令可以完成这个任务: **array.tolist()** 。

# 索引和切片

索引和切片 NumPy 数组的工作方式与处理 Python 列表非常相似:

```
array[0]
```

将返回第 0 个索引中的元素，并且

```
array[2,4]
```

将返回索引[2][4]中的元素。

您也可以选择前五个元素，例如，使用冒号(:)。

```
array[0:5]
```

将返回前五个元素(索引 0–4)和

```
array[0:5,4]
```

将返回 2D 数组中第 4 列的前 5 个元素。

你可以用

```
array[:2]
```

从开始直到索引 2(不包括索引 2)获取元素，或者

```
array[2:]
```

从第二个索引返回，直到数组结束。

```
array[:,1]
```

将返回所有行中索引 1 处的元素，同样是在 2D 数组中。

因此，逗号前的索引指的是行，而逗号后的索引指的是列。:用于切片；在本例中，它告诉 Python 包含所有行。

索引和切片的更多示例:

```
**import** numpy **as** np
​**def** f(x,y):
 **return** 10*****x**+**y
​
b **=** np.fromfunction(f,(5,4),dtype**=**int)
b
Output:
array([[ 0,  1,  2,  3],
       [10, 11, 12, 13],
       [20, 21, 22, 23],
       [30, 31, 32, 33],
       [40, 41, 42, 43]])
b[2,3]
Output:
23
b[0:5, 1]                   # each row in the second column of b
Output:
array([ 1, 11, 21, 31, 41])
b[ : ,1]                    # equivalent to the previous example
Output:
array([ 1, 11, 21, 31, 41])
b[1:3, : ]                  # each column in the 2nd and 3rd row of b
Output:
array([[10, 11, 12, 13],
       [20, 21, 22, 23]])
```

# 成型和分类

为了对 NumPy 数组进行排序，我们使用 Array.sort(array，axis，kind，orderby)函数。

示例:

```
np.sort(array1,axis = 1, kind = 'mergesort') # sort the array along axis 1
```

更多示例:

```
import numpy as np
a = np.array([[1,9,3],
              [8,5,6],
              [3,4,2],
              [4,3,7]])                 # Creates 2D Array
np_sorted = a[:,a[1].argsort()]         # Sorts by second row
print(np_sorted)
Output:
[[9 3 1]
 [5 6 8]
 [4 2 3]
 [3 7 4]]
```

整形中使用的一些函数有:

```
a.flatten() or a.ravel()
```

它会将二维数组展平为一维数组。这里，flatten()将返回数组的副本，而 ravel()将返回原始数组的视图。如果你修改了 ravel()返回的数组，它可能会修改原始数组中的条目，但是如果你修改了 flatten()返回的数组中的条目，这种情况永远不会发生。因为没有复制内存，所以 ravel()通常会更快，但是在修改它返回的数组时必须更加小心。

要将数组重新调整为新的维度，可以使用

```
array.reshape(x,y)
```

它会把你的数组调整到你用 x 和 y 设置的大小。

示例:

```
import numpy as np
a =  np.arange(1001,1241,10).reshape(6,4)
a
Output:
array([[1001, 1011, 1021, 1031],
       [1041, 1051, 1061, 1071],
       [1081, 1091, 1101, 1111],
       [1121, 1131, 1141, 1151],
       [1161, 1171, 1181, 1191],
       [1201, 1211, 1221, 1231]])
```

它将使用 6 * 4 的值(介于 1001 和 1241 之间，相差 10)对数组进行整形。

# 连接和分割

您可以使用 **np.concatenate((array1，array2)，axis=0)** 来组合两个 NumPy 数组—这将把数组 2 作为行添加到数组 1 的末尾，而 **np.concatenate((array1，array 2)，axis=1)** 将把数组 2 作为列添加到数组 1 的末尾。np.split(array，2)会将数组拆分成两个子数组，而**NP . hs split(array，5)** 会在*第 5 个*索引处水平拆分数组。

# 添加和删除元素

当然，有一些命令可以在 NumPy 数组中添加和删除元素:

*   **np.append(array，values)** 将值追加到数组的末尾。
*   **np.insert(array，4，values)** 将在索引 4 之前向数组中插入值
*   **np.delete(array，3，axis=0)** 将删除数组索引 3 上的行
*   **np.delete(array，6，axis=1)** 将删除数组索引 6 上的列

# NumPy 数组的基本算法

基本数学函数对数组进行元素运算，既可以作为运算符重载，也可以作为 NumPy 模块中的函数:

```
import numpy as np
nump_arr = np.array([[1,2,3,4,5],
                    [6,7,8,9,10]])
nump_md_arr = np.array([[2,1,4,3,2],[2,3,4,2,2]])
nump_mul = nump_arr * 2
nump_mul
*Output:* array([[ 2,  4,  6,  8, 10],
       [12, 14, 16, 18, 20]])

nump_add_new = nump_arr + nump_md_arr
nump_add_new
*Output:*
array([[ 3,  3,  7,  7,  7],
       [ 8, 10, 12, 11, 12]])

nump_sub_arr = nump_mul - nump_md_arr
*Output:*
array([[ 0,  3,  2,  5,  8],
       [10, 11, 12, 16, 18]])
```

Numpy 中的基本运算**功能**:

**np.add(array，1)** 将把数组中的每个元素加 1， **np.add(array1，array2)** 将把数组 2 加到数组 1。对于 **np.subtract()、np.multiply()、np.divide()** 和 **np.power()** 也是如此——所有这些命令的工作方式都与上面描述的完全相同。您还可以让 NumPy 从数组中返回不同的值，比如:

*   **np.sqrt(array)** 将返回数组中每个元素的平方根
*   **np.sin(array)** 将返回数组中每个元素的正弦值
*   **np.log(array)** 将返回数组中每个元素的自然对数
*   **np.abs(arr)** 将返回数组中每个元素的绝对值
*   如果数组具有相同的元素和形状，np.array_equal(arr1，arr2) 将返回 True

可以对数组中的不同值进行舍入: **np.ceil(array)** 会向上舍入到最接近的整数， **np.floor(array)** 会向下舍入到最接近的整数， **np.round(array)** 会向下舍入到最接近的整数。

您可以使用 NumPy 方法获取 NumPy 数组的描述性统计信息:

*   **np.mean(array，axis=0)** 将返回沿特定轴(0 或 1)的平均值
*   **array.sum()** 将返回数组的总和
*   **array.min()** 将返回数组的最小值
*   **array.max(axis=0)** 将返回特定轴的最大值
*   **np.var(array)** 将返回数组的方差
*   **np.std(array，axis=1)** 将返回特定轴的标准偏差
*   **array.corrcoef()** 将返回数组的相关系数
*   **numpy.median(array)** 将返回数组元素的中值

而这只是冰山一角。这些只是我试图在这里列出的一些特性和功能。NumPy 绝对是一个值得初露头角的 Python 程序员/学习者探索的库；像我:-)。它非常受欢迎，被认为是可以使用的关键 Python 库之一。

*原载于 2020 年 10 月 24 日*[*【https://www.numpyninja.com】*](https://www.numpyninja.com/post/numpy-package-in-python-a-tutorial-for-beginners)*。*