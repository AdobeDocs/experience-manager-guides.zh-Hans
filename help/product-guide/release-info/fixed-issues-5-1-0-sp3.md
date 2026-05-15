---
title: 发行说明 |修复了Adobe Experience Manager Guides 5.1.0 Service Pack 3版本中的问题
description: 了解Adobe Experience Manager Guides 5.1.0 Service Pack 3版本中的错误修复
role: Leader
exl-id: faa9a5d7-616f-4692-98d1-23abc78556b6
TQID: https://experienceleague.adobe.com/qiVY-B-D3FcHq2PH7Go2AAFpnstCrPJ2MVLEalQCVn0
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 297
ht-degree: 1%

---

# 修复了5.1.0 Service Pack 3版本（2025年12月）中的问题


本文介绍Adobe Experience Manager Guides 5.1.0 Service Pack 3版本中修复的各个方面的错误。

了解5.1.0 Service Pack 3版本[&#128279;](upgrade-instructions-5-1-0-sp3.md)的升级说明。


## 创作

- 在浏览器刷新时，在主题或映射的文件夹级别配置文件中应用的自定义CSS将恢复到预览模式中的默认样式。 （指南 — 31098）
- 无法从&#x200B;**另存为新版本**&#x200B;对话框向主题添加多个&#x200B;**版本标签**。 （指南 — 32716）


## 资产管理

- 无法从Assets UI的&#x200B;**版本历史记录**&#x200B;面板中删除版本标签。 （指南 — 38276）


## 审阅

- 当审核者完成审核任务或发起者更新审核任务而未输入注释时，发送的通知电子邮件将显示最近的前一个注释。 （指南 — 33590）

## 发布

- 使用旧版组件映射生成AEM Sites输出时，使用`copy-to`属性的主题将通过`copy-from`主题的名称（而不是`copy-to`属性中设置的名称）发布。 （指南 — 22155）
- 使用动态基线生成本机PDF输出时，术语&#x200B;**PDFProject**&#x200B;显示为PDF标题，而不是实际的映射标题。 （指南 — 31102）

## 平台

- 在主题或映射中使用`scope="external"`引用DAM内容会导致资源的相对路径被替换为GUID。 （指南 — 35605）

## 已知问题

Adobe已发现5.1.0 Service Pack 3版本的以下已知问题：

- 当您从任务详细信息页面将审核任务标记为完成时，任务已完成并关闭；但是，其状态在审核功能板上继续显示为&#x200B;**进行中**。 （指南 — 39375）
