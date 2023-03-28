# 如何在 jupyter 实验室中逐步添加 conda 环境

> 原文：<https://medium.datadriveninvestor.com/how-to-add-conda-environment-to-jupyter-lab-step-by-step-431cd2c47708?source=collection_archive---------0----------------------->

## ✍Tips 和 Python 中的技巧

![](img/bdde413df3d06c49690fb3078eb30bb8.png)

Photo by [Dave Gandy](http://skuawk.com/) under the [Public Domain Dedication License](https://creativecommons.org/licenses/publicdomain/)

**警告** : *这里没有神奇的配方或圣杯，尽管一个新的世界可能会为你打开大门。*

# 📈Python for finance 系列

1.  [识别异常值](https://medium.com/me/stats/post/c0a31d9faefa?source=main_stats_page)
2.  [识别异常值—第二部分](https://medium.com/me/stats/post/4c00b2523362?source=main_stats_page)
3.  [识别异常值—第三部分](https://medium.com/me/stats/post/257b09f5940b?source=main_stats_page)
4.  [程式化的事实](https://towardsdatascience.com/data-whispering-eebb77a422da)
5.  [特征工程&特征选择](https://medium.com/@kegui/feature-engineering-feature-selection-8c1d57af18d2)
6.  [数据转换](https://towardsdatascience.com/data-transformation-e7b3b4268151)
7.  [微小差异特征](https://medium.com/swlh/fractionally-differentiated-features-9c1947ed2b55)

20200720 更新:

若要移除包络:

```
conda env remove --name yourenv
```

也没有必要

```
(tf-gpu)$ conda deactivate
```

在打开朱庇特实验室之前。

原故事:

打开 anaconda 提示符，创建一个新的 env，比如 tf-gpu

```
conda create -n tf-gpu
```

然后激活新的 env:

```
$ conda activate tf-gpu 
```

然后安装 ipykernel

```
(tf-gpu)$ conda install ipykernel 
```

之后，安装一个新的内核，比如 tf-gpu-2:

```
(tf-gpu)$ ipython kernel install --user --name=tf-gpu-2 
```

然后，停用环境:

```
(tf-gpu)$ conda deactivate
```

去 jupyter 实验室:

```
(base)$ jupyter lab
```

在启动屏幕下，选择 kernel: tf-gpu-2。

要删除内核，请执行以下操作:

运行`jupyter kernelspec list`获得所有内核的路径。然后简单地卸载你不想要的内核

```
jupyter kernelspec uninstall unwanted-kernel
```

点击订阅英特尔。

在这里加入我们的网络:[https://datadriveninvestor.com/collaborate](https://datadriveninvestor.com/collaborate)