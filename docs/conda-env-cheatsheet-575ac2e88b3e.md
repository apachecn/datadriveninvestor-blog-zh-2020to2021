# 康达环境备忘单

> 原文：<https://medium.datadriveninvestor.com/conda-env-cheatsheet-575ac2e88b3e?source=collection_archive---------12----------------------->

日常使用的快速入门 anaconda 环境备忘单。

![](img/f20d4b89b851353a3c9edd700480f37e.png)

Photo by [Lucas Benjamin](https://unsplash.com/@aznbokchoy?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 创造环境

我们选择创建一个名为`myenv`的环境

## 在 Conda 文件夹内

`conda create --name myenv`

## 自定义位置

自定义位置(例如，名为 myenv 的目录)

`conda create --prefix ./myenv python=3.7 --yes;`

## 克隆现有环境

`conda create --name myenv --clone env2clone`

# 激活/停用环境

## 列出所有环境

`conda info --envs`

## 激活一个环境

`conda activate myenv`

## 激活自定义定位环境

在位置`./myenv`激活环境

`conda activate ./myenv`

## 停用环境

`conda deactivate`

## 移除现有环境

`conda env remove --name myenv`

# 导出/导入环境

## 保存现有的环境依赖关系

```
conda env export > environment.yml
```

如果我们想避免版本号，我们可以使用以下命令:

```
conda env export | cut -f 1 -d '=' > environment.yml
```

## 从 YAML 文件创建新环境

```
conda env create -f environment.yml
```

## 使用 YAML 文件更新 conda 环境

```
conda env update --file environment.yml
```

# 结论

这就是你需要的大部分日常 conda env 命令。如果你有任何额外的问题，欢迎在评论中添加。