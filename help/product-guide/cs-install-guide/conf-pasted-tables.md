---
title: 自定义Web编辑器
description: 了解如何在编辑器中自定义粘贴表的显示
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: d03ac6ba3ec8e5c52c31a3239e2043bbae79622e
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# 配置已粘贴表的显示

使用编辑器中的辅助工具栏，可以在主题的当前或下一个有效位置插入一个简单的表。 您还可以从Microsoft Word或Excel复制表，并将其直接粘贴到主题文件中。

管理员可以配置复制表的显示方式。 默认情况下，此类复制的表在编辑器中显示为`simpletable`。 但是，您可以通过更新XML编辑器配置设置来更改此设置以将复制的表显示为`tgroup`。

>[!NOTE]
>
> 如果复制具有合并行或列的表，则该表将粘贴为普通表`trgoup`，而不是`simpletable`，无论XML编辑器配置中配置的表设置如何。

要更新缺省表格式，请执行以下步骤：

1. 打开“Adobe Experience Manager导航”页面，然后选择左侧的&#x200B;**工具**。
2. 在“工具”面板中，从工具列表中选择&#x200B;**参考线**。
3. 选择&#x200B;**文件夹配置文件**，然后选择要更新表设置的配置文件。
4. 导航到&#x200B;**XML编辑器配置**&#x200B;选项卡。
5. 选择顶部的&#x200B;**编辑**&#x200B;图标。
6. 选择&#x200B;**下载**&#x200B;图标以在您的本地系统上下载`ui_config.json`文件。
7. 在`ui_config.json`文件中，更新`simpletable`设置，如下所示：

   ```
   "htmlToDitaMapping":{ "table": {
   "name" : "tgroup",
   "wrapTag" : {
       "dita" : "table",
       "html" : "div"
   }
   } },
   ```


更新后，保存文件并将其上传。

