# 用 Django Admin 中的 LogEntry 监视用户操作

> 原文：<https://medium.datadriveninvestor.com/monitoring-user-actions-with-logentry-in-django-admin-8c9fbaa3f442?source=collection_archive---------0----------------------->

Django 是最好的 web 框架之一，主要集中在速度和可伸缩性上，因为它非常容易使用和部署，你会发现自己正在处理一个拥有大量数据集的大型应用程序。虽然这绝对不是什么令人难过的事情，但它确实为可用性和可维护性带来了一些新的挑战。我发现自己要应对的挑战之一是从 Django 管理页面查看用户活动并跟踪他们做了什么的能力。非常方便的是，它可以用几行代码实现。

![](img/745a915c8921da655849e619cd5529df.png)

Photo by [Carlos Muza](https://unsplash.com/@kmuza?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# **TL；博士:**

您可以通过在项目中的任何 admin.py 文件的底部添加 GitHub Gist 来实现用户活动监控系统。这将允许您看到任何模型中发生的任何更改、添加和删除，并通过使用 Django Admin 的 LogEntry 模型中已经保存的数据知道是谁做的。

## Django 管理员的日志条目是什么

每当用户在 Django admin 中添加、删除甚至更改一个对象时，这个动作都会被记录下来，记录在数据库 django_admin_log 的一个表中，这个表名为 **LogEntry** 。LogEntry 的模型非常简单，它包括如下字段:action_time、user、object_id、action_flag 和 change_message，其中包括被更改的字段的名称。

现在模型已经由标准管理 Django 应用程序提供给我们，当我们使用`django-admin startprojet`命令启动 Django 项目时，它会自动初始化。因此，我们不必对模型进行任何更改，相反，我们需要做的是在任何 admin.py 文件中注册 LogEntery 模型，就像注册任何其他模型一样。

Register Django’s LogEntry model in Django Admin

现在，如果我们运行服务器，我们可以看到在管理页面中有一个名为 Administration 的新应用程序，其中有我们的日志条目。

虽然这是我们在管理页面中显示日志条目时必须做的主要工作，但我们仍然可以对其进行一些补充，以使其使用起来更加安全和直观:

## 管理权限:

为我们的日志条目设置某种权限系统是非常重要的。在目前的状态下，任何员工用户都可以查看、更改甚至删除任何日志条目，这是很危险的。所以我们要为 LogEntryAdmin 类设置 4 个权限:has_add_permission，has_change_permission，has_delete_permission，has_view_permission。对于前三个，我认为应用程序中的任何人都不应该有这样的权限，因为添加、删除或更改日志条目对数据库来说可能是非常有害的，所以我们应该将其设置为总是返回 False。
至于第四个，查看权限，是个人喜好问题。我喜欢为超级用户保留查看日志条目的权限。但是你可以自由地改变它来返回你想要的任何东西。我们可以通过覆盖 LogEntryAdmin 类中的以下方法来设置权限:

set user permission for log entries

## 添加已编辑对象的链接

我们可以添加到这个特性中的另一个巧妙之处是通过点击链接来打开编辑过的对象的能力。这可以通过使用 Django 的 urls.reverse 函数来完成，方法是将它添加为 LogEntryAdmin 类的一个方法:

get object link in LogEntryAdmin

您还可以将 object_link 添加到 list_display，以便它显示在日志列表中。

## 结论

将所有这些结合在一起，我们得到了 LogEntryAdmin 类，当添加到任何 admin.py 文件中时，超级用户将能够看到所有日志并监视 Django 管理页面中发生的所有活动。

您可以在此处找到组合的 LogEntryAdmin 类:

LogEntryAdmin class

就这样，就像 this🥳.一样简单

如果你喜欢这个教程，请不要忘记给它一个掌声，在社交媒体上分享它，并关注我更多这样的教程。