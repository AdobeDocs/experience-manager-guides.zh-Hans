---
title: 发行说明 | Adobe Experience Manager Guides 4.2版本
description: 了解错误修复以及如何升级到Adobe Experience Manager Guides的4.2版本
exl-id: 8a7fef77-63af-462f-89c5-054ab31e079b
feature: Release Notes
role: Leader
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '1391'
ht-degree: 1%

---

# 4.2版本的Adobe Experience Manager Guides（2023年2月）

本发行说明涵盖了升级说明、兼容性矩阵，以及Adobe Experience Manager Guides 4.2版(以后称为 *AEM指南*)。

有关新增功能和增强功能的更多信息，请参阅 [Adobe Experience Manager Guides 4.2版的新增功能](whats-new-4-2-release.md).

## 升级到AEM Guides的4.2版

您可以轻松将AEM Guides的当前版本升级到版本4.2。在继续升级到版本4.2的AEM Guides之前，您必须考虑以下几点：
* 如果您使用的是版本4.0、4.1或4.1.x，则可以直接升级到版本4.2。
* 如果您使用的是版本3.8.5，则在升级到版本4.2之前需要升级到版本4.0。
* 如果您使用的版本低于3.8.5，请参阅 *升级AEM指南* 特定产品的安装指南中的部分。

>[!NOTE]
>
>在升级AEM Guides版本之前，必须安装AEM Service Pack。

有关详细信息，请参阅 [升级说明](assets/Adobe-Experience-Manager-Guides-Upgrade-Instructions-EN.pdf).

## 兼容性矩阵

本节列出了AEM Guides 4.2版本支持的软件应用程序的兼容性矩阵。

### Adobe Experience Manager

**非UUID**
版本6.5 Service Pack 15、14、13或12

**UUID**
版本6.5 Service Pack 15、14、13或12

欲知更多详情，请参见 *技术要求* 安装和配置Adobe Experience Manager Guides指南中的部分。

### FrameMaker和FrameMaker Publishing Server

| 发行版本 | FMPS 2022 | FMPS 2020 | Fm 2022 | Fm 2020 |
| --- | --- | --- | --- | --- |
| 4.2（非UUID） | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.3或更高版本 |
| 4.2 (UUID) | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.4或更高版本 |
| | | | |

*从2020.2开始的FMPS版本支持在AEM中创建的基线和条件。

### 氧气连接器

| 发行版本 | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- |--- |--- |
| 4.2（非UUID） | 2.1 — 常规–4 | 2.1 — 常规–4 | 1.6 | 1.6 |
| 4.2 (UUID) | 2.8-uuid-8 | 2.8-uuid-8 | 2.3 | 2.3 |
|  |  |   |

## 修复的问题

修复了多个区域中的错误如下：

### 创作

* 添加选项卡时左侧面板断开。 (11126)
* 在Web编辑器html中进行的更改会导致以下问题 `<dl>` 和 `<dlentry>`. (11024)
* 某些属性不会被视为条件属性，从而导致出现问题。 (10895)
* 三个或更高级别嵌套 `<indexterm>` 未嵌套在本机PDF导出中。 (10799)
* 从“创作”视图切换到“源”视图时，内容在任务正文中消失。 (10735)
* 审核评论在审核任务中放置错误。 (10625)
* `<conref>` para标记内的注释在预览模式下不会显示。 (10559)
* 在列表项末尾点击空格会删除整个列表。 (10540)
* 在从UI拖放任何元素时（例如，从“条件”面板），屏幕在Chrome v106中显示为空白。 (10524)
* 在的工具栏中缺少自动缩进按钮 **来源** 视图。 (10448)
* 在编辑器中创作列表时，有时列表项的第一个字符会丢失。( 10447)
* **还原** 或 **重做** 在某些文件上无法正常工作。 (10373)
* 在复制和粘贴操作中，自定义元数据未保留。 (10367)
* 执行内容的复制(ctrl+c)和粘贴(ctrl+v)时出现错误。 (10304)
* 从创作模式切换到源模式时，大纲面板不显示内容。 (10296)
* 当子映射引用DITA模板中的主映射时，不会创建子映射。 (10231)
* 升级4.0后，Web编辑器中出现导航问题。 (10159)
* XML编辑器中的“撤消”选项会将用户带到页面顶部。 (10091)
* 对资产执行复制和粘贴操作后，将删除节点属性。 (10053)
* 在编辑器的预览模式下，不会显示添加到DITA主题的SVG文件。 (10010)
* 在Web编辑器中查找和替换的搜索结果在深色模式下不可读。 (9978)
* 从映射模板创建映射时，不存在加载器。 (9891)
* 主题模板中的Conref不起作用，且复制的哈希ID未在内容副本中更新。 (9890)
* 不显示用于浏览主题或映射文件夹的子文件夹中的主题或映射模板的选项。 (9889)
* 没有用于在主题或映射的子文件夹上创建新模板的选项。 (9888)
* XML编辑器不更新主题上的图像。 (9500)
* mimetype是为DITA资产创建和更新进行硬编码的。 (8979)
* 选择中的无破断连字符时，会插入一个普通连字符 **插入特殊字符** 对话框。 (8919)
* 对于通过Assets UI上传的文件，版本历史记录中的版本创建者名称是“fmdita-serviceuser”。 (8910)
* 在资产UI的列视图中工作时，“编辑”选项不适用于图像。 (8758)
* DITA主题不会自动更新并完成更改 **属性** 页面。 (8745)
* 在Web编辑器的主题中移动元素时，元素上分配的ID会被自动分配的ID覆盖。 (7895)

