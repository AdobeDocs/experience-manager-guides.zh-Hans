---
title: 发行说明 | 修复了Adobe Experience Manager Guides 2024.06.0版本中的问题
description: 了解Adobe Experience Manager Guidesas a Cloud Service2024.06.0版本中的错误修复。
source-git-commit: dff625a841ea9fc758de83b1d830ddffa15646cd
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 3%

---


# 修复了2024.06.0版本中的问题

本文介绍Adobe Experience Manager Guidesas a Cloud Service2024.06.0版各个方面修复的错误。

有关新功能和增强功能的更多信息，请查看 [2024.06.0 版本中的新增功能](whats-new-2024-06-0.md)。

了解 [2024.06.0版的升级说明](upgrade-instructions-2024-06-0.md).

## 创作

- 超过15KB主题的复制和粘贴操作因意外错误而失败。 (17171)
- 用于更改文档状态的功能  **文件属性** 面板无法正常工作，并且已更改为 *草稿* 省/州。 (17088)
- 使用自定义文件夹配置文件更改XML编辑器设置时， `ui_config.json` 将使用不正确的文件进行更新。 (17011)
- 在 **存储库** 面板， **筛选** 搜索未保留值 **签出者** 字段。 **高级过滤器** 对话框。 (16935)
- 创建版本后，主题中的链接图像无法显示在基线中。 (16931)
- 可重用内容面板在 **用户首选项** 设置为通过以下方式查看文件 **文件名**. (16896)
- 表标题元素中的子元素无法在 **预览** Experience Manager指南模式。 (16691)
- 执行后处理脚本失败，原因是 **FileNotFoundException** 例外。 (16517)
- Vimeo视频不支持《Experience Manager指南》中的全屏功能。 (15996)
- 在中粘贴长预格式化的文本序列 `<pre>` 或 `<codeblock>` 元素会导致文本被截断。 (15859)
- 在通过代码安装模板但未处理模板时，由于重复的GUID会发生内容删除。 (15858)
- Experience Manager指南未能遵守 **处理角色** 中的属性 **预览** 模式。 (15787)
- 编辑器会间歇性地删除选定区域之外的额外文本。  (15708)
- 无法从Word文档或HTML复制大型表格并将其粘贴到Web编辑器中。 (15369)
- 此 **复制** 对于“Experience Manager指南”as a Cloud Service中的空文件夹，函数失败。 (15353)
- 缺少API或事件来捕获向元素添加属性或插入新元素。 (15351)
- 无法添加 `<data>` 标记范围 `<ol>` 标记。 (15161)
- 启用Unified Shell后， **版本标签管理** 对话框显示不正确 **主要内容** 适用于没有标签的版本。 (15039)
- 大型文件在Web编辑器中加载缓慢，延迟几秒钟。 (14958)
- 按下 **输入** 文本内表单元格中的键未按预期拆分段落。 (14251)
- Experience ManagerDITA Guide无法触发 **保存** 函数进行缩进。 (16482)
- 评论主题的显示顺序不正确。 (16319)
- 在 **作者** 视图，在使用不间断空格时会发生复制并粘贴问题，导致文本溢出。 (15541)

- 在 `<othermeta>` 元素范围 `<topicmeta>`，在添加 `<conref>`在另一个DITA映射中，映射ID也会与元素的ID一起附加。 (15226)
- 此 `<conref>` 无法从更新 **属性** 进行更改时显示的面板。 (15209)
- 在表单元格中选择图像时，会选择整个单元格。 (15188)

## 发布


- 交叉映射链接无法在具有的链接的发布上下文设置中显示所有父映射。 `peer @scope`. (16700)
- 添加任何新属性或移除任何现有属性时，旧属性将保留在 **条件预设**. (15890)
- 在本机PDF发布输出中，无法正确处理RTL语言内容。 (15709)
- 生成本机PDF输出时，不会对第一个PDF进行版本控制。 (10305)
- 在本机PDF中，嵌套的DITA主题在目录(TOC)中无法正确显示。 (16742)
- 从Dynamic Media为视频文件生成的缩略图无法保留在发布的输出中。 (15656)
- 在ARM64处理器上生成本机PDF失败。 (16968)

## 管理

- 编辑现有基线并选择特定版本会触发应用程序错误。 (14451)

## 翻译

- 翻译项目无法在2023年10月版的《Experience Manager指南》中向Adobe Experience Manager 6.5 SP18添加新语言作业。 (15398)

## Cloud Service

- Adobe Experience Manager工具导航无响应。 (17118)
- Cloud Service部署中的生成转换阶段失败，并出现DITA代码库中的错误。 (14432)

## 报告

- 不准确 **主题列表** 由于复制DITA资源时未打补丁的属性，Experience Manager指南UI中的计数会影响为DTIA映射生成的报表。 (15529)
- 包含外部引用的主题 *%20* 在URL中显示损坏的文件引用。 (15347)


## 已知问题

Adobe发现了2024.06.0版本的以下已知问题：

- 将VimeoPDF添加到主题后，本机内容发布失败。
- 此 **主题属性** 不会按照所选格式显示在页面布局的元数据字段中。
- `xrefs` 在中不可点击 **资产** 在启用Dynamic Media时查看。
