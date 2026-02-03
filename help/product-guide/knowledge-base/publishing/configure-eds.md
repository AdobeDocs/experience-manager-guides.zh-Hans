---
title: Experience Manager Guides和Edge Delivery Services (Beta)
description: 了解Edge Delivery Services (Beta)如何扩展Experience Manager Guides的创作和发布可能性。
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 7ca2eeb0356f3c82a8d970f291006fc6d19aca23
workflow-type: tm+mt
source-wordcount: '1532'
ht-degree: 0%

---

# Experience Manager Guides和Edge Delivery Services (Beta)

Adobe Experience Manager Guides允许您通过基于GitHub的专用发布配置文件，直接将DITA内容发布到Edge Delivery Services (EDS)(当前在&#x200B;*Beta*&#x200B;中提供)。 此功能使组织能够提供高性能、响应式文档体验，同时在Experience Manager Guides中维护基于DITA的创作工作流。

有关在Adobe Experience Manager中使用EDS的详细信息，请查看[Edge Delivery Services概述](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/edge-delivery/overview)。

要支持从Experience Manager Guides发布到EDS (Beta)，您必须在GitHub和Experience Manager Guides中完成一系列配置步骤。 以下各节将依次概述每个步骤，并解释它们如何在整个发布工作流程中协同工作。

1. [设置和配置适用于EDS的GitHub (Beta)](#set-up-and-configure-github-for-eds-beta)
2. [在Experience Manager Guides中创建并配置EDS (Beta)的发布配置文件](#create-and-configure-a-publish-profile-for-eds-beta-in-experience-manager)
3. [使用EDS块自定义输出](#customize-output-using-eds-blocks)

若要快速视频演练，请查看AEM Guides中的[发布](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-guides/using/knowledge-base/expert-session/publishing-in-aem-guides-aug25)。



## 设置和配置适用于EDS的GitHub (Beta)

本节介绍如何设置和配置GitHub以与EDS (Beta)一起使用。 它介绍如何使用Adobe样板创建存储库，通过AEM代码同步将GitHub连接到Adobe Experience Manager，配置所需的GitHub和OAuth应用程序，以及定义用于发布内容的存储库装入点。

### 创建适用于EDS (Beta)的GitHub存储库

EDS (Beta)需要一个具有预定义结构的GitHub存储库。 Adobe提供了专为Experience Manager Guides用户设计的官方模板存储库。

执行以下步骤可创建存储库：

1. 打开Experience Manager Guides模板存储库[`aem-guides-boilerplate`](https://github.com/adobe/aem-guides-boilerplate)。
   ![](assets/eds-boilerplate-template.png){align="left"}

2. 使用此模板创建新存储库。 了解[从模板创建存储库](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)。 确保将存储库可见性设置为&#x200B;*Public*，以便EDS可以访问该存储库。

   ![](assets/eds-create-new-repo.png){align="left"}

存储库现已创建并与样板模板结构保持一致。

![](assets/eds-repo-created-github-view.png){align="left"}

### 通过AEM代码同步将GitHub连接到Adobe

Adobe Experience Manager使用名为&#x200B;**AEM Code Sync**&#x200B;的GitHub应用程序将内容从Experience Manager Guides推送到GitHub。

执行以下步骤以安装和配置&#x200B;*AEM代码同步*&#x200B;应用程序：

1. 导航到[AEM代码同步](https://github.com/apps/aem-code-sync)页面，然后选择&#x200B;**安装**。
2. *AEM代码同步*&#x200B;监视存储库更改并确保将更新正确推送到GitHub。

   >[!NOTE]
   >
   > 安装应用程序时，请确保您使用的是拥有存储库的同一GitHub帐户。

   ![](assets/eds-aem-code-sync-page.png){align="left"}
3. 在下一页上，授予对您创建的存储库的访问权限。 为此，请选择&#x200B;**仅选择存储库**&#x200B;选项，然后从下拉列表中选择您的存储库。

   ![](assets/eds-aem-code-sync-install-authorize.png){width="350" align="left"}
4. 选择&#x200B;**安装并授权**。

您将被重定向到GitHub设置页面，同时确认已成功注册&#x200B;*AEM代码同步*&#x200B;应用程序。 您还可以从此页面保存您网站的预览和实时URL。

![](assets/eds-aem-code-sync-registered.png){align="left"}

### 创建新的GitHub应用程序

1. 在GitHub上，导航到左侧边栏并选择&#x200B;**开发人员设置**。
2. 在左侧边栏中，选择&#x200B;**GitHub应用程序**。
3. 选择&#x200B;**新GitHub应用程序**。

   ![](assets/eds-new-github-app.png){width="650" align="left"}
4. 在&#x200B;**注册新的GitHub应用程序**&#x200B;页面上，提供以下详细信息：
   - **GitHub应用名称**：输入应用名称。 例如，`USERNAME-eds-app`，其中USERNAME是您的GitHub用户名。
   - **主页URL**：输入Experience Manager Guides实例的URL。

     示例URL（格式）： `https://<aem-author-url>/libs/fmdita/clientlibs/xmleditor/page.html`

     示例URL： `https://author-p16602-e335172-cmstg.adobeaemcloud.com/libs/fmdita/clientlibs/xmleditor/page.html`
   - **回调URL**：与主页URL相同。
   - **Webhook URL**：禁用此选项。
   - **存储库权限**：为&#x200B;**操作、管理和证明**&#x200B;设置&#x200B;*读取和写入*&#x200B;权限。
5. 选择&#x200B;**创建GitHub应用程序**。

您的应用程序现已准备就绪。 您将被重定向到GitHub应用程序的&#x200B;**设置**&#x200B;页面。

![](assets/eds-github-app-registered-page.png){align="left"}

### 创建新的OAuth应用程序

在Experience Manager Guides中创建EDS (Beta)发布配置文件时，需要使用OAuth应用程序对用户进行身份验证。 它使用&#x200B;*客户端ID*&#x200B;和&#x200B;*客户端密钥*&#x200B;启用安全登录流程。

执行以下步骤可创建新的OAuth应用程序：

1. 在GitHub上，导航到左侧边栏并选择&#x200B;**开发人员设置**。
2. 在左侧边栏中，选择&#x200B;**OAuth应用程序**。
3. 选择&#x200B;**新建OAuth应用程序**。

   ![](assets/eds-new-oauth-app.png){width="650" align="left"}
4. 通过提供以下强制性详细信息注册您的应用程序：
   - **应用程序名称**：输入EDS存储库的名称
   - **主页URL**：输入Experience Manager Guides实例的URL。 （有关示例URL格式，请参阅[创建新的GitHub应用程序](#create-a-new-github-app)部分的步骤4）。
   - **授权回调URL**：与主页URL相同
5. 选择&#x200B;**启用设备流**&#x200B;选项，然后选择&#x200B;**注册应用程序**&#x200B;以完成注册。

   ![](assets/eds-new-github-app-register.png){width="650" align="left"}

您的应用程序现已准备就绪。 记下&#x200B;*客户端ID*。 在Experience Manager Guides中配置发布配置文件时，您现在或以后最多可以生成五个&#x200B;*客户端密钥*。

![](assets/eds-new-oauth-app-page.png){align="left"}


### 在EDS (Beta)存储库中配置装载点URL

EDS (Beta)从&#x200B;*文件中定义为*&#x200B;装入点`fstab.yaml` URL的GitHub存储库路径中读取内容。

要在`fstab.yaml`文件中配置挂载点URL，请执行以下操作：

1. 在存储库中打开`fstab.yaml`文件并更新以下内容：
   - `your-user-name`
   - `your-repo-name`

   >[!NOTE]
   >
   > 在装入点URL中，`main`表示要发布内容的分支，`docs`表示您正在处理的EDS (Beta)存储库的根文件夹。 如果您希望在GitHub上更改分支名称，则必须在&#x200B;*装入点* URL（在`fstab.yaml`文件中）以及Experience Manager Guides中的相应EDS发布配置文件中更新相同的分支名称。

   ![](assets/eds-fstab-yaml-file.png){width="650" align="left"}
2. 选择&#x200B;**提交更改**，输入提交详细信息，然后确认。
3. 返回[开发人员设置](https://github.com/settings/apps)，找到您的应用程序，然后选择&#x200B;**编辑**。

   ![](assets/eds-edit-github-app.png){width="650" align="left"}
4. 导航到&#x200B;**安装应用程序**&#x200B;页面，然后选择&#x200B;**安装**。

   ![](assets/eds-install-eds-app.png){width="650" align="left"}
5. 重复步骤2和3，从[通过AEM代码同步](#connect-github-to-adobe-via-aem-code-sync)部分将GitHub连接到Adobe以授权存储库。

## 在Experience Manager中创建并配置EDS (Beta)的发布配置文件

以下部分将依次概述每个步骤，并解释如何在Experience Manager Guides中设置EDS (Beta)发布配置文件、配置输出预设以及使用EDS (Beta)生成输出。

### 创建EDS (Beta)发布配置文件

1. 转到&#x200B;**[Workspace设置](/help/product-guide/cs-install-guide/workspace-settings.md)** **>** **发布配置文件**。
2. 选择&#x200B;**+**&#x200B;图标以创建新的发布配置文件并提供以下详细信息：
   - **服务器类型**：从下拉列表中选择&#x200B;**GitHub Edge Delivery Services (Beta)**。
   - **名称**：输入此配置文件的名称。
   - **存储库名称**：使用从样板创建的GitHub存储库名称。
   - **用户名**：输入您的GitHub用户名。
   - **分支main**：设置为主要（默认）。
   - **根文件夹**：设置为文档（默认）。
   - **客户端ID和客户端密钥**：从GitHub应用程序获取它们（有关详细信息，请参阅[创建新的OAuth应用程序](#create-a-new-oauth-app)部分）。
3. 选择&#x200B;**登录**&#x200B;以进行身份验证。

   ![](assets/eds-publish-profile.png){width="650" align="left"}
4. 成功验证后，选择&#x200B;**保存**。

您的EDS (Beta)发布配置文件现已配置完成。

### 创建EDS (Beta)的输出预设并生成输出

1. 在地图控制台中打开您的地图。
2. 在&#x200B;**输出预设**&#x200B;选项卡中，选择&#x200B;**+**&#x200B;以创建新的输出预设。
3. 在&#x200B;**新建输出预设**&#x200B;对话框中，提供以下详细信息：
   - **类型**：选择&#x200B;**Edge Delivery服务(Beta)**
   - **名称**：提供此预设的名称
4. 选择&#x200B;**添加**。

   ![](assets/eds-output-preset.png){width="650" align="left"}
5. 打开新创建的EDS (Beta)输出预设，并导航到&#x200B;**配置**&#x200B;选项卡。
   - 选择在上一步中创建的发布配置文件。
   - 启用&#x200B;**推送至**。

   启用&#x200B;**实时推送**&#x200B;后，生成的输出将提交到GitHub，并且相应的更新将立即传播到实时网站。

   ![](assets/eds-output-preset-config-tab.png){width="650" align="left"}

6. 选择&#x200B;**保存**，然后选择&#x200B;**生成输出**。

>[!NOTE]
>
> 生成的输出存储在EDS (Beta)存储库的&#x200B;**文档**&#x200B;文件夹中。

现在会生成EDS (Beta)输出。 内容以简洁的响应布局显示。 它包括常规元素，例如页面标题、痕迹导航、正文内容以及主题中使用的任何块。 左侧的目录（从地图生成）可帮助您跨主题导航，而右侧的迷你目录会突出显示当前页面中的部分。 整个输出完全响应，确保跨设备优化、一致的读取体验。

![](assets/eds-site-output.png){align="left"}

## 使用EDS块自定义输出

EDS使用`blocks`来控制内容的不同部分的样式和显示方式。 您可以修改现有块或创建自定义块。

以下列出的示例将指导您逐步自定义现有块并创建新块以设置Experience Manager Guides中最终EDS (Beta)输出的样式。

### 自定义痕迹导航块以更新其文本颜色

跨页面使用痕迹导航，以帮助用户了解它们在文档中的位置。 由于此块在整个网站中始终显示，因此更新其样式可以统一更新设计。

执行以下步骤可自定义痕迹导航块以更新其文本颜色：

1. 转到您的GitHub存储库并打开`blocks`文件夹。
2. 选择&#x200B;**痕迹导航**&#x200B;块。

   ![](assets/eds-breadcrumbs.png){width="650" align="left"}
3. 打开`css`文件并更新文本颜色。
4. 将更改提交到GitHub。
5. 刷新实时网站以查看更新。

### 更新EDS (Beta)脚本以在发布的输出中创建自定义元素

在某些情况下，您可能希望仅设置内容特定部分的样式。 请使用自定义块执行以下步骤来实现这一点。

1. 打开主题文件并选择标记元素中的文本。

   在以下屏幕截图中，选择了`example`标记中的内容。
   ![](assets/eds-example-tag-org-output.png){width="650" align="left"}
2. 要配置`example`标记中的文本，请执行以下操作：
   - 导航到&#x200B;**内容属性**。
   - 添加`outputclass`属性。
   - 将其值设置为`example eds-force-block`。
   - 选择&#x200B;**添加**。
     ![](assets/eds-example-tag.png){width="650" align="left"}
3. 保存并重新生成输出。
4. 在`outputclass`目录中创建一个与`blocks`同名的新文件夹。 了解[将文件添加到存储库](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository#adding-a-file-to-a-repository-using-the-command-line)。

   ![](assets/eds-example-folder.png){width="650" align="left"}
5. 添加必需的`css`和可选的`js`文件。

   ![](assets/eds-example-folder-subfolders.png){width="650" align="left"}
6. 提交更改并重新生成输出。

所选内容现在显示块中定义的自定义样式。

![](assets/eds-example-output.png){width="650" align="left"}