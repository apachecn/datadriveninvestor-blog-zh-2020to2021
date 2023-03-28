# 开始使用 Python 的 ElementTree 导航 XML 文件

> 原文：<https://medium.datadriveninvestor.com/getting-started-using-pythons-elementtree-to-navigate-xml-files-dc9bc720eaa6?source=collection_archive---------0----------------------->

## 一些关于开始和避免一些未被记录在案的挫折来源的提示。

通常，当你通过 API 收集数据时，你会看到 [***JSON***](https://www.w3schools.com/whatis/whatis_json.asp) 格式，这是一个方便打包的嵌套字典(或它们的列表)。尽管 JSON 的采用无处不在，但有时您可能不得不使用旧的 [***XML***](https://www.w3schools.com/xml/xml_whatis.asp) 标准。

如何使用 XML？这取决于你使用什么库，因为有四个常用的库。其中三个包含在 Python 的标准库中:[***MiniDom***](https://docs.python.org/3/library/xml.dom.minidom.html)，[***Sax***](https://docs.python.org/3/library/xml.sax.reader.html)和[***element tree***](https://docs.python.org/3.8/library/xml.etree.elementtree.html)；每个都提供不同的 API 来与 XML 文件交互；而[***lxml***](https://lxml.de/)(构建在元素树上的库)需要通过 Python 的包管理器额外下载。

[](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) [## 2019 年最值得学习的编码语言|数据驱动的投资者

### 在我读大学的那几年，我跳过了很多次夜游去学习 Java，希望有一天它能帮助我在…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/02/21/best-coding-languages-to-learn-in-2019/) 

这些库都有自己的取舍。ElementTree 的优点在于，它提供了方便读写整个 XML 的能力，该 API 是 Python 特有的，并针对 Python 进行了优化，而且它已经包含在大多数 Python 安装中。

![](img/fa88ee303dc444f9e84156e86b6932e1.png)

Image composed using [Krita](https://krita.org).

我在下面列出了智能手表生成的[***【TCX】***](https://en.wikipedia.org/wiki/Training_Center_XML)文件(一种 XML)中的一些代码示例。还提供了我编写 Python 类的一个非常规用例的编辑片段:修改低端智能手表创建的 XML 文件，以便在上传到在线运动跟踪器时提供关于游泳活动的额外见解。您可以在此处看到完整的回购代码:

[https://github.com/coreyryanhanson/y_u_no_swim](https://github.com/coreyryanhanson/y_u_no_swim):

# XML 是如何工作的？

![](img/ebed7d03a8fd4a55c69043ef1d6f1b67.png)

Image composed using [Inkscape](https://inkscape.org/) and public domain sources.

如果您熟悉 HTML，您可能会觉得在 XML 结构中导航很轻松。每个[元素都由标签标记，形成分层数据层](https://www.w3schools.com/xml/xml_elements.asp)。

开始标签由符号“<*标签名称* >”表示，而结束标签在名称前包含一个斜杠:“< / *标签名称* >”。开始标签还可以包含属性，这些属性提供关于标签的特定实例的额外信息，并且还可以将其与其他标签区分开来。

```
*# An excerpt of an xml document that recorded a swim showing how tags can fit inside other tags. Here "Activities" can contain one or more instances of an "Activity" which contains one or more instances of a Lap.*
<Activities>
    <Activity Sport="Other">
        <Id>2019-08-21T23:43:28.000Z</Id>
        <Lap StartTime="2019-08-21T23:43:29.000Z">
            <TotalTimeSeconds>81.0</TotalTimeSeconds>
            <DistanceMeters>0.0</DistanceMeters>
            <Calories>279</Calories>
            *#The data continues with the closing tag for the lap,
            followed by the closing tag for the activity, and
            finally a closing tag for all of the activities.*
```

默认情况下，Python 会将这些标签中包含的所有数据视为一个庞大的文本字符串，但是使用 element tree 之类的库可以实现更高效的列表式导航。

# ElementTree 入门

使用 ElementTree 时，整个 XML 被解析并存储在一个 [***ElementTree 对象***](https://docs.python.org/3.8/library/xml.etree.elementtree.html#xml.etree.ElementTree.ElementTree) 中。该 API 功能强大，不仅可以搜索特定的标签，将特定的 [***元素***](https://docs.python.org/3.8/library/xml.etree.elementtree.html#xml.etree.ElementTree.Element) 保存在其他变量中，而且对它们的任何修改和插入都将反映到整个树中。

```
import xml.etree.ElementTree as ET*#Uses element tree to parse the url or local file and stores it in memory.*
tree = ET.parse(*path*)*#Stores the top level tag (and all children) of the tree into a variable. You will mostly be using this in your xml interactions with the entire document.*
root = tree.getroot()
```

# 输入名称空间:ElementTree 中最不直观的部分

因此，您已经导入了库，解析了文件，并准备开始研究数据。还是你？如果您的 XML 恰好包含 [***名称空间***](https://www.w3schools.com/xml/xml_namespaces.asp) ，答案是否定的

```
*#Prints a string of the entire XML document* print(ET.tostring(root, 'utf-8')
```

对文本的快速预览显示，一个奇怪的异常决定将自己插入到整个 XML 中。通过文本编辑器直接查看或用另一个库解析时，原始文档中不存在的对象。

```
*#Unknown namespace causes "ns0:" to be inserted in every single tag.* <ns0:Trackpoint>
    <ns0:Time>
        2019-08-22T00:10:16.000Z
    </ns0:Time>
    <ns0:HeartRateBpm>
        <ns0:Value>
            120
        </ns0:Value>
    </ns0:HeartRateBpm>
    <ns0:SensorState>
        Present
    </ns0:SensorState>
</ns0:Trackpoint>
```

为什么会这样？未定义的名称空间会破坏 ElementTree 工作流。因为 XML 是一种可扩展的标准，允许任何人创建自己的系统和定义自己的标签集，所以 XML 提供了一种方法来确保不同 XML 生态系统中的这些标签彼此是唯一的，从而防止在必然会发生重叠时出现混淆。

虽然其他库会在后台处理这些问题，但 ElementTree 需要显式定义这些名称空间，否则您的 XML 将充斥着笨重的占位符注释。

手动定义名称空间可能听起来令人生畏，但并不像听起来那么难。所有需要的信息都应该出现在您正在使用的 XML 中。ElementTree 只需要用包含在由***【xmlns】***(顺便说一下，它代表 ***XML 名称空间*** )指示的属性中的信息进行适当的配置。你会看到它后面有一个 [***uri***](https://dev.to/flippedcoding/what-is-the-difference-between-a-uri-and-a-url-4455) ，通常采用 url 的形式。

```
*#An xml namespace attribute inside that element's tag follows this basic format.* <Author xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="Application_t">
```

乍一看，它可能看起来像一个依赖于互联网连接的复杂组件， ***它仅仅是一个唯一的标识符*** 。任何超链接都只是作为约定和资源添加的，开发者可以根据自己的选择找到更多信息。还要注意，如果在 xmlns 属性和 uri 之间没有指定参数，那么它表示一个 ***默认名称空间*** 。

```
*#Default namespaces follow this format.*
lc">namespaceURI"
```

要在 ElementTree 中定义名称空间，可以找到并逐个传递它们…

```
*#Be sure to replace "URI" with the actual URI in your XML document.*
ET.register_namespace('', "URI")
ET.register_namespace('xsi', "http://www.w3.org/2001/XMLSchema-instance")
```

…或者您可以直接从文档中抽象出定义名称空间的过程，以更程序化的方式处理事情。做到这一点说起来容易做起来难，但可以通过 ElementTree 提供的[***ITER parse***](https://docs.python.org/3.8/library/xml.etree.elementtree.html?highlight=iterparse#xml.etree.ElementTree.iterparse)函数中的一些低级诡计来实现。

```
*#Uses a list comprehension and element tree's iterparse function to create a dictionary containing the namespace prefix and it's uri. The underscore is utilized to remove the "start-ns" output from the list.*
namespaces = {node[0]: node[1] for _, node in ET.iterparse(self.filepath, events=['start-ns'])}*#Iterates through the newly created namespace list registering each one.*
for key, value in namespaces.items():
    ET.register_namespace(key, value)
```

这个特定代码块的有用之处在于，它将文档的所有名称空间存储在一个字典中，这在以后执行搜索时会很方便，因为该字典需要作为参数传递。如果没有它，当使用类似于[***find all***](https://docs.python.org/3.8/library/xml.etree.elementtree.html?highlight=findall#xml.etree.ElementTree.Element.findall)的命令时，很可能得不到匹配。

# 准备开始工作了吗？不完全是…名称空间再次出击！

虽然可以说，如果您面临标记名重叠的情况，ElementTree 所需的名称空间特异性水平可能会很高，但有一个特别的奇怪之处很难证明:ElementTree 对默认名称空间的处理。

长话短说， [***它不知道如何处理空字符串***](https://stackoverflow.com/questions/34009992/python-elementtree-default-namespace) 的名称空间键。

虽然这种笨拙的疏忽可能有些令人失望，但是您可以通过将允许在默认名称空间内手动搜索的文本存储到一个变量中以备后用，从而将不便之处降至最低并继续前进。

```
*#The curly brackets are needed around the uri when using Element Tree's find command with a manually passed namespace.*
default_ns = "{" + namespaces[""] + "}"*# By inserting your namespace variable immediately before the search term your code will return the results you expect.*
activ_tag = root.find(".//" + default_ns + "Activity")
```

现在，您将可以毫无障碍地在 XML 上利用 ElementTree 的功能。参考[文档](https://docs.python.org/3.8/library/xml.etree.elementtree.html)中关于你能做什么的例子。

# 最后一个格式化说明

XML 是一种完全忽略空白的语言。如果出于某种原因，您需要无缝地将 XML 输出到一种使层次结构更易于阅读的格式中，那么在 ElementTree 中可能更难做到这一点。

为了克服这一点，[有几种方法你可以采用](https://stackoverflow.com/questions/749796/pretty-printing-xml-in-python)。对于我的智能手表脚本，我使用了一种变通方法，包括为了简洁而牺牲效率，在 MiniDom 中导入整个 XML，以便在导出时使用它们的[***toprettyxml***](https://docs.python.org/2/library/xml.dom.minidom.html?highlight=prettyxml#xml.dom.minidom.Node.toprettyxml)方法，因为文件不是太大。你可以查看[我的代码](https://github.com/coreyryanhanson/y_u_no_swim)中关于如何设置的例子。

根据 XML 的结构，第一次使用 ElementTree 可能会有些困难。开始使用对我来说是一个挫折的来源，但是一旦我想出了一些技巧，我发现它是一个非常通用的工具，正是我所需要的！