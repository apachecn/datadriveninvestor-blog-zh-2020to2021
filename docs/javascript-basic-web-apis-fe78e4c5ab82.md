# Javascript 基本 Web APIs

> 原文：<https://medium.datadriveninvestor.com/javascript-basic-web-apis-fe78e4c5ab82?source=collection_archive---------18----------------------->

![](img/c328013d78ed7e7db31144c997d75a8c.png)

Photo by [Braden Collum](https://unsplash.com/@bradencollum?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

这几天我开始复习香草 Javascript 来更新和巩固我对这门语言的知识。我相信，在当今开发的流动框架中，掌握一门基础语言是非常重要的。我可能会将这些内容制作成一个系列，这将是我的第一篇笔记。让我们从一些我们经常用于 HTML 文档、节点和元素的基本 Web APIs 开始。

以下是我今天查看的 API 列表。

*   createElement()
*   setAttribute()
*   appendChild()
*   scrollIntoView()
*   焦点()

1.  ***document . createelement()***方法创建由 tagName 指定的 HTML 元素。
    **//语法:
    //let element = document . createelement(标记名)；** **标记名**是一个字符串，指定要创建的元素类型。比如‘李’，‘div’，还有‘span’。
2.  ***element . set attribute()***设置指定元素的属性值。如果属性已经存在，则更新该值。
    要获取一个属性的当前值，使用**get attribute()**；要删除一个属性，调用 **removeAttribute()** 。
    /**语法:**
    /**element . set attribute(name，value)；**
3.  将一个节点添加到指定父节点的子节点列表的末尾。
    /**语法:**
    /**element . appendchild(aChild)；**
4.  元素接口的***scrollIntoView()***方法滚动元素的父容器，以便元素对用户可见。有两种类型的参数可以作为选项放置。
    **align top(可选)——**是一个**布尔值**:
     **scrollintoview options(可选)——**是一个**对象**，具有以下属性:- *行为*:自动、平滑
    - *块*(定义垂直对齐):开始、居中、结束或最近的
    -
5.  方法的作用是:在指定的元素上设置焦点。
    // **语法:**
    //**element . focus()；**

希望这些内容能帮助你刷新你的普通 JS 记忆！