---
title: Web编辑器中的DITA映射报表
description: 从AEM Guides中的Web编辑器生成DITA映射报告。 了解如何为主题列表、多媒体、元数据和断开链接报表生成CSV。
feature: Report Generation
role: User
source-git-commit: 76c731c6a0e496b5b1237b9b9fb84adda8fa8a92
workflow-type: tm+mt
source-wordcount: '2366'
ht-degree: 0%

---

# Web编辑器中的DITA映射报表 {#id231HF0Z0NXA}

AEM Guides在Web编辑器中提供了一项功能，通过该功能，您可以检查引用的整体完整性并为其生成报告。

您可以从Web编辑器的&#x200B;**报告**&#x200B;选项卡中查看主题列表、管理所有引用的元数据以及查看当前映射的多媒体列表。

## 从“主题列表”视图中生成CSV

**主题列表**&#x200B;视图提供有关您的主题的详细信息，如引用类型、文档状态和作者。

可通过执行以下步骤来创建主题报告：

1. 在&#x200B;**存储库**&#x200B;面板中，在映射视图中打开DITA映射文件。
1. 单击&#x200B;**管理**&#x200B;选项卡。
1. 双击左侧的&#x200B;**主题列表**。 将显示DITA映射中存在的主题列表。

   ![](images/web-editor-topiclist-panel.png){width="800" align="left"}

1. 从&#x200B;**筛选器**&#x200B;面板中，您可以根据&#x200B;**引用类型** \（直接或间接\）、**文档状态** \（主题的当前状态）筛选主题。 例如，如果您的主题处于“编辑”、“正在审阅”或“已审阅”状态，则会列出这些主题\)或主题的&#x200B;**作者**。

1. 您还可以使用以下主题过滤选项来选择在列表中显示以下列：

   - **主题**&#x200B;主题标题在DITA映射中指定。 您可以单击该主题进行编辑。
   - **文件名**&#x200B;文件的名称。
   - **UUID**&#x200B;文件的通用唯一标识符\(UUID\)。
   - **文件位置**&#x200B;主题的完整路径。
   - **引用类型**&#x200B;引用类型 — 直接或间接引用。
   - **文档状态**&#x200B;主题的当前状态。
   - **作者**&#x200B;上次处理该主题的用户。
   - **父映射**&#x200B;直接引用主题的所有映射的列表。
   >[!NOTE]
   >
   > 单击&#x200B;**刷新**&#x200B;以获取新的主题列表，并查看映射文件中的任何更改或主题文件中的任何引用是否已更新。

1. 单击&#x200B;**下载CSV**&#x200B;可下载DITA映射中主题的当前快照。 CSV包含在&#x200B;**主题列表**&#x200B;视图中过滤的选定列和主题。 然后，您可以在任何CSV编辑器中打开此主题列表CSV文件。

**从元数据报表批量管理元数据**

AEM Guides允许您从Web编辑器标记DITA内容。 可以在单个主题中应用标记，或者使用批量标记功能在多个主题、DITA映射或子映射中应用多个标记。 您也可以将所有选定主题的文档状态更改为下一个可能的公共文档状态。

## 查看元数据

要在当前DITA映射中查看引用的元数据，请执行以下步骤：

1. 在“存储库”面板中，在“映射视图”中打开DITA映射文件。
1. 单击&#x200B;**管理**&#x200B;选项卡。
1. 双击左侧的&#x200B;**元数据**。 将显示DITA映射中所有引用的元数据列表。 这还包括媒体引用。

   ![](images/web-editor-metadata-panel.png){width="800" align="left"}

1. 从&#x200B;**筛选器**&#x200B;面板中，您可以根据&#x200B;**文档状态** \（主题的当前状态）筛选主题。 例如，如果您的主题处于“编辑”、“正在审阅”或“已审阅”状态，则将列出这些主题\)、**引用** \（直接或间接\）、**文件类型** \（映射、主题和图像\）。
1. 您还可以选择仅查看没有标记的&#x200B;**文件**，或者也可以从&#x200B;**标记**&#x200B;筛选器中选择特定标记以查看与其关联的文件。
   1. 您还可以使用以下主题过滤选项来选择在元数据列表中显示以下列：
      - **标题** \（默认选中\）在DITA映射中指定引用文件的标题。 您可以单击该文件进行编辑。您还可以在Web编辑器中单击并播放音频或视频文件。 您可以更改视频的音量或视图。 在快捷菜单中，您还可以选择下载、更改播放速度或查看画中画。

        >[!NOTE]
        >
        > 签出图标也会出现在签出文件的标题附近。 您可以将鼠标悬停在图标上以查看用户的名称。

      - **文件名**&#x200B;文件的名称。
      - **文件位置**&#x200B;文件的完整路径。
      - **标记** \（默认选中\）应用于文件的标记。

        >[!NOTE]
        >
        > 默认情况下，您可以查看文件的两个标记。 要查看更多标记，请单击&#x200B;**显示更多**。 单击&#x200B;**显示更少**&#x200B;以再次约定列表。

      - **引用类型**&#x200B;引用类型 — 直接或间接引用
      - **文档状态** \（默认选中\）引用文件的当前状态。
      - **文件类型** \（默认选中\）源文件的类型。 可用的选项有“映射”、“主题”和“图像”。
      - **签出者**&#x200B;已签出文件的用户。
