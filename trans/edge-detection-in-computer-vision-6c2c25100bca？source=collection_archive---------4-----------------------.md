# 计算机视觉中的边缘检测

> 原文：<https://medium.datadriveninvestor.com/edge-detection-in-computer-vision-6c2c25100bca?source=collection_archive---------4----------------------->

![](img/251c1e66aa50cfa483c870f32e161437.png)

credits [Unsplash](https://unsplash.com/photos/fVzz6Fy4SbU)

边缘检测是计算机视觉中一项基本但重要的任务。这样做通常是为了减少数据量，同时保留图像中对象的结构属性。使用边缘检测的常见任务是车道检测和将图像转换为草图。

虽然边缘检测的算法很多，但是今天我们要讨论的是 **Canny 边缘检测算法**(John f . Canny 于 1986 年提出)。

```
import numpy as np
import cv2
import matplotlib.pyplot as plt
%matplotlib inline
```

*它是一个多阶段算法:*

# 步骤 1:使用高斯模糊降低噪声:

高斯滤波器在图像上进行卷积，以去除噪声并防止将噪声假设为边缘。像素强度的突然变化不应被视为边缘，因此首先对输入图像进行平滑处理是至关重要的。

```
A typical Gaussian filter: 
          [[2,  4,   5,  4,  2],
          [ 4,  9,  12,  9,  4],
(1 / 159)*[ 5, 12,  15, 12,  5],
          [ 4,  9,  12,  9,  4],
          [ 2,  4,   5,  4,  2]]
```

## 展示如何在图像上使用高斯模糊的示例

```
# input image
img = cv2.imread("plant2.jpg", 0)# gaussian smoothing
blurred=cv2.GaussianBlur(img,(5, 5),1.4) f,(ax1, ax2) = plt.subplots(1,2)
ax1.imshow(img,cmap='gray')
ax1.title.set_text("Original image")
ax2.imshow(blurred,cmap='gray')
ax2.title.set_text("after Gaussian blur")
```

![](img/496e3b467cf6049ae2558c42960e2caf.png)

# 第二步:寻找渐变:

渐变只不过是图像像素强度的变化。图像平滑后，使用 Sobel 算子计算沿 x 和 y 方向的梯度。然后，通过应用毕达哥拉斯定律，可以将梯度幅度(也称为边缘强度)确定为欧几里德距离度量。

```
The Sobel kernels are convolved 
over the image to determine 
gradient magnitudes.Along X direction Kx:  
            [[-1, 0, 1],
            [-2, 0, 2],
            [-1, 0, 1]] Along Y direction Ky:  
            [[1, 2, 1],
            [0, 0, 0],
            [-1,-2,-1]]gradient magnitude = sqrt(Gx^2 + Gy^2)
angle = arctan(|Gy| / |Gx|)
```

## 演示如何使用 Sobel 算子查找梯度的示例

```
# input image
img = cv2.imread("plant2.jpg", 0)sobelx = cv2.Sobel(img,cv2.CV_64F,1,0,ksize=5)
sobely = cv2.Sobel(img,cv2.CV_64F,0,1,ksize=5)f, (ax1,ax2,ax3) = plt.subplots(1,3)
ax1.imshow(img, cmap='gray')
ax1.title.set_text("Original image")
ax2.imshow(sobelx, cmap='gray')
ax2.title.set_text("Sobel along X axis")
ax3.imshow(sobely, cmap='gray')
ax3.title.set_text("Sobel along Y axis")
```

![](img/a771d2e72b737c496485b35e648eedbb.png)

Sobel-operator along X and Y axis

# 步骤 3:非最大抑制:

应用非最大抑制来寻找强度值变化最剧烈的位置。梯度图像中每个像素的算法是:

1.  将梯度方向θ四舍五入到最近的 45 度，对应于使用 8-连通邻域。
2.  将当前像素的边缘强度与该像素在正负梯度方向上的边缘强度进行比较。
3.  如果当前像素的边缘强度与掩模中具有相同方向的其他像素相比是最大的(例如，指向 y 方向的像素将与垂直轴上其上方和下方的像素进行比较)，则该值将被保留。否则，该值将被抑制。

# 第四步:双阈值

在非最大值抑制步骤之后剩余的边缘像素被(仍然)逐个像素地标记其强度。这些边缘中的许多可能是图像中的真实边缘，但一些可能是由噪声或颜色变化引起的，例如由于粗糙的表面。辨别它们的最简单的方法是使用阈值，以便只保留比某个值更强的边缘。Canny 边缘检测算法使用双阈值。比高阈值强的边缘像素被标记为强；比低阈值弱的边缘像素被抑制，两个阈值之间的边缘像素被标记为弱

# 步骤 5:通过滞后进行边缘跟踪

这个阶段决定了哪些是真正的边，哪些不是。为此，我们需要两个阈值，minVal 和 maxVal。任何强度梯度大于 maxVal 的边缘肯定是边缘，而小于 minVal 的边缘肯定是非边缘，因此被丢弃。位于这两个阈值之间的那些根据它们的连通性被分类为边缘或非边缘。如果它们连接到“确定边缘”像素，它们被认为是边缘的一部分。否则，它们也会被丢弃。

> *openCV 有一个很好的实现* ***cv2。Canny()*** *将所有这些步骤包装成一个函数。*

```
img = cv2.imread("noctua.jpg", 0)
# detect edges 
canny = cv2.Canny(img,30,100)f, (ax1, ax2) = plt.subplots(1,2)
ax1.imshow(img, cmap='gray')
ax1.title.set_text("Original image")
ax2.imshow(canny, cmap='gray')
ax2.title.set_text("Edges detected")
```

![](img/b36392b3f0a87c0cd84a0a115abd96b2.png)

noctua NH-D15 from my Deep Learning rig

# 参考资料:

*   [https://en.wikipedia.org/wiki/Canny_edge_detector](https://en.wikipedia.org/wiki/Canny_edge_detector)
*   [https://www.cse.iitd.ac.in/~pkalra/col783-2017/canny.pdf](https://www.cse.iitd.ac.in/~pkalra/col783-2017/canny.pdf)
*   [https://opencv-python-tutro als . readthedocs . io/en/latest/py _ tutorials/py _ imgproc/py _ canny/py _ canny . html](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_imgproc/py_canny/py_canny.html)
*   [https://www . geeks forgeeks . org/implement-canny-edge-detector-in-python-using-opencv/](https://www.geeksforgeeks.org/implement-canny-edge-detector-in-python-using-opencv/)
*   [https://www . tutorialspoint . com/opencv/opencv _ canny _ edge _ detection . htm](https://www.tutorialspoint.com/opencv/opencv_canny_edge_detection.htm)

在 github 页面 [iWriteHere](https://rahulbakshee.github.io/iWriteHere/) 上阅读我的其他故事，或者在 [twitter](https://twitter.com/rahulbakshee) 和 [linkedin](https://www.linkedin.com/in/rahulbakshee/) 上与我联系