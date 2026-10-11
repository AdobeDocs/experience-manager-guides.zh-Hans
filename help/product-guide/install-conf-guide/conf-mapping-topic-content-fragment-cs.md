---
title: 配置主题和内容片段模型之间的基于JSON的映射。
description: 了解如何配置主题和内容片段模型之间的基于JSON的映射。
feature: Output Generation
role: Admin
level: Experienced
exl-id: 764a46b0-dc3f-45bb-b64f-d45574a96875
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%
---
# 为Cloud Service创建主题与内容片段之间的映射

Adobe Experience Manager Guides允许您在主题和内容片段模型之间创建基于JSON的映射。 您可以使用基于JSON的映射将主题中部分或所有元素中存在的内容发布到内容片段。

>[!NOTE]
> 
> 如果您使用的是4.6或更高版本，则无需创建此映射，您可以将主题元素拖到内容片段模型中呈现的字段。
> 详细了解如何[发布内容片段](../user-guide/publish-content-fragment.md)。


1. 要下载&#x200B;*contentFragmentMapping.json*，请以管理员身份登录Adobe Experience Manager。
1. 选择顶部的Adobe Experience Manager链接，然后选择&#x200B;**工具**。
1. 从工具列表中选择“参考线”，然后选择&#x200B;**文件夹配置文件**。
1. 选择&#x200B;**全局配置文件**&#x200B;磁贴。
1. 选择&#x200B;**XML编辑器配置**&#x200B;选项卡，然后选择顶部的&#x200B;**编辑**&#x200B;图标。
1. 选择&#x200B;**下载**&#x200B;图标可在您的本地系统上下载&#x200B;*contentFragmentMapping.json*&#x200B;文件。 然后，您可以对文件进行更改，然后上传相同的更改。

1. 您需要遵循以下验证操作：

   1. 它应该是一个JSON文件
   2. 它应包含一个至少包含一个对象的数组，每个对象应包含以下内容：


      `"name": string `

      `"mapping": array`

      映射的每个对象必须包含以下内容：

      `"modelField": string`

      `"xpath": string`

      `"outputType": string`
1. 保存文件并将其上传。

示例文件：

```
[
  {
    "mapping": [
      {
        "modelField": "title",
        "xpath": "/topic[1]/title[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "shortdesc",
        "xpath": "/topic[1]/shortdesc[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "topicData",
        "xpath": "/topic[1]/body[1]",
        "outputType": "outerHTML"
      }
    ],
    "name": "Full Topic"
  },
  {
    "mapping": [
      {
        "modelField": "title",
        "xpath": "/topic[1]/title[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "shortdesc",
        "xpath": "/topic[1]/shortdesc[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "heroImage",
        "xpath": "/topic[1]/body[1]/p[1]/image[1]",
        "outputType": "outerHTML"
      },
      {
        "modelField": "dataTable",
        "xpath": "/topic[1]/body[1]/table[1]",
        "outputType": "outerHTML"
      }
    ],
    "name": "Sample Example with XPath"
  }
]
```

您可以使用默认映射发布整个主题。 从下拉列表&#x200B;**生成内容片段**&#x200B;对话框中选择`Full Topic`映射，并在内容片段模型中具有“topicData”字段。
