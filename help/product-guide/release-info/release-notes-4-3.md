---
title: 发行说明 | Adobe Experience Manager Guides 4.3.0版本中的升级说明和修复的问题
description: 了解错误修复以及如何升级到Adobe Experience Manager Guides的4.3.0版本
exl-id: 7fb568a0-0b88-4ea0-9b79-2625336348ff
feature: Release Notes
role: Leader
source-git-commit: 5a444e88b0adba7fa3d498437df39b729b10b5eb
workflow-type: tm+mt
source-wordcount: '1086'
ht-degree: 1%

---

# 4.3.0版本的Adobe Experience Manager Guides（2023年7月）

此发行说明涵盖了升级说明、兼容性矩阵，以及Adobe Experience Manager Guides版本4.3.0中修复的问题(更高版本称为&#x200B;*AEM Guides*)。

有关新增功能和增强功能的详细信息，请参阅[Adobe Experience Manager Guides 4.3.0版本中的新增功能](./whats-new-4-3-release.md)。

## 升级到AEM Guides的4.3.0版本


您可以轻松地将当前版本的AEM Guides升级到版本4.3.0。在继续升级到版本4.3.0的AEM Guides之前，必须考虑以下几点：
您可以将当前版本的AEM Guides升级到版本4.3.0

- 如果您使用的是版本4.2或4.2.x ，则可以直接升级到版本4.3.0。
- 如果您使用的是版本4.1或4.1.x ，则需要先升级到版本4.2或4.2.x ，然后再升级到版本4.3.0。
- 如果您使用的是版本4.0，则需要先升级到版本4.2，然后再升级到版本4.3.0。
- 如果您使用的是版本3.8.5，则在升级到版本4.2之前需要升级到版本4.0。
- 如果您使用的版本低于3.8.5，请参阅特定于产品的安装指南中的升级AEM Guides部分。



>[!NOTE]
>
>在升级AEM Guides版本之前，必须安装AEM Service Pack。

有关详细信息，请参阅[升级说明](../install-guide/upgrade-xml-documentation.md)。

## 兼容性矩阵

本部分列出了AEM Guides 4.3.0版本支持的软件应用程序的兼容性矩阵。

### Adobe Experience Manager

**4.3.0非UUID**
版本6.5 Service Pack 18、17、16、15或14

**4.3.0 UUID**
版本6.5 Service Pack 18、17、16、15或14

有关更多详细信息，请参阅《安装和配置Adobe Experience Manager Guides指南》中的&#x200B;*技术要求*&#x200B;部分。

### FrameMaker和FrameMaker Publishing Server

| 发行版本 | FMPS 2022 | FMPS 2020 | Fm 2022 | Fm 2020 |
| --- | --- | --- | --- | --- |
| 4.3.0（非UUID） | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.3或更高版本 |
| 4.3.0 (UUID) | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.4或更高版本 |
| | | | |

*从2020.2开始的FMPS版本支持在AEM中创建的基线和条件。

### 氧气连接器

| 发行版本 | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- |--- |--- |
| 4.3.0（非UUID） | 2.3 — 常规–5 | 2.3 — 常规–5 | 1.6 | 1.6 |
| 4.3.0 (UUID) | 3.0-uuid-4 | 3.0-uuid-3 | 2.3 | 2.3 |
|  |  |   |

## 修复的问题

修复了多个区域中的错误如下：

### 创作

- 虽然已选中“解锁文件”选项和“不保存”选项，但不会在Web编辑器中解锁主题文件。 (12558)
- 无法在Web编辑器中签出文件，尽管选择了NO选项以在签入前放弃更改。 (12557)
- 在Web编辑器中，主工具栏中锁定和解锁文件图标的工具提示与存储库视图中显示的图标不一致。(12555)
- 在Web编辑器中，对于尚未在“映射视图”中签出的文件，将显示“取消签出”和“解锁”选项。 (12556)
- 无法在现有“topicref”链接中选择PDF资源。 (12477)。
- 在表中执行合并和拆分时，AEM Guides 4.2会生成额外的表单元格。 (11793)
- 在“存储库视图”中，使用搜索/筛选功能后无法拖动主题或图像。 (12396)
- 打开一个搜索的文件后，会在“查找和替换”面板中禁用搜索结果。 (12142)
- 侧键盘上的“8”数字键在AEM Guides编辑器中不起作用。 (12106)
- 内联/显示属性不会显示在Web编辑器的“布局”视图中。 (12498)
- 全局配置文件UI配置与文件夹配置文件不匹配。 (11970)
- 复制和粘贴DITA文件时会破坏内容引用。 (11959)
- 安装AEM Guides后无法在列视图中编辑内容片段。 (7342)
- 当未包装的xref位于子元素标记下时，内容丢失。 (12532)
- 当docstate从右侧面板的“文件”属性更改为“结束状态”时，审批工作流不起作用。 (11026)
- 资产UI | 在“列表”视图中，叠加的可用列不可合并。 (11528)
- 未在映射视图中解析Keyref。 (11490)
- 通过XML编辑器导航时，顶部菜单不显示。 (10868)
- ph标记中的`conref` | 显示的浏览对话框不正确。 (9481)
- 在Web编辑器中不会解析指向其他元素的本地链接。 (8790)
- Matches()函数在架构功能中不起作用。 (11224)



### 管理

- DITA映射元数据属性中的“title”字段被映射的`<title>`元素覆盖。 (10702)
- 当尝试打开或更新基线中的主题版本时，“从服务器获取信息”加载程序将无限期运行。(12478)


### 审查

- 新建审核UI | 这些条件会高亮显示，并且显示隐藏的工作方式与它们在Web编辑器中的工作方式有所不同。 (11628)

### 发布

- 重命名本机PDF预设时，发布失败。 (12564)
- 复制本机PDF模板会复制到默认模板位置，而不是提供的自定义模板位置。 (12563)
- 本机PDF | 无法将生成的PDF中的语言元数据设置为符合WCAG 2.0。 (12407)
- 从可能刷新或重新启动的面板中读取临时文件时，发布到AEM站点失败。 (12113)
- 本机PDF | 自定义属性不会传播到临时HTML或PDF引擎。 (DXML-12005)
- 本机PDF |  发布大型内容时出现Java OutOfMemoryError。 (11789)
- 本机PDF | Xref正在打印href主题标题的内容而不是Xref标签。 (11322)
- 本机PDF | 无法保存PDF模板设置。 (10751)
- 本机PDF | 文本在包含多个xref时超出列宽。 (10876)
- 本机PDF | `<note>` `</note>`元素未生成其类型的额外范围标题。 (10549)
- JSON输出 | JSON的jcr：content节点上的`fmUuid`属性不同于JSON中的“id”。 (11564)
- JSON输出 | 如果存在具有相同文件名的映射和主题，则将删除映射的JSON。 (11524)

## 已知问题

Adobe已发现AEM Guides 4.3.0版本的以下已知问题：

- 在基本模板中定义的通用页面布局不会应用为默认模板。

  解决方法：
添加通用页面布局作为前后封面，然后它会开始出现每个页面。
- 在AEM Service Pack 16或17的AEM站点输出页面中搜索时，站点搜索中出现问题。

  解决方法：

   1. 在`crx/de`中打开路径为`/libs/foundation/components/search/search.jsp`的文件
   1. 将行号234替换为以下代码：

      ```
      <a href="<c:url value="${hit.URL}" context="/"/>" onclick="trackSelectedResult(this, ${status.index + 1})"><%= xssAPI.filterHTML(((Search.Hit) pageContext.getAttribute("hit")).getTitle()) %></a>
      
      *(Add the missing closing anchor tag at the end).
      ```

   1. 保存文件。
