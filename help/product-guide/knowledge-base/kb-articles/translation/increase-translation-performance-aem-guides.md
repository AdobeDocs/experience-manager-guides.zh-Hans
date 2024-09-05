---
title: 在AEM guides中提高DITA文件的翻译性能
description: 在AEM Guides中提高DITA翻译项目性能的最佳实践、提示和技巧
feature: Translation
role: User, admin
source-git-commit: b22dcdf2c040159b30128dfe97f0e5a0605ca068
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# 在AEM Guides中翻译要遵循的最佳实践

随着时间的推移，系统上的翻译活动增加，翻译项目的性能可能会降低。

每个翻译项目会生成多个用户组以供访问，从而增加系统内的用户组数量。 随着用户组数量的扩展，它会逐渐降低与用户权限相关的CRUD操作的速度，从而可能会影响整体AEM性能。 此外，如果翻译项目在完成后保持活动状态，可能会对AEM和翻译供应商之间的翻译同步性能产生负面影响。

**遵循下面概述的最佳实践将有助于保持高效的环境。**

## 如果您使用的版本低于4.6（内部部署）或2404（云）：

- 一旦翻译完成并批准，将所有项目标记为“非活动”。项目仍可供审查，并且只是标记为非活动。
   - 遵循这些步骤将有助于保持整体翻译性能的良好状态。
     ![不活动的翻译项目](../assets/translation/translation-project-image1.png)

- 对于标记为不活动的旧项目文件夹，应删除已批准和已审阅的文件夹
   - 执行以下步骤将有助于通过清除与此项目文件夹关联的临时翻译文件和用户组，保持整体翻译性能良好。
     ![删除翻译项目和文件夹](../assets/translation/translation-project-image2.png)


## 如果您位于上，请构建4.6或2404或更高版本：

您可以继续执行上述相同步骤。 从版本4.6/2404开始，AEM Guides为管理员引入了一个编辑器设置，用于禁用自动删除翻译项目。

参考：[自动删除或禁用已完成的翻译项目](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/user-guide/author-content/create-preview-topics/author-content-aem-guides/work-with-web-editor/translate-documents-web-editor#automatically-delete-or-disable-a-completed-translation-project)

![在AEM Guides ](../assets/translation/translation-project-image3.png)中删除并禁用翻译项目的自动设置