---
title: 非UUID到UUID内容迁移
description: 了解如何将非UUID迁移到UUID内容
feature: Migration
role: Admin
level: Experienced
source-git-commit: d721c263384703f8b4db7c6cfed7d54fa77ac42b
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 1%

---

# 非UUID到UUID内容迁移 {#id226TI0U20XA}


执行以下步骤，将内容从非UUID版本4.3.1迁移到UUID版本4.3.2。

>[!IMPORTANT]
>
> * 在开始迁移过程之前，请确保您已：
>
>   1. 已关闭所有活动审核。
>   1. 已关闭所有翻译任务。
> * 在将内容迁移到UUID服务器之前，请确保您的非UUID服务器上安装了兼容的AEM Guides版本。
> * 如果您使用的版本低于4.3.1，请升级到版本4.3.1。按照特定于您的产品的许可版本的[升级说明](./upgrade-xml-documentation.md)执行操作。
> * 当前，不支持版本高于4.3.1的迁移。


## 软件包安装

根据您的版本，从Adobe软件分发门户下载所需的包：


1. **预迁移**：[com.adobe.guides.pre-uuid-migration-1.2.27.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2Fother-packages%2Fuuid-migration%2F3-0%2Fcom.adobe.guides.pre-uuid-migration-1.2.27.zip)
1. **下载UUID版本4.3.2**：[com.adobe.fmdita-6.5-uuid-4.3.2.1977.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2Fother-packages%2Fuuid-migration%2F3-0%2Fcom.adobe.fmdita-6.5-uuid-4.3.2.1977.zip)
1. **迁移**：[com.adobe.guides.uuid-upgrade-1.2.110.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2Fother-packages%2Fuuid-migration%2F3-0%2Fcom.adobe.guides.uuid-upgrade-1.2.110.zip)

## 预迁移检查

对非UUID版本4.3.1执行以下检查：

1. 与版本4.3.1相比，安装预迁移包[com.adobe.guides.pre-uuid-migration-1.2.27.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2Fother-packages%2Fuuid-migration%2F3-0%2Fcom.adobe.guides.pre-uuid-migration-1.2.27.zip)。

   >[!NOTE]
   >
   >* 您需要管理员权限才能执行迁移。
   >* 建议先修复有错误的文件，然后再继续迁移。

1. 如果系统中有超过100,000个DITA文件，请更新查询限制配置以使脚本正常工作：

   * 导航到`/system/console/configMgr and increase both the configs to more than number of assets - queryLimitInMemory`和`queryLimitReads under org.apache.jackrabbit.oak.query.QueryEngineSettingsService`

1. 启动`http://<server-name>/libs/fmdita/clientlibs/xmleditor_uuid_upgrade/page.html`。
1. 从左侧面板中选择&#x200B;**兼容性评估**，然后浏览所有资产的`/content/dam`文件夹路径。
1. 检查兼容性以列出以下信息：
   * 文件总数
   * 预计迁移时间
   * 有错误的文件数
   * 具有GUID文件名的文件

   迁移中的![兼容性评估选项卡](assets/migration-compatibility-assessment.png)


1. 如果出现错误，则分析日志并修复这些错误。 修复错误后，可以重新运行兼容性矩阵。

1. 从左侧面板中选择&#x200B;**配置验证**。 然后，**选择映射**&#x200B;和&#x200B;**选择映射的预设**&#x200B;以进行配置。 当前输出验证列表显示迁移前存在的输出文件，并可在稍后针对迁移后生成的输出文件进行验证。

   通过选择多个和大型DITA映射，您可以验证是否已成功迁移所有内容且没有问题。 选择其中含有基线的预设也可确保基线和版本成功迁移。

   ![迁移中的“配置验证”选项卡](assets/migration-configure-validation.png)


1. （可选）对内容执行版本清除以删除不必要的版本并加快迁移过程。 要执行版本清除，请从迁移屏幕中选择选项&#x200B;**版本清除**，然后使用URL `http://<server- name>/libs/fmdita/clientlibs/xmleditor_uuid_upgrade/page.html`转到用户界面。
   >[!NOTE]
   >
   >此实用程序不删除基线或审阅中使用的任何版本，也不具有任何标签。

