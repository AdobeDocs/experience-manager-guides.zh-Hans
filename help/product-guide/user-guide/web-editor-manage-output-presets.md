---
title: 管理全局和文件夹配置文件输出预设
description: 了解如何在AEM Guides中作为管理用户创建、编辑、重命名、复制和删除全局和文件夹配置文件输出预设。
exl-id: 549c9fe2-77f8-423c-8b3e-b43e56055732
feature: Authoring, Features of Web Editor, Publishing
role: User
TQID: https://experienceleague.adobe.com/FCtMWJZh9bc9sayuHsMWnd-c6mZ0Uvi0ZAgv2lOSu-4
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
  - id: f9dbea21-a714-40dd-bc90-080d8046c93f
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 478
ht-degree: 0%

---

# 管理全局和文件夹配置文件输出预设 {#id22BLJ0D0V1U}

全局和文件夹配置文件预设仅适用于文件夹级别的管理用户。

作为管理员，Adobe Experience Manager Guides允许您为全局和文件夹配置文件创建和管理输出预设。 然后，您可以轻松地使用这些输出预设为与该全局或文件夹配置文件相关的所有映射生成输出。

执行以下步骤，为全局配置文件和文件夹配置文件创建输出预设：

1. 选择要为其创建输出预设的DITA映射。
1. 从映射文件的&#x200B;**选项**&#x200B;菜单中选择&#x200B;**编辑主题**&#x200B;选项。 将在编辑器中打开映射文件进行编辑。
1. 选择&#x200B;**在映射控制台中打开**&#x200B;图标以在映射控制台中打开映射文件。
1. 在“映射”控制台中，导航到&#x200B;**输出预设**&#x200B;选项卡，然后选择+图标以创建DITA映射的输出预设。

   ![](images/add-global-output-preset.png){width="350"}

1. 在&#x200B;**添加预设**&#x200B;对话框中输入以下详细信息：
   - 类型
   - 名称
   - Target \（对于知识库预设\）
1. 选中&#x200B;**添加到文件夹配置文件**&#x200B;复选框可为相关文件夹配置文件创建输出预设，然后选择&#x200B;**添加**。 预设已创建，并显示在所有相关映射的&#x200B;**输出预设**&#x200B;选项卡下。 \( ![](images/global-preset-icon.svg)\)图标表示文件夹配置文件级别预设。
1. 输入配置详细信息。 有关输出预设的详细信息，请查看[了解输出预设](./generate-output-understand-presets.md)。

   >[!NOTE]
   >
   > 添加到文件夹配置文件的这些预设与映射无关，因此这些预设不存在映射特定的配置。

1. 您可以选择右上角的&#x200B;**生成输出**&#x200B;图标来生成与所创建输出预设相关的映射的输出。 您可以查看输出生成过程的状态。 要查看输出，请在&#x200B;**成功**&#x200B;对话框中选择&#x200B;**查看输出**。

>[!NOTE]
>
> Experience Manager Guides还提供了现成的PDF输出预设，用于生成DITA映射的输出。

**选项菜单中的其他操作**

也可以从“选项”菜单对预设执行以下操作：

- **生成输出**：允许您为现有预设生成输出。
- **查看输出**&#x200B;和&#x200B;**查看日志**：用于查看生成的输出和日志的快速链接。
- 从&#x200B;**选项**&#x200B;菜单&#x200B;**重命名**、**复制**&#x200B;或&#x200B;**删除**&#x200B;现有的输出预设。
- **默认PDF**：允许您选择现有PDF预设作为默认PDF预设。 所选预设将为，然后用作默认预设，以使用地图的&#x200B;**下载为PDF**&#x200B;选项生成PDF输出。

>[!NOTE]
>
> 删除全局和文件夹配置文件中的输出预设时，该预设将反映在所有相关映射中，并且不会显示在&#x200B;**输出预设**&#x200B;选项卡下。

**父主题：**&#x200B;[&#x200B;使用Web编辑器](web-editor.md)
