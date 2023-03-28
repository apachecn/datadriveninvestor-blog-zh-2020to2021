# 在 Matplotlib 中创建具有自定义 Bin 大小的离散颜色条

> 原文：<https://medium.datadriveninvestor.com/creating-a-discrete-colorbar-with-custom-bin-sizes-in-matplotlib-50b0daf8dd46?source=collection_archive---------7----------------------->

如何在 matplotlib 中创建完全定制的颜色映射。

![](img/98609767ce14279e993acfc26b343371.png)

Photo by [David Pisnoy](https://unsplash.com/@davidpisnoy?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 问题

我们的数据被分成不一致的类别，线性颜色条将是低效的。在本教程中，我们将介绍如何创建一个自定义的颜色图，颜色与我们选择的尺寸相匹配。

# 解决方案:离散色条

我们从导入所需的包开始

```
import matplotlib as mpl
import matplotlib.pyplot as plt
import numpy as np
```

接下来，我们决定我们的颜色:

```
colours = ['#ffbe0b', '#fb5607', '#ff006e', '#8338ec', '#3a86ff']
```

以及对应于它们的容器大小。—例如{0 → .3}、{0.3 → .7 }等。我有意选择了不均匀的面元。

```
bins = [0 , 0.3 , 0.7 , 1.75 , 1.9]
```

## 设置映射

已经决定了我们的颜色和箱，我们现在可以生成我们的 cmap

```
assert len(bins)== len(colours)
cmap = mpl.colors.ListedColormap(colours)
norm = mpl.colors.BoundaryNorm(boundaries=bins, ncolors=len(cmap.colors)-1 )
```

## 创建颜色条

为了测试我们的产品系列，我们可以画出相应的颜色条

```
fig, ax = plt.subplots(figsize=(6, 1))
fig.subplots_adjust(bottom=0.5)cb2 = mpl.colorbar.ColorbarBase(ax, cmap=cmap,
                                norm=norm,
                                boundaries= [-.1] + bins + [2.1],
                                extend='both',
                                ticks=bins,
                                spacing='proportional',
                                orientation='horizontal')
cb2.set_label('Custom colour bar')
plt.show()
```

![](img/7f6d4b32f1bef3495fe8c064642296de.png)

# 最后，将其应用于一些样本数据

我们首先生成一个样本数据集:

```
x = np.linspace(0,2.5,100)
y = [np.random.random()*2 for i in range(100)]
```

## 彩色散点图

然后在我们的情节中，我们需要提供我们之前生成的`norm`和`cmap`。此外，我们需要分配用于给我们的点着色的变量，在这种情况下，它将是 x 距离，以便它与上面的颜色条匹配。尺寸是随机选择的，随高度而减小。

```
size = 2 + (1.2-np.array(y))*2plt.scatter(x,y,c=x,cmap=cmap,norm = norm, s=2 + (1.2-y)*2)plt.show()
```

![](img/d78efa455d7bcef2e310f934d90ce618.png)

我们到了。—如果你觉得这有用，请鼓掌。