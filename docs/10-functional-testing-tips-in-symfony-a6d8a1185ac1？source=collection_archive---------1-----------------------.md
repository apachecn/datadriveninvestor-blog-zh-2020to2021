# Symfony 中的 10 个功能测试技巧。

> 原文：<https://medium.datadriveninvestor.com/10-functional-testing-tips-in-symfony-a6d8a1185ac1?source=collection_archive---------1----------------------->

通过参与超过 50 个项目的测试，我们看到了测试是如何增强对代码库的信心，开始为整个开发团队节省时间，并帮助满足业务需求的。

对于那些来自其他生态系统的人，让我们首先解释一下术语“功能测试”在 Symfony 中的含义。文档中给出了以下定义:

> “功能测试验证应用程序不同级别的集成(从路由到视图)”。

本质上，这些是端到端的测试。您编写向应用程序发送 HTTP 请求的代码。您得到一个 HTTP 响应，并基于它做出假设。但是，您可以联系数据库并对数据存储级别进行更改，这有时会为检查状态提供额外的机会。

今天，[根据我们的经验，我们准备了 10 个关于用 Symfony 编写功能测试的技巧](https://geniusee.com/single-blog/10-functional-testing-tips-in-symfony)。

[](https://www.datadriveninvestor.com/2020/02/14/turn-hobby-showcase-into-money-maker/) [## 将爱好展示变成赚钱机器|数据驱动的投资者

### 这是造梦者奥斯卡·冈萨雷斯响应号召的地方。他是一名独立的在家工作的顾问，担任…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/02/14/turn-hobby-showcase-into-money-maker/) 

# 1.使用数据存储层进行测试

运行功能测试时，您可能要做的第一件事就是将测试基础与开发基础分开。这样做是为了创建一个运行测试的干净工作台，并允许您创建和管理应用程序的期望状态。此外，测试不应该将随机数据写入开发数据库的副本。

通常，当运行测试时，Symfony 应用程序连接到另一个数据库。如果您有 Symfony 4 或 5，那么您可以在. env.test 文件中定义用于测试的环境变量。另外，配置 PHPUnit，将环境变量 APP_ENV 更改为 test。幸运的是，当您安装 PHPUnit Bridge 的 Symfony 组件时，默认情况下会发生这种情况。

对于低于 4 的版本，当您运行功能测试时，您可以在测试模式下使用内核引导。使用 config_test.yml 文件，您可以定义您的测试配置。

# 2.LiipFunctionalTestBundle

![](img/eb71eb73b117645cd15418bfaa964bae.png)

这个包包含了一些编写 Symfony 测试的重要支持工具。有时他试图做得太多，可能会干涉，但总的来说有助于工作。

例如，在测试期间，您可以模拟用户输入，上传夹具数据，统计数据库查询以检查回归性能，等等。我们建议在开始测试新的 Symfony 应用程序时安装这个包。

# 3.每次测试后清理数据库

测试期间我什么时候需要清洁底座？Symfony 工具包没有给出提示。我们更喜欢在每个测试方法之后更新数据库。测试套件如下所示:

```
<?php
namespace Tests;
use Tests\BaseTestCase;
class SomeControllerTest extends TestCase
{
public function test_a_registered_user_can_login()
{
// Clean slate. Database is empty.
// Create your world. Create users, roles and data.
// Execute logic
// Assert the outcome.
// Database is reset.
}}
```

清理数据库的一个很好的方法是将空的 fixtures 加载到 PHPUnit 中一个特殊的 setUp 方法中。如果已经安装了 LiipFunctionalTestBundle，就可以这样做。

```
<?php
namespace Tests;
class BaseTestCase extends PHPUnit_Test_Case
{
public function setUp()
{
$this->loadFixtures([]);
}
}
```

# 4.数据创建

如果您从一个空数据库开始每个测试，那么您需要有几个实用程序来创建测试数据。这些可以是数据库创建模型或实体对象。

Laravel 对模型工厂有一个非常简单的方法。我们试着遵循同样的方法，制作创建我经常在测试中使用的对象的接口。下面是一个创建用户实体的简单界面示例:

```
<?php
namespace Tests\Helpers;
use AppBundle\Entity\User;
trait CreatesUsers
{
public function makeUser(): User
{
$user = new User();
$user->setEmail($this->faker->email);
$user->setFirstName($this->faker->firstName);
$user->setLastName($this->faker->lastName);
$user->setRoles([User::ROLE_USER]);
$user->setBio($this->faker->paragraph);
return $user;
}
```

我们可以将这样的接口添加到所需的测试套件中:

```
<?php
namespace Tests;
use Tests\BaseTestCase;
use Tests\Helpers\CreatesUsers;
class SomeControllerTest extends TestCase
{
use CreatesUsers;
public function test_a_registered_user_can_login()
{
$user = $this->createUser();
// Login as a user. Do some tests.
}
}
```

# 5.替换容器中的服务

在 Laravel 应用程序中，在容器中交换服务非常容易，但是在 Symfony 项目中，这就比较困难了。在 Symfony 3.4–4.1 版本中，容器中的服务被标记为私有。这意味着在编写测试时，您不能访问容器中的服务，也不能指定另一个服务(存根)。

尽管有些人认为功能测试不需要使用存根，但是可能会有这样的情况，您没有第三方服务的沙箱，并且您不想给他们随机的测试数据。

幸运的是，在 Symfony 4.1 中，您可以按照自己的意愿访问容器和更改服务。例如:

```
<?php
namespace Tests\AppBundle;
use AppBundle\Payment\PaymentProcessorClient;
use Tests\BaseTestCase;
class PaymentControllerTest extends BaseTestCase
{
public function test_a_user_can_purchase_product()
{
$paymentProcessorClient = $this->createMock(PaymentProcessorClient::class);
$paymentProcessorClient->expects($this->once())
->method('purchase')
->willReturn($successResponse);
// this is a hack to make the container use the mocked instance after the redirects
$client->disableReboot();
$client->getContainer()->set(PaymentProcessorClient::class, $paymentProcessorClient)
}
}
```

但是请注意，在功能测试期间，Symfony 核心可以在测试期间启动几次，重新组装所有依赖项并丢弃您的存根。

# 6.内存中的 SQLite 执行

![](img/e4e26662fa54b771df301006099cab99.png)

在测试时，SQLite 经常被用作数据存储层，因为它非常紧凑并且非常容易配置。这些特性也使得它在 CI / CD 环境中使用非常方便。

SQLite 是无服务器的，即程序将从文件中写入和读取所有数据。毫无疑问，这将成为性能方面的瓶颈，因为 I / O 操作增加了，其完成将不得不等待。因此，您可以使用内存选项。然后，数据将从内存中写入和读取，这可以加快操作速度。

在 Symfony 应用中配置数据库时，不需要指定 database.sqlite 文件，只需用关键字:memory:进行传输即可。

# 7.使用 tmpfs 在内存中执行 SQLite

在内存中工作很好，但是有时用旧版本的 LiipFunctionalTestBundle 配置这种模式会非常困难。如果你也碰到这个，那就有这样一招。

在 Linux 系统上，您可以分配部分 RAM，这将像正常存储一样。这就是所谓的 tmpfs。本质上，您创建一个 tmpfs 文件夹，将 SQLite 文件放入其中，并使用它来运行测试。

您可以对 MySQL 使用相同的方法，但是设置会更复杂。

# 8.弹性搜索级别测试

与连接到数据库的测试实例一样，您也可以连接到 Elasticsearch 的测试实例。或者更好的是:您可以使用其他索引名称来以这种方式分隔测试和开发环境。

测试 Elasticsearch 看似简单，但实际上可能很难。我们有强大的工具来生成数据库模式、创建夹具以及用测试数据填充数据库。当涉及到 Elasticsearch 时，这些工具可能不存在，你必须创建你的解决方案。也就是说，很难进行测试。

还存在着为新数据编制索引和确保信息可用性的问题。一个常见的错误是 Elasticsearch 的更新间隔。通常，经过配置中指定的时间后，索引文档变得可搜索。默认情况下，这是 1 秒钟，如果你不小心，它可能会成为你测试的一个插头。

# 9.使用 Xdebug 过滤器加速覆盖率报告

覆盖率是测试的一个重要方面。不需要把它当作素数，它有助于在代码中找到未测试的分支和线程。

通常，Xdebug 负责评估覆盖率。

您将会看到，开始覆盖率分析降低了测试的速度。在每分钟都要花钱的 CI / CD 环境中，这可能是一个问题。

幸运的是，可以进行一些优化。当 Xdebug 生成运行测试的覆盖率报告时，它会对测试中的每个 PHP 文件都这样做。这包括位于供应商文件夹中的文件—不属于我们的代码。

通过在 Xdebug 中设置代码覆盖过滤器，我们可以让它不对我们不需要的文件生成报告，从而节省大量时间。

如何创建过滤器？这可以通过 PHPUnit 来实现。创建过滤器配置文件只需要一个命令:

```
phpunit --dump-xdebug-filter build/xdebug-filter.php
```

然后我们在运行测试时传递这个配置:

```
phpunit --prepend build/xdebug-filter.php --coverage-html build/coverage-report
```

# 10.并行化工具

运行功能测试会花费很多时间。例如，一组 77 个测试和 524 个假设的完整运行可能需要 3-4 分钟。这是正常的，考虑到每个测试都会对数据库进行一系列查询，生成模式簇，在这些模式上运行爬虫，并做出某些假设。

如果您打开活动监视器，您会看到测试只使用了计算机的一个核心。您可以使用 paratest 和 fast 等并行化工具来使用其他内核。它们很容易配置来运行单元测试，如果您需要数据库连接，您可能需要修补。

我们希望这些建议对你有用。如果您有任何问题— [请填写联系我们表格。你可以在我们的](https://geniusee.com)[博客](https://geniusee.com/blog)中找到更多有趣的文章。

**进入专家视角—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)