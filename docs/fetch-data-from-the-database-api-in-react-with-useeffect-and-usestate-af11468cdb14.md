# 用 useEffect 和 useState 从数据库/API 中提取数据

> 原文：<https://medium.datadriveninvestor.com/fetch-data-from-the-database-api-in-react-with-useeffect-and-usestate-af11468cdb14?source=collection_archive---------1----------------------->

![](img/1aeb048de88b072f53adc1b3464873be.png)

# 对应于`componentdidmount`

很多时候，当组件安装在 React 中时，我们希望获取大量数据。如果你熟悉 React 中的类组件，你知道我们可以使用`componentdidmount`。对于功能组件，对应的是`useEffect`。我们可以使用`useState`来处理从数据库或 API 获取的数据。

# 例子

例如，我想在主页上显示大量从数据库中获取的附近餐馆的数据。

如果我们像这样正常地做:

```
const homepage = () => {
  let restaurants = fetchData()return(
        renderRestaurants(restaurants)
    )
}
```

当我们的组件想要使用`restaurants`值时，因为获取过程可能需要很长时间，所以我们不会看到我们期望的餐馆数据显示。

但是我们不能在一个功能组件中使用`async/await`。我们通常会得到这样的错误，因为 React 没有将`Promise`作为一个组件(因为在您放置了`async`之后，React 会将其视为`Promise`):

```
Objects are not valid as a React child (found: [object Promise]).
```

那我们能做什么？

# 解决办法

```
 useEffect(() => {
   fetchData()
      })
```

可以看到，`useEffect`将一个函数作为第一个参数。它会在每次渲染后自动触发。它将在其他事情之前被触发，所以我们可以确保当我们想要显示数据时，数据就在那里。

## 我们如何处理获取的数据？

答:我们可以用`useState`来处理:

```
const [restaurants, setRestaurants] = useState([])useEffect(() => {
   let data = fetchData();
   setRestaurants(data)
      })
```

在这个例子中，我们为组件设置了一个`restaurants`状态，并将默认值设置为一个数组。`setRestaurants`是改变`restaurants`值的方法。

因此，在`useEffect`中，我们调用`fetchData()`从 db 或 API 中获取数据，然后我们应该会得到附近的一系列餐馆数据。然后我们可以将该数据传递给`setRestaurants`，这样`restaurants`将被更新以供我们将来在文档中使用。

## 异步部分呢？

明确地说，如果你试图这样做:

```
useEffect( async() => {
   let data = await fetchData();
   setRestaurants(data)
      })
```

你也会得到一个错误。您可以像这样调用异步函数:

```
useEffect(() => {
    getRestaurants = async() => {
       await fetchData()  
       setRestaurants(data)    
     }
    getRestaurants();  
      })
```

解决方案是我们将异步部分包装在另一个函数中，然后在以后调用它。

## 如果我们希望它只在一个值被改变时被触发呢？

答:如果我们将第二个参数传递给`useEffect`，代码看起来会像这样:

```
useEffect(() => {
    getRestaurants = async() => {
       await fetchData()  
       setRestaurants(data)    
     }
    getRestaurants();  
     }, [restaurants]
     )
```

第二个论点是什么意思？基本上，它告诉组件比较先前的`restaurants`和当前的`restaurants`值，如果没有差异，那么效果将被跳过。

感谢阅读！