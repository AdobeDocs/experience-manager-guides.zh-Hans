---
title: 升级Adobe Experience Manager Guides
description: 了解如何升级Adobe Experience Manager Guides
feature: Installation
role: Admin
level: Experienced
source-git-commit: 453da51a42984b912547570f2e1de70806b41171
workflow-type: tm+mt
source-wordcount: '1661'
ht-degree: 0%

---

# 升级Adobe Experience Manager Guides 4.6.0及更高版本

本文介绍了如何升级您的Experience Manager Guides 4.6.0及更高版本。

>[!NOTE]
>
> 按照特定于您的产品的许可版本的升级说明进行操作。

您可以将当前版本的Experience Manager Guides升级到版本5.1.0 Service Pack 3：

- 如果您使用的是版本5.1.0或5.1.x ，则可以直接升级到版本5.1.0 Service Pack 3。
- 如果您使用的是版本4.6.0、4.6.x、5.0.0或5.0.x，则需要升级到版本5.1.0。
- 如果您使用的版本低于4.6.0，有关详细的升级说明，请参阅[升级Adobe Experience Manager Guides的版本4.4.0和更早版本](./upgrade-aemg-prev-versions.md)。

>[!NOTE]
>
> 在升级AEM版本之前，必须安装Experience Manager Guides Service Pack。

有关更多详细信息，请参阅以下过程：

