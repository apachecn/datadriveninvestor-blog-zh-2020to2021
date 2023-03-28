# PsFTP —致命:服务器意外关闭了网络连接

> 原文：<https://medium.datadriveninvestor.com/psftp-fatal-server-unexpectedly-closed-network-connection-188e6f402d01?source=collection_archive---------11----------------------->

Windows 用户使用 Ps FTP 以编程方式向/从 Linux 服务器上传/下载文件。

![](img/28d023b518317a0b048d0dabc7c14c26.png)

Photo by [Sigmund](https://unsplash.com/@sigmund?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/ftp?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

在讨论这个错误之前，先下载如何使用 PsFTP 的简介。远程 Linux 服务器上的 jpg 文件。

```
c:\somefolder>psftp.exe -v remoteLinuxHostName -i location_of_ppk_file  -l remote_user_name -b c:\somefolder\script.sh
```

> sample script.sh(从远程服务器/home/somefoler/images 文件夹下载 jpg 文件)

```
#script.shcd /home/somefolder/images
mget *.jpg
quit
```

在正常情况下，这应该可以正常工作…而且一切正常。在某些情况下，您可能会看到类似这样的错误

> ***使用 Diffie-Hellman 与标准组【第 14 组】
> 使用哈希 SHA-1 进行 Diffie-Hellman 密钥交换
> 致命:服务器意外关闭网络连接***

**原因**:服务器升级了最新的安全策略/算法。

**解决方案**:没什么好惊慌的，因为解决方案很简单。访问这个网址，获得最新版本的 PsFTP.exe

[https://www . chiark . greenend . org . uk/~ sgtatham/putty/latest . html](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

**注**:同样的解决方案也适用于 FileZilla 等其他 FTP 客户端。

SSH 上的相关帖子

[](https://www.datadriveninvestor.com/2020/11/24/mobile-network-o2-launch-uks-first-driverless-car-lab-testing-driverless-cars-using-5g-and-satellite-technology/) [## 移动网络 O2 发布英国首个无人驾驶汽车实验室测试使用 5G 和…

### 随着时间的推移，技术越来越强大。我们不仅成功地登上了月球，我们现在…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/11/24/mobile-network-o2-launch-uks-first-driverless-car-lab-testing-driverless-cars-using-5g-and-satellite-technology/) [](https://gchandra.medium.com/ssh-exchange-identification-read-connection-reset-by-peer-48e2f7a8e312) [## ssh _ exchange _ identificati on:read:对等方重置连接

### 类型:错误消息

gchandra.medium.com](https://gchandra.medium.com/ssh-exchange-identification-read-connection-reset-by-peer-48e2f7a8e312) 

## 访问专家视图— [订阅 DDI 英特尔](https://datadriveninvestor.com/ddi-intel)