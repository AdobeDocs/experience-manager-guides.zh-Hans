---
title: 发行说明 | 修复了Adobe Experience Manager Guides 2024.12.0版本中的问题
description: 了解Adobe Experience Manager Guidesas a Cloud Service2024.12.0版本中的错误修复。
exl-id: 04a57e1a-6e74-46f6-acde-5045d3dcacdc
source-git-commit: dd404c42863f0b4a5f31b54f770c0bf296d68ab9
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 1%

---

# 修复了2024.12.0版本中的问题

本文介绍Adobe Experience Manager Guides as a Cloud Service 2024.12.0版本中修复的各个方面的错误。

了解2024.12.0版本[&#128279;](./upgrade-instructions-2024-12-0.md)的升级说明。

## 创作

- 在`XMLEditorConfig`中启用`xmleditor.uniquefilenames`时，在UUID实例上创建DITA映射失败。 (21201)
- 关闭文件时，在&#x200B;**保存更改和解锁文件**&#x200B;对话框中添加的注释和标签未使用新版本保存在版本历史记录中。 这特定于在`XMLEditorConfig`中启用了&#x200B;**Ask for Check in Close**&#x200B;或&#x200B;**Ask for New Version on Close**&#x200B;的使用案例。 (20065)
- 在保存新版本之前，标记为&#x200B;**Done**&#x200B;的文档状态将还原为&#x200B;**Draft**，从而导致&#x200B;**Done**&#x200B;状态不会在任何文档版本中持续存在。 (20006)
- 无法在Web编辑器的主题中将PDF文件添加为图像引用。 (21206)
- 在Assets UI中选择DITA文件会显示&#x200B;**在FrameMaker中打开**&#x200B;选项，即使在配置中禁用也是如此。 (20082)

## 发布

- 在本机PDF输出中，目录中的章节标题缺失，导致层次结构不正确。 (21840)


## 管理

- 由于日志中存在&#x200B;**未关闭的ResourceResolver**&#x200B;错误，因此发生资源泄漏。 (18488)
- 创建新基线或复制基线时，标签以随机顺序显示。 (19307)


## 基准线

- 如果基线具有大量主题或地图，则编辑1分钟后在云设置上保存基线会超时。 (19558)

## 翻译

- 使用基线的映射转换变得缓慢，最终无法加载所有关联主题和映射文件的列表。 (19733)

## 存在已知问题的解决方法

Adobe已在Adobe Experience Manager Guidesas a Cloud Service的2024.12.0版本中发现以下已知问题。

处理内容翻译时，**项目创建失败**

发送内容以进行翻译时，项目创建会失败，并出现以下日志错误：

处理翻译项目时出现`com.adobe.cq.wcm.translation.impl.TranslationPrepareResource`错误

`com.adobe.cq.projects.api.ProjectException`：无法创建项目

原因为： `org.apache.jackrabbit.oak.api.CommitFailedException`： `OakAccess0000`：访问被拒绝


**解决方法**：要解决此问题，请执行以下步骤：

1. 添加repoinit文件。 如果文件不存在，请执行[示例repoinit配置创建步骤](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-cloud-questions/repoinit-configuration-for-property-set-on-aem-as-cloud-service/m-p/438854?profile.language=zh-Hans)来创建该文件。
2. 在文件中添加以下行并部署代码：

   ```
   { "scripts": [ "set principal ACL for translation-job-service\n allow jcr:all on /home/users/system/cq:services/internal/translation\nend" ] }
   ```

3. 部署后测试翻译。

