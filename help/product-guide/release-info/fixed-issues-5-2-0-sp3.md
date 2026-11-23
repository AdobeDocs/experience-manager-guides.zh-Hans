---
title: 发行说明 |修复了Adobe Experience Manager Guides 5.2.0 Service Pack 3版本中的问题
description: 了解Adobe Experience Manager Guides 5.2.0 Service Pack 3版本中的错误修复
role: Leader
TQID: https://experienceleague.adobe.com/HEWV5RxPUfqUYf6m6kQW-fU-LiAM0UFGbfzKjtOCZxk
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
source-git-commit: a3144f0078b2073289043befacc5e2358b9c0e02
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%
---
# 修复了5.2.0 Service Pack 3版本（2026年11月）中的问题

本文介绍Adobe Experience Manager Guides 5.2.0 Service Pack 3版本中修复的各个方面的错误。

了解5.2.0 Service Pack 3版本[&#128279;](upgrade-instructions-5-2-0-sp3.md)的升级说明。

## 编辑器2.0

- 将表从创作模式复制并粘贴到创作模式会删除`colwidth`等属性以及在`colspec`上定义的任何其他属性，从而导致列宽设置丢失。 （指南 — 52916）
- 从Microsoft Word粘贴表时，将创建标题行单元格，但标题行单元格内容会丢失。 （指南 — 49847）
- 当使用Ctrl+V将代码从Microsoft Word或类似的文本编辑器粘贴到`codeblock`元素中时，换行符和行首空格将丢失，代码将拼合到一行中。 （指南 — 33247）

## 资产管理

- 资源状态API不会为路径包含逗号的资源返回正确的状态。 （指南 — 49065）

## 发布

- 在AEM Sites上发布包含`processing-role=resource-only`个元素的DITA映射（使用旧版组件映射）时，会在其他方案（如`topicgroup`元素和特定内容配置）中为这些元素生成孤立网站页面。 （指南 — 37650）
- 分支筛选会为用作`keydef`的不需要的主题生成额外页面（这些主题由DITA-OT标记`resource-only ="true"`）。 （指南 — 19701）
- 在“地图”功能板中，选择其他预设会触发获取对等链接的调用，从而导致其他处理。 （指南 — 53703）
- 在本机PDF输出中，以`toc="no"`属性标记的主题引用仍包含在目录中，从而导致冗长而混乱的目录。 （指南 — 20156）
- 在某些情况下，当使用动态基线生成完整的DITA映射并将其发布到AEM Sites时，某些主题会与较早或未批准的版本一起发布，而不是与当前的批准版本一起发布。 （指南 — 55646）
- 在处理大量资源时，`PurgePresetExecutionDataJob`有时会遇到未经处理的`RuntimeNodeTraversalException`，从而导致作业陷入无限循环并生成过多日志。 （指南 — 53897）
- 在本机PDF输出中，对`topichead`或`topicgroup`元素设置的`outputclass`属性未应用或结转到生成的PDF部分。 （指南 — 22950）
- 在某些情况下，使用本机PDF引擎v1发布时，具有辅助功能`settingsenabled`的内容的读取顺序不正确。 页脚中的页码在主内容之前而不是结尾处读取。(GUIDES-27790)


## 翻译

- 将基线应用于具有多个资源的映射会延迟加载所选语言的翻译报表，有时会导致报表渲染前的请求超时。 （指南 — 45508）
- 当所选语言文件夹使用连字符区域设置代码（例如，`da-DK`）而不是下划线格式(`da_dk`)时，Workspace设置下的“翻译”选项卡中的语言组不会保留。 （指南 — 37843）
- 使用XLIFF项目启动翻译会创建一个从不变为进行中状态的空项目。 （指南 — 51759）
- 当仅具有参与者角色的用户访问编辑器时，全局文件夹配置文件中的`propagateVersionLabel`设置间歇性地重置为`false`。 （指南 — 51870）

## 基准线

- 删除基线后或仍在创建动态基线时，预设保存的基线选择错误地显示为&#x200B;*无基线*。 （指南 — 52690）
- 在某些情况下，动态基线在重建失败后仍处于处理状态，这会导致导出和输出生成使用过时的主题和映射版本，而不会显示任何错误。 （指南 — 56739）

## 审阅

- 在涉及大量审阅任务的场景中，打开审阅面板或应用项目筛选器需要比预期更长的时间来加载任务列表。 （指南 — 48893）
- 审核UI中的内容窗格在某些屏幕分辨率上显示水平滚动条，包括推荐的1600px分辨率，当内容超出窗格宽度时，会导致隐藏审核注释。 （指南 — 44082）

## 平台

- 移动API、重命名API和Assets UI可防止将具有基于GUID的文件名的DITA资源重命名为人类可读的文件名。 Assets现在可以重命名为人类可读的文件名，但是仍然不允许将基于GUID的文件名重命名为另一个基于GUID的文件名。 （GUIDES-43006和GUIDES-59684）
- 从非UUID设置迁移到UUID设置的非DITA资产（例如图像）恢复或分支到其他版本时，其UUID会发生更改。 不再解析对资产的现有引用，并且图像在引用资产的主题中显示为断开。 （指南 — 58414）
- 安装Experience Manager Guides Service Pack将从AEM **工具**&#x200B;部分中删除以前安装的外部工具，如ACS Commons。 （指南 — 60365）

## 已知问题

Adobe已发现5.2.0 Service Pack 3版本的以下已知问题：

- 安装Service Pack后，架构验证可能会失败，并出现`NoClassDefFoundError`异常，并且无法在编辑器中保存主题。 (GUIDES-60062)<br>**解决方法：**&#x200B;从AEM Web控制台(`/system/console/bundles`)刷新`com.adobe.fmdita.schematron-wrapper`捆绑包。
