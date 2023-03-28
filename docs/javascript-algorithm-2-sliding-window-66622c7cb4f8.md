# Javascript 算法 2——“滑动窗口”

> 原文：<https://medium.datadriveninvestor.com/javascript-algorithm-2-sliding-window-66622c7cb4f8?source=collection_archive---------1----------------------->

## 嗨，我带来了另一种常见的 Javascript 算法类型！这就是所谓的“滑动窗口”。它在跟踪数组或字符串中的数据子集时非常有用，并且在降低时间复杂度方面非常有用。

![](img/e31790d3ea9d1dbdc406e76cf4c0eb4f.png)

如果我们看一个例子，就更容易理解了。

让我们定义一个返回 num 大小的子数组的最大和的函数。我们将添加数组中的前三个元素，从索引 0 开始，连续移动到下一个元素。当我们添加下一个子集时，我们将通过减去起始索引元素并添加新的索引元素来移动窗口。

[](https://www.datadriveninvestor.com/2019/03/22/the-seductive-business-logic-of-algorithms/) [## 算法诱人的商业逻辑|数据驱动的投资者

### 某些机器行为总是让我感到惊讶。我对他们从自己的成就中学习的能力感到惊讶…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/03/22/the-seductive-business-logic-of-algorithms/) 

这里有一个例子。

**输入数组** : [2，6，9，2，1，8，5，6，3]

**数字** : 3

1.  让我们定义两个变量来跟踪结果子集的总和以及与临时总和相比的最大总和。

```
function maxSumArr(arr, num) {
    let maxSum = 0;
    let tempSum = 0;}
```

2.如果一个数组的长度小于 num，我们应该在开始循环数组之前返回 **null** 。

```
function maxSumArr(arr, num) {
    let maxSum = 0;
    let tempSum = 0;
    if(arr.length < num) return null;}
```

3.开始从索引 0 到 num 大小的数组循环，并将每个元素添加到 tempSum 中

```
function maxSumArr(arr, num) {
    let maxSum = 0;
    let tempSum = 0;
    if(arr.length < num) return null;
    for(let i = 0; i < num; i++) {
       tempSum += arr[i]; }}
```

4.将 tempSum 设置为 maxSum 变量，并从 num 开始再次遍历数组以获得新的 tempSum。新的 tempSum 是通过滑动数组的窗口获得的，因此我们可以减去新子集的前一个元素并添加新元素

```
function maxSumArr(arr, num) {
    let maxSum = 0;
    let tempSum = 0;
    if(arr.length < num) return null;
    for(let i = 0; i < num; i++) {
       tempSum += arr[i]; }
    tempSum = maxSum;
    for(let i = num; i < arr.length; i++) {
       tempSum = tempSum - arr[i - num] + arr[i]; }}
```

5.现在，是时候比较 maxSum 和 tempSum，并将较大的和设置为 maxSum，我们将在最后返回。

```
function maxSumArr(arr, num) {
    let maxSum = 0;
    let tempSum = 0;
    if(arr.length < num) return null;
    for(let i = 0; i < num; i++) {
       tempSum += arr[i]; }
    tempSum = maxSum;
    for(let i = num; i < arr.length; i++) {
       tempSum = tempSum - arr[i - num] + arr[i];
       maxSum = Math.max(tempSum, maxSum); }      
       return maxSum;}
```

Yayyy！！！我们得到了最大子阵列的和！利用滑动窗口算法，将运算时间减少到 O(n)。干得好。