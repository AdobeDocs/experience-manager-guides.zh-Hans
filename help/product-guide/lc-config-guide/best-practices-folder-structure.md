---
title: 设置文件夹结构的最佳实践
description: 了解在Experience Manager Guides中处理学习和培训内容时设置文件夹结构的最佳实践。
feature: Authoring
role: Admin
level: Experienced
exl-id: 1b99ade0-0eee-42c3-a383-0c3774b6c1f6
TQID: https://experienceleague.adobe.com/jfoPbeASfVpgWYR2-cKacAdhWKPw-2j6qliqzjEzgFw
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
  - id: b1210526-416b-4ef6-bcc0-1692e99f30e9
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
subfeature_v2:
  - id: a7a242db-c88c-4e44-818b-bfb4ef92efdf
  - id: c8841798-1a28-4264-a46a-984860f8e6f6
  - id: dc1f7602-db3c-4ad4-a440-ff999bb16455
  - id: f7774ebe-aec9-42b6-97e4-5002acdc712e
  - id: f9dbea21-a714-40dd-bc90-080d8046c93f
  - id: fd456af4-cb12-4a34-8cc4-b74adf885626
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ff832d30f88c5810017e1a1ee41d644619f7331f
workflow-type: tm+mt
source-wordcount: 625
ht-degree: 0%

---

# 设置文件夹结构的最佳实践

本文为管理员提供了在Adobe Experience Manager Guides中设置文件夹结构的基本步骤和最佳实践。 组织良好的文件夹层次结构可确保用于学习和培训内容的流畅的创作、发布和翻译工作流。

## 设置文件夹结构

要允许访问Experience Manager Guides的各种创作、发布和翻译功能，请确保在正确的层次结构中设置文件夹，如下所述。

**创建根级文件夹**

首先，为您的组织创建根文件夹。 这是所有部门级文件夹和常用共享资产的基础。

示例：`/content/dam/ABC-Corp/`

在此根文件夹中，创建一个专用文件夹来管理将在多个部门中使用的资产。 例如，创建一个&#x200B;**常用**&#x200B;文件夹以包含共享资源，如图像、视频等。

![](assets/root-level-folder.png)

**创建部门级文件夹**

为每个部门（如HR、Finance、Legal）创建单独的文件夹，以便他们能够管理自己的内容。

![](assets/department-level-folders.png)
*Caption：在根文件夹*&#x200B;中为HR部门创建了单独的文件夹结构

**设置部门级文件夹的最佳实践**

- 在每个部门下为部门级公用资产创建专用&#x200B;**公用** > **资产**&#x200B;文件夹（如果需要）。
- 如果要共享内容以进行翻译，请创建特定于语言的文件夹（例如en、de、fr）。 作者应仅在源语言文件夹（如en）中创建或更新内容，因为翻译工作流中不包含源语言文件夹之外的内容。 其他语言文件夹可以作为占位符保留为空。 了解有关[内容翻译](../user-guide/translation.md)的详细信息。
- 可以利用权限来限制特定部门或用户对新创建的文件夹结构的访问权限。 例如，分配权限以确保只有HR部门用户可以创建或修改指定文件夹中的内容。

对金融、法律等其他部门重复相同的结构。

## 设置输出文件夹结构

`fm-ditaoutputs`文件夹用作从学习和培训内容生成的输出的默认存储位置。 这些输出通常包括&#x200B;**alm**&#x200B;文件夹中的SCORM包（ZIP文件）和&#x200B;**pdf**&#x200B;文件夹中的PDF。如果需要，可以从&#x200B;**映射控制台**&#x200B;在预设级别更改此默认输出路径。

![](assets/fmdita-output-lc.png)

使用多个部门时，请考虑在`fm-ditaoutputs`文件夹结构中创建部门特定的文件夹，以确保特定部门内的用户有权访问相关的输出文件夹。

## 创建用户并将其分配给适当的组

建立文件夹层次结构后，您可以开始创建用户并将他们添加到组，以便他们有权访问Experience Manager Guides中的相关功能。 Experience Manager Guides提供三个现成的组 — Authors、Reviewer和Publishers。 根据用户关联的组，允许他们执行特定任务。 例如，发布任务只能由发布者执行，而不能由作者执行。

要创建新用户并将他们添加到组，请导航到&#x200B;**工具** > **安全性** > **用户**。

在“用户管理”页面上，选择&#x200B;**创建**&#x200B;以创建新用户。 添加用户详细信息并将其分配给组。

![](assets/create-users-page.png)

有关详细信息，请查看[用户管理和安全性](../cs-install-guide/user-admin-sec.md)


## 为每个用户组分配权限

将用户添加到相应的组后，请在组级别配置权限，以确保他们有权访问存储库中的正确创作和输出文件夹。

要分配权限，请导航到&#x200B;**工具** > **安全性** > **权限**。

这些权限可帮助确保用户只能在其指定的文件夹中创建或修改内容。

有关详细信息，请在AEM中查看[权限](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/security#permissions-in-aem)。

