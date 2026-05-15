---
title: 发行说明 |修复了Adobe Experience Manager Guides 2024.06.0版本中的问题
description: 了解Adobe Experience Manager Guides as a Cloud Service 2024.06.0版本中的错误修复。
exl-id: 608e5b2c-72af-4498-9b63-935e698231d4
TQID: https://experienceleague.adobe.com/PWXSeB-BhL9Gc104XoVpfqdWqywq7T6bphx8im92C4c
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
  - id: c6d09140-3c91-45d3-b7ed-b681af752f43
  - id: d90290ec-3e61-4ebd-8649-bcafe0836803
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: d4f22c6d-7923-41e5-9da3-527ff8df4bc8
  - id: d6596f3f-92a7-43ec-b444-237db6adad05
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 781
ht-degree: 8%

---

# 修复了2024.06.0版本中的问题

本文介绍Adobe Experience Manager Guides as a Cloud Service 2024.06.0版本中修复的各个方面的错误。

有关新功能和增强功能的更多信息，请查看 [2024.06.0 版本中的新增功能](whats-new-2024-06-0.md)。

了解2024.06.0版本[&#128279;](upgrade-instructions-2024-06-0.md)的升级说明。

## 创作

- 超过15KB主题的复制和粘贴操作因意外错误而失败。 (17171)
- 从&#x200B;**文件属性**&#x200B;面板更改文档状态的功能无法正常工作，并更改为&#x200B;*草稿*&#x200B;状态。 (17088)
- 使用自定义文件夹配置文件更改XML编辑器设置时，`ui_config.json`会更新为不正确的文件。 (17011)
- 在&#x200B;**存储库**&#x200B;面板中，重新打开&#x200B;**高级筛选器**&#x200B;对话框时，**筛选器**&#x200B;搜索未保留&#x200B;**由**&#x200B;字段签出的值。 (16935)
- 创建版本后，主题中的链接图像无法显示在基线中。 (16931)
- 当&#x200B;**用户首选项**&#x200B;设置为&#x200B;**文件名**&#x200B;查看文件时，可重用内容面板不会列出元素。 (16896)
- 表标题元素中的子元素无法在Experience Manager Guides的&#x200B;**预览**&#x200B;模式下渲染。 (16691)
- 由于&#x200B;**FileNotFoundException**&#x200B;异常，后进程脚本执行失败。 (16517)
- Vimeo视频不支持Experience Manager Guides中的全屏功能。 (15996)
- 在`<pre>`或`<codeblock>`元素中粘贴长预格式化的文本序列会导致文本被截断。 (15859)
- 在通过代码安装模板但未处理模板时，由于重复的GUID会发生内容删除。 (15858)
- 在&#x200B;**预览**&#x200B;模式下，Experience Manager Guides无法遵循&#x200B;**处理角色**&#x200B;属性。 (15787)
- 编辑器会间歇性地删除选定区域之外的额外文本。  (15708)
- 无法将Word文档或HTML中的大表格复制并粘贴到Web编辑器中。 (15369)
- Experience Manager Guides as a Cloud Service中的空文件夹的&#x200B;**复制**&#x200B;功能失败。 (15353)
- 缺少API或事件来捕获向元素添加属性或插入新元素。 (15351)
- 无法在Web编辑器的`<ol>`标记中添加`<data>`标记。 (15161)
- 启用Unified Shell后，**版本标签管理**&#x200B;对话框为没有标签的版本错误地显示&#x200B;**主内容**。 (15039)
- 大型文件在Web编辑器中加载缓慢，延迟几秒钟。 (14958)
- 在文本中的表单元格中按&#x200B;**Enter**&#x200B;键无法按预期拆分段落。 (14251)
- 使用自动缩进功能后，Experience Manager DITA Guide无法触发&#x200B;**保存**&#x200B;功能。 (16482)
- 评论主题的显示顺序不正确。 (16319)
- 在&#x200B;**创作**&#x200B;视图中，使用不间断空格时出现复制粘贴问题，导致文本溢出。 (15541)

- 在`<topicmeta>`内的`<othermeta>`元素中，将`<conref>`添加到另一个DITA映射时，映射ID也将与元素的ID一起附加。 (15226)
- 进行更改时无法从&#x200B;**属性**&#x200B;面板中更新`<conref>`。 (15209)
- 在表单元格中选择图像时，会选择整个单元格。 (15188)

## 发布


- 交叉映射链接无法在具有`peer @scope`的链接的发布上下文设置中显示所有父映射。 (16700)
- 添加任何新属性或删除任何现有属性时，旧属性将保留在&#x200B;**条件预设**&#x200B;中。 (15890)
- 在本机PDF发布输出中，无法正确处理RTL语言内容。 (15709)
- 生成本机PDF输出时，不会对第一个PDF进行版本控制。 (10305)
- 在本机PDF中，嵌套DITA主题在目录(TOC)中显示不正确。 (16742)
- 从Dynamic Media为视频文件生成的缩略图无法保留在发布的输出中。 (15656)
- 在ARM64处理器上生成本机PDF发布时输出失败。 (16968)

## 管理

- 编辑现有基线并选择特定版本会触发应用程序错误。 (14451)

## 翻译

- 翻译项目无法通过2023年10月版的Adobe Experience Manager向Experience Manager Guides 6.5 SP18添加新语言作业。 (15398)

## 云服务

- Adobe Experience Manager工具导航无响应。 (17118)
- 云服务部署中的生成转换阶段失败，并出现DITA代码库中的错误。 (14432)

## 报告

- 由于复制DITA资源时未修补的属性，Experience Manager Guides UI中的&#x200B;**主题列表**&#x200B;计数不准确，这会影响为DTIA映射生成的报表。 (15529)
- 包含URL中具有&#x200B;*%20*&#x200B;的外部引用的主题显示损坏的文件引用。 (15347)


## 已知问题

Adobe发现了2024.06.0版本的以下已知问题：

- 将Vimeo内容添加到主题后，本机PDF发布失败。
- **主题属性**&#x200B;未按所选格式显示在页面布局的元数据字段中。
- 启用Dynamic Media后，`xrefs`在&#x200B;**Assets**&#x200B;视图中不可点击。
