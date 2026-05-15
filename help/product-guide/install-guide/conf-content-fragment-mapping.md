---
title: 配置主题和内容片段模型之间的基于JSON的映射。
description: 了解如何配置主题和内容片段模型之间的基于JSON的映射。
exl-id: 21446bcb-e7df-4823-acc3-1fdc7473f0d1
feature: Output Generation
role: Admin
level: Experienced
hidefromtoc: yes
TQID: https://experienceleague.adobe.com/RQfBAqnFbJwbscxdqkuPFf8N8HnXXy-Z-SuiwlleofY
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 239
ht-degree: 0%

---

# 创建主题和内容片段之间的映射

AEM Guides提供了在主题和内容片段模型之间创建基于JSON的映射的功能。 您可以使用此映射将主题中部分或所有元素中存在的内容发布到内容片段。

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

您可以使用默认映射发布整个主题。 从&#x200B;**发布为内容片段**&#x200B;对话框中的下拉列表中选择`Full Topic`映射，并在内容片段模型中具有“topicData”字段。
