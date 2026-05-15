---
title: 性能优化建议
description: 了解性能优化建议
exl-id: 92ac1f81-2f51-44b0-82c3-56b39e8f3027
feature: Performance Optimization
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/vh0hogZNMjKrCL12WdKVuwF2qXdzy64KxIhhB-K4esA
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: b1210526-416b-4ef6-bcc0-1692e99f30e9
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
subfeature_v2:
  - id: baa3aa24-d162-4a57-b73a-d27341145083
  - id: c8841798-1a28-4264-a46a-984860f8e6f6
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 162
ht-degree: 5%

---

# 性能优化建议 {#id213BD0JG0XA}

对于性能优化，请考虑以下几点：

- 要优化内容和索引体验，请参阅AEM文档中的[优化内容搜索和索引](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html)。

- 使用自定义DITA-OT进行发布时修补Xerces Jar。 这是一个强制性配置，具体取决于您的用例。 仅当使用自定义DITA-OT发布输出时，才需要此更改。

  *必需的配置*：将自定义DITA-OT包中的Xerces Jar文件替换为附带的OOTB文件。 默认的OOTB xercesImpl-2.11.0.jar文件在/libs/fmdita/dita\_resources/DITA-OT.zip文件中提供。 确保重命名xercesImpl-2.11.0.jar文件以匹配要替换的旧Xerces Jar文件。 这可以在运行时完成。

  此更改可减少发布时间和内存使用率，同时发布包含大量主题的DITA映射。


**父主题：**&#x200B;[&#x200B;下载并安装](download-install.md)
