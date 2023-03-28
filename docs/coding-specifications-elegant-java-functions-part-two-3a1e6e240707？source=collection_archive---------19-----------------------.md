# 编码规范|优雅的 Java 函数(第二部分)

> 原文：<https://medium.datadriveninvestor.com/coding-specifications-elegant-java-functions-part-two-3a1e6e240707?source=collection_archive---------19----------------------->

![](img/9ddfcaecc404e7a4f2a8134dbc094db7.png)

*由* [*Amap_tech 团队*](https://community.alibabacloud.com/users/5241164025409916) *。*

# 背景

本文描述了一组与 Java 函数相关的编码规则，旨在为 Java 程序员提供一些编码建议，帮助他们编写出更优雅、更高质量、更高效的代码。

参考此[链接](https://www.alibabacloud.com/blog/coding-specifications-%7C-elegant-java-functions-part-one_596181)查看本文的第一部分。

# 使用内部函数参数的基本类型

## 案例 1)尽可能使用内部函数参数的基本类型

以下代码片段显示了症状描述。

```
// 调用代码
double price = 5.1D;
int number = 9;
double total = calculate(price, number);// 计算金额函数
private double calculate(Double price, Integer number) {
    return price * number;
}
```

请参考以下推荐的解决方案。

```
// 调用代码
double price = 5.1D;
int number = 9;
double total = calculate(price, number);// 计算金额函数
private double calculate(double price, int number) {
    return price * number;
}
```

## 情况 2)尽可能对内部函数的返回值使用基本类型

以下代码片段显示了症状描述。

```
// 获取订单总额函数
public double getOrderAmount(List<Product> productList) {
    double amount = 0.0D;
    for (Product product : productList) {
        if (Objects.isNull(product) || Objects.isNull(product.getPrice())
            || Objects.isNull(product.getNumber())) {
            continue;
        }
        amount += calculate(product.getPrice(), product.getNumber());
    }
    return amount;
}// 计算金额函数
private Double calculate(double price, double number) {
    return price * number;
}
```

请参考以下推荐的解决方案。

```
// 获取订单总额函数
public double getOrderAmount(List<Product> productList) {
    double amount = 0.0D;
    for (Product product : productList) {
        if (Objects.isNull(product) || Objects.isNull(product.getPrice())
            || Objects.isNull(product.getNumber())) {
            continue;
        }
        amount += calculate(product.getPrice(), product.getNumber());
    }
    return amount;
}// 计算金额函数
private double calculate(double price, double number) {
    return price * number;
}
```

该示例仅用于说明目的。在这种情况下，最好使用流编程。

[](https://www.datadriveninvestor.com/2019/01/15/the-path-of-mobile-app-development-in-2019/) [## 2019 年移动应用开发之路|数据驱动的投资者

### 任何在移动应用程序开发行业工作的人，无论他们是专注于在伦敦开发 iOS 应用程序还是…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/15/the-path-of-mobile-app-development-in-2019/) 

## 利益

*   尽可能使用内部函数的基本类型，以避免打包和解包隐式封装类型。
*   当基本类型用于内部函数参数时，这在语法上避免了对这些参数的空指针判断。
*   当基本类型用于内部函数的返回值时，这在语法上避免了调用函数时对返回值的空指针判断。

# 避免返回空数组和列表

## 情况 1)尽可能避免空数组的返回，以避免不必要的空指针判断

以下代码片段显示了症状描述。

```
// 调用代码
UserVO[] users = queryUser();
if (Objects.nonNull(users)) {
    for (UserVO user : users) {
        // 处理用户信息
    }
}// 查询用户函数
private UserVO[] queryUser() {
    // 查询用户列表
    List<UserDO> userList = userDAO.queryAll();
    if (CollectionUtils.isEmpty(userList)) {
        return null;
    } // 转化用户数组
    UserVO[] users = new UserVO[userList.size()];
    for (int i = 0; i < userList.size(); i++) {
        UserDO user = userList.get(i);
        users[i] = new UserVO();
        users[i].setId(user.getId());
        users[i].setName(user.getName());
    } // 返回用户数组
    return users;
}
```

请参考以下推荐的解决方案。

```
// 调用代码
UserVO[] users = queryUser();
for (UserVO user : users) {
    // 处理用户信息
}// 查询用户函数
private UserVO[] queryUser() {
    // 查询用户列表
    List<UserDO> userList = userDAO.queryAll();
    if (CollectionUtils.isEmpty(userList)) {
        return new UserVO[0];
    } // 转化用户数组
    UserVO[] users = new UserVO[userList.size()];
    for (int i = 0; i < userList.size(); i++) {
        UserDO user = userList.get(i);
        users[i] = new UserVO();
        users[i].setId(user.getId());
        users[i].setName(user.getName());
    } // 返回用户数组
    return users;
}
```

## 情况 2)尽可能避免空列表的返回，以避免不必要的空指针判断

以下代码片段显示了症状描述。

```
// 调用代码
List<UserVO> userList = queryUser();
if (Objects.nonNull(userList)) {
    for (UserVO user : userList) {
        // 处理用户信息
    }
}// 查询用户函数
private List<UserVO> queryUser(){
    // 查询用户列表
    List<UserDO> userList = userDAO.queryAll();
    if(CollectionUtils.isEmpty(userList)) {
        return null;
    } // 转化用户列表
    List<UserVO> userVoList = new ArrayList<>(userList.size());
    for(UserDO user : userList) {
        UserVO userVo = new UserVO();
        userVo.setId(user.getId());
        userVo.setName(user.getName());
        userVoList.add(userVo);
    } // 返回用户列表
    return userVoList;
}
```

请参考以下推荐的解决方案。

```
// 调用代码
List<UserVO> userList = queryUser();
for (UserVO user : userList) {
   // 处理用户信息
 }// 查询用户函数
private List<UserVO> queryUser(){
    // 查询用户列表
    List<UserDO> userList = userDAO.queryAll();
    if(CollectionUtils.isEmpty(userList)) {
        return Collections.emptyList();
    } // 转化用户列表
    List<UserVO> userVoList = new ArrayList<>(userList.size());
    for(UserDO user : userList) {
        UserVO userVo = new UserVO();
        userVo.setId(user.getId());
        userVo.setName(user.getName());
        userVoList.add(userVo);
    } // 返回用户列表
    return userVoList;
}
```

## 利益

*   确保返回的数组和列表不为空，以避免空指针判断。

# 封装函数输入参数

## 情况 1)当输入太多参数时，应该将它们封装成参数类

Java 规范不允许太多的函数参数，这使得函数的维护和扩展变得很困难。

以下代码片段显示了症状描述。

```
// 修改用户函数
public void modifyUser(Long id, String name, String phone, Integer age, 
    Integer sex, String address, String description) {
    // 具体实现逻辑
}
```

请参考以下推荐的解决方案。

```
// 修改用户函数
public void modifyUser(User user) {
    // 具体实现内容
}// 用户类
@Getter
@Setter
@ToString
private class User{
    private Long id;
    private String name;
    private String phone;
    private Integer age;
    private Integer sex;
    private String address;
    private String description;
}
```

# 将组参数封装为参数类

由于参数是成组出现的，所以有必要封装一个类来描述这种情况。

以下代码片段显示了症状描述。

```
// 获取距离函数
public double getDistance(double x1, double y1, double x2, double y2) {
    // 具体实现逻辑
}
```

请参考以下推荐的解决方案。

```
// 获取距离函数
public double getDistance(Point point1, Point point2) {
    // 具体实现逻辑
}// 点类
@Getter
@Setter
@ToString
private class Point{
    private double x;
    private double y;
}
```

## 利益

*   将多个函数参数封装成类，使函数更容易扩展和维护。
*   将组功能参数封装为类，以阐明业务。

## 尽可能使用函数实现匿名内部类

Java 中匿名内部类的优缺点:在匿名内部类(包括 Lambda 表达式)中，你可能直接访问外部类的成员，包括类的成员变量和函数的内部变量。在这种情况下，由于你随意访问外部变量，代码的边界就不清楚了。

我们建议使用 Lambda 表达式来简化匿名内部类，然后使用函数来实现复杂的 Lambda 表达式。

## 案例 1)尽可能使用函数实现匿名内部类(包括 Lambda 表达式)

以下代码片段显示了症状描述。

```
// 发送结算数据
sendWorkerSettleData(WorkerPushDataType.CHECKER, () -> {
    Date beginDate = DateUtils.addDays(currDate, -aheadDays);
    Date endDate = DateUtils.addDays(currDate, 1);
    return auditTaskDAO.statCheckerSettleData(beginDate, endDate);
});
```

请参考以下推荐的解决方案。

```
// 发送结算数据
sendWorkerSettleData(WorkerPushDataType.CHECKER, () -> statCheckerSettleData(currDate, aheadDays));// 统计验收员结算数据函数
private List<WorkerSettleData> statCheckerSettleData(Date currDate, int aheadDays) {
    Date beginDate = DateUtils.addDays(currDate, -aheadDays);
    Date endDate = DateUtils.addDays(currDate, 1);
    return auditTaskDAO.statCheckerSettleData(beginDate, endDate);
}
```

其实还有一个更简单的方法。要在调用`sendWorkerSettleData`函数(将数据发送给操作员进行结算)之前计算开始日期和结束日期，请使用函数`auditTaskDAO.statCheckerSettleData` (beginDate，end date)而不是匿名内部类。

## 情况 2)将复杂的匿名内部类实现 API 拆分成多个函数类 API

如果由匿名内部类实现的 API 的函数相互之间的相关性较低，则将 API 拆分成几个函数 API，以便于使用 Lambda 表达式。

以下代码片段显示了症状描述。

```
// 清除过期数据
cleanExpiredData("用户日志表", new CleanExpiredDataOperator() {
    @Override
    public List<Date> queryExpiredDate(Integer remainDays) {
        return userDAO.queryExpiredDate(remainDays);
    }
    @Override
    public void cleanExpiredData(Date expiredDate) {
        userDAO.cleanExpiredData(expiredDate);
    }
});// 清除过期数据函数
private void cleanExpiredData(String tableName, CleanExpiredDataOperator ,
cleanExpiredDataOperator) {
    // 功能实现代码
}// 清除过期操作接口
interface CleanExpiredDataOperator {
    // 查询过期日期
    public List<Date> queryExpiredDate(Integer remainDays);
    // 清除过期数据
    public void cleanExpiredData(Date expiredDate);
}
```

请参考以下推荐的解决方案。

```
// 清除过期数据
cleanExpiredData("用户日志表", userDAO::queryExpiredDate,userDAO::cleanExpiredData);// 清除过期数据函数
private void cleanExpiredData(String tableName, QueryExpiredDateOperator queryExpiredDateOperator, CleanExpiredDataOperator cleanExpiredDataOperator) {
    // 功能实现代码
}// 查询过期日期接口
interface QueryExpiredDateOperator {
    // 查询过期日期
    public List<Date> queryExpiredDate(Integer remainDays);
}// 清除过期操作接口
interface CleanExpiredDataOperator {
    // 清除过期数据
    public void cleanExpiredData(Date expiredDate);
}
```

## 利益

*   定义函数并指定参数，以明确匿名内部类的代码边界。
*   使用 Lambda 表达式来简化匿名内部类的实现并简化代码。

# 使用 return 移除不必要的代码

## 案例 1)删除不必要的“如果”

以下代码片段显示了症状描述。

```
// 是否通过函数
public boolean isPassed(Double passRate) {
    if (Objects.nonNull(passRate) && passRate.compareTo(PASS_THRESHOLD) >= 0) {
        return true;
    }
    return false;
}
```

请参考以下推荐的解决方案。

```
// 是否通过函数
public boolean isPassed(Double passRate) {
    return Objects.nonNull(passRate) && passRate.compareTo(PASS_THRESHOLD) >= 0;
}
```

## 情况 2)删除不必要的“别人的”

以下代码片段显示了症状描述。

```
// 结算工资函数
public double settleSalary(Long workId, int workDays) {
    // 根据是否合格处理
    if (isQualified(workId)) {
        return settleQualifiedSalary(workDays);
    } else {
        return settleUnqualifiedSalary(workDays);
    }
}
```

请参考以下推荐的解决方案。

```
// 结算工资函数
public double settleSalary(Long workId, int workDays) {
    // 根据是否合格处理
    if (isQualified(workId)) {
        return settleQualifiedSalary(workDays);
    }
    return settleUnqualifiedSalary(workDays);
}
```

## 情况 3)删除不必要的变量

以下代码片段显示了症状描述。

```
// 查询用户函数
public List<UserDO> queryUser(Long id, String name) {
    UserQuery userQuery = new UserQuery();
    userQuery.setId(id);
    userQuery.setName(name);
    List<UserDO> userList = userDAO.query(userQuery);
    return userList;
}
```

请参考以下推荐的解决方案。

```
// 查询用户函数
public List<UserDO> queryUser(Long id, String name) {
    UserQuery userQuery = new UserQuery();
    userQuery.setId(id);
    userQuery.setName(name);
    return userDAO.query(userQuery);
}
```

## 利益

*   删除不必要的代码行，以获得更精简、更方便的代码。

# 使用临时变量来优化代码

在一些代码段中，你经常会看到`a.getB().getC()...getN()`语法。这被称为级联函数调用，会导致代码健壮性和可读性较差。我们建议您不要执行级联函数调用。相反，使用临时变量来拆分调用并对对象执行空指针检查。

## 案例 1)使用临时变量来阐明逻辑

以下代码片段显示了症状描述。

```
// 是否土豪用户函数
private boolean isRichUser(User user) {
    return Objects.nonNull(user.getAccount())
        && Objects.nonNull(user.getAccount().getBalance())
        && user.getAccount().getBalance().compareTo(RICH_THRESHOLD) >= 0;
}
```

这是一种简化代码控制的简单方法，但是可读性很差。

请参考以下推荐的解决方案。

```
// 是否土豪用户函数
private boolean isRichUser(User user) {
    // 获取用户账户
    UserAccount account = user.getAccount();
    if (Objects.isNull(account)) {
        return false;
    } // 获取用户余额
    Double balance = account.getBalance();
    if (Objects.isNull(balance)) {
        return false;
    } // 比较用户余额
    return balance.compareTo(RICH_THRESHOLD) >= 0;
}
```

这个解决方案增加了代码行，但是澄清了逻辑。当你发现很难平衡简单性和可读性时，我们建议更多地权衡可读性。

## 情况 2)使用临时变量来简化代码

以下代码片段显示了症状描述。

```
// 构建用户函数
public UserVO buildUser(UserDO user) {
    UserVO vo = new UserVO();
    vo.setId(user.getId());
    vo.setName(user.getName());
    if (Objects.nonNull(user.getAccount())) {
        vo.setBalance(user.getAccount().getBalance());
        vo.setDebt(user.getAccount().getDebt());
    }
    return vo;
}
```

这样写代码是为了减少临时变量。

请参考以下推荐的解决方案。

```
// 构建用户函数
public UserVO buildUser1(UserDO user) {
    UserVO vo = new UserVO();
    vo.setId(user.getId());
    vo.setName(user.getName());
    UserAccount account = user.getAccount();
    if (Objects.nonNull(account)) {
        vo.setBalance(account.getBalance());
        vo.setDebt(account.getDebt());
    }
    return vo;
}
```

## 利益

*   使用临时变量来阐明业务逻辑。
*   使用临时变量来简化代码。变量名表明了它的用途，避免了大量无用的代码。
*   如果检索函数很复杂很耗时，使用临时变量来提高运行效率。
*   使用临时变量来避免级联函数调用，并防止空指针异常。

# 仅保留函数所需的参数

在一些代码段中，你经常会看到`a.getB().getC()...getN()`语法。这被称为级联函数调用，会导致代码健壮性和可读性较差。我们建议您不要执行级联函数调用。相反，使用临时变量来拆分调用并对对象执行空指针检查。

## 情况 1)删除冗余参数

以下代码片段显示了症状描述。

```
// 修改用户状态函数
private void modifyUserStatus(Long userId, Integer status, String unused) {
    userCache.modifyStatus(userId, status);
    userDAO.modifyStatus(userId, status);
}
其中，unused 参数是无用参数。建议方案：// 修改用户状态函数
private void modifyUserStatus(Long userId, Integer status) {
    userCache.modifyStatus(userId, status);
    userDAO.modifyStatus(userId, status);
}
```

## 情况 2)用属性替换对象

以下代码片段显示了症状描述。

```
// 删除用户函数
private void deleteUser(User user) {
    userCache.delete(user.getId());
    userDAO.delete(user.getId());
}
```

请参考以下推荐的解决方案。

```
// 删除用户函数
private void deleteUser(Long userId) {
    userCache.delete(userId);
    userDAO.delete(userId);
}
```

当调用一个函数时，不需要构建一个专用的参数对象。当一个函数使用三个以上的属性时，您不需要应用这个规则。

## 利益

只保留函数需要的参数，以明确在调用过程中需要赋值的参数，避免在调用过程中构造无用的参数。

# 附言

如果你有更好的建议或者更好的代码案例，我们欢迎你的输入。我们希望这篇文章可以作为参考，有助于形成一套完整的 Java 编码规范。

# 原始来源:

[](https://www.alibabacloud.com/blog/coding-specifications-%7C-elegant-java-functions-part-two_596182) [## 编码规范|优雅的 Java 函数(第二部分)

### 本文描述了一组与 Java 函数相关的编码规则，旨在…

www.alibabacloud.com](https://www.alibabacloud.com/blog/coding-specifications-%7C-elegant-java-functions-part-two_596182) 

**进入专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)