有关详细信息，请查看[清除旧版本](../install-guide/version-management.md#purge-older-versions-of-dita-files)。


## 迁移先决条件

1. 仅在创作实例上执行UUID迁移。
1. 确保为以下基础架构做好准备：
   * 创作实例在CPU和内存方面进行了升级，以支持更快速的处理和批量活动所需的额外内存。 例如，如果当前分配的CPU和内存是8 vCPU和24 GB栈，则请将此活动的大小加倍。
   * 总磁盘空间和临时磁盘空间`(crx-quickstart directory)`的缓冲区应为已使用的10倍。 完成迁移后，您可以通过运行压缩来回收大部分磁盘空间。
   * 在启动此活动之前，请运行&#x200B;**脱机Tar压缩**。
   * 请确保在此迁移期间没有计划索引或系统维护。

1. 在非UUID版本上安装受支持发行版的UUID版本。 例如，如果您使用的是4.3.1非UUID内部版本，则需要安装UUID版本4.3.2 [com.adobe.fmdita-6.5-uuid-4.3.2.1977.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2Fother-packages%2Fuuid-migration%2F3-0%2Fcom.adobe.fmdita-6.5-uuid-4.3.2.1977.zip))并运行迁移。


1. 安装uuid迁移升级包[com.adobe.guides.uuid-upgrade-1.2.110.zip](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2Fother-packages%2Fuuid-migration%2F3-0%2Fcom.adobe.guides.uuid-upgrade-1.2.110.zip)。
1. 使用URL为以下工作流禁用启动器： `http://<server-name>/libs/cq/workflow/content/console.html`。

   * DAM更新资产工作流
   * DAM元数据写回工作流

   >[!NOTE]
   >
   >理想情况下，应禁用任何在`content/dam`内的任何路径上运行的工作流启动器。

1. 根据建议的更改更新以下配置：

   | 配置 | 属性 | 价值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | 启用后处理工作流启动器 | 禁用 |
   | `com.adobe.fmdita.config.ConfigManager` | uuid。 正则表达式 | `^GUID-(?<id>.*)` |
   | `com.adobe.fmdita.postprocess.version.PostProcessVersionObservation` | 启用版本后处理 | 禁用 |
   | Day CQ标记服务 | 启用验证(validation.enabled) | 禁用 |

1. 添加单独的日志记录器：
   * `com.adobe.fmdita.uuid`
   * `com.adobe.guides.uuid`。


1. （如果之前未这样做）如果系统中有超过100,000个DITA文件，请将`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`下的`queryLimitReads`更新为更大的值（任何大于存在的资产数的值，例如200,000）。

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitRead | 值： 200000 <br>默认值： 100000 |

## 迁移

1. 启动`http://<server-name>/libs/fmdita/clientlibs/xmleditor_uuid_upgrade/page.html`。

   迁移中的![系统升级选项卡](assets/migration-system-upgrade.png)
   >[!NOTE]
   >
   > 如果选择“启用DITA资产备份”，则临时备份文件将存储在`/content/uuid-upgrade`下，并且在文件迁移完成时删除DITA文件备份。


1. 从左侧面板中选择&#x200B;**系统升级**&#x200B;以运行迁移。 建议一次迁移所有数据，因为系统以最佳方式在内部处理批处理。 只能跳过非DITA资源且未用于任何DITA资源的文件进行迁移。

1. （可选）选择要跳过迁移的文件夹。 使用此选项可在以后迁移这些文件夹或跳过迁移它们。 确保这些文件夹没有任何DITA资产，并且未被任何DITA资产引用（将来不会被任何DITA资产引用）。 例如：`content/dam/projects`。

1. 选择&#x200B;*启用DITA资源备份*&#x200B;以在迁移之前创建资源的备份。 此备份用于在迁移文件时出错时回滚。 如果迁移成功，将删除备份。 但是，这会减慢迁移过程。

1. 开始迁移。
   >[!NOTE]
   >
   > 下载完整日志并观察是否有任何错误。 如果发现任何错误或异常&#x200B;*，请不要继续*，但首先修复错误。 本文末尾列出了常见错误。

