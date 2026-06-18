---
title: 为文件浏览对话框配置筛选器
description: 了解如何为文件浏览对话框配置过滤器
exl-id: 1ef09820-3b18-4762-b177-4d40926e21f0
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/7AzojwFiEQkwYtDnwsHhmMOwSCG3vWgsZW5oXZRsTFw
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: 323
ht-degree: 0%

---

# 为文件浏览对话框配置筛选器 {#id20CIL7009GN}

在编辑器中工作时，需要使用文件浏览对话框插入图像、引用或键引用等元素。 默认的文件浏览对话框不提供任何文件过滤选项。 您可以添加自己的过滤器，以便轻松快速地访问所需的文件。

执行以下步骤，将自定义文件过滤选项添加到文件浏览对话框：

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到以下位置提供的默认配置文件：

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在以下位置创建默认配置文件的副本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 导航到`apps`节点中的`ui_config.json`文件并将其打开以进行编辑。

1. 在`ui_config.json`文件中，添加要添加筛选器的定义。

   以下代码段显示了如何添加两个过滤选项 — DITA文件和图像文件。

   ```json
   "browseFilters": [
       {
         "title": "DITA Files",
         "property": "jcr:content/metadata/dita_class",
         "operation": "exists"
       },
       {
         "title": "Image Files",
         "property": "jcr:content/metadata/dc:format",
         "value": [        
           "image/jpeg",
           "image/gif",
           "image/png"
         ]
       }
   ]
   ```

   在上述代码片段中，第一个过滤器用于DITA文件。 过滤器定义采用以下参数：

   - **title：**&#x200B;过滤器的显示名称。 此标题将作为筛选选项显示在文件浏览对话框中。

   - **属性：**&#x200B;要与文件的元数据匹配的属性。 例如，要仅允许属性中包含`dita_class`元数据的文件，属性筛选器将“`jcr:content/metadata/dita_class`”作为其值。

   - **操作：**&#x200B;指定“`exists`”以匹配属性参数中指定的值的存在。

   第二个滤镜用于图像文件。 除了`value`参数之外，这些参数与第一个筛选器相似。 `value`参数采用图像类型的数组作为其值。 在value参数中指定的所有文件类型都将被搜索并显示在文件浏览对话框中，所有其他文件类型将被忽略。

1. 保存&#x200B;*ui\_config.json*&#x200B;文件并重新加载编辑器。

   启动文件浏览对话框时，将显示在ui\_config.json文件中配置的过滤器选项。

   ![](assets/file-browse-custom-filters.png){width="300"}
