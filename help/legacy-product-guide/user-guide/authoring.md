---
title: 管理内容
description: 在AEM Guides中管理内容并确定您的角色和权限。 了解内容管理以及使用全局或文件夹级别配置文件的主要概念。
feature: Content Management
role: User
hide: true
exl-id: 54b960cf-fb00-4d4a-a836-9de4738c49a8
source-git-commit: 7286c3fb36695caa08157296fd6e0de722078c2b
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 9%

---

# 管理内容 {#id164JBG0M0T1}

在开始创建实际内容之前，您必须熟悉AEM Guides中内容管理的一些基本概念。 然后，从创建不同的用户组并组织资源开始。

## 重要概念

AEM中内容管理的一些关键概念如下所示：

**资产管理**

AEM Guides使用AEM的数字资源管理\(DAM\)来管理您的DITA文件。 您上传或签入DAM的文件存储为数字资产。 您可以在AEM Assets中管理和编辑资源。 有关资产管理的详细信息，请参阅[管理资产](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/manage-digital-assets.html?lang=zh-Hans)。

**链接管理**

移动或重命名文件或更改内容存储库中的文件夹结构，无需担心引用的损坏。 对受影响内容的所有引用和来自这些内容的引用都会自动更新。 删除从其他位置引用的内容时收到警告，以防止无意中断。

**管理版本**

AEM Guides为您的数字资源提供版本管理。 您可以从所选的DITA创作应用程序中轻松启用此功能。 允许编写器执行标准版本控制功能，如签入和签出。

有关创建版本或还原到特定版本的更多信息，请参阅[分支、还原和后续版本控制](web-editor-preview-topics.md#id193PG0Y051X)。

**本机DITA处理**

在AEM Guides维护DITA文件结构的同时，它还允许AEM使用元素映射将DITA元素映射到AEM组件，以本机方式处理DITA。 本机DITA处理在主题预览、AEM Sites发布和审阅工作流等功能中使用。

## 确定您的角色和权限 {#id181TF0K0MHT}

AEM Guides提供了三个现成的组。 这些组是： *作者*、*审阅者*&#x200B;和&#x200B;*发布者*。 根据您关联的组，您有权执行下表中所述的特定任务。 例如，发布任务只能由发布者执行，而不能由作者或审阅者执行。 同样，作者可以创建新主题，查看者只能查看主题。

>[!TIP]
>
> 有关设置用户权限的最佳实践，请参阅最佳实践指南中的&#x200B;*权限*&#x200B;部分。

下表列出了各种任务以及可以执行这些任务的组：

| 任务 | 作者 | 审阅者 | 发布者 |
|----|-------|---------|----------|
| 创建DITA主题 | 是 |   | 是 |
| 创建DITA映射 | 是 |   | 是 |
| 映射收藏集 | 是 |   | 是 |
| 创建审阅任务 | 是 |   | 是 |
| 审核主题[1](#fntarg_1) | 是 | 是 | 是 |
| 关键分辨率 | 是 |   | 是 |
| 签出/签入 | 是 |   | 是 |
| 编辑主题 | 是 |   | 是 |
| 移动主题 | 是 |   | 是 |
| 编辑主题属性 | 是 |   | 是 |
| 复制 | 是 |   | 是 |
| 删除 | 是 |   | 是 |
| 共享 | 是 |   | 是 |
| **文档状态** |
| 创建/编辑文档状态配置文件 |   |   | 是 |
| 更改文档状态[2](#fntarg_2) | 是 | 是 | 是 |
| **DITA映射控制台中可用的功能\（输出预设选项卡\）** |
| 生成 |   |   | 是 |
| 编辑 |   |   | 是 |
| 复制 |   |   | 是 |
| 创建 |   |   | 是 |
| 删除预设 |   |   | 是 |
| **DITA映射控制台中可用的功能\（输出选项卡\）** |
| 查看生成的输出 | 是 |   | 是 |
| **DITA映射控制台中可用的功能\（主题选项卡\）** |
| 创建审阅任务 | 是 |   | 是 |
| 编辑 | 是 |   | 是 |
| **DITA映射控制台中可用的功能\（“基线”选项卡\）** |
| 创建 |   |   | 是 |
| 编辑 |   |   | 是 |
| 复制 |   |   | 是 |
| 移除 |   |   | 是 |
| DITA映射控制台\（报表选项卡\） | 是 |   | 是 |
| DITA映射控制台中可用的&#x200B;**功能\（条件预设\）** |
| 创建/编辑条件预设 |   |   | 是 |

[1](#fnsrc_1)如果邀请了&#x200B;*作者*&#x200B;和&#x200B;*发布者*&#x200B;进行审阅。

[2](#fnsrc_2)取决于在文档状态配置文件中授予用户的权限。

## 内容创作的先决条件

**使用全局或文件夹级别的配置文件**

在企业中，不同的组或产品可能使用不同的创作模板、输出模板、条件属性配置文件\（或主题方案\）和Web编辑器配置。 仅在企业\（或全局\）级别配置这些组件会让作者难以获得体验，因为他们会看到与其无关的模板或配置文件。

AEM Guides允许您在企业\(global\)级别和文件夹级别配置创作\（topic或map\）模板、输出模板、条件属性和Web编辑器配置。 这样，您就可以分离企业中不同部门或产品的配置。

此外，您还可以将特定于文件夹的配置委派给部门或产品管理员，以分散管理。

有关设置全局和文件夹级别配置文件的详细信息，请参阅安装和配置Adobe Experience Manager Guides as a Cloud Service中的&#x200B;*配置全局或文件夹级别配置文件*。
