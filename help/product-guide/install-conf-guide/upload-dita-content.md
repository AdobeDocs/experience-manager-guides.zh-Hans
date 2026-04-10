---
title: 上载现有DITA内容
description: 了解如何使用WebDAV工具和FrameMaker在Experience Manager Guides中上传现有DITA内容
feature: Migration
role: Admin
level: Experienced
source-git-commit: 834959a6a0e22cd5d2b2c5d0e57ceb6d45c0c666
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# 使用WebDAV工具和FrameMaker for On-Premise上载现有DITA内容

您很可能有一个包含要与AEM Guides一起使用的现有DITA内容的存储库。 对于此类现有内容，您可以使用以下任意方法将您的内容批量上传到AEM存储库。

- [使用WebDAV工具](#use-a-webdav-tool)
- [使用FrameMaker](#use-framemaker)

## 使用WebDAV工具

如果在任何其他DITA编辑器中创作主题和映射，则可以使用任何WebDAV工具上载文件。 本节中给出的过程使用WinSCP作为WebDAV工具来上载内容。

执行以下步骤以使用WinSCP上载文件：

1. 在计算机上下载并安装WinSCP。

1. 启动WinSCP应用程序。

   此时将显示“登录”对话框。

1. 在“登录”对话框中，通过选择WebDAV作为&#x200B;**文件协议**&#x200B;并提供其他连接详细信息来指定“新建站点”设置，例如：

   - 托管AEM服务器的URL，

   - 端口号`\(default is 4502\)`，并且

   - 用于访问AEM服务器的用户名和密码。

1. 选择&#x200B;**登录**。

   成功连接后，您将在WinSCP用户界面中看到AEM Assets的内容。 您可以使用WinSCP文件资源管理器轻松浏览、创建、更新或删除内容。

## 使用WebDav工具以UUID上传内容 {#id201MI0I04Y4}

您可以使用以下任意方法通过UUID上传内容：

- 从本地系统拖放内容。
- 从AEM的Assets UI中使用&#x200B;**创建** \> **文件**&#x200B;工作流。
- 使用诸如WinSCP之类的工具。

如果您使用诸如WinSCP之类的工具，则可以通过在configMgr中设置&#x200B;**将具有相同UUID的旧文件移动到新文件夹**&#x200B;选项来定义要对重复文件执行的操作。 此选项定义对AEM存储库中其他某个位置可用的文件执行的操作。 此设置在configMgr的`*com.adobe.fmdita.config.ConfigManager*`包中可用。

默认情况下，**将具有相同UUID的旧文件移动到新文件夹**&#x200B;选项处于打开状态。 这意味着，如果上传的文件位于存储库中的其他某个文件夹中，则现有文件会被移动到当前位置并被上传的文件覆盖。 如果不选择此选项，则文件将在其现有位置被覆盖。

**有关使用基于UUID的文件的其他说明**：

在AEM存储库中移动或复制内容时，必须考虑以下几点：

- 将一个或多个文件从一个位置复制到另一个位置时，将为没有任何UUID的文件生成新的UUID。 此UUID会添加到文件的元数据中。

- 如果文件存在冲突或重复，则会为要复制或移动的新文件生成唯一的文件名。

- 任何两个文件都不能具有相同的UUID。 为所有新文件分配一个唯一的UUID。


将内容从本地系统移动或复制到AEM存储库时，必须考虑以下几点：

- 如果文件由两个不同的用户同时上传，则以后处理的文件会覆盖较早的文件。 然而，这种做法非常少见，应当避免。

- 当您从AEM存储库签出内容并在本地系统上做出更改时，请确保在上传文件时文件名未发生更改。

## 使用FrameMaker

Adobe FrameMaker附带强大的AEM连接器，可让您轻松地将现有DITA和其他FrameMaker文档`\(.book and .fm\)`上传到AEM。 您可以使用各种文件上传功能，例如上传单个文件、上传具有或不具有依赖关系的完整文件夹\（如内容引用、交叉引用和图形\）。

执行以下步骤以使用FrameMaker的AEM Connector上传内容：

1. 启动FrameMaker。

1. 打开&#x200B;**连接管理器**&#x200B;对话框。

   ![](assets/fm-aem-connector.png){width="550" align="left"}

1. 输入以下详细信息以连接到AEM存储库：

   - **名称**：输入描述性名称以标识与AEM服务器的连接。
   - **服务器**：输入AEM服务器的URL和端口号。

   - **用户名**/**密码**：输入用户名和密码以访问AEM服务器。

1. 选择&#x200B;**连接**。

   成功建立连接后，AEM存储库中的Assets将显示在存储库管理器窗口中。

   ![](assets/fm-repo-manager.png){width="550" align="left"}

   右键单击任何文件或文件夹可让您执行相关操作。 例如，如果右键单击文件夹，可以获得以下选项：上传文件、上传具有依赖关系的文件、上传整个文件夹等。






**父主题：**&#x200B;[&#x200B;迁移现有内容](migrate-content.md)
