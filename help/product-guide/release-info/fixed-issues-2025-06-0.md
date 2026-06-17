---
title: 发行说明 |修复了Adobe Experience Manager Guides 2025.06.0版本中的问题
description: 了解Adobe Experience Manager Guides as a Cloud Service 2025.06.0版本中的错误修复。
exl-id: 0f362ab3-0fae-4eba-bbd6-0b64ae1f2599
TQID: https://experienceleague.adobe.com/kfgmTuMdfq1c1IUcTKiPef9ijJ0tG-fPUuoJlaQEhQA
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: d6596f3f-92a7-43ec-b444-237db6adad05
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 514
ht-degree: 4%

---

# 修复了2025.06.0版本中的问题

本文介绍Adobe Experience Manager Guides as a Cloud Service 2025.06.0版本中修复的各个方面的错误。

有关新功能和增强功能的更多信息，请查看 [2025.06.0 版本中的新增功能](whats-new-2025-06-0.md)。

了解2025.06.0版本](upgrade-instructions-2025-06-0.md)的[升级说明。

## 创作

- 在更新或创建主题时无法关闭JCR会话连接，会导致内存泄漏和服务停机。 （指南 — 26282）
- 拖动列会将其宽度从百分比更改为像素值，从而导致表格扭曲或无法对齐。(GUIDES-23128)
- 将内容粘贴到`code block`中或在`code block`中添加空格并切换视图时，间距将丢失。 （指南 — 27478）
- 将映射添加到`bookmap`时，它将存储在`fmditatopicrefs`中，而不是`fmditamaprefs`中。 （指南 — 25480）
- **插入图像**&#x200B;对话框在高分辨率或缩小屏幕上无法正确呈现，从而导致插图标题和替换文本字段消失。 （指南 — 26459）


## 发布

- 如果DITA内容具有Weblink且范围不为`external`，则本机PDF发布将无限期继续。 （指南 — 26434）
- 当内容中出现错误时，原生PDF和AEM站点的发布会停止并排队等候。 （指南 — 26516）
- 创建具有大量标签的新基线时，它会阻止获取所有标签。 （指南 — 16232）
- 在生成其标题包含多个以空格分隔的单词的AEM网站页面时，地图标题显示连字符而不是空格。 （指南 — 27903）
- 对于本机PDF，未解析无效的元数据属性名称，在&#x200B;**文档属性**&#x200B;中显示为`unresolved property name`。 （指南 — 25680）
- `codeblock`中的多行文本导致在PDF生成期间出现文本溢出问题。 （指南 — 15541）
- 将映射添加到映射收藏集时，映射以外的资产（喜欢的主题等） 显示，并且翻译的地图语言也未正确排序。(GUIDES-25085)


## 审阅

- 审阅UI中的文档视图不会包住某些屏幕大小的内容，因此要求用户水平滚动才能查看完整内容。 （指南 — 25292）


## 已知问题

Adobe发现了2025.06.0版本的以下已知问题：

- 使用“查找并替换”选项时，在对文件应用“替换单次出现”操作后，无法在“查找并替换”面板中执行任何进一步操作。 （指南 — 28930）

- 在启用Unified Shell的情况下打开DITA映射时，编辑器会间歇性地刷新。 （指南 — 26919）

- 对于文件夹配置文件下的AI配置，当从UI中删除已编制索引的资源时，不会删除相应的编制索引路径，并且重新编制索引的尝试会失败，并出现错误消息。 (GUIDES-29147) <br>**解决方法：**&#x200B;在启动重新索引之前，必须删除不再存在的过时路径。

- 如果映射包含循环依赖关系，并且您打开了映射预览，则在刷新浏览器之前，将无法访问Source、创作和布局视图。 (GUIDES-28334) <br>**解决方法：**&#x200B;必须刷新浏览器才能恢复对这些视图的访问。
