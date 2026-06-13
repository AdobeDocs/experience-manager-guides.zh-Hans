---
title: 配置文本过滤器
description: 了解如何配置文本过滤器
exl-id: 180e4ab5-5259-4a00-ac3c-bb1d6814ce0d
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/QKz6-i6p4g0QOThLQdoR6HN2uCgZyQClaSizBM4kKO8
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b0521e56-a0b2-40b6-bf47-ebc98751f9baid: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 366
ht-degree: 0%

---

# 配置文本过滤器 {#id21BPD0FK0XA}

AEM Guides提供用于搜索位于AEM存储库选定路径上的文件中的文本的功能。 您可以使用过滤器搜索从存储库面板中搜索文件或浏览文件。 在Web编辑器中工作时，需要使用文件浏览对话框插入图像、引用或键引用等元素。

默认情况下，您可以使用一些增强型过滤器来搜索AEM存储库中的文件。 您可以筛选选定路径中存在的所有DITA文件或非DITA文件。 您还可以在DITA元素的属性中搜索特定值。 您还可以查找由指定用户签出的文件。

>[!NOTE]
>
> 您还可以配置全局配置文件并添加更多用于搜索的过滤器。

执行以下步骤来配置文本过滤器：

1. 以管理员身份登录Adobe Experience Manager。
1. 单击顶部的&#x200B;**Adobe Experience Manager**&#x200B;链接，然后选择&#x200B;**工具**。
1. 从工具列表中选择&#x200B;**指南**，然后单击&#x200B;**文件夹配置文件**。
1. 单击&#x200B;**全局配置文件**&#x200B;拼贴。
1. 单击&#x200B;**XML编辑器配置**。
1. 单击顶部的&#x200B;**编辑**&#x200B;图标。
1. 下载ui\_config.json文件。
1. 在文件中配置过滤器。 您还可以添加自定义筛选条件，如下例所示：

   以下代码段显示了如何添加过滤选项“DITA文件”、“非DITA”、“DITA元素”和“由文件签出”。 它还包含一个自定义筛选条件 — 标记。

   ```json
   [
     {
       "title": "DITA files",
       "property": "jcr:content/metadata/dita_class",
       "operation": "like",
       "children": [
         {
           "title": "DITA Topics",
           "value": "- topic/topic",
           "checked": true
         },
         {
           "title": "DITA Maps",
           "value": "- map/map",
           "checked": true
         }
       ]
     },
     {
       "title": "DITA elements",
       "property": "jcr:content/ditameta",
       "widgetId": "dita_filter",
       "operation": "like"
     },
     {
       "title": "Checked out by",
       "property": "jcr:content/cq:drivelock",
       "operation": "like",
       "itemConfig": {
         "component": "textfield",
         "placeholder": "Checked out by"
       },
       "children": [
         {
           "title": "Check out"
         }
       ]
     },
     {
       "title": "Tags",
       "property": "jcr:content/metadata/cq:tags",
       "itemConfig": {
         "component": "textfield",
         "placeholder": "Enter Tag"
       },
       "children": [
         {
           "title": "Tags"
         }
       ]
     }
   ]
   ```

   在上述代码片段中，第一个过滤器用于DITA文件。 过滤器定义采用以下参数：

   - **标题：**&#x200B;过滤器的显示名称。 此标题将作为筛选选项显示在文件浏览对话框中。

   - **属性：**&#x200B;在文件的元数据中匹配的属性。 例如，要仅允许属性中包含dita\_class元数据的文件，属性过滤器会将“jcr:content/metadata/dita\_class”作为其值。

   - **操作**&#x200B;指定“存在”以匹配属性参数中指定的值的存在

1. 上载更新的ui\_config.json文件，该文件包含添加的过滤器。

配置的筛选器在筛选器面板中可用。

**父主题：**[&#x200B;自定义Web编辑器](conf-web-editor.md)
