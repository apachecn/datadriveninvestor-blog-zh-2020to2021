# 使用 Javascript 创建单链表

> 原文：<https://medium.datadriveninvestor.com/create-singly-linked-lists-using-javascript-29c77b0557ad?source=collection_archive---------8----------------------->

![](img/c2deb2e815b3c23fd82723c74be096f0.png)

Photo by [Anika Huizinga](https://unsplash.com/@iam_anih?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

链表是一种数据结构，包含一个**头**、**尾**和**长度**属性。链表由节点组成，每个节点都有一个值和一个指向另一个节点或 null 的指针。

当我们比较链表和数组时，最大的区别就是链表没有索引。链表通过带有下一个**指针**的节点连接，这意味着不允许随机访问。为了做到这一点，我们必须遍历链接。链表擅长**插入**和**删除**。与数组不同，链表在插入或删除元素时不需要重新分配索引。

在这一课中，我将向你展示如何使用 Javascript 编写链表的插入和删除方法。

# 推

记住，链表是链接节点的集合，所以我们可以通过在链表的末尾添加一个新节点来将一个元素推送到链表中！

所以让我们从为每个节点定义一个类开始。一个节点很简单。它需要一段数据(**值**)和对下一个节点的引用( **next** )。

```
Class Node {
      constructor (val) {
          this.val = val;
          this.next = null;
//at the beginning nothing comes after val }}
```

然后，我们定义自己的 sinlyLinkedList 类来利用 node 类。我们初始化新创建的链表的头、尾和长度。

```
Class singlyLinkedList {
      constructor () {
          this.head = null;
          this.tail = null;
          this.length = 0; }
//here, we are going to define the push method}
```

## 推送伪代码

*   这个函数应该接受一个值
*   使用传递给函数的值创建一个新节点
*   如果列表中没有 head 属性，则将 head 和 tail 设置为新创建的节点
*   否则，将尾部的下一个属性设置为新节点，并将列表的尾部属性设置为新创建的节点
*   将长度增加一
*   返回链表

这是代码！

```
Class singlyLinkedList {
      constructor () {
          this.head = null;
          this.tail = null;
          this.length = 0;}
      push(val) { var newNode =new Node(val); //implementing the node class we created before
           if(!this.head) {
             this.head = new Node;
             this.tail = this.head; } else {
             this.tail.next = newNode;
             this.tail = newNode; }
           this.length++;
           return this; }}
```

# 间歇的

我们从链表的末尾移除一个**节点**！这比 pushing 方法稍微复杂一点，因为单链表没有向后指针。我们必须遍历列表。

## 弹出伪代码

*   如果列表中没有节点，返回 undefined
*   循环遍历列表，直到到达末尾
*   将第二个到最后一个节点的 next 属性设置为 null
*   将尾部设置为倒数第二个节点
*   将列表长度减 1
*   返回被删除节点的值

我们将在 singlyLinkedList 类中编写 pop 方法。

```
pop(val) { if(!this.head) return undefined;
   var current = this.head;
   var newTail = current;
   while(current.next){
        newTail = current;
        current = current.next; }
   this.tail = newTail;
   thils.tail.next = null;
   this.length--;//when there is one item left in the link, we have to set the head and tail to be null after popping if(this.length === 0) {
     this.head = null;
     this.tail = null; } return current;}
```