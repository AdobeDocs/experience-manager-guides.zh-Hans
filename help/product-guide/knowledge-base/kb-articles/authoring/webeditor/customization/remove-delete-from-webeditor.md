---
title: 从软件中针对特定用户的文件上下文菜单中移除“删除”选项
description: 了解如何通过从特定用户/组的文件上下文菜单中移除“删除”选项来自定义编辑器
exl-id: 31b4dd53-3938-42e1-bbc6-64806d668696
TQID: https://experienceleague.adobe.com/dzbMsXUoEibR5QxKB-Z-h4qGnQaX2NmIYLTtxVJHE-A
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: 240
ht-degree: 0%

---

# 删除Webeditor中文件上下文菜单中的“删除”选项

在本文中，我们将了解如何在AEM Guides编辑器的文件上下文菜单中向特定用户或组隐藏“删除”选项。 有关文件上下文菜单选项的其他自定义设置，请查看Guides扩展框架。 可在[此处](https://github.com/adobe/guides-extension/tree/main)找到更多详细信息。

正如您从下面的代码片段中所看到的，文件上下文菜单具有适用于此特定用户的“删除”选项。

删除了![File contextmenu](../../../assets/authoring/file-contextmenu-Delete.png)

现在，让我们看看如何为此用户隐藏“删除”选项。

## 实施步骤：

- 从AEM主页导航到工具>安全>权限。
- 从搜索框中选择组或用户。
- 单击右上角的“添加ACE”。
- 选择文件夹路径。
- 包括特权“jcr:removeChildNodes”和“jcr:removeNode”。
- 选择“权限类型”作为“拒绝”，然后单击“添加”，如下所示。

![用户权限拒绝ACE](../../../assets/authoring/permission-ACE-Delete.png)

![权限中的访问控制列表](../../../assets/authoring/delete-acl.png)

### 测试

- 以已添加ACE的用户身份登录AEM。
- 打开Web编辑器。
- 转到存储库视图，然后选择已添加ACE的文件夹。
- 打开文件上下文菜单。
- “删除”选项将不会显示在上下文菜单中。

文件上下文菜单现在将如下所示：

![File contextmenu，不删除](../../../assets/authoring/file-contextmenu-Delete-removed.png)

```
Please note that these steps would also remove 'move' and 'rename' options from the Editor as they are also tied to delete process at the backend.
```
