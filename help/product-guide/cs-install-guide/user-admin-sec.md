---
title: 用户管理和安全性
description: 了解用户管理和安全的工作原理
exl-id: 10ab0f3c-97dc-4293-ab73-75b438c03d99
feature: User Management
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/QpFE9DrZXxZTfONQFEtNCZCBRu5zOhjFkf1PcVj9sfU
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: b1210526-416b-4ef6-bcc0-1692e99f30e9
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
  - id: d90290ec-3e61-4ebd-8649-bcafe0836803
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
subfeature_v2:
  - id: a7a242db-c88c-4e44-818b-bfb4ef92efdf
  - id: c8841798-1a28-4264-a46a-984860f8e6f6
  - id: f7774ebe-aec9-42b6-97e4-5002acdc712e
  - id: f9dbea21-a714-40dd-bc90-080d8046c93f
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 728
ht-degree: 12%

---

# 用户管理和安全性 {#id181AED00G5Z}

要在AEM Guides中访问和配置功能，您需要创建用户。 然后，可以为这些用户分配访问AEM Guides中所有功能或特定功能的权限。 了解如何配置和维护用户授权，并了解在AEM中身份验证和授权的工作原理基础。

AEM文档中的以下主题将帮助您了解用户管理与安全相关的概念和功能：

- [AEM 用户、组和权限](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=zh-Hans)

- [用户管理与安全性](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=zh-Hans)


## AEM Guides创建的用户组 {#id181TF0K0MHT}

AEM Guides提供了三个现成的组。 这些组是： *作者*、*审阅者*&#x200B;和&#x200B;*发布者*。 根据用户关联的组，允许他们执行特定任务。 例如，发布任务只能由发布者执行，而不能由作者或审阅者执行。 同样，作者可以创建新主题，查看者只能查看主题。

>[!TIP]
>
> 有关设置用户权限的最佳实践，请参阅最佳实践指南中的&#x200B;*权限*&#x200B;部分。

下表列出了各种任务以及可以执行这些任务的组：

| 任务 | 作者 | 审阅者 | 发布者 |
|----|-------|---------|----------|
| 创建DITA主题 | 是 |   | 是 |
| 创建DITA映射 | 是 |   | 是 |
| 映射收藏集 | 是 |   | 是 |
| 创建审核任务 | 是 |   | 是 |
| 审核主题[1](#fntarg_1) | 是 | 是 | 是 |
| 关键分辨率 | 是 |   | 是 |
| 签出/签入 | 是 |   | 是 |
| 编辑主题 | 是 |   | 是 |
| 移动主题 | 是 |   | 是 |
| 编辑主题属性 | 是 |   | 是 |
| 复制 | 是 |   | 是 |
| 删除 | 是 |   | 是 |
| 共享 | 是 |   | 是 |
| **文档状态** |  |  |  |
| 创建/编辑文档状态配置文件 |   |   | 是 |
| 更改文档状态[2](#fntarg_2) | 是 | 是 | 是 |
| **DITA映射控制台中可用的功能\（输出预设选项卡\）** |  |  |  |
| 生成 |   |   | 是 |
| 编辑 |   |   | 是 |
| 复制 |   |   | 是 |
| 创建 |   |   | 是 |
| 删除预设 |   |   | 是 |
| **DITA映射控制台中可用的功能\（输出选项卡\）** |  |  |  |
| 查看生成的输出 | 是 |   | 是 |
| **DITA映射控制台中可用的功能\（主题选项卡\）** |  |  |  |
| 创建审核任务 | 是 |   | 是 |
| 编辑 | 是 |   | 是 |
| **DITA映射控制台中可用的功能\（“基线”选项卡\）** |  |  |  |
| 创建 |   |   | 是 |
| 编辑 |   |   | 是 |
| 复制 |   |   | 是 |
| 移除 |   |   | 是 |
| DITA映射控制台\（报表选项卡\） | 是 |   | 是 |
| DITA映射控制台中可用的&#x200B;**功能\（条件预设\）** |  |  |  |
| 创建/编辑条件预设 |   |   | 是 |

## 有关用户组的其他说明

以下列表包含与用户组和相应权限相关的一些推荐和点：

- 如果您希望用户启动翻译或审核工作流，请确保该用户是&#x200B;*发布者*&#x200B;和&#x200B;*项目管理员组*&#x200B;的成员。

- 用户必须具有所需的源语言文件夹和目标语言文件夹的读取、创建、删除和修改权限。

- 如果您创建项目，则您是具有&#x200B;*发布者*&#x200B;权限的项目的所有者。 为使项目中的其他用户能够查看其团队成员、创建任务或创建工作流，他们必须对`/home/users`和`/home/groups`节点具有读取访问权限。 授予`/home/users`和`/home/groups`节点的读取访问权限的一种方法是授予`projects-users`组的读取访问权限。

- *审阅人*&#x200B;可以从“项目”控制台或收件箱通知链接访问和添加有关审阅主题的审阅注释。 此外，此访问权限仅在审核任务打开时可用。

- 默认情况下，*发布者*&#x200B;被授予对DAM中以下文件夹的访问和权限：

   - `/content/fmdita` -\>读写

   - `/content/dam/fmdita-outputs` -\>读写

   - `/content/output/sites` -\>读写

  如果您使用除上述默认发布位置之外的任何其他位置，则必须向发布者授予明确的读写权限。

- *作者*、*审阅者*&#x200B;和&#x200B;*发布者*&#x200B;组下的所有用户都拥有DAM中所有内容的读取权限。

- 必须通过用户管理页面向用户分配文件夹级别的权限。

- 如果您希望您的用户能够在DAM上执行搜索操作，则让您的用户成为&#x200B;*dam-users*&#x200B;组的成员。

- 如果要向任何用户授予管理员权限，可以通过授予他们通过AEM标准组(如&#x200B;*管理员*、*projects-administrators*&#x200B;或OSGI配置\（Felix控制台\）)的访问权限来实现此目的。

- 要授予用户更改文档状态的权限，请确保在文档状态配置文件的状态转换部分中添加用户。

[1](#fnsrc_1)如果邀请了&#x200B;*作者*&#x200B;和&#x200B;*发布者*&#x200B;进行审阅。[2](#fnsrc_2)取决于在文档状态配置文件中授予该用户的权限。
