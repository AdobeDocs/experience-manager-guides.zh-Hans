---
title: 发行说明 | 修复了Adobe Experience Manager Guides 2024.2.0版本中的问题
description: 了解Adobe Experience Manager Guidesas a Cloud Service2024.2.0版本中的错误修复。
exl-id: fae1ff07-6232-4e9a-a89e-5e760e807b9d
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 4%

---

# 修复了2024.2.0版本中的问题

本文介绍2024.2.0版本的Adobe Experience Manager Guidesas a Cloud Service中修复的各个方面的错误。

有关新功能和增强功能的更多信息，请查看 [2024.2.0 版本中的新增功能](whats-new-2024-2-0.md)。

了解2024.2.0版本](upgrade-instructions-2024-2-0.md)的[升级说明。



## 创作

- 编辑器中的拼写检查不允许选择建议。 (15045)
- 全局导航按钮不起作用，无法加载仪表板。 (14968)
- 在Web编辑器中，下载映射功能在可以下载时无法触发弹出通知。 (14626)
- 在Web编辑器中，下载映射功能无法下载带有基线的映射。 (14622)
- 2023年10月版的Experience Manager Guidesas a Cloud Service中出现无效DTD错误。 (14482)
- 将词汇表主题从存储库拖到词汇表映射中会创建`topicref`。 (10767)
- 片段的预览屏幕已冻结。 (14840)
- `labels.json`文件中的标签在Web编辑器中以随机顺序显示。 (10508)

## 发布

- 在本机PDF发布中，条件预设中的自定义属性不适用于本机PDF发布。 (14943)
- 在本机PDF发布中，无法解析2023年12月版本的Adobe Experience Manager Guides的关键引用。 (15085)
- AEM Sites发布失败，并导致对以“HTTP”开头的DITA文件执行`xref`文件的范围错误。 (15154)
- 无法从编辑器中的&#x200B;**输出**&#x200B;选项卡添加自定义模板。 (14846)
- 由于模板路径为空，**AEM Site**&#x200B;预设无法正常工作。 (14804)
- 对于主题包含MathML方程式的DITA映射，AEM站点重新生成失败。 (14790)
- 在本机PDF发布中，生成PDF会在`Node.js`发布的获取依赖项时抛出错误。 (14445)
- AEM预设不允许在Web编辑器中选择`/content`层次结构以外的模板。 (14260)
- 在AEM Sites输出中，具有子元素的`<lines>`元素的样式或换行符丢失。 (12542)
- 自定义元数据在最终输出中不可用。 (12116)
- 在本机PDF发布中，无法使用DITA映射元数据属性来填充PDF文件输出的元数据。 (15159)



## 管理

- **基线筛选器**&#x200B;文件未在Web编辑器中使用文件名。 (13486)
- 禁用父DITA map的索引以获取更好的性能可能会影响某些功能的功能。(12213)


## 审查

- 右键单击上下文菜单无法用于&#x200B;**接受**&#x200B;或&#x200B;**拒绝**&#x200B;跟踪更改。 (14607)
- 在2023年12月版的Adobe Experience Manager Guides中，在审核屏幕中切换以关闭DITA主题不起作用。 (14537)
- 自定义审核工作流的电子邮件模板不适用于叠加。 (13954)

## 已知问题

Adobe发现了2024.2.0版本的以下已知问题：

- 对于重复的DITA文件，版本1.0不会显示在UI上。
- 为任何预设启用微服务后，资产元数据的传播在2024.2.0版本中不起作用。
