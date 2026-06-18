---
title: 发行说明 |修复了Adobe Experience Manager Guides 4.6.0 Service Pack 3版本中的问题
description: 了解Adobe Experience Manager Guides 4.6.0 Service Pack 3版本中的错误修复
role: Leader
exl-id: 8ff26c28-4a88-4eb2-b359-5b1b0138dd4b
TQID: https://experienceleague.adobe.com/bsiTHK--FPkvfF4bdYUnL-HbAMuhtBKj7wT2eCmd7hM
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: 370
ht-degree: 4%

---

# 修复了4.6.0 Service Pack 3版本（2025年1月）中的问题


本文介绍Adobe Experience Manager Guides 4.6.0 Service Pack 3版本中修复的各个方面的错误。

了解4.6.0 Service Pack 3版本[&#128279;](upgrade-instructions-4-6-0-sp2.md)的升级说明。

## 创作

- 从文件夹配置文件更新条件时，所有条件组都将丢失，并且条件会扁平化。 (23526)
- 更改&#x200B;**内容属性**&#x200B;面板中表的标题行值不会应用更新的值。 (23213)
- 在布局视图中使用&#x200B;**主题引用**&#x200B;元素对话框在DITA映射中添加新主题引用时，添加的引用将显示为断开链接。 (22859)
- 在创作视图中使用&#x200B;**主题引用**&#x200B;元素对话框在DITA映射中添加主题时，所选主题将按相反的选定顺序插入。 (22858)
- 从任何外部产品（例如，MS PowerPoint）复制图像并将其粘贴到“指南”中时，动态上传资产以用于文件的功能会中断。 (24983)
- 使用&#x200B;**搜索和筛选**&#x200B;功能搜索存储库中的文件时，无法选择多个文件。 (25104)

## 发布

- 当内容包含不间断的空格时，发布到Salesforce失败。 (23664)
- 对于链接断开等错误的主题，Salesforce发布将失败，并且进度条会无限期显示。 (22985)
- 对于链接断开的映射，Salesforce发布会失败，并且进度条会无限期显示。 (24963)
- 如果外部链接包含UUID，则它会进行后期处理，并将外部链接转换为UUID链接，从而断开编辑器和发布站点上的链接。 (22574)
- 即使链接的&#x200B;**作用域**&#x200B;设置为&#x200B;**外部**，`xref`也可以转换为相对链接。 (23059)
- 对于将&#x200B;**chunk**&#x200B;属性设置为&#x200B;**to-content**&#x200B;的内容，本机PDF生成失败。 (21772)
- 基线的&#x200B;**编辑属性**&#x200B;对话框不显示以前保存的动态基线标准。 (23964)


## 翻译

- 对于非旧版翻译（对于非UUID），将源路径中的主题移动到其他文件夹会导致目标区域设置中的引用损坏。 (24152)
