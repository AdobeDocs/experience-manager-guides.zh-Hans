---
title: Cloud Service性能优化建议
description: 了解性能优化建议
feature: Performance Optimization
role: Admin
level: Experienced
exl-id: 6c9684d4-180f-4ccb-bfd6-6c82a8a7b720
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: baa3aa24-d162-4a57-b73a-d27341145083
    internal-label: Performance optimization
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 5%
---
# Cloud Service性能优化建议 {#id213BD0JG0XA}

对于性能优化，请考虑以下几点：

- 要优化内容和索引体验，请参阅AEM文档中的[优化内容搜索和索引](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html)。

- 使用自定义DITA-OT进行发布时修补Xerces Jar。 这是一个强制性配置，具体取决于您的用例。 仅当使用自定义DITA-OT发布输出时，才需要此更改。

  *必需的配置*：将自定义DITA-OT包中的Xerces Jar文件替换为附带的OOTB文件。 默认的OOTB `xercesImpl-2.11.0.jar`文件在`/libs/fmdita/dita\_resources/DITA-OT.zip`文件中可用。 请确保重命名`xercesImpl-2.11.0.jar`文件以匹配要替换的旧Xerces Jar文件。 这可以在运行时完成。

  此更改可减少发布时间和内存使用率，同时发布包含大量主题的DITA映射。
