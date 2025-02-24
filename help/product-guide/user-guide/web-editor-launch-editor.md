---
title: 启动编辑器
description: 了解如何从Adobe Experience Manager Guides的AEM导航页面、AEM Assets UI和映射控制台中启动编辑器。
exl-id: cdde7c29-ee49-4e17-902e-1e2bd6f32e8a
feature: Authoring, Web Editor
role: User
source-git-commit: b8f3756e0e8f0338942efb77f00600703be8f6d8
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# 启动编辑器 {#id2056B0140HS}

您可以从以下位置启动编辑器：

- [Adobe Experience Manager导航页面](#adobe-experience-manager-navigation-page)
- [ADOBE EXPERIENCE MANAGER ASSETS UI](#adobe-experience-manager-assets-ui)
- [映射控制台](#map-console)

以下部分介绍了如何从各种位置访问和启动编辑器的详细信息。

## Adobe Experience Manager导航页面

登录Experience Manager时，您会看到“导航”页面：

![](images/web-editor-from-navigation-page.png){width="800" align="left"}

选择&#x200B;**指南**&#x200B;链接将转到[Adobe Experience Manager Guides主页](./intro-home-page.md)。

![](images/aem-home-page.png){width="800" align="left"}

要启动编辑器，请转到导航栏，然后从下拉列表中选择&#x200B;**编辑器**。 默认情况下，“主页”处于选中状态。

![](images/editor-home-page-dropdown.png){width="350" align="left"}

由于您在不选择任何文件的情况下启动了“编辑器”，因此会显示一个空白的“编辑器”屏幕。 您可以从Experience Manager **存储库**&#x200B;或您的&#x200B;**收藏集**&#x200B;打开文件进行编辑。

![](images/web-editor-launch-page.png){width="800" align="left"}

或者，您也可以通过打开[Adobe Experience Manager Guides主页体验](./intro-home-page.md)的&#x200B;**最近使用的文件**&#x200B;构件和&#x200B;**收藏集**&#x200B;构件中存在的现有文件来启动编辑器。


要返回到Experience Manager导航页面，请选择位于顶部标题左上角的Adobe Experience Manager徽标。


## ADOBE EXPERIENCE MANAGER ASSETS UI

可以从中启动编辑器的另一个位置来自Experience Manager Assets UI。 您可以选择一个或多个主题并直接在编辑器中打开它们。

要在编辑器中打开主题，请执行以下步骤：

1. 在Assets UI中，导航到要编辑的主题。

   >[!NOTE]
   >
   > 您还可以查看主题的UUID。

   ![](images/assets_ui_with_uuid_cs.png){width="800" align="left"}

   >[!IMPORTANT]
   >
   > 确保您对包含要编辑的主题的文件夹具有读写权限。

1. 若要获得该主题的独占锁定，请选择该主题并选择&#x200B;**签出**。

   >[!IMPORTANT]
   >
   > 如果管理员配置了&#x200B;**禁用编辑而不锁定文件**&#x200B;选项，则必须在编辑之前签出文件。 如果不签出文件，您将无法查看编辑选项。

1. 关闭资源选择模式并选择要编辑的主题。

   此时将显示主题的预览。

   您可以从“列表”视图、“卡片”视图和“预览”模式中打开编辑器。

   >[!IMPORTANT]
   >
   > 如果要打开多个主题进行编辑，请从资产UI中选择所需的主题，然后选择&#x200B;**编辑**。 请确保您的浏览器未启用弹出窗口阻止程序，否则将仅打开选定列表中的第一个主题进行编辑。

   ![](images/edit-from-preview_cs.png){width="800" align="left"}

   如果您不想预览某个主题并希望直接在编辑器中打开该主题，请从卡片视图中选择快速操作菜单中的&#x200B;**编辑**&#x200B;图标：

   ![](images/edit-topic-from-quick-action_cs.png){width="800" align="left"}

   将在编辑器中打开主题。

   ![](images/edit-mode.png){width="800" align="left"}

您还可以在Assets UI中打开映射文件，并启动编辑器以编辑映射文件中的主题。

要在编辑器中打开映射，请执行以下步骤：

1. 在Assets UI中，导航到包含要编辑的主题的映射文件并将其选定。
1. 在DITA映射控制台中，导航到&#x200B;**主题**&#x200B;选项卡。 将显示映射文件中的主题列表。
1. 选择要编辑的主题文件。
1. 选择&#x200B;**编辑主题**。

   ![](images/edit-topics-map-console_cs.png){width="800" align="left"}

1. 将在编辑器中打开主题。

   >[!IMPORTANT]
   >
   > 如果管理员配置了&#x200B;**禁用编辑而不锁定文件**&#x200B;选项，则必须在编辑之前签出文件。 如果未签出文件，则文档将在编辑器中以只读模式打开。

## 映射控制台

要从“映射”控制台中打开编辑器，请执行以下步骤：

1. 打开主页，然后启动地图控制台。

   ![](images/editor-map-console-dropdown.png){width="350" align="left"}

   由于您在不选择任何映射文件的情况下启动了“映射”控制台，因此将显示一个空白的“映射”控制台屏幕。 您还可以从Experience Manager **存储库**&#x200B;或您的&#x200B;**收藏集**&#x200B;打开映射文件。

   ![](images/launch-map-console.png){width="500" align="left"}

1. 选择&#x200B;**选择映射**&#x200B;可打开包含要在编辑器中编辑的主题的映射文件。
1. 选择映射文件所在的路径。 选定的映射文件将添加到“映射”控制台。
1. 导航到映射文件，然后从下拉列表中选择&#x200B;**在编辑器中打开**。

   ![](images/map-console-open-in-editor.png){width="800" align="left"}

   将在编辑器中打开包含主题的映射文件进行编辑。

   ![](images/map-console-edit-topics.png){width="800" align="left"}






**父主题**： [编辑器简介](web-editor.md)
