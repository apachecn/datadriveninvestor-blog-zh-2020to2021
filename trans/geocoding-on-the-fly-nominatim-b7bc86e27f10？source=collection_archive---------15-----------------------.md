# 动态地理编码:命名

> 原文：<https://medium.datadriveninvestor.com/geocoding-on-the-fly-nominatim-b7bc86e27f10?source=collection_archive---------15----------------------->

![](img/0bb2a2aff1a99c54c27cb816ddeb2211.png)

Photo by [Sangga Rima Roman Selia](https://unsplash.com/@sxy_selia?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

现在我们有了一致的服务地址字段，我们可以开始地理编码来查找 XY 坐标。在这篇文章中，我将专注于地理编码器，解释我研究的选项。然后在另一篇文章中，我将提供一个用于从熊猫数据帧中获取坐标的 python 脚本。

我看了几个地理编码器。使用 OpenStreetMap 的 Nominatim 是我最喜欢的选项。我已经简单的提到过，nomist 在格式上更严格，但是对于一个免费的服务来说，它是非常好的。我已经关注 OpenStreetMap 好几年了，它的全球开源社区非常稳定。世界各地有几家大型咨询公司，如 Geofabrik [data extracts](http://download.geofabrik.de/) ，他们在 OpenStreetMap 数据上编写产品，这有助于使其成为稳定的产品。

我在他们的开发者[网站](https://developers.google.com/maps/documentation/geocoding/usage-and-billing)上查看了谷歌的 API。截至 2021 年 2 月 15 日，每 1000 个请求大约 5 美元。这是一个合理的价格，地理编码 API 非常宽容。因此，如果清理和格式化数据帧不适合您，这将是一个低成本的选择。但是，如果您需要多次运行代码，这可能不会长期保持低成本。我在调试时已经运行了几次我的代码。和许多软件公司一样，谷歌历来提供低价服务，价格会随着时间的推移悄悄上涨。

行业标准通常是 ESRI 的 ArcGIS 产品，它们非常好，但也非常昂贵。还有一个行业选项可以与 ArcGIS 相媲美，那就是 QGIS。它确实提供了 MMQGIS，同样使用 OpenStreetMap 对地址进行地理编码。所以 OpenStreetMap 再次出手相救。ArcGIS 和 QGIS 的一个重要方面是，如果您不是 GIS 专家，可能很难浏览该软件。

这又回到了提名。它运行在 [Geopy](https://geopy.readthedocs.io/en/stable/) 上，这是一个用于处理地理数据的 python 库。这些是我将演练的导入和设置:

访问 Nominatim API 时，需要有一个用户名。您可以创建您的用户名，我在这里使用了“我的用户代理”。我使用速率限制器来防止 API 超时太快。代码越长，ping API 所需的时间就越长。对于大多数代码块来说，超时错误会在 2 秒内发生，因为处理代码的时间太长。速率限制器将延迟 ping API 的时间，从而避免 API 错误。在下一篇文章中，当我逐步介绍 python 代码时，您将会看到为什么需要这样做。

这个代码代表了地理编码器正在做什么。如果我需要英国伦敦的坐标，我可以将这些变量放入我的地理定位器中，方法是将它们组合成地理编码方法参数中的一个字符串。一旦它通过地理定位器传递到 limit，地理编码就对 pings 进行限制，OpenStreetMap 返回地址信息。从那里我可以提取属性*。纬度*和*。来自*位置*变量的经度*。我将在以后的文章中更详细地解释来自 geolocator.geocode 的位置信息的变量。