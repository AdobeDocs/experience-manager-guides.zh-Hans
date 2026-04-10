---
title: Cloud Service性能优化建议
description: 了解性能优化建议
feature: Performance Optimization
role: Admin
level: Experienced
source-git-commit: 834959a6a0e22cd5d2b2c5d0e57ceb6d45c0c666
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Cloud Service性能优化建议 {#id213BD0JG0XA}

对于性能优化，请考虑以下几点：

- 要优化内容和索引体验，请参阅AEM文档中的[优化内容搜索和索引](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=zh-Hans)。

- 使用自定义DITA-OT进行发布时修补Xerces Jar。 这是一个强制性配置，具体取决于您的用例。 仅当使用自定义DITA-OT发布输出时，才需要此更改。

  *必需的配置*：将自定义DITA-OT包中的Xerces Jar文件替换为附带的OOTB文件。 默认的OOTB `xercesImpl-2.11.0.jar`文件在`/libs/fmdita/dita\_resources/DITA-OT.zip`文件中可用。 请确保重命名`xercesImpl-2.11.0.jar`文件以匹配要替换的旧Xerces Jar文件。 这可以在运行时完成。

  此更改可减少发布时间和内存使用率，同时发布包含大量主题的DITA映射。

