---
title: 创建映射
description: 在AEM Guides中使用“映射编辑器”创建映射。 查找基于映射模板创建映射文件的步骤。
feature: Authoring, Map Editor
role: User
source-git-commit: fa07db6a9cb8d8f5b133258acd5647631b22e28a
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# 创建映射 {#id176FEN0D05Z}

AEM Guides提供两个现成的映射模板 — DITA映射和Bookmap。 您还可以创建自己的映射模板并与作者共享这些模板以创建映射文件。

执行以下步骤以创建映射文件：

1. 在Assets UI中，导航到要创建映射文件的位置。

1. 单击&#x200B;**创建** \> **DITA映射**。

1. 在Blueprint页面上，选择要使用的映射模板类型，然后单击&#x200B;**下一步**。

   >[!NOTE]
   >
   > 在映射文件中引用主题的方式取决于映射模板。 例如，如果选择“映射”模板，则使用主题引用\(`topicref`\)来引用主题。 如果是Bookmap，则使用DITA中的`chapter`元素创建主题引用。

   ![](images/map-template.png){width="650" align="left"}

1. 在“属性”页面上，指定映射&#x200B;**标题**。

1. \（可选\）指定文件&#x200B;**名称**。

   如果管理员已根据UUID设置配置了自动文件名，则您将看不到用于指定文件名的选项。 基于UUID的文件名会自动指定给该文件。

   如果文件命名选项可用，则也会根据地图的标题自动建议名称。 如果要手动指定映射文件名，请确保文件名不包含任何空格、撇号或大括号，并且以`.ditamap`结尾。

1. 单击&#x200B;**创建**。

   出现“Map Created（映射已创建）”消息。

   您从Assets UI **创建** \> **DITA映射**&#x200B;或Web编辑器创建的每个新映射文件都分配了一个唯一的映射ID。 此外，新映射还会另存为DAM中的最新工作副本。 在保存新创建的映射的修订版之前，您不会在“版本历史记录”中看到任何版本号。 如果打开映射进行编辑，则版本信息将显示在映射文件选项卡的右上角：

   ![](images/first-version-map-none.png){width="650" align="left"}

   新创建的映射的版本信息显示为&#x200B;*none*。 保存新版本时，会为其分配一个版本号1.0。有关保存新版本的更多信息，请参阅[另存为新版本](web-editor-features.md#save-as-new-version-id209ME400GXA)。

   您可以选择在配置的映射编辑器中打开映射进行编辑，或将映射文件保存在AEM存储库中。

   >[!NOTE]
   >
   > 要使用高级映射编辑器，请在Web编辑器中访问映射文件。 如果管理员已将高级映射编辑器配置为映射文件中的默认编辑器，则直接在高级映射编辑器中打开映射文件以进行编辑。 请参阅安装和配置Adobe Experience Manager Guidesas a Cloud Service中的&#x200B;*将高级映射编辑器设置为默认值*&#x200B;部分。


**父主题：**[&#x200B;使用映射编辑器](map-editor.md)