1. 迁移完成后，即可下载报表并下载整个日志。

1. 选择&#x200B;**在迁移运行时下载报表**，检查文件夹中的所有文件是否正确升级，以及所有功能是否仅对该文件夹起作用。


   >[!NOTE]
   >
   > 内容迁移可以在文件夹级别、完整`/content/dam`或同一文件夹上运行（重新运行迁移）。

   此外，确保为所有媒体资产（例如您在DITA内容中使用的图像和图形）完成内容迁移也很重要。

1. 迁移所有文件后，从左侧面板中选择&#x200B;**基线/审阅升级**&#x200B;以迁移基线并在文件夹级别进行审阅。

迁移中的![基线和审核选项卡](assets/migration-baseline-review-upgrade.png)

>[!NOTE]
>
>如果重新启动系统或迁移中止，则当您使用与之前相同的参数重新运行脚本时，脚本将继续。 如果您因关机而遇到问题，请与您的客户成功团队联系。

## 分析每个步骤的报告

**步骤：系统升级**

| 流程完成后的摘要 | 如何解释？ | 操作 |
|---|---|---|
| 文件总数：345997 | 在给定文件夹集下处理的文件总数。 | NA |
| 已成功升级的文件数： 344516 | 成功迁移到UUID的文件数。 | NA |
| 升级后出现错误的文件数： 29 | 在这些文件中发生错误，这些错误应与预迁移步骤中报告的错误相同。 | NA |
| 跳过的文件数： 1452 | DAM存储库中的某些文件可能具有子资产，并且会跳过这些子资产，因为它们不符合UUID迁移的条件。 | NA |
| 升级失败的文件数： 0 | 如果计数不为0，则必须分析日志中的任何问题。 | 检查例外，您可能必须修复错误并重新运行迁移。 |
| 所用总时间： 2:40:06.157 |  |  |

**步骤：升级基线**

| 流程完成后的摘要 | 如何解释？ | 操作 |
|---|---|---|
| 文件总数：4833 | 至少1个基线的DITA映射数。 |
| 已成功升级的文件数： 4705 | 已成功升级为所有基线的DITA映射数。 |
| 升级后出现错误的文件数： 0 | 基线未升级的DITA映射数。 |
| 跳过的文件数： 1647 | 没有任何基线的DITA映射数。 |
| 升级失败的文件数： 128 | 无效基线对象的数量（为空）将列在报表(Excel)中。 | 检查是否存在除`baselineObj not found on`以外的错误 |


## 迁移后

1. 迁移完成后，从左侧面板中选择&#x200B;**验证系统升级**，并在迁移之前和之后验证输出文件，以确保迁移成功。

   ![验证迁移中的系统升级选项卡](assets/migration-validate-system-upgrade.png)

1. 成功迁移服务器后，启用以下工作流和配置（包括迁移期间最初禁用的所有其他工作流）以继续在服务器上工作：

   * DAM更新资产工作流
   * DAM元数据工作流

   >[!NOTE]
   >
   >理想情况下，任何工作流启动器，在应该启用迁移之前它们在`content/dam`内的任何路径上运行。

1. 启用以下配置：

   | 配置 | 属性 | 价值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | *启用后处理工作流启动器* | 启用 |
   | `com.adobe.fmdita.postprocess.version.PostProcessVersionObservation` | *启用版本后处理* | 启用 |
   | Day CQ标记服务 | *启用验证(validation.enabled)* | 启用 |

1. 要在迁移后审查的Assets资产：

   | 配置 | 属性 | 非UUID上的预迁移值 | UUID上的迁移后值 |
   |---|---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | **使用AEM站点页面名称的标题** | False（默认值） | 真 |

   >[!NOTE]
   >
   > 如果在迁移前，属性&#x200B;**在`com.adobe.fmdita.config.ConfigManager`内使用AEM站点页面名称**&#x200B;的标题，设置为&#x200B;*False*，则在迁移后需要更新此属性。

1. 完成验证后，可以通过运行压缩回收大部分磁盘空间（请参阅`https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=en`）。