- [升级到版本5.1.0](#upgrade-to-version-510)
- [升级到版本5.0.0](#upgrade-to-version-500)
- [升级到版本4.6.0](#upgrade-to-version-460)

>[!IMPORTANT]
>
> 在开始升级之前，请进行完整的系统备份以避免任何数据丢失。


## 升级到版本5.1.0


>[!IMPORTANT]
>
> 如果您当前使用AEM 6.5，并计划迁移到AEM 6.5 LTS，请确保先完成AEM升级，然后再继续进行Experience Manager Guides 5.1.0升级。 有关详细信息，请查看[升级到Adobe Experience Manager (AEM) 6.5 LTS](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/implementing/deploying/upgrading/upgrade)。

**先决条件**

>[!NOTE]
>
>如果您要升级到5.1.0 Service Pack 3，则需要使用Experience Manager Guides的5.1.0或5.1.x版本。 5.1.0 Service Pack 3版本的升级过程与5.1.0版本的升级过程相同。

在开始Experience Manager Guides 5.1.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.6.3、4.6.4、5.0.0或5.0.0 Service Pack 1。
1. （可选）已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。

>[!NOTE]
>
> 后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

**安装版本5.1.0**

从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载5.1.0版本包，并按照[安装和安装后升级工作流](#installation-and-post-installation-upgrade-workflow)中提供的说明完成升级过程。


## 升级到版本5.0.0

>[!TIP]
>
> 升级到5.0.0版Service Pack 3取决于当前版本的Experience Manager Guides。 如果您使用的是版本5.0.0 Service Pack 2、5.0.0 Service Pack 1或5.0.0，则可以直接升级到版本5.0.0 Service Pack 3。 升级步骤与版本5.0.0相同。

>[!NOTE]
>
> 后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

**先决条件**

在开始Experience Manager Guides 5.0.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.6.3、4.6.1、4.6.0或4.4。
1. （可选）已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。


**安装版本5.0.0**

从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载5.0.0版本包，并按照[安装和安装后升级工作流](#installation-and-post-installation-upgrade-workflow)中提供的说明完成升级过程。

## 升级到版本4.6.0

>[!TIP]
>
> 建议在版本4.6.0、4.6.0 Service Pack 1或4.6.0 Service Pack 3的基础上安装4.6.0 Service Pack 4。 4.6.0 Service Pack 4版本的升级过程与4.6.0版本遵循的步骤相同。

升级到版本4.6.0取决于Experience Manager Guides的当前版本。 如果您使用的是版本4.4.0、4.3.1、4.3.0、4.2或4.2.1（修补程序4.2.1.3），则可以直接升级到版本4.6.0。

>[!NOTE]
>
> 后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

**先决条件**

在开始Experience Manager Guides 4.6.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.3.1、4.3.0或4.2.1（修补程序4.2.1.3）。
1. （可选）已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。

**安装版本4.6.0**

从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.6.0版本包，并按照[安装和安装后升级工作流](#installation-and-post-installation-upgrade-workflow)中提供的说明完成升级过程。

## 安装和安装后升级工作流

### 安装版本包

执行以下步骤以安装版本包：

1. 安装要升级的版本包。
1. 您可以选择点击触发器以启动翻译图升级作业。 有关详细信息，请参阅[通过Servlet启用脚本触发器](#enable-trigger-of-script-via-a-servlet)。

1. 完成软件包安装后，请等待日志中显示以下消息：

   `Completed the post deployment setup script`

   上述消息指示所有安装步骤均已完成。

   如果您遇到以下任何错误，请向客户成功团队报告：

   - 部署后设置脚本出错
   - 移植翻译映射时出现异常
   - 无法为属性将翻译映射从v1端口转换为v2
1. （可选）随要升级到的版本一起发布的升级氧气连接器插件。
1. 安装包后清除浏览器缓存。

### 安装后流程

安装Experience Manager Guides后，您可以将适用于从新安装的版本到设置的各种配置合并到一起。

>[!NOTE]
>
> 可以自定义dam-update-asset模型。 因此，如果已完成任何自定义设置，那么我们需要将自定义设置和Experience Manager Guides同步到模型的工作副本中。

**DAM更新资产工作流\（后处理更改\）：**

1. 打开URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 选择&#x200B;**DAM更新资产工作流**。
1. 选择&#x200B;**编辑**。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件存在，请确保已同步自定义项。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件不存在，请执行以下步骤以插入该组件：

   - 选择&#x200B;**插入组件** \（负责将Experience Manager Guides后处理作为流程的最后一步\）。
   - 使用以下详细信息配置&#x200B;**流程步骤**：

     **常用选项卡：**

      - **标题：** DXML后处理发起程序

      - **描述**： DXML后处理发起程序步骤，它将触发用于已修改/创建的资产的DXML后处理的Sling作业

     **进程选项卡**

      - 从&#x200B;**进程**&#x200B;下拉列表中选择&#x200B;**DXML后处理启动器**
      - 选择&#x200B;**处理程序前进**
      - 选择&#x200B;**完成**

1. 完成更改后，选择右上角的&#x200B;**同步**。 您将收到成功通知。

   >[!NOTE]
   >
   > 刷新并验证最终工作流模型中是否存在自定义更改和Experience Manager Guides后处理步骤。

1. 验证&#x200B;**DAM更新资产工作流**&#x200B;后，检查相应的启动器配置。 为此，请转到AEM工作流界面并打开启动器。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   查找并更改对应于&#x200B;**DAM更新资产工作流**&#x200B;的以下两个启动器\（如果必要\）：

1. 已为&#x200B;*DAM更新资产工作流*&#x200B;创建“**节点**”的启动器 — 对于条件`"jcr:content/jcr:mimeType!=video"`，“通配”值应为：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - “excludeList”应具有`"event-user-data:changedByWorkflowProcess"`。
   - 针对&#x200B;*DAM更新资产工作流 —*&#x200B;的“**节点已修改**”的启动器，对于条件“`jcr:content/jcr:mimeType!=video`”，“通配”值应为：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList`应具有`"event-user-data:changedByWorkflowProcess"`。

1. 升级完成后，请确保验证并更新任何自定义项/叠加图，以匹配新的应用程序代码。 下面给出了一些示例：
   - 任何从`/libs/fmditaor/libsshould`叠加的组件都应与新的产品代码进行比较，并且更新应在/apps下的叠加文件中完成。
   - 应审查产品中使用的任何`clientlib`类别是否有更改。 应将任何覆盖的配置`\(examples below\)`与最新的配置进行比较，以获取最新的功能：
   - elementmapping.xml
   - `ui\_config.json\(may have been set in folder profiles\)`
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您在damAssetLucene中添加了任何自定义项，则可能需要再次应用它们。 完成这些更改后，将reindex设置为true。 这将使用自定义项重新索引所有现有节点。 完成后，重新索引标志将再次设置为false。 这可能需要几个小时，具体取决于系统中的资源数量。

### 重新索引Experience Manager Guides索引的步骤

1. 打开`crx/de`并导航到索引路径： `/oak:index/guidesAssetProperties`
2. 将重新索引属性设置为`true` （默认为`false`），然后单击&#x200B;**全部保存**。
3. 重新索引完成后，重新索引属性再次设置为`false`，并且重新索引计数以1为单位递增。

   >[!NOTE]
   >
   > 这可能需要几分钟的时间，具体取决于存在的数据量。
4. 对其他添加或修改的索引执行相同的步骤： `guidesBulkActivation`、`guidesPeerLinkIndex`和`guidesKonnectTemplateIndex`。

### 索引现有内容的步骤

执行以下步骤来索引现有内容：

- 对服务器运行POST请求\（使用正确的身份验证\） - `http://<server:port\>/bin/guides/map-find/indexing`。 （可选：您可以传递映射的特定路径来索引它们，默认情况下，所有映射都将索引||示例： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`）

- 该API将返回`jobId`。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： ` http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

- 作业完成后，上述GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。


>[!NOTE]
>
> 如果使用自定义架构，则必须在&#x200B;**集成目录**&#x200B;选项中定义AEM存储库中自定义DTD和XSD catalog.xml文件的路径。

### 处理`'fmdita rewriter'`冲突的步骤

Experience Manager Guides有一个&#x200B;[**自定义sling重写器**](../install-conf-guide/conf-output-generation.md#custom-rewriter)&#x200B;模块，用于处理在交叉映射（两个不同映射的主题之间的链接）情况下生成的链接。

如果您的代码库中有另一个自定义sling重写器，请使用大于50的`'order'`值，因为Experience Manager Guides sling重写器使用`'order'` 50。  要覆盖此值，您需要一个大于50的值。 有关详细信息，请查看[输出重写管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升级过程中，由于`'order'`值从1000更改为50，因此您需要将现有的自定义重写器（如果有）与`'fmdita-rewriter'`合并。


### 重新索引damAssetLucene的步骤

使用AEM Guides更新了damAssetLucene的索引定义。 升级到所需版本后，请参阅[本文](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-16460)以重新索引damAssetLucene。

>[!NOTE]
>
> 在跟踪文档时，请确保通过“保存”操作同时更新了属性（`reindex=true`的`reindex-async=true`和`/oak:index/damAssetLucene`）。

