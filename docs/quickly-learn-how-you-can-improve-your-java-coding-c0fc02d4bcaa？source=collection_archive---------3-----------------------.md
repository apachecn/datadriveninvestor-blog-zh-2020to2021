# 快速了解如何改进 Java 编码

> 原文：<https://medium.datadriveninvestor.com/quickly-learn-how-you-can-improve-your-java-coding-c0fc02d4bcaa?source=collection_archive---------3----------------------->

![](img/1c8496805383456b75eaf3d96b68bcb4.png)

在《实践论》和其他新儒家著作中，伟大的中国政治家和哲学家王阳明写下了这样的话:

> 情欲与日俱增，就像地板上的灰尘。如果你不每天打扫灰尘，它会积累。如果你努力了，你会发现人生的旅程没有尽头。你探索得越多，剩下的知识就越多。必要的是精确、清晰和完整。

王阳明的至理名言对我们今天的日常生活仍然非常有意义。坏代码就像欲望和灰尘一样，每天都在增加。如果你不经常清理它，它会积累。但是，如果你努力清理糟糕的代码，你可以提高你的编程能力，让你的代码精确清晰，没有怀疑的余地。本文基于一位阿里云工程师的实际编码工作，介绍了三种改进你的 Java 代码的方法，并提供了糟糕的代码样本。

