---
title: 自定义Web编辑器
description: 了解如何在编辑器中自定义粘贴表的显示
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 839128b4-4889-4c61-b1c0-214ba1d3165e
TQID: https://experienceleague.adobe.com/0g3LyLfKxZEbtl968wJK6r1xPHRjagayeBF4xSvJF6c
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b0521e56-a0b2-40b6-bf47-ebc98751f9baid: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 223
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