1. 单击&#x200B;**下载CSV**&#x200B;可下载DITA映射中引用的当前快照。 CSV包含所选列和在“主题列表”视图中过滤的引用。 然后，您可以在任何CSV编辑器中打开此元数据CSV文件。

**更新元数据**

1. 要更新元数据，请选择要更新的文件。

   >[!NOTE]
   >
   > 您不能选择任何已签出的文件。 签出图标也会出现在签出文件的标题附近。 您可以将鼠标悬停在图标上以查看用户的名称。

1. 从顶部选择&#x200B;**管理**。

   ![](images/web-editor-manage-metadata.png){width="350" align="left"}

1. 如果要添加任何新标记，请从下拉列表中选择新标记，以将其应用于所有选定主题。 您还可以通过单击标记旁边的交叉图标来删除任何标记。

   >[!NOTE]
   >
   > 列出了应用于所有选定主题的通用标记。

1. 如果要更改所有选定参照的文档状态，请选择新文档状态。 该下拉菜单显示所有选定主题的常见可能状态。 例如，如果主题的当前状态为“正在审阅”，则可以查看“草稿”、“已批准”或“已审阅”状态。
1. 单击&#x200B;**更新**&#x200B;以更新元数据。 将显示元数据更新成功还是更新失败的确认消息。 您还可以单击&#x200B;**下载报表**，从确认对话框下载元数据CSV。 此CSV包含所选引用的更新状态的详细信息。

## 生成多媒体报告

**多媒体**&#x200B;报告提供了地图中使用的多媒体的详细信息，如标题、类型\（音频、视频和图像\）、使用多媒体的文件以及使用这些文件的引用类型。 您还可以查看存储库中的UUID和多媒体位置。 您可以通过执行以下步骤来创建多媒体的报告：

1. 在&#x200B;**存储库**&#x200B;面板中，在映射视图中打开DITA映射文件。
1. 单击&#x200B;**管理**&#x200B;选项卡。
1. 双击左侧的&#x200B;**多媒体**。 显示DITA映射中存在的多媒体列表。
1. 从&#x200B;**筛选器**&#x200B;面板中，您可以按多媒体或引用中使用的名称对列表进行排序。

   - 按&#x200B;**多媒体**&#x200B;排序时，多媒体的****name显示在第一列中，而使用它们的所有引用的名称显示在同一行的另一列中。 例如，以下屏幕截图显示了多媒体WarmCoolForC.gif在第一列以及使用该多媒体的三个引用显示在同一行的第三列中。

     ![](images/multimedia-report-file-order.png){width="650" align="left"}

   - 如果按&#x200B;**用于**&#x200B;列进行排序，您将查看转换视图，其中已使用多媒体的引用的名称列在第一列，而多媒体名称列在单独行上的另一列。 例如，下面的屏幕截图显示了第一列中三个引用\（调整座椅温度、更改座椅温度显示和Crew area\）的名称，多媒体WarmCoolForC.gif显示在第三列中三个单独的行。

     ![](images/multimedia-report-used-in-order.png){width="650" align="left"}

1. 您可以根据&#x200B;**多媒体类型**&#x200B;和&#x200B;**引用类型**&#x200B;筛选多媒体。 根据您在下拉菜单中的选择，将显示多媒体文件列表。 例如，您可以选择仅显示DITA映射中的音频引用，而文件仅显示其中使用的音频引用。

   >[!NOTE]
   >
   > 根据地图中使用的多媒体类型，图像、视频和音频列在&#x200B;**多媒体类型**&#x200B;下拉列表中，直接或间接列在&#x200B;**引用类型**&#x200B;下拉列表中。

1. 您还可以使用以下筛选选项来选择在列表中显示以下列：

   - **多媒体** \（默认选中\）在DITA映射中指定多媒体的标题。 您可以单击多媒体进行编辑。
   - **多媒体位置**&#x200B;多媒体的完整路径。
   - **多媒体UUID**&#x200B;文件的通用唯一标识符\(UUID\)。
   - **多媒体类型** \（默认选中\）多媒体类型。 可用的选项有“音频”、“视频”或“图像”。
   - **在**&#x200B;中使用\（默认选中\）已使用多媒体的引用。 可单击参照对其进行编辑。
   - **引用类型** \（默认选中\）引用的类型 — 直接或间接引用。
   >[!NOTE]
   >
   > 单击&#x200B;**刷新**&#x200B;以获取新的多媒体列表，并查看映射文件中的任何更改或DITA映射中的任何多媒体已更新。

