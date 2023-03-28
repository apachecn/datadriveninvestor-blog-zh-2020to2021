# 编码规范|优雅的 Java 函数(第一部分)

> 原文：<https://medium.datadriveninvestor.com/coding-specifications-elegant-java-functions-part-one-dd6bcb01983b?source=collection_archive---------14----------------------->

![](img/1b9b8fa4e78a8abe93a8ab6db39c8570.png)

*由* [*Amap_tech 团队*](https://community.alibabacloud.com/users/5241164025409916) *。*

# 介绍

随着软件项目代码的不断积累，系统维护成本也在上升。这个问题在所有软件团队中都很普遍。不断优化和提高代码质量是提高系统活力的一个很好的方法。此外，正如开发人员中流行的说法:多思考，无代码。所以我们在编程的时候需要多思考，努力提高自己的编码技能。这样，我们可以产生更优雅、更高质量、更高效的代码。

本文将描述一组与 Java 函数相关的编码规则。我们希望能给 Java 程序员一些编码建议，帮助他们制作出具有前述亮点的代码。Amap 数据收集部门将这些规则付诸实践，取得了很好的效果。

[](https://www.datadriveninvestor.com/2019/01/15/the-path-of-mobile-app-development-in-2019/) [## 2019 年移动应用开发之路|数据驱动的投资者

### 任何在移动应用程序开发行业工作的人，无论他们是专注于在伦敦开发 iOS 应用程序还是…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2019/01/15/the-path-of-mobile-app-development-in-2019/) 

# 使用通用工具功能

## 案例 1

以下代码片段显示了症状描述。

**不完整代码**

```
thisName != null && thisName.equals(name);
```

**更完整的代码**

```
(thisName == name) || (thisName != null && thisName.equals(name));
```

请参考以下推荐的解决方案。

```
Objects.equals(name, thisName);
```

## 案例 2

以下代码片段显示了症状描述。

```
!(list == null || list.isEmpty());
```

请参考以下推荐的解决方案。

```
import org.apache.commons.collections4.CollectionUtils;
CollectionUtils.isNotEmpty(list);
```

## 利益

*   函数式编程减少了业务代码的数量，直观地显示了逻辑。
*   通用工具功能允许我们仔细考虑逻辑并减少出错的可能性。

# 拆分大型函数

当一个函数的代码超过 80 行时，它就是一个大函数，因此需要拆分。

## 情况 1)每个代码块必须封装成一个函数

每个代码块都必须包含注释来解释其功能。如果代码块前面有注释行，它允许用函数替换代码，并根据注释命名函数。如果一个函数有一个描述性的名字，就很容易直接更新，而不必检查内部代码是如何实现的。

以下代码片段显示了症状描述。

```
// 每日生活函数
public void liveDaily() {
    // 吃饭
    // 吃饭相关代码几十行 // 编码
    // 编码相关代码几十行 // 睡觉
    // 睡觉相关代码几十行
}
```

请参考以下推荐的解决方案。

```
// 每日生活函数
public void liveDaily() {
    // 吃饭
    eat(); // 编码
    code(); // 睡觉
    sleep();
}// 吃饭函数
private void eat() {
    // 吃饭相关代码
}// 编码函数
private void code() {
    // 编码相关代码
}// 睡觉函数
private void sleep() {
    // 睡觉相关代码
}
```

## 情况 2)每个循环体必须封装成一个函数

以下代码片段显示了症状描述。

```
// 生活函数
public void live() {
    while (isAlive) {
        // 吃饭
        eat(); // 编码
        code(); // 睡觉
        sleep();
    }
}
```

请参考以下推荐的解决方案。

```
// 生活函数
public void live() {
    while (isAlive) {
        // 每日生活
        liveDaily();
    }
}// 每日生活函数
private void liveDaily() {
    // 吃饭
    eat(); // 编码
    code(); // 睡觉
    sleep();
}
```

## 情况 3)每个条件体必须封装为一个函数

以下代码片段显示了症状描述。

```
// 外出函数
public void goOut() {
    // 判断是否周末
    // 判断是否周末: 是周末则游玩
    if (isWeekday()) {
        // 游玩代码几十行
    }
    // 判断是否周末: 非周末则工作
    else {
        // 工作代码几十行
    }
}
```

请参考以下推荐的解决方案。

```
// 外出函数
public void goOut() {
    // 判断是否周末
    // 判断是否周末: 是周末则游玩
    if (isWeekday()) {
        play();
    }
    // 判断是否周末: 非周末则工作
    else {
        work();
    }
}// 游玩函数
private void play() {
    // 游玩代码几十行
}// 工作函数
private void work() {
    // 工作代码几十行
}
```

## 利益

*   功能越短，功能越简单，生命周期越长。
*   一个函数越长，就越难理解和维护。在这种情况下，维护人员会尽可能不修改它。
*   长函数通常包含难以定位的重复代码。

# 在同一函数中保持代码块级别一致

## 案例 1

以下代码片段显示了症状描述。

```
// 每日生活函数
public void liveDaily() {
    // 吃饭
    eat(); // 编码
    code(); // 睡觉
    // 睡觉相关代码几十行
}
```

如你所见，睡眠代码块和吃饭代码不是一个级别的，比较奇怪。如果你把写代码比作写一篇短文，那么吃饭和写代码就是一个段落的主要思想，而睡觉是一个详细的段落。对于 LiveDaily 功能，你只需要写出主要的流程，也就是段落的思路。

请参考以下推荐的解决方案。

```
public void liveDaily() {
    // 吃饭
    eat(); // 编码
    code(); // 睡觉
    sleep();
}// 睡觉
private void sleep() {
    // 睡觉相关代码
}
```

## 利益

*   函数调用表明它们的目的，而函数实现表达式逻辑。为了便于理解，逻辑清楚地按层次排列。
*   函数中的代码块不必是分层的，因为这会使函数看起来头重脚轻。

# 将相同的功能代码封装为一个函数

## 情况 1)将相同的代码封装为一个函数

以下代码片段显示了症状描述。

```
// 禁用用户函数
public void disableUser() {
    // 禁用黑名单用户
    List<Long> userIdList = queryBlackUser();
    for (Long userId : userIdList) {
        User userUpdate = new User();
        userUpdate.setId(userId);
        userUpdate.setEnable(Boolean.FALSE);
        userDAO.update(userUpdate);
    } // 禁用过期用户
    userIdList = queryExpiredUser();
    for (Long userId : userIdList) {
        User userUpdate = new User();
        userUpdate.setId(userId);
        userUpdate.setEnable(Boolean.FALSE);
        userDAO.update(userUpdate);
    }
}
```

请参考以下推荐的解决方案。

```
// 禁用用户函数
public void disableUser() {
    // 禁用黑名单用户
    List<Long> userIdList = queryBlackUser();
    for (Long userId : userIdList) {
        disableUser(userId);
    } // 禁用过期用户
    userIdList = queryExpiredUser();
    for (Long userId : userIdList) {
        disableUser(userId);
    }
}// 禁用用户函数
private void disableUser(Long userId) {
    User userUpdate = new User();
    userUpdate.setId(userId);
    userUpdate.setEnable(Boolean.FALSE);
    userDAO.update(userUpdate);
}
```

## 情况 2)将类似的代码封装成一个函数

将相似的代码封装成一个函数，不同之处由函数参数控制。

以下代码片段显示了症状描述。

```
// 通过工单函数
public void adoptOrder(Long orderId) {
    Order orderUpdate = new Order();
    orderUpdate.setId(orderId);
    orderUpdate.setStatus(OrderStatus.ADOPTED);
    orderUpdate.setAuditTime(new Date());
    orderDAO.update(orderUpdate);
}// 驳回工单函数
public void rejectOrder(Long orderId) {
    Order orderUpdate = new Order();
    orderUpdate.setId(orderId);
    orderUpdate.setStatus(OrderStatus.REJECTED);
    orderUpdate.setAuditTime(new Date());
    orderDAO.update(orderUpdate);
}
```

请参考以下推荐的解决方案。

```
// 通过工单函数
public void adoptOrder(Long orderId) {
    auditOrder(orderId, OrderStatus.ADOPTED);
}// 驳回工单函数
public void rejectOrder(Long orderId) {
    auditOrder(orderId, OrderStatus.REJECTED);
}// 审核工单函数
private void auditOrder(Long orderId, OrderStatus orderStatus) {
    Order orderUpdate = new Order();
    orderUpdate.setId(orderId);
    orderUpdate.setStatus(orderStatus);
    orderUpdate.setAuditTime(new Date());
    orderDAO.update(orderUpdate);
}
```

## 利益

*   封装常用函数，减少代码行数，提高代码质量。
*   封装常用功能以细化业务代码，使其更易于理解和维护。

## 封装获取参数值的函数

## 案例 1

以下代码片段显示了症状描述。

```
// 是否通过函数
public boolean isPassed(Long userId) {
    // 获取通过阈值
    double thisPassThreshold = PASS_THRESHOLD;
    if (Objects.nonNull(passThreshold)) {
        thisPassThreshold = passThreshold;
    } // 获取通过率
    double passRate = getPassRate(userId); // 判读是否通过
    return passRate >= thisPassThreshold;
}
```

请参考以下推荐的解决方案。

```
// 是否通过函数
public boolean isPassed(Long userId) {
    // 获取通过阈值
    double thisPassThreshold = getPassThreshold(); // 获取通过率
    double passRate = getPassRate(userId); // 判读是否通过
    return passRate >= thisPassThreshold;
}// 获取通过阈值函数
private double getPassThreshold() {
    if (Objects.nonNull(passThreshold)) {
        return passThreshold;
    }
    return PASS_THRESHOLD;
}
```

## 利益

*   参数值独立地从业务功能中获得，阐明了业务逻辑。
*   封装的 GET 参数值函数是一个独立的函数，可以在代码中重用。

# 通过基于参数的 API 封装相同的逻辑

## 案例 1

以下代码片段显示了症状描述。

```
// 发送审核员结算数据函数
public void sendAuditorSettleData() {
    List<WorkerSettleData> settleDataList = auditTaskDAO.statAuditorSettleData();
    for (WorkerSettleData settleData : settleDataList) {
        WorkerPushData pushData = new WorkerPushData();
        pushData.setId(settleData.getWorkerId());
        pushData.setType(WorkerPushDataType.AUDITOR);
        pushData.setData(settleData);
        pushService.push(pushData);
    }
}// 发送验收员结算数据函数
public void sendCheckerSettleData() {
    List<WorkerSettleData> settleDataList = auditTaskDAO.statCheckerSettleData();
    for (WorkerSettleData settleData : settleDataList) {
        WorkerPushData pushData = new WorkerPushData();
        pushData.setId(settleData.getWorkerId());
        pushData.setType(WorkerPushDataType.CHECKER);
        pushData.setData(settleData);
        pushService.push(pushData);
    }
```

请参考以下推荐的解决方案。

```
// 发送审核员结算数据函数
public void sendAuditorSettleData() {
    sendWorkerSettleData(WorkerPushDataType.AUDITOR, () -> auditTaskDAO.statAuditorSettleData());
}// 发送验收员结算数据函数
public void sendCheckerSettleData() {
    sendWorkerSettleData(WorkerPushDataType.CHECKER, () -> auditTaskDAO.statCheckerSettleData());
}// 发送作业员结算数据函数
public void sendWorkerSettleData(WorkerPushDataType dataType, WorkerSettleDataProvider dataProvider) {
    List<WorkerSettleData> settleDataList = dataProvider.statWorkerSettleData();
    for (WorkerSettleData settleData : settleDataList) {
        WorkerPushData pushData = new WorkerPushData();
        pushData.setId(settleData.getWorkerId());
        pushData.setType(dataType);
        pushData.setData(settleData);
        pushService.push(pushData);
    }
}// 作业员结算数据提供者接口
private interface WorkerSettleDataProvider {
    // 统计作业员结算数据
    public List<WorkerSettleData> statWorkerSettleData();
}
```

## 利益

*   从各种业务功能中提取核心逻辑，明确业务代码，更易于维护。
*   避免重复编写相同的代码。功能越复杂，好处越大。

# 减少功能代码级别的数量

为了实现优雅的功能，我们建议将代码级别的数量保持在 1 到 4 之间。过多的缩进使得函数难以阅读。

## 情况 1)使用 return 提前检索一个函数

以下代码片段显示了症状描述。

```
// 获取用户余额函数
public Double getUserBalance(Long userId) {
    User user = getUser(userId);
    if (Objects.nonNull(user)) {
        UserAccount account = user.getAccount();
        if (Objects.nonNull(account)) {
            return account.getBalance();
        }
    }
    return null;
}
```

请参考以下推荐的解决方案。

```
// 获取用户余额函数
public Double getUserBalance(Long userId) {
    // 获取用户信息
    User user = getUser(userId);
    if (Objects.isNull(user)) {
        return null;
    } // 获取用户账户
    UserAccount account = user.getAccount();
    if (Objects.isNull(account)) {
        return null;
    } // 返回账户余额
    return account.getBalance();
}
```

## 情况 2)使用 continue 提前终止循环

以下代码片段显示了症状描述。

```
// 获取合计余额函数
public double getTotalBalance(List<User> userList) {
    // 初始合计余额
    double totalBalance = 0.0D; // 依次累加余额
    for (User user : userList) {
        // 获取用户账户
        UserAccount account = user.getAccount();
        if (Objects.nonNull(account)) {
            // 累加用户余额
            Double balance = account.getBalance();
            if (Objects.nonNull(balance)) {
                totalBalance += balance;
            }
        }
    } // 返回合计余额
    return totalBalance;
}
```

请参考以下推荐的解决方案。

```
// 获取合计余额函数
public double getTotalBalance(List<User> userList) {
    // 初始合计余额
    double totalBalance = 0.0D; // 依次累加余额
    for (User user : userList) {
        // 获取用户账户
        UserAccount account = user.getAccount();
        if (Objects.isNull(account)) {
            continue;
        } // 累加用户余额
        Double balance = account.getBalance();
        if (Objects.nonNull(balance)) {
            totalBalance += balance;
        }
    } // 返回合计余额
    return totalBalance;
}
```

**注释**

**其他方法:**在循环体中，调用例 1 中的 getUserBalance 函数，获取用户余额，然后计算累计余额。

在循环体中，我们建议只使用 continue 一次。如果您想多次使用 continue，我们建议您将循环体封装为一个函数。

## 情况 3)使用条件表达式函数来减少级别的数量

有关更多信息，请参见下一节中的“案例 2:将复杂的条件表达式封装为函数”。

## 利益

*   减少代码级别数和代码缩进量。
*   模块划分清晰，便于阅读和维护。

# 封装条件表达式函数

## 情况 1)将简单条件表达式封装为函数

以下代码片段显示了症状描述。

```
// 获取门票价格函数
public double getTicketPrice(Date currDate) {
    if (Objects.nonNull(currDate) && currDate.after(DISCOUNT_BEGIN_DATE)
        && currDate.before(DISCOUNT_END_DATE)) {
        return TICKET_PRICE * DISCOUNT_RATE;
    }
    return TICKET_PRICE;
}
```

请参考以下推荐的解决方案。

```
// 获取门票价格函数
public double getTicketPrice(Date currDate) {
    if (isDiscountDate(currDate)) {
        return TICKET_PRICE * DISCOUNT_RATE;
    }
    return TICKET_PRICE;
}// 是否折扣日期函数
private static boolean isDiscountDate(Date currDate) {
    return Objects.nonNull(currDate) && 
currDate.after(DISCOUNT_BEGIN_DATE)
        && currDate.before(DISCOUNT_END_DATE);
}
```

## 情况 2)将复杂条件表达式封装为函数

以下代码片段显示了症状描述。

```
// 获取土豪用户列表
public List<User> getRichUserList(List<User> userList) {
    // 初始土豪用户列表
    List<User> richUserList = new ArrayList<>(); // 依次查找土豪用户
    for (User user : userList) {
        // 获取用户账户
        UserAccount account = user.getAccount();
        if (Objects.nonNull(account)) {
            // 判断用户余额
            Double balance = account.getBalance();
            if (Objects.nonNull(balance) && balance.compareTo(RICH_THRESHOLD) >= 0) {
                // 添加土豪用户
                richUserList.add(user);
            }
        }
    } // 返回土豪用户列表
    return richUserList;
}
```

请参考以下推荐的解决方案。

```
// 获取土豪用户列表
public List<User> getRichUserList(List<User> userList) {
    // 初始土豪用户列表
    List<User> richUserList = new ArrayList<>(); // 依次查找土豪用户
    for (User user : userList) {
        // 判断土豪用户
        if (isRichUser(user)) {
            // 添加土豪用户
            richUserList.add(user);
        }
    } // 返回土豪用户列表
    return richUserList;
}// 是否土豪用户
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

也可以通过使用流编程来过滤前面的代码。

## 利益

*   条件表达式独立于业务函数，阐明业务逻辑。
*   封装的条件表达式是一个独立的函数，可以在代码中重用。

# 避免不必要的空指针判断

本节仅适用于您熟悉的内部项目代码。它演示了如何避免不必要的空指针判断。对于第三方中间件和系统 API，空指针判断是确保代码健壮性的必要条件。

## 情况 1)调用一个函数来确保参数不为空，以避免不必要的空指针判断

以下代码片段显示了症状描述。

```
// 创建用户信息
User user = new User();
... // 赋值用户相关信息
createUser(user);// 创建用户函数
private void createUser(User user){
    // 判断用户为空
    if(Objects.isNull(user)) {
        return;
    } // 创建用户信息
    userDAO.insert(user);
    userRedis.save(user);
}
```

请参考以下推荐的解决方案。

```
// 创建用户信息
User user = new User();
... // 赋值用户相关信息
createUser(user);// 创建用户函数
private void createUser(User user){
    // 创建用户信息
    userDAO.insert(user);
    userRedis.save(user);
}
```

## 情况 2)被调用的函数确保响应不为空，以避免不必要的空指针判断

以下代码片段显示了症状描述。

```
// 保存用户函数
public void saveUser(Long id, String name) {
    // 构建用户信息
    User user = buildUser(id, name);
    if (Objects.isNull(user)) {
        throw new BizRuntimeException("构建用户信息为空");
    } // 保存用户信息
    userDAO.insert(user);
    userRedis.save(user);
}// 构建用户函数
private User buildUser(Long id, String name) {
    User user = new User();
    user.setId(id);
    user.setName(name);
    return user;
}
```

请参考以下推荐的解决方案。

```
// 保存用户函数
public void saveUser(Long id, String name) {
    // 构建用户信息
    User user = buildUser(id, name); // 保存用户信息
    userDAO.insert(user);
    userRedis.save(user);
}// 构建用户函数
private User buildUser(Long id, String name) {
    User user = new User();
    user.setId(id);
    user.setName(name);
    return user;
}
```

## 情况 3)值分配逻辑确保列表中的数据不为空，以避免不必要的空指针判断

以下代码片段显示了症状描述。

```
// 查询用户列表
List<UserDO> userList = userDAO.queryAll();
if (CollectionUtils.isEmpty(userList)) {
    return;
}// 转化用户列表
List<UserVO> userVoList = new ArrayList<>(userList.size());
for (UserDO user : userList) {
    UserVO userVo = new UserVO();
    userVo.setId(user.getId());
    userVo.setName(user.getName());
    userVoList.add(userVo);
}// 依次处理用户
for (UserVO userVo : userVoList) {
    // 判断用户为空
    if (Objects.isNull(userVo)) {
        continue;
    } // 处理相关逻辑
    ...
}
```

请参考以下推荐的解决方案。

```
// 查询用户列表
List<UserDO> userList = userDAO.queryAll();
if (CollectionUtils.isEmpty(userList)) {
    return;
}// 转化用户列表
List<UserVO> userVoList = new ArrayList<>(userList.size());
for (UserDO user : userList) {
    UserVO userVo = new UserVO();
    userVo.setId(user.getId());
    userVo.setName(user.getName());
    userVoList.add(userVo);
}// 依次处理用户
for (UserVO userVo : userVoList) {
    // 处理相关逻辑
    ...
}
```

## 情况 4)MyBatis 查询函数的返回列表和数据项不为空，所以不需要空指针判断

MyBatis 是一个优秀的持久层框架，是项目中广泛使用的数据库中间件组件。通过分析 MyBatis 源代码，您可以确保查询函数返回的列表和数据项不为空，并且代码中不需要空指针判断。

以下代码片段显示了症状描述。

这个发展思路不错，但是太保守了。

```
// 查询用户函数
public List<UserVO> queryUser(Long id, String name) {
    // 查询用户列表
    List<UserDO> userList = userDAO.query(id, name);
    if (Objects.isNull(userList)) {
        return Collections.emptyList();
    } // 转化用户列表
    List<UserVO> voList = new ArrayList<>(userList.size());
    for (UserDO user : userList) {
        // 判断对象为空
        if (Objects.isNull(user)) {
            continue;
        } // 添加用户信息
        UserVO vo = new UserVO();
        BeanUtils.copyProperties(user, vo);
        voList.add(vo);
    } // 返回用户列表
    return voList;
}
```

请参考以下推荐的解决方案。

```
// 查询用户函数
public List<UserVO> queryUser(Long id, String name) {
    // 查询用户列表
    List<UserDO> userList = userDAO.query(id, name); // 转化用户列表
    List<UserVO> voList = new ArrayList<>(userList.size());
    for (UserDO user : userList) {
        UserVO vo = new UserVO();
        BeanUtils.copyProperties(user, vo);
        voList.add(vo);
    } // 返回用户列表
    return voList;
}
```

## 利益

*   避免不必要的空指针判断，精简业务代码处理逻辑，提高运行效率。
*   这些不必要的空指针判断基本上都是死代码，永远不会执行。因此，删除它们将有助于代码维护。

# 原始来源:

[](https://www.alibabacloud.com/blog/coding-specifications-%7C-elegant-java-functions-part-one_596181) [## 编码规范|优雅的 Java 函数(第一部分)

### 阿里巴巴云 2020 年 4 月 29 日 288 随着软件项目代码日积月累，系统维护成本上升。这个…

www.alibabacloud.com](https://www.alibabacloud.com/blog/coding-specifications-%7C-elegant-java-functions-part-one_596181) 

**进入专家视角—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)