[](https://www.datadriveninvestor.com/2020/02/26/surviving-in-a-digital-age-of-instability/) [## 在不稳定的数字时代生存|数据驱动的投资者

### 如果你是一名计算机科学家，你可能已经注意到新的框架不断出现。编程…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/26/surviving-in-a-digital-age-of-instability/) 

# 提高代码性能

# 当使用映射的主键和值时，迭代`entrySet()`

当使用主键和值时，应该迭代`entrySet()`。这比迭代`keySet()`然后获取值更有效。

错误代码:

```
Map<String, String> map = ...;
for (String key : map.keySet()) {
    String value = map.get(key);
    ...
}
```

好代码:

```
Map<String, String> map = ...;
for (Map.Entry<String, String> entry : map.entrySet()) {
    String key = entry.getKey();
    String value = entry.getValue();
    ...
}
```

# 使用`Collection.isEmpty()`检测空值

与`Collection.size()`相比，`Collection.isEmpty()`可读性更强，在检测空值时提供了更好的性能。`Collection.isEmpty()`的时间复杂度永远是`O(1)`，但是`Collection.size()`的时间复杂度可能是`O(n)`。

错误代码:

```
if (collection.size() == 0) {
    ...
}
```

好代码:

```
if (collection.isEmpty()) {
    ...
}
```

要检测空值，可以使用`CollectionUtils.isEmpty(collection)`和`CollectionUtils.isNotEmpty(collection)`。

# 不要将集合对象传递给集合本身

将集合作为参数传递给集合本身是一个错误或无意义的代码。

对于在执行过程中需要不变参数的方法，当您将集合传递给其自身时，可能会发生错误。

错误代码:

```
List<String> list = new ArrayList<>();
list.add("Hello");
list.add("World");
if (list.containsAll(list)) { // 无意义,总是返回 true
    ...
}
list.removeAll(list); // 性能差, 直接使用 clear()
```

# 在集合初始化期间指定集合大小

Java 的集合类很好用，但是在源代码中集合大小是有限制的。每次缩放操作的时间复杂度可以是`O(n)`。您可以尽可能指定可预测的集合大小，以减少集合缩放的发生。

错误代码:

```
int[] arr = new int[]{1, 2, 3};
List<Integer> list = new ArrayList<>();
for (int i : arr) {
    list.add(i);
}
```

好代码:

```
int[] arr = new int[]{1, 2, 3};
List<Integer> list = new ArrayList<>(arr.length);
for (int i : arr) {
    list.add(i);
}
```

# 使用`StringBuilder`连接字符串

在 Java 中，连接的字符串在编译期间被调优。但是，在循环中串联的字符串在编译期间不会串联。在这种情况下，使用`StringBuilder`连接字符串。

错误代码:

```
String s = "";
for (int i = 0; i < 10; i++) {
    s += i;
}
```

好代码:

```
String a = "a";
String b = "b";
String c = "c";
String s = a + b + c; // 没问题，java 编译器会进行优化
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 10; i++) {
    sb.append(i);  // 循环中，java 编译器无法进行优化，所以要手动使用 StringBuilder
}
```

# 随机访问列表

随机访问数组比访问链表更有效。当被调用的方法需要随机访问获取的`List`中的数据，而不知道内部实现的是数组还是链表时，可以检查是否使用了`RandomAccess`操作。

好代码:

```
// 调用别人的服务获取到 list
List<Integer> list = otherService.getList();
if (list instanceof RandomAccess) {
    // 内部数组实现，可以随机访问
    System.out.println(list.get(list.size() - 1));
} else {
    // 内部可能是链表实现，随机访问效率低
}
```

# 使用 Set 频繁调用`Collection.contains`方法

在 Java 的集合类库中，`List`的 contains 方法的时间复杂度为`O(n)`。如果需要频繁调用代码中的 contains 方法来搜索数据，可以将`List`转换成`HashSet`来降低到`O(1)`的时间复杂度。

错误代码:

```
ArrayList<Integer> list = otherService.getList();
for (int i = 0; i <= Integer.MAX_VALUE; i++) {
    // 时间复杂度 O(n)
    list.contains(i);
}
```

好代码:

```
ArrayList<Integer> list = otherService.getList();
Set<Integer> set = new HashSet(list);
for (int i = 0; i <= Integer.MAX_VALUE; i++) {
    // 时间复杂度 O(1)
    set.contains(i);
}
```

# 让你的代码更优雅

# 将大写字母"`L`"附加到长整型常量上

将大写字母`L`附加到长整型常量上。不要使用小写的`l`，因为它很容易与数字`1`混淆。

错误代码:

```
long value = 1l;
long max = Math.max(1L, 5);
```

好代码:

```
long value = 1L;
long max = Math.max(1L, 5L);
```

# 不要使用神奇的数字

幻数可能会让你的代码非常清晰，但是会很难调试。因此，幻数必须定义为可读的常数。但是，`-1`、`0,`、`1`都不算幻数。

错误代码:

```
for (int i = 0; i < 100; i++){
    ...
}
if (a == 100) {
    ...
}
```

好代码:

```
private static final int MAX_COUNT = 100;
for (int i = 0; i < MAX_COUNT; i++){
    ...
}
if (count == MAX_COUNT) {
    ...
}
```

# 不要通过使用集合实现为静态成员变量赋值

通过使用静态代码块而不是集合实现，为集合类型的静态成员变量赋值。

错误代码:

```
private static Map<String, Integer> map = new HashMap<String, Integer>() {
    {
        put("a", 1);
        put("b", 2);
    }
};private static List<String> list = new ArrayList<String>() {
    {
        add("a");
        add("b");
    }
};
```

好代码:

```
private static Map<String, Integer> map = new HashMap<>();
static {
    map.put("a", 1);
    map.put("b", 2);
};private static List<String> list = new ArrayList<>();
static {
    list.add("a");
    list.add("b");
};
```

# 使用`try-with-resources`语句

Java 7 引入了`try-with-resources`语句，用于关闭相关资源，使程序代码更简单、更安全。比原来的`try-catch-finally`说法要好。

错误代码:

```
private void handle(String fileName) {
    BufferedReader reader = null;
    try {
        String line;
        reader = new BufferedReader(new FileReader(fileName));
        while ((line = reader.readLine()) != null) {
            ...
        }
    } catch (Exception e) {
        ...
    } finally {
        if (reader != null) {
            try {
                reader.close();
            } catch (IOException e) {
                ...
            }
        }
    }
}
```

好代码:

```
private void handle(String fileName) {
    try (BufferedReader reader = new BufferedReader(new FileReader(fileName))) {
        String line;
        while ((line = reader.readLine()) != null) {
            ...
        }
    } catch (Exception e) {
        ...
    }
}
```

# 删除未使用的私有方法和字段

删除未使用的私有方法和字段，使代码更简单、更易于维护。您可以从历史提交中恢复已删除的方法和字段。

错误代码:

```
public class DoubleDemo1 {
    private int unusedField = 100;
    private void unusedMethod() {
        ...
    }
    public int sum(int a, int b) {
        return a + b;
    }
}
```

好代码:

```
public class DoubleDemo1 {
    public int sum(int a, int b) {
        return a + b;
    }
}
```

# 删除未使用的局部变量

删除不用的局部变量，使代码更简单，更易于维护。

错误代码:

```
public int sum(int a, int b) {
    int c = 100;
    return a + b;
}
```

好代码:

```
public int sum(int a, int b) {
    return a + b;
}
```

# 删除未使用的方法参数

未使用的方法参数会产生误导。删除它们，使代码更简单，更易于维护。但是，对于基于父类的方法或接口方法定义的重写方法，不要删除未使用的参数。

错误代码:

```
public int sum(int a, int b, int c) {
    return a + b;
}
```

好代码:

```
public int sum(int a, int b) {
    return a + b;
}
```

# 删除表达式中多余的括号

表达式的多余括号被一些编码者认为是不必要的，但是对其他编码者的代码阅读是有帮助的。对于 Java 专家来说，这些多余的括号只会让代码看起来复杂。

错误代码:

```
return (x);
return (x + 2);
int x = (y * 3) + 1;
int m = (n * 4 + 2);
```

好代码:

```
return x;
return x + 2;
int x = y * 3 + 1;
int m = n * 4 + 2;
```

# 工具类的掩码构造函数

工具类是静态字段和函数的集合，不能实例化。在 Java 中，隐式公共构造函数被添加到每个类中，而没有构造函数定义。如果您是 Java 新手，我们建议您定义一个显式的私有构造函数来屏蔽隐式的公共构造函数。

错误代码:

```
public class MathUtils {
    public static final double PI = 3.1415926D;
    public static int sum(int a, int b) {
        return a + b;
    }
}
```

好代码:

```
public class MathUtils {
    public static final double PI = 3.1415926D;
    private MathUtils() {}
    public static int sum(int a, int b) {
        return a + b;
    }
}
```

# 删除并抛出多余的捕获异常

如果使用 catch 语句捕获的异常未经处理就被抛出，结果与未捕获异常相同。要解决这个问题，可以删除相关的代码块或添加另一个处理方法。

错误代码:

```
private static String readFile(String fileName) throws IOException {
    try (BufferedReader reader = new BufferedReader(new FileReader(fileName))) {
        String line;
        StringBuilder builder = new StringBuilder();
        while ((line = reader.readLine()) != null) {
            builder.append(line);
        }
        return builder.toString();
    } catch (Exception e) {
        throw e;
    }
}
```

好代码:

```
private static String readFile(String fileName) throws IOException {
    try (BufferedReader reader = new BufferedReader(new FileReader(fileName))) {
        String line;
        StringBuilder builder = new StringBuilder();
        while ((line = reader.readLine()) != null) {
            builder.append(line);
        }
        return builder.toString();
    }
}
```

# 使用类访问公共静态常数

虽然可以通过类实例访问公共静态常量，但这可能会导致误解，以为每个类的实例都有一个公共静态常量。我们建议您通过类访问公共静态常量。

错误代码:

```
public class User {
    public static final String CONST_NAME = "name";
    ...
}User user = new User();
String nameKey = user.CONST_NAME;
```

好代码:

```
public class User {
    public static final String CONST_NAME = "name";
    ...
}String nameKey = User.CONST_NAME;
```

# 不要使用 NullPointerException 来确定空指针

通过编码(例如，没有检测到空值)而不是通过捕获异常来防止空指针异常

错误代码:

```
public String getUserName(User user) {
    try {
        return user.getName();
    } catch (NullPointerException e) {
        return null;
    }
}
```

好代码:

```
public String getUserName(User user) {
    if (Objects.isNull(user)) {
        return null;
    }
    return user.getName();
}
```

# 将`""+value`替换为`String.valueOf(value)`

使用`String.valueOf(value)`而不是`""+value`更有效地将其他对象或类型转换成字符串。

错误代码:

```
int i = 1;
String s = "" + i;
```

好代码:

```
int i = 1;
String s = String.valueOf(i);
```

# 给过时的代码添加`@Deprecated`注释

如果一段代码已经过时，但是由于兼容性的原因而无法删除，您可以在代码中添加`@Deprecated`注释，这样就不会再使用它了。将`@deprecated`添加到文档注释中，以给出解释并提供替代解决方案。

好代码:

```
/**
 * 保存
 *
 * @deprecated 此方法效率较低，请使用{@link newSave()}方法替换它
 */
@Deprecated
public void save(){
    // do something
}
```

# 防止代码中的错误

# 不要使用构造函数方法`BigDecimal(double)`

`BigDecimal(double)`在精确计算或值比较过程中，可能导致准确性损失和业务逻辑异常。

错误代码:

```
BigDecimal value = new BigDecimal(0.1D); // 0.100000000000000005551115...
```

好代码:

```
BigDecimal value = BigDecimal.valueOf(0.1D);; // 0.1
```

# 返回空数组或集合，而不是空值

若要返回空值，需要调用方检测空值。否则，可能会引发空指针异常。当调用方没有检测到空值时，返回空数组或集合可以防止引发空指针异常。为了简化代码，可以删除指示调用方检测空值的语句。

错误代码:

```
public static Result[] getResults() {
    return null;
}public static List<Result> getResultList() {
    return null;
}public static Map<String, Result> getResultMap() {
    return null;
}public static void main(String[] args) {
    Result[] results = getResults();
    if (results != null) {
        for (Result result : results) {
            ...
        }
    } List<Result> resultList = getResultList();
    if (resultList != null) {
        for (Result result : resultList) {
            ...
        }
    } Map<String, Result> resultMap = getResultMap();
    if (resultMap != null) {
        for (Map.Entry<String, Result> resultEntry : resultMap) {
            ...
        }
    }
}
```

好代码:

```
public static Result[] getResults() {
    return new Result[0];
}public static List<Result> getResultList() {
    return Collections.emptyList();
}public static Map<String, Result> getResultMap() {
    return Collections.emptyMap();
}public static void main(String[] args) {
    Result[] results = getResults();
    for (Result result : results) {
        ...
    } List<Result> resultList = getResultList();
    for (Result result : resultList) {
        ...
    } Map<String, Result> resultMap = getResultMap();
    for (Map.Entry<String, Result> resultEntry : resultMap) {
        ...
    }
}
```

# 使用常量或确定值调用`equals`方法

对象的`equals`方法经常抛出空指针异常。要解决这个问题，请使用常量或具有确定值的对象来调用 equals 方法。最好的解决方法是使用`java.util.Objects.equals()`方法。

错误代码:

```
public void isFinished(OrderStatus status) {
    return status.equals(OrderStatus.FINISHED); // 可能抛空指针异常
}
```

好代码:

```
public void isFinished(OrderStatus status) {
    return OrderStatus.FINISHED.equals(status);
}public void isFinished(OrderStatus status) {
    return Objects.equals(status, OrderStatus.FINISHED);
}
```

# 仅使用私有和不可更改的枚举属性字段

枚举通常以与常量相同的方式使用。如果枚举包含公共属性字段或字段设置方法，这些枚举常数的属性很容易被修改。理想情况下，枚举属性字段是私有的，并在私有构造函数中赋值。由于缺少`Setter`方法，我们建议您添加最终修改器。

错误代码:

```
public enum UserStatus {
    DISABLED(0, "禁用"),
    ENABLED(1, "启用"); public int value;
    private String description; private UserStatus(int value, String description) {
        this.value = value;
        this.description = description;
    } public String getDescription() {
        return description;
    } public void setDescription(String description) {
        this.description = description;
    }
}
```

好代码:

```
public enum UserStatus {
    DISABLED(0, "禁用"),
    ENABLED(1, "启用"); private final int value;
    private final String description; private UserStatus(int value, String description) {
        this.value = value;
        this.description = description;
    } public int getValue() {
        return value;
    } public String getDescription() {
        return description;
    }
}
```

# 注意`String.split(String regex)`

特定于字符串的 split 方法传递一个分隔符字符串，它是一个正则表达式。有些关键词，比如`.[]() \|`，必须转义。

错误代码:

```
"a.ab.abc".split("."); // 结果为[]
"a|ab|abc".split("|"); // 结果为["a", "|", "a", "b", "|", "a", "b", "c"]
```

好代码:

```
"a.ab.abc".split("\\."); // 结果为["a", "ab", "abc"]
"a|ab|abc".split("\\|"); // 结果为["a", "ab", "abc"]
```

# 摘要

仅此而已。希望你也从王阳明的至理名言中学到了一二。如果没有别的，我希望我们的 Java 编码指南能帮助您编写更有效、更优雅的代码。

*你渴望了解阿里云的最新科技趋势吗？在我们新推出的系列产品* [*科技展*](https://resource.alibabacloud.com/webinar/topic/tech-show.html) *中，听听我们的顶级专家是怎么说的吧！*

# 原始来源:

[](https://www.alibabacloud.com/blog/quickly-learn-how-you-can-improve-your-java-coding_596101) [## 快速了解如何改进 Java 编码

### 《实用生活指南及其他新儒家著作》中的 299 页

www.alibabacloud.com](https://www.alibabacloud.com/blog/quickly-learn-how-you-can-improve-your-java-coding_596101) 

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)