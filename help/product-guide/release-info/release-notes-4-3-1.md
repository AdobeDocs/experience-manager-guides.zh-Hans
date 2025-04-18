---
title: 发行说明 | Adobe Experience Manager Guides 4.3.1版本中的升级说明和修复的问题
description: 了解错误修复以及如何升级到Adobe Experience Manager Guides的4.3.1版本
exl-id: 3fb6dc31-ec6e-40f5-ab3f-a6e591da315e
feature: Release Notes
role: Leader
source-git-commit: 1b25f1df67fa2442ab79830dc2ac5a6eabd0394c
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 1%

---

# 4.3.1版本的Adobe Experience Manager Guides（2023年10月）

此发行说明涵盖了升级说明、兼容性矩阵，以及Adobe Experience Manager Guides版本4.3.1中修复的问题(更高版本称为&#x200B;*Experience Manager Guides*)。

有关新增功能和增强功能的详细信息，请参阅[Adobe Experience Manager Guides 4.3.1版的新增功能](./whats-new-4-3-1-release.md)。

## 升级到Experience Manager Guides的4.3.1版本


您可以轻松地将当前版本的Experience Manager Guides升级到版本4.3.1。在继续升级到版本4.3.1的Experience Manager Guides之前，必须考虑以下几点：
您可以将当前版本的Experience Manager Guides升级到版本4.3.1


- 如果您使用的是版本4.3.0、4.2或4.2.1，则可以直接升级到版本4.3.1。
- 如果您使用的是版本4.1或4.1.x ，则需要先升级到版本4.3.0、4.2或4.2.x ，然后再升级到版本4.3.1。
- 如果您使用的是版本4.0，则需要先升级到版本4.2，然后再升级到版本4.3.1。
- 如果您使用的是版本3.8.5，则在升级到版本4.2之前需要升级到版本4.0。
- 如果您使用的版本低于3.8.5，请参阅特定于产品的安装指南中的升级Experience Manager Guides部分。


>[!NOTE]
>
>在升级Experience Manager Guides版本之前，必须安装AEM Service Pack。

有关详细信息，请参阅[升级说明](../install-guide/upgrade-xml-documentation.md)。

## 兼容性矩阵

本部分列出了Experience Manager Guides 4.3.1版本支持的软件应用程序的兼容性矩阵。

### Adobe Experience Manager

**4.3.1非UUID**
版本6.5 Service Pack 18、17、16、15或14

**4.3.1 UUID**
版本6.5 Service Pack 18、17、16、15或14

有关更多详细信息，请参阅《安装和配置Adobe Experience Manager Guides指南》中的&#x200B;*技术要求*&#x200B;部分。

### FrameMaker和FrameMaker Publishing Server

| 发行版本 | FMPS 2022 | FMPS 2020 | Fm 2022 | Fm 2020 |
| --- | --- | --- | --- | --- |
| 4.3.1（非UUID） | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.3或更高版本 |
| 4.3.1 (UUID) | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.4或更高版本 |
| | | | |

*从2020.2开始的FMPS版本支持在AEM中创建的基线和条件。

### 氧气连接器

| 发行版本 | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- |--- |--- |
| 4.3.1（非UUID） | 2.3 — 常规–5 | 2.3 — 常规–5 | 1.6 | 1.6 |
| 4.3.1 (UUID) | 3.2-uuid-5 | 3.2-uuid-5 | 2.3 | 2.3 |
|  |  |   |



### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的Experience Manager Guides组件内容包 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 修复的问题

修复了多个区域中的错误如下：

### 创作

- 没有为创建基线在&#x200B;**日期**&#x200B;设置下午时间。 (12712)
- 无法在Web编辑器的`<codeblock>`元素中粘贴JSON代码。 (12326)
- 未保存的版本更改，大型文件不会显示更改后的指示符。 (11784)
- 以韩语编辑时，第一个字符会更改为默认字符。 (10049)

- 前缀在Web编辑器的预览模式下重复。 (13133)
- `Choicetable`行未显示或无法选择。 (12616)
- 使用自定义架构创建主题时，Web编辑器在特定情况下会引发验证错误。 (12576)
- 从映射模板创建映射时，复制主题模板引用不会在内容文件夹中创建副本。 (12150)

- DITA映射中的搜索框没有关闭按钮。 (11867)
- 在Web编辑器中保存长文件时，`DirtyChecker`会引发具有长栈栈跟踪的异常并填充日志文件。 (11860)
- 创建DITA主题需要对相应的文件夹节点具有“删除”权限，但可以使用“写入”权限创建映射。 (11706)
- 当出现斜杠时，Web编辑器显示不正确的标题。 (10949)

- 如果主题的标题包含斜杠“/”，则编辑器中的选项卡仅显示在该斜杠之后出现的字母。 (13455)
- 在编辑器中显示预览后，图像预览未消失。 (13454)
- 升级到4.x后，某些现有版本或其标签未显示在版本历史记录中。(13247)
- Assets UI中的“版本历史记录”面板显示&#x200B;**当前**&#x200B;字段的时间戳不正确。 (12624)
- 在存储库视图或映射视图中，带有控制台标题的主题未解析。(13304)


### 发布

- 本机PDF | 生成PDF输出时，主题的顺序未固定。 (13157)
- 本机PDF| `<p>`元素没有可用的默认样式标记。 (12559)
- 本机PDF | 应用于内容区域的内联样式不会应用于前件和后件主题。 (13510)
- 生成AEM Site输出时未传播`DeliveryTarget`特性。  (13132)
- 为包含某些错误的内容生成AEM站点输出时，**Publish**&#x200B;工作流卡住。 (12000)

- 本机PDF | 包含多个Xref可将文本扩展至超出列宽的位置。 (13004)
- 本机PDF | 当主题和标题具有相同的ID时，会导致生成的PDF输出格式不正确。 (12644)
- 本机PDF | 向DITA映射中的父`<topicref>`元素添加outputclass并将自定义样式应用于outputclass时，该样式将应用于主题正文中的元素，包括节标题。 (12166)
- 如果DITA映射具有多个ditavalref，则增量发布不起作用。 (12117)
- AEM站点 | 在创建映射时，使用keydef指向作为变量的主题并添加processing-role=resource-only会创建一些意外页面。 (12099)
- 如果在AEM站点以外的任何输出中使用来自AEM DAM的任何资源，则元数据“jcr：createdBy”不会反映发布者的名称或上次修改DITA映射或主题的用户的名称。 (12090)
- AEM Sites | DITA映射的navtitle中带有主题头（包含不受支持的字符）会导致页面URL损坏。 (11978)
- 本机PDF | 在Frontmatter和Backmatter中支持topichead / topicmeta / navtitle时出现问题。 (11969)
- 本机PDF | 为大型文档生成PDF非常耗时。 (11955)
- 本机PDF | 在生成PDF输出时，重命名预设会引发NullPointerException。 (11889)
- PDF输出中未显示`<conref>`内容。 (11131)
- 在页面布局编辑器中的“创作”视图和“Source”视图之间切换时，`<div>`元素内会添加一个额外的空间。 (10750)
- 在AEM Cloud Manager上复制的内容在Publish实例上不可见。 (9564)


### 管理

- 即使资产的`dc:format`属性不存在，版本历史记录也不会显示。 (10463)
- 当主题ID与GUID不同时，内容引用是损坏的复制粘贴DITA文件。 (12614)
- 在动态基线中，不会从DITA映射的工作副本的直接引用中提取标签列表。 (11917)
- 使用“浏览所有主题”功能时，“基线”在“映射仪表板”上显示不正确的文件数。 (13265)
- 在Web编辑器中，基线显示DITA文件的先前版本（而非所选版本）的标题。 (13444)

### 审查

- 有关主题的“复查”显示不正确的注释。 (13453)
- Experience Manager Guides中“查看”页面上的“关闭”按钮会将用户转到AEM主页。 (13535)
- 对于正在审阅的主题，附件不会显示在编辑器的右侧面板上。 (13011)



### 翻译

- 从&#x200B;**翻译**&#x200B;仪表板导出的基线失败，且未以目标语言打开。 (13466)

- 将创建新的翻译项目，而不是向选定的现有翻译项目添加新作业。  (10214)
- 将显示已翻译文件的标题来代替源文件的标题。 (11630)
- 自动批准有时不起作用，如果翻译状态中设置的值不正确，则会发生异常。 (13607)
- 从翻译仪表板导出的基线会失败，并且不会以目标语言打开。 (12993)
- 在翻译中使用基线时某些文件丢失。 (13021)