### 管理

* 复制DITA映射资产（从资产UI ）会导致复制的资产中出现错误的基线。 (11218)
* 对于大于AEM所允许限制（默认为2 GB）的文件，上传时不会显示警告消息。 (10817)
* Web编辑器 — 基线 | 在Web编辑器中的新基线仪表板中，“最新”列的行为不同。 (10808)
* 翻译 | 由于/libs/fmdita/i18n/ja.json无效，翻译作业未开始。 (10543)
* 翻译 | 从翻译仪表板（人工翻译）创建的范围设定翻译项目出错。 (10526)
* 翻译 | 对于资产位于活动翻译项目中的整个语言文件夹，后处理将被阻止。 (10332)
* 翻译| 元数据和标记不会传播到翻译的副本。 (4696)
* 如果在基线编辑器中更改并保存了版本，则会为任何资产显示多个弹出窗口。 (10399)
* 会话泄漏发生在com.day.cq.search.impl.builder.QueryBuilderImpl.createResourceResolver(QueryBuilderImpl.java：210)。 (10279)
* 如果父文件夹名称中包含空格，则基线中缺少视频文件。 (10031)

### 发布

* 主题重新生成不适用于某些场景。 (10635)
* PDF发布在为（现有预设的）重复预设生成输出时失败。 (10584)
* 如果预设的PDF生成失败，则“查看日志”按钮不起作用。 (10576)
* Publishlistener不在信息日志中显示请求的数据，并且还包含一些垃圾日志。( 10567)
* 本机PDF | PDF生成失败，出现空指针异常。 (10950)
* 本机PDF | 在生成的输出中未解析conkeyref。 (10564)
* 本机PDF | 映射的元数据出现问题，需要在PDF输出中引用。( 10556)
* 本机PDF | 旋转表标题时出现问题。 (10555)
* 本机PDF | 删除具有处理role=&#39;resource-only&#39;的主题时出现问题。 (10554)
* 本机PDF | PDF输出中显示空的键参照。 (10553)
* 本机PDF | 嵌套 `<indexterm>` 未嵌套在本机PDF导出中。 (10521)
* 本机PDF | 本机PDF使用内联样式，而不是生成的标记的类名称。 (10498)
* 本机PDF | 附录中嵌套的topicref全部转换为临时HTML中的h1。( 10454)
* 本机PDF | 无法从目录隐藏主题标题。 (10355)
* 本机PDF | 表框架属性未传播到临时HTML(as class)。 (10353)
* 本机PDF | 临时HTML文件将colsep和rowsep类添加到 <td> 和 <th> 即使它们的值在源DITA中为0。 (10352)
* 本机PDF | 在章节布局中重新启动页码会从上一章的结尾开始随机编号。 (10154)
* 本机PDF | 未解析包含图像或外部链接的keydef的关键引用。 (10063)
* 本机PDF | 正在将附录显示为所生成PDF中的章节。 (9829)
* XML编辑器中的“模板”选项卡未向文件夹配置文件管理员显示。 (10266)
* 对于使用FrameMaker Publishing Server2020生成的PDF，基线发布失败。 (10551)
* 在“快速生成”弹出菜单中选择通过输出预设的所有预设复选框后，单击编辑按钮时出现应用程序错误。 (10388)
* 如果Web编辑器中的“输出”选项卡具有更多预设，则预设部分无法垂直滚动，并且不会显示所有可用的预设。 (9787)
* 通过编辑器发布时，无法从输出工作流中删除预设。 (9100)
* 对等链接在生成的页面上呈现为普通文本而不是链接。 (7774)

## 已知问题

Adobe已发现AEM Guides 4.2版本的以下已知问题：

* 即使在审阅任务完成后，用户也可以执行审阅操作。