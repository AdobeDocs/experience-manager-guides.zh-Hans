---
title: 配置基于UUID的链接的显示
description: 了解如何配置基于UUID的链接的显示
exl-id: ab1b0ecf-cb50-4fcd-b36e-d16a8c396054
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/QlYbIRVwAM10wfcu-Fz3CzOkCCUDZHbVzZo3xCxT3wI
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 211
ht-degree: 0%

---

# 配置基于UUID的链接的显示 {#id2035G20M0QN}

默认情况下，在Web编辑器中使用“插入引用”或“插入重用内容”选项创建链接时，将使用引用内容的UUID创建链接。 引用内容的&#x200B;**Link**&#x200B;属性\（在“属性”面板中\）可以配置为显示引用内容的相对文件路径或UUID。 此显示由configMgr中的&#x200B;**启用UUID**&#x200B;选项控制。 默认情况下，此功能处于打开状态，这意味着引用内容的UUID显示在“属性”面板中。

执行以下步骤以在Web编辑器中显示引用内容的相对路径或UUID：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;包。

1. 在&#x200B;*XmlEditorConfig*&#x200B;设置中，**启用UUID**&#x200B;选项默认处于启用状态。 这意味着引用内容的UUID显示在“属性”面板的&#x200B;**Link**&#x200B;属性中。

   如果要显示链接内容的相对路径，请取消选择&#x200B;**启用UUID**&#x200B;选项。

1. 单击&#x200B;**保存**。


**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
