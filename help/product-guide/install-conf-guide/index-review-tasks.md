---
title: 执行索引以在“注释”面板中包含所有审阅任务
description: 了解如何为现有的审核任务编制索引，以便它们与较新的任务一起显示在评论面板的审核任务下拉列表中。
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 7d0c757b647a2e6c5e563f0ed7db6a7225769033
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# 执行索引以将主题的所有审阅任务包含在“注释”面板中

通过“注释”面板中提供的[查看主题](../user-guide/review-address-review-comments.md#view-all-review-tasks-for-a-topic)的所有审阅任务，作者可以选择与当前打开的主题关联的任何审阅任务（打开或已关闭），而无需切换审阅项目。 启用后，编辑器中的&#x200B;**注释**&#x200B;面板包含一个下拉列表，其中列出了主题所属的每个审核任务，以及每个任务的状态和其所属的项目。

默认情况下，在实例上启用此功能后，审阅任务在创建时即被编入索引，因此它们自动在此下拉菜单中可用。

但是，如果在实例上部署Experience Manager Guides时禁用了此功能，则对于在禁用期间创建的审核任务，将不会编制索引。 作为管理员，如果在已经存在此类审阅任务后启用该功能，则这些任务在编制索引之前不会出现在下拉列表中。 要使其可用，必须运行一次性脚本来索引现有的审阅任务。

运行以下cURL命令一次，为现有的审阅任务编制索引：

```bash
curl --location 'http://<host>:<port>/bin/guides/script/start' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Basic <base64-encoded-credentials>' \
--header 'Cookie: cq-authoring-mode=TOUCH' \
--data-urlencode 'jobType=review-topic-guids-migration'
```
