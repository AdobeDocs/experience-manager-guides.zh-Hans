---
title: 处理资产
description: 了解如何处理资源
feature: Migration
role: Admin
level: Experienced
exl-id: 27786098-119c-4b7a-8275-8a89d435294f
source-git-commit: 62221031e445ccdbf1f2567f38fa888ff52017d4
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# 处理资产

在发布等数据密集型工作流程中，高效的资产管理对于保持性能和可靠性至关重要。 资产处理工作流旨在管理需要密集数据操作的特定于用户的资产。 它主要处理两种情况：初始处理因错误而失败时，或文件因未启动资产处理触发器而保持未处理状态。 通过启用有针对性的文件夹级别处理，用户可以仅隔离和处理必要的资源，从而避免不必要的计算开销。 这种选择性方法可显着提升性能，减少发布和生成报告等关键操作所需的时间。 总体而言，它有助于在处理复杂数据任务时提高效率和速度。

>[!NOTE]
>
> - 对于大型数据集，最好在非高峰时间运行处理，以免影响系统性能。 处理任务完成后，您可以查看详细信息以分析结果。<br>
>- 系统每15分钟触发一次`/content/dam`文件夹的资产处理。 在每个周期中，系统都会选取并重新处理最近的15分钟间隔内新添加或未处理的资产。 要配置自动资源处理功能视图，[配置资源处理功能](../cs-install-guide/configure-asset-processing-cs.md)。

## 处理资源

请按照以下所述步骤处理资产：

1. 选择顶部的Adobe Experience Manager徽标，然后选择&#x200B;**工具**。
1. 在&#x200B;**工具**&#x200B;面板中选择&#x200B;**指南**。
1. 选择&#x200B;**批量处理器**&#x200B;磁贴。

   ![flow-asset-processor](images/flow-asset-processor.png){align="left"}

1. 将打开“Guides Bulk Processor（指南批量处理器）”窗口，详细信息如下所示。 此外，此窗口中仅显示与最近五次迁移有关的信息。

   - **功能类型**：显示正在执行的进程的功能。

   - **执行ID**：它是您执行的每个处理任务的唯一ID。

   - **文件夹**：显示选定要处理的文件夹。

   - **排除的文件夹**：显示从处理中排除的文件夹。

   - **创建者**：显示任务或进程的创建者。 既可能是你，也可能是系统。

   - **开始时间：**&#x200B;显示启动处理流程的日期和时间。

   - **结束时间**：显示处理过程结束的日期和时间。

   - **状态**：将处理状态显示为“进行中”、“已完成”或“已取消”。

   ![Guides-asset-processor](images/guides-asset-processor-new.png){align="left"}

1. 选择窗口右上角的&#x200B;**新建进程**&#x200B;选项卡以启动新的处理任务。

   **新进程**&#x200B;对话框打开。

   ![New-process-asset-processor](images/new-asset-processor.png){width="350" align="left"}

1. 在对话框中提供以下详细信息：

   1. **功能类型**：从下拉列表中选择&#x200B;**正在处理资源**。
   1. **选择文件夹和文件**：导航并选择一个或多个要处理的文件夹和文件。
   1. **选择要忽略的文件夹**： （可选）选择要从处理中排除的所选父文件夹中的子文件夹。
   1. **资源类型**：从下拉列表中，选择要处理的特定资源类型(例如，DITA主题、DITA映射、Markdown、HTML/CSS、DITAVAL或其他文件)。 仅从您之前指定的文件夹中处理选定的资源类型。
示例：选择DITA主题仅处理选定文件夹中的DITA主题，从而启用目标筛选。
   1. **创建于**&#x200B;之后/之前：应用日期筛选器以处理在指定时间范围内创建的资源。

   >[!NOTE]
   >
   > 如果某个文件夹已在运行一个进程，则在当前任务完成之前，不能启动该文件夹的新进程。

1. 选择&#x200B;**创建**。出现一个显示&#x200B;**成功且进程已成功触发的弹出窗口**。 您可以在窗口中查看处理任务的状态。

   ![消息资产处理器](images/message-asset-processor.png){width="350" align="left"}


## 用于资产处理任务的其他选项

处理任务启动后，还有其他选项可用。 您可以将鼠标悬停在任务的执行ID上，以访问这些选项。 该等购股权之详情如下：

- **重新启动** ：重新启动之前成功的资源处理任务。

  ![重新启动asset-processor](images/restart-asset-processor.png){width="650" align="left"}

- **继续** ：继续先前取消或失败的资产处理任务。

  ![resume-asset-processor](images/resume-asset-processor.png){width="650" align="left"}

- **取消** ：取消当前正在处理的资源处理任务。

  ![cancel-asset-processor](images/cancel-asset-processor.png){width="650" align="left"}

- **查看日志**：显示资源处理任务的日志。 对于正在进行的任务，日志会显示详细的处理信息，包括预计剩余时间和资源状态。 此日志列表最多可显示500个最新条目。 可以下载完整日志。

  ![logs-asset-processor](images/logs-asset-processor.png){width="650" align="left"}
