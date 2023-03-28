# 算法求解策略

> 原文：<https://medium.datadriveninvestor.com/algorithm-solving-strategies-89ce5248cb03?source=collection_archive---------12----------------------->

![](img/045fd360c9a0d2a2c2dda5e6beed32e4.png)

Photo by [Christina @ wocintechchat.com](https://unsplash.com/@wocintechchat?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

如果你读过我之前关于 [Big O Notation](https://medium.com/swlh/big-o-notation-128b7b8051c9) 的博客，你可能记得算法被定义为“一个定义明确的、计算机可实现的指令的有限序列，通常是为了解决一类问题或执行一种计算”([维基百科](https://en.wikipedia.org/wiki/Algorithm))。算法对所有软件工程师来说都很重要，因为它们可以帮助我们解决工作中可能遇到的问题。

你可能正在读这篇博文，因为你目前正在找工作。如果是这样的话， [LeetCode](https://leetcode.com/) 和 [HackerRank](https://www.hackerrank.com/) 都有数百个练习算法的问题供求职者利用。这篇博客的目的是用一些策略来武装你，帮助你解决这些类型的问题，以及你在面试和工作中可能遇到的问题。

本博客将要讨论的三个策略包括:

1.  **频率计数器**
2.  **多指针**
3.  **推拉窗**

*这些策略来自柯尔特·斯蒂尔的 JavaScript 算法和数据结构大师班 Udemy 课程，我强烈推荐。这些例子主要来自 LeetCode。*

## 计数式频率计

频率计数器方法可以应用于需要收集值或检查某个值出现的次数的算法。这种策略利用了对象或集合，避免了对嵌套循环的需要(Steele)。此外，频率计数器将我们的解决方案的时间复杂度从 O(n )(如果使用嵌套循环)提高到 O(n)。

现在，为了在实践中展示频率计数器策略，让我们看一个来自 Leetcode 的例子。

```
**Source**: [https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)**Problem**:Given two strings *s* and *t* , write a function to determine if *t* is an anagram of *s*. Test Case #1 **Input:** *s* = "tennis", *t* = "entsno"
     **Output:** false Test Case #2 **Input:** *s* = "tan", *t* = "nat"
     **Output:** true
```

在这个示例中，我们将使用频率计数器方法来检查每个字符串是否都有相同的字母，以及这些字母出现的次数是否相同。如果这两个检查都为真，我们知道 s 和 t 是变位词。

```
**Solution:****var** isAnagram = function(s, t) {
  // if string lengths are different, it's impossible for string t 
    // to be an anagram
  **if** (s.length !== t.length) {
    **return** false;
  } **const** lookup = {}; **for** (let i = 0; i < s.length; i++) {
    **let** letter = s[i];
    // if letter exists, increment by 1, otherwise set to 1
    lookup[letter] ? lookup[letter] += 1 : lookup[letter] = 1;
  }

  **console.log**(lookup) **for** (let i = 0; i < t.length; i++) {
    **let** letter = t[i];
    // if letter not found or letter value is zero then string t is
      // not an anagram of string s
    **if** (!lookup[letter]) {
      **return** false;
    } **else** {
      lookup[letter] -= 1;
    }
    **console.log**(lookup)
   } **return** true;
};isAnagram("tennis", "entsno")
isAnagram("tan", "nat")**Test Case #1 Output**: // lookup object after looping over s string
{ t: 1, e: 1, n: 2, i: 1, s: 1 }// lookup object decrementing by matching letters in t string 
  //  after each loop
{ t: 1, e: 0, n: 2, i: 1, s: 1 }
{ t: 1, e: 0, n: 1, i: 1, s: 1 }
{ t: 0, e: 0, n: 1, i: 1, s: 1 }
{ t: 0, e: 0, n: 1, i: 1, s: 0 }
{ t: 0, e: 0, n: 0, i: 1, s: 0 }false**Test Case #2 Output**:// lookup object after looping over s string
{ t: 1, a: 1, n: 1 }// lookup object decrementing by matching letters in t string 
  //  after each loop
{ t: 1, a: 1, n: 0 }
{ t: 1, a: 0, n: 0 }
{ t: 0, a: 0, n: 0 }true
```

在上面的解决方案中，我们首先检查字符串是否长度相同。我们进行这种检查是因为如果字符串长度不同，我们知道它们不可能是变位词，因此不需要通过任何额外的代码。解决方案中的第一个循环将字符串 s 中所有字母及其频率的汇总创建到一个名为 lookup 的对象中。第二个循环检查字符串 t 中的字母是否出现在 lookup 中，并且值是否大于 0。如果这些条件都为真，则字母在查找中的频率递减 1；如果不是，我们知道字符串 t 不是字符串 s 的变位词。如果第二个循环遍历字符串 t 中的最后一个字母，那么我们返回 true 作为频率，lookup 中的所有字母都将是 0。

## 多个指针

多指针策略通常用于线性结构(即数组、字符串和链表)。当您需要搜索满足特定条件的一个值或一对值时，多指针非常有用。柯尔特·斯蒂尔对其工作过程描述如下，“创建对应于索引或位置的指针或值，并根据特定条件向开始、结束或中间移动”(斯蒂尔)。Steele 还提到，多指针解决方案具有高效的时间复杂度 O(n)和最小的空间复杂度 O(1)。

现在，为了在实践中展示多指针策略，让我们看一个例子。

```
**Source**: [C](https://leetcode.com/problems/valid-anagram/)olt Steele's JavaScript Algorithms and Data Structures Masterclass Course on Udemy**Problem**:Write a function called sumZero which accepts a **sorted array** of integers.The function should find the first pair where the sum is 0\. Return an array that includes both values that sum to zero or undefined if a pair does not exist.Test Case #1

     **Input** = [-3, -2, -1, 0, 1, 2, 3]
     **Output** = [-3, 3]Test Case #2

     **Input** = [-2, 0, 1, 3]
     **Output** = undefinedTest Case #3

     **Input** = [1, 2, 3]
     **Output** = undefined
```

在这个例子中，我们将使用多指针策略来查看一个数组是否包含两个相加后等于 0 的值。因为我们的数组是排序的，所以我们可以在数组的开头和结尾各放一个指针。然后返回两个指针的值，如果它们的和为 0。

```
**Solution:****var** sumZero = function(arr) {
     **let** pointer1 = 0
     **let** pointer2 = arr.length - 1;
     // Needs to be less than instead of less than or equal to
        // to prevent a single 0 creating a false positive.
      **while**(pointer1 < pointer2) {
         **let** sum = arr[pointer1] + arr[pointer2];
         **console.log**(sum, arr[pointer1], arr[pointer2])     
         **if**(sum === 0) {
              return [arr[pointer1], arr[pointer2]];
         } **else if**(sum > 0) {
              pointer2--;
         } **else** {
              pointer1++;
         }
      }
};sumZero([-3, -2, -1, 0, 1, 2, 3])
sumZero([-2, 0, 1, 3])
sumZero([1, 2, 3])**Test Case #1 Output**:// console.log of sum, value at pointer1, and value at pointer2
0 -3 3// result
[ -3, 3 ]**Test Case #2 Output**:// console.log of sum, value at pointer1, and value at pointer2
1 -2 3
-1 -2 1
1 0 1// result
undefined**Test Case #3 Output**:// console.log of sum, value at pointer1, and value at pointer2
4 1 3
3 1 2// result
undefined
```

在上面的解决方案中，我们首先将指针 1 的位置设置为数组的开头，将指针 2 的位置设置为数组的结尾。然后我们看看指针 1 和指针 2 的值之和等于多少。如果总和为负，我们需要将指针 1 向右移动一个值。如果和为正，我们需要将指针 2 向左移动一个值。如果总和为 0，那么我们已经找到了我们要寻找的对，并返回这些值。我们继续这种模式，直到找到一个和为 0 的对，或者到达 while 循环的最后一次迭代，其中指针 1 的位置小于指针 2 的位置并返回 undefined。

**附加示例:**

```
**Source**: [https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/727/](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/727/)**Problem**: Given a sorted array nums, remove the duplicates [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) such that each element appears only once and returns the new length.Do not allocate extra space for another array, you must do this by modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) with O(1) extra memory. **Input:** nums = [0,0,1,1,1,2,2,3,3,4]
     **Output:** 5, nums = [0,1,2,3,4] **Solution:****var** removeDuplicates = function(nums) {
    **if** (nums.length === 0) {
        **return** 0
    }

    **let** pointer1 = 0**for** (let pointer2 = 1; pointer2 < nums.length; pointer2++) {
        **if** (nums[pointer1] !== nums[pointer2]) {
            pointer1++;
            nums[pointer1] = nums[pointer2]
        }
    }

    **return** pointer1 + 1

};**Source**: [https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/567/](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/567/)**Problem**: Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements. **Input:** [0,1,0,3,12]
     **Output:** [1,3,12,0,0]**Solution**:**var** moveZeroes = **function**(nums) { **let** pointer1 = 0

       **for**(**let** pointer2 = 0; pointer2 < nums.length; pointer2++) {
           **if**(nums[pointer2] !== 0) {
               **let** temp = nums[pointer1]
               nums[pointer1] = nums[pointer2]
               nums[pointer2] = temp
               pointer1++
           }
       }
       **return** nums
};moveZeroes([0,1,0,3,12])**Video Explanation:** [https://www.youtube.com/watch?v=0rPuILjoVsg](https://www.youtube.com/watch?v=0rPuILjoVsg)
```

## 推拉窗

我们将在博客中讨论的最后一个策略是滑动窗口。类似于多指针策略，滑动窗口通常用于线性结构(即数组和字符串)。当您需要查找/跟踪遵循某种模式的输入子集时，滑动窗口非常有用。柯尔特·斯蒂尔这样描述它的工作过程:“这个模式包括创建一个窗口，它可以是一个数组，也可以是从一个位置到另一个位置的数字。根据特定条件，窗口要么增大，要么关闭(并创建一个新窗口)”(Steele)。此外，使用滑动窗口是优选的，因为它具有 O(n)时间复杂度。

现在，为了在实践中展示滑动窗口策略，让我们看一个例子。

```
**Source**: [C](https://leetcode.com/problems/valid-anagram/)olt Steele's JavaScript Algorithms and Data Structures Masterclass Course on Udemy**Problem**:Write a function called maxSubarraySum which accepts an array of integers and a number called n. the function should calculate the maximum sum of n consecutive elements in the array.Test Case #1

     **Input** = [1,2,5,2,8,1,5], n = 2
     **Output** = 10Test Case #2

     **Input** = [1,2,5,2,8,1,5], n = 4
     **Output** = 17
```

在本例中，我们将使用滑动窗口策略从数据子集中找出最大和。为此，我们将创建一个窗口，其大小由 n 决定。接下来，我们将窗口 1 的位置向右滑动，并确定该总和是否大于前面的总和。一旦最后的窗口被求和，我们将返回最大的和。

```
**Solution:****function** maxSubarraySum(arr, n){
  **let** maxSum = 0;
  **let** tempSum = 0;
  **if** (arr.length < n) return null;
  **for** (let i = 0; i < n; i++) {
    maxSum += arr[i];
  }
  tempSum = maxSum;
  **for** (let i = n; i < arr.length; i++) {
    tempSum = tempSum - arr[i - n] + arr[i];
    maxSum = Math.max(maxSum, tempSum);
  }
  **return** maxSum;
}maxSubarraySum([1,2,5,2,8,1,5],2)
maxSubarraySum([1,2,5,2,8,1,5],4)**Test Case #1 Output**:// the initial maxSum
3// sliding window, tempSum on left and previous maxSum on right
7 3
7 7
10 7
9 10
6 10// result
10**Test Case #2 Output**:// the initial maxSum
10// sliding window, tempSum on left and previous maxSum on right
17 10
16 17
16 17// result
17
```

在上面的解决方案中，我们首先声明两个变量 maxSum 和 tempSum，并将它们设置为 0。然后，我们设置一个边界条件，如果窗口的大小 n 大于数组，则返回 null。接下来，我们通过仅循环指定数量的 n 个数字并将每个数字添加到 maxSum 变量来找到第一个窗口的总和。然后，我们将 tempSum 变量设置为 maxSum 的值；临时 sum 将是我们的滑动窗口。然后在我们的第二个循环中，我们通过从我们的初始窗口(arr[0])中减去第一个值，并添加数组中不在我们的初始窗口中的下一个值(即，如果第一个窗口包含 arr[0]，arr[1]，arr[2])，来找到下一个窗口的值，并将该值设置为 tempSum 的值。然后，我们将 maxSum 的值设置为 tempSum 和先前的 maxSum 中的较大值。我们继续这个过程，直到到达数组的末尾并返回 maxSum

感谢您花时间了解更多算法求解策略。我希望这篇博客能为你提供一些策略，帮助你寻找工作和/或工作场所。

**资源**

斯蒂尔，加州(未注明)。 *JavaScript 算法和数据结构大师班*。在线课程。

算法。(2020 年 07 年 10 月)。检索于 2020 年 10 月 10 日，发自 https://en.wikipedia.org/wiki/Algorithm