# 使用 Scala 从网上下载 PDF 文件

> 原文：<https://medium.datadriveninvestor.com/download-covid-19-pdf-reports-from-the-web-using-scala-191dd2a78729?source=collection_archive---------5----------------------->

![](img/d6713feb7dbe90ae318169ce143d5a54.png)

Photo by [Sara Bakhshi](https://unsplash.com/@sarabakhshi?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

最近我一直在用 Scala 练习函数式编程，为了练习，我想做一个小项目，从世界卫生组织自动下载新冠肺炎报告。

## **关于 Scala 的一点信息**

Scala(**SCA**lable**la**language)是一种静态类型的、函数式的、面向对象的语言，如果需要的话，它还允许你编写命令式代码。它编译到 Java 虚拟机，并针对大数据工作负载进行了优化，例如分布式大数据处理技术 Apache Spark 就是用 Scala 编写的。

[](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) [## 2019 年最值得学习的编码语言|数据驱动的投资者

### 在我读大学的那几年，我跳过了很多次夜游去学习 Java，希望有一天它能帮助我在…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) 

这意味着您可以使用现有的 java 库(以及许多堆栈溢出答案！)，并编写优雅、简洁的代码来完成工作。糟糕的是你必须学习函数式编程。不过，相信我，你不会后悔的。

向前！

## **第 0 步:依赖和导入**

出于本教程的目的，我使用 SBT (Scala 构建工具)启动了一个关于 IntelliJ 的新项目。我已经在 IntelliJ 项目的 build.sbt 文件中作为依赖项导入了 JSoup 库。我们将使用 JSoup 作为库来解析来自世卫组织网站的 HTML:

```
*libraryDependencies* ++= Seq(
  "org.jsoup" % "jsoup" % "1.8.3"
)
```

下面是我们将在整个项目中使用的导入。就个人而言，我对 scala 标准库的了解非常有限。因此，我不会在这一点上深入细节。

```
package main

import scala.language.*postfixOps* import scala.jdk.CollectionConverters._

import sys.process._
import java.net.URL
import java.io.File

import org.jsoup.Jsoup
import org.jsoup.nodes.Document
import org.jsoup.select.Elements
```

## **第一步:从网页中获取链接**

首先，让我们写一个函数，允许我们从一个叫做 getLinks 的网页上抓取链接。获取链接需要两个参数，url 和选择器。

```
def getLinks(url: String, selector: String) = {/* url is the page you want to scrape for links, and selector, is the JSoup HTML content selector. JSoup is a Java Library that allows you to parse and read through HTML documents. It uses the content selector syntax to allow you to target the specific information you want on your target website. You can read more about JSoup [here](https://jsoup.org/). */ // download the document
    val document: Document = Jsoup.*connect*(url).get()
    // get our target a tags val aTags: Elements = document.select(selector)

   // get the links from our a tags
    val links = for(aTag <- aTags.asScala) yield aTag.attr("href") // convert our java collection in links to an IndexedSeq
   links.toIndexedSeq
  }
```

## **第二步:清理我们的网址**

在世界卫生组织网站链接结构中，hrefs 删除了根 url 并使用相对 URL。为了处理这个问题，我们需要添加逻辑来将根 url 附加到我们的每个链接上

```
def appendRootUrl(rootUrl: String, links: IndexedSeq[String]) ={/*We'll provide the rootUrl as a string and the IndexedSequence of Strings we get from our getLinks function
*/ //for each link, return the rootUrl appended with the link
    val loadableLinks = for(link <- links) yield rootUrl + link // convert our links to a List.
    loadableLinks.toList
```

## **第三步:下载文件**

最后，我们将编写 downloadFiles 函数，它将下载文件并将其写入指定的路径。

```
def downloadFiles(downloadableFileLinks: List[String], path: String): Unit = {/*
 given a set of links that are downloadable, and a target path, will download the files.

Below, for each downloadable link, we'll instantiate a new URL object, then we will create our target filepath with the filename. 
Then, we will clean the file name.
Finally, we will write to disk. *//* map functions are super cool! they essentially apply logic to each element in your collection. Below, for each downloadableLink in downloadableFileLinks, we're initializing a URL, creating a filepath, and then writing the urlObject to disk. downloadableFileLinks.map( downloadableLink =>
    {val urlObject = new URL(downloadableLink)
      val filePath = path + "/" + urlObject.getPath().replaceAll("/", "")
      urlObject #> new File(filePath)!!
    })
  }
```

## **第四步:让我们把它们放在一起**

```
package main

import scala.language.*postfixOps* import scala.jdk.CollectionConverters._

import sys.process._
import java.net.URL
import java.io.File

import org.jsoup.Jsoup
import org.jsoup.nodes.Document
import org.jsoup.select.Elements

object main extends App {

  def getLinks(url: String, selector: String) = {

    val document: Document = Jsoup.*connect*(url).get()
    val aTags: Elements = document.select(selector)
    val links = for(aTag <- aTags.asScala) yield aTag.attr("href")
    links.toIndexedSeq
  }

  def appendRootUrl(rootUrl: String, links: IndexedSeq[String]) ={

    val loadableLinks = for(link <- links) yield rootUrl + link
    loadableLinks.toList
  }

  def downloadFiles(downloadableFileLinks: List[String], path: String): Unit = {
    downloadableFileLinks.map( downloadableLink =>
    {
      // *TODO: Only write if fileNotExists?* val urlObject = new URL(downloadableLink)
      val filePath = path + "/" + urlObject.getPath().replaceAll("/", "")
      urlObject #> new File(filePath)!!
    })
  }

  val *rootUrl* = "https://www.who.int/"
  val *scrapedUrl* = "https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports?fbclid=IwAR0bANT83XoqEwhEWnGvjmBSsGjy0S9smn1wP5wTtIyy_Oe78_NtMUATEqA"
  val *regexPattern* = ".*\\/(.*)\\?".r
  val *aLinksContentSelectpr* = ".sf-content-block a[target=_blank]"
  val *linksOnPage* = *getLinks*(*scrapedUrl*, *aLinksContentSelectpr*)
  val *downloadableLinks* = *appendRootUrl*(*rootUrl*, *linksOnPage*)

  *downloadFiles*(*downloadableLinks*, "./files")

}
```

## **步骤 4:使用 Python 从 PDF 文件中提取数据**

我还没有用 Scala 解决这个问题，我以前写过如何使用 Python 从一个 [PDF 文件中提取数据。你可以参考这篇文章来大致了解如何提取这些数据。](https://medium.com/@rqaiserr/convert-tables-from-pdfs-to-pandas-with-python-d74f8ac31dc2)

喜欢我的作品吗？雇用我做升级工作！