1. 您还可以在Web编辑器中单击并播放音频或视频文件。 您可以更改视频的音量或视图。 在快捷菜单中，您还可以选择下载、更改播放速度或查看画中画。

   ![](images/video-web-editor.png){width="800" align="left"}

1. 单击&#x200B;**下载CSV**&#x200B;即可在DITA映射中下载多媒体的当前快照。 CSV包含在&#x200B;**多媒体**&#x200B;视图中过滤的选定列和多媒体。 然后，您可以使用任何CSV编辑器打开此多媒体CSV文件。


## 查看和修复断开的链接{#report-broken-links}

**断开的链接**是一个有用的报表，它提供了当前映射中存在的断开链接的详细信息。 您可以查看断开的链接，这些链接可用于DITA主题、多媒体文件引用、内容键引用等。 你自己也能修好它们。
报告提供详细信息，例如断开的链接、链接类型、使用引用的文件以及使用的文件类型。
您可以通过执行以下步骤来查看断开链接报表：
1. 在&#x200B;**存储库**&#x200B;面板中，在映射视图中打开DITA映射文件。
1. 单击&#x200B;**管理**&#x200B;选项卡。
1. 双击左侧的&#x200B;**断开的链接**。 将显示DITA映射中存在的断开链接或引用列表。
1. 从&#x200B;**筛选器**&#x200B;面板中，您可以按链接或引用中使用的名称对列表进行排序。

    — 当您按&#x200B;**断开链接**&#x200B;排序时，断开链接的路径将显示在第一列中，而使用它们的所有引用的名称将显示在单独行上的另一列中。 如果在多个文件中使用了相同的断开链接，则它们将显示在一行中，并显示为分组行或子行。 例如，以下屏幕截图显示第一列中三个断开的链接以及使用这些链接的引用，`TestMap.ditamap`显示在第三列中的三个单独行中。
   ![](images/broken-link-report.png){width="800" align="left"}

    — 如果按&#x200B;**在**&#x200B;列中使用，您将查看变换视图，其中已使用断开链接的引用的名称在第一列中列出，而断开的链接在同一行的另一列中列出。 例如，以下屏幕截图显示了第一列中的引用（使用了断开的链接） `TestMap.ditamap`，并且断开的链接显示在同一行的第三列中。
   ![](images/broken-link-filter-usedin.png){width="800" align="left"}
1. 您可以根据&#x200B;**文件类型**&#x200B;和&#x200B;**链接类型**&#x200B;筛选断开的链接。 系统会根据您在下拉列表中的选择，显示断开的链接列表。 例如，您可以选择仅显示DITA映射中的内容引用，而文件仅显示其中使用的内容引用。

   根据映射中使用的引用类型，文件引用、键引用、内容引用、内容键引用、图像引用和多媒体文件引用在&#x200B;**链接类型**&#x200B;下拉列表中列出，而&#x200B;**DITA主题**&#x200B;或&#x200B;**DITA映射**&#x200B;在&#x200B;**文件类型**&#x200B;下拉列表中列出。
1. 您还可以使用以下筛选选项来选择在列表中显示以下列：

   - **断开的链接**（默认选中）断开的链接的路径在DITA映射中指定。

   - **链接类型**（默认选中）链接的类型。 可用的选项有“内容键引用”、“内容引用”、“DITA主题”、“文件引用”、“图像引用”、“键引用”和“多媒体文件引用”。

   - **在**&#x200B;中使用（默认选中）已使用断开链接的引用。 您可以单击引用以在创作模式下查看它。

   - **文件类型**（默认选中）引用类型 — DITA映射或DITA主题。
单击**刷新**&#x200B;以获取断开链接的新列表，并查看映射文件中的任何更改或DITA映射中的任何断开链接是否已更新。
1. 您可以单击&#x200B;**修复链接**&#x200B;图标(![](images/fix-broken-link.svg))来修复断开的链接。

   >[!NOTE]
   >
   > 将鼠标悬停在“断开链接”列下的断开链接路径上，以查看修复链接(![](images/fix-broken-link.svg))图标。

   您可以修复两个视图中的链接 — 当您按&#x200B;**断开的链接**&#x200B;或&#x200B;**在**&#x200B;中使用的链接进行排序时。

   >[!NOTE]
   >
   > 如果在按断开链接排序时修复断开的链接，则将在使用该链接的所有文件（这些文件在一行中分组）中修复该链接。

1. 您需要在&#x200B;**更新链接**&#x200B;对话框中更新所需的引用详细信息。 **更新链接**&#x200B;对话框中所需的详细信息将取决于引用的类型。\
   修复链接后，该链接不会显示在断开链接列表下。 而是可以在“主题列表”或“元数据”下查看它。

1. 单击&#x200B;**下载CSV**&#x200B;可下载DITA映射中断开链接的当前快照。 CSV包含在“断开链接”视图中过滤的选定列和断开链接。 然后，您可以在任何CSV编辑器中打开并查看此CSV文件。


**父主题：**[&#x200B;报告](reports-intro.md)