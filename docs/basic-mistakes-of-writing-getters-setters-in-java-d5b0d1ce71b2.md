# 用 Java 编写 getter/setter 的基本错误

> 原文：<https://medium.datadriveninvestor.com/basic-mistakes-of-writing-getters-setters-in-java-d5b0d1ce71b2?source=collection_archive---------2----------------------->

这篇博客最初发表在我的博客@linqz.io [这里](https://www.linqz.io/2019/04/basic-mistakes-of-writing-getters-setters-in-java.html)。

![](img/d3fe083a39a9be7bed2c9da68d34254a.png)

嗯，看完标题，首先想到的是“**Java 中有 Getter/Setter 的指导方针吗？**”。

答案是“**不，没有**，这个博客条目是我在过去 10 年的编码过程中犯下的错误(或者很多时候人们称之为“体验”:D)”。

所以让我们开始吧，我不会深入到面向对象编程的什么、为什么、如何等等的细节，以及 getter/setter 适合在哪里，但是如果你谷歌一下，你会找到关于这些主题的详细解释。

## 错误 1:是**将对象引用直接**分配到业务对象的 S **信中。**

例如:考虑一个 Employee 类，它有一个包含 employeeIds 的 int[]数组，并为其编码了一个默认的 setter。假设下面的代码是用某种方法编写的:

```
.....Some business code...
.....Some business code...int[] employeeIds= {5001, 5002, 4002, 3002, 2004, 9874};employeeObj.setEmployeeIds(employeeIds);
.....
**employeeIds[1] = 1; // setting the value 1 resets the value of employeeObj** **employeeIds array index 1’s value from 5002 to 1.**
.....
```

因此，我总是建议像下面这样编写 setter:

```
public void setEmployeeIds(int[] ids) 
{
  **this.employeeIds = new int[ids.length];
  System.arraycopy(ids, 0, this.employeeIds, 0, ids.length);**
}
```

## 错误 2:对于业务对象，直接从 G **返回对象引用**更好。

假设在业务逻辑的某个地方，代码如下:

```
.....Some business code...
// lets say employee Obj has these Ids= {5001, 6002, 4002, 3002};
.....Some business code...**int[] employeeIds= employeeObj.getEmployeeIds();**
.....
**employeeIds[1] = 891; // setting the value 1 resets the value of employeeIds array index 1’s value from 6002 to 891.**
.....
```

因此，要解决上述问题，我建议编写如下的 getter:

```
public int[] getEmployeeIds() 
{
  **int len = this.employeeIds.length;
**  **int[] copyIds = new int[len];
  System.arraycopy(this.employeeIds, 0, copyIds, 0, len);
  return copyIds;** 
}
```

## 第三个错误。为可变 Java 数据类型编写 **Getter/Setter，例如 java.util. **Date。**或**日历等。****

Java 有一些**可变的**数据类型，如日期、日历等，如果任何一个使用 get 方法或使用 reference 方法重置该值，这在调试时会成为一个巨大的可维护性问题(使用方法引用进行搜索可能会变成一个非常棘手的任务)。

[](https://www.datadriveninvestor.com/2020/01/16/software-development-process-how-to-pick-the-right-process/) [## 软件开发过程:如何选择正确的过程？数据驱动的投资者

### 软件是任何企业组织成功的生命线。没有软件的帮助，一个…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/01/16/software-development-process-how-to-pick-the-right-process/) 

因此，我总是建议总是使用防御性副本(即深度克隆)来编写 getter 和 setter。

```
public void **setDateOfJoining**(Date date) 
{
  **this.dateOfJoining = (Date) date.clone();**
}public Date **getDateOfJoining**() 
{
  **return (Date) this.dateOfJoining.clone();**
}
```

## 错误 4: **业务对象集合的 Getter/Setter。**

第三个错误指出了 java 可变数据类型的克隆，这也适用于可变业务对象或可变对象集合。

假设每个雇员都参与多个项目，那么在每个 employee 对象中，我们保存一个项目列表，记住上面的内容，总是返回一个副本，我们编写 getter/setter 如下:

```
private List<Project> projectList;public void setProjectList(List<Project> list)
{
  this.projectList = new ArrayList<Project>(list);
}public List<Project> getProjectList()
{
  return new ArrayList<Project>(this.projectList);
}
```

但是有一个缺陷可以暴露如下:

```
...In some business method...
...some business Code ...**List<Project> list1 = new ArrayList<>();
list1.add(new Project("Government Project 1"));
list1.add(new Project("Internal Project #20"));
list1.add(new Project("Self Project #12"));**employeeObj.setProjectList(list1);

**list1.get(2).setProjectName("Dummy Wrong Project"); // This line sets wrong project name since new collection is pointing to same Project object.**
```

因此，为了避免上述错误，请始终使用深度克隆来实现克隆方法，如下所示:

```
public Object clone() 
{
  **Project cloneProject = new Project(this.projectName);
  ....
  ....** **return cloneProject;**
}
```

在员工课堂上

```
public void setProjectList(List<Project> list) 
{
  for (Project project: list) 
  {
    this.projectList.add(**(Project) project.clone()**);
  }
}public List<Project> getProjectList() 
{
  List<Project> listReturn = new ArrayList<>();
  for (Project project: this.projectList) 
  {
    listReturn.add(**(Project) project.clone()**);
  }
  return listReturn;
}
```

## 错误 5 : Getter/Setter 是私有作用域所必需的，如果是为公共作用域变量提供的话，它们几乎是无用的。

这是不言自明的，这种错误很少发生，但需要小心。

如果你喜欢这个博客内容，请考虑买一杯咖啡。谢谢大家的支持！

[![](img/7b3b86e7b1337900b3557fda835b6ad3.png)](http://buymeacoff.ee/cyby0109)

有问题吗？建议？评论？

下一步是什么？ [**在 Medium 上关注我**](https://medium.com/@vaibhav0109) 成为第一个阅读我的故事的人。