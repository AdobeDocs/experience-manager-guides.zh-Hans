---
title: 配置文本过滤器
description: 了解如何配置文本过滤器
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 0%

---

# 配置文本过滤器 {#id21BPD0FK0XA}

AEM Guides提供用于搜索位于AEM存储库选定路径上的文件中的文本的功能。 您可以使用过滤器搜索从存储库面板中搜索文件或浏览文件。 在Web编辑器中工作时，需要使用文件浏览对话框插入图像、引用或键引用等元素。

默认情况下，您可以使用一些增强型过滤器来搜索AEM存储库中的文件。 您可以筛选选定路径中存在的所有DITA文件或非DITA文件。 您还可以在DITA元素的属性中搜索特定值。 您还可以查找由指定用户签出的文件。

>[!NOTE]
>
> 您还可以配置全局配置文件并添加更多用于搜索的过滤器。

以下选项卡提供了根据Experience Manager Guides设置配置文本过滤器的说明：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 以管理员身份登录Adobe Experience Manager。
1. 单击顶部的Adobe Experience Manager链接，然后选择&#x200B;**工具**。
1. 从工具列表中选择&#x200B;**指南**，然后单击&#x200B;**文件夹配置文件**。
1. 单击&#x200B;**全局配置文件**&#x200B;拼贴。
1. 单击&#x200B;**XML编辑器配置**。
1. 单击顶部的&#x200B;**编辑**&#x200B;图标。
1. 单击&#x200B;**下载**&#x200B;图标可在本地系统上下载ui\_config.json文件。 然后，您可以对文件进行更改，然后上传相同的更改。
   1. 在文件中配置过滤器。 您还可以添加自定义筛选条件，如下例所示：

      以下代码段显示了如何添加过滤选项“DITA文件”、“非DITA”、“DITA元素”和“由文件签出”。 它还包含一个自定义筛选条件 — 标记。

      ```
       "operation":"like"
                                      },
                                      {
                                      "title":"Checked out by",
                                      "property":"jcr:content/cq:drivelock",
                                      "operation":"like",
                                      "itemConfig":{
                                      "component":"textfield",
                                      "placeholder":"Checked out by"
                                      },
                                      "children":[
                                      {
                                      "title":"Check out"
                                      }
                                      ]
                                      },
                                      {
                                      "title":"Tags",
                                      "property":"jcr:content/metadata/cq:tags",
                                      "itemConfig":{
                                      "component":"textfield",
                                      "placeholder":"Enter Tag"
                                      },
                                      "children":[
                                      {
                                      "title":"Tags"
                                      }
                                      ]
                                      }
                                      ]
      ```

      在上述代码片段中，第一个过滤器用于DITA文件。 过滤器定义采用以下参数：

      ****标题****：筛选器的显示名称。 此标题将作为筛选选项显示在文件浏览对话框中。

      ****属性****：在文件的元数据中匹配的属性。 例如，要仅允许属性中包含dita\_class元数据的文件，属性过滤器会将“jcr:content/metadata/dita\_class”作为其值。

      ****操作&#x200B;**：**指定“存在”以匹配属性参数中指定的值的存在

1. 上载更新的ui\_config.json文件，该文件包含添加的过滤器。

配置的筛选器在筛选器面板中可用。

>[!TAB 内部部署]

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

>[!ENDTABS]

**父主题：**[&#x200B;自定义Web编辑器](customize-overview.md)
