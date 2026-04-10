---
title: 升级Adobe Experience Manager Guides On Premise先前版本
description: 了解如何升级Adobe Experience Manager Guides
feature: Installation
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '3159'
ht-degree: 0%

---

# 升级Adobe Experience Manager Guides On Premise（版本4.4.0和更早版本）

本文提供了有关将&#x200B;**Adobe Experience Manager Guides**&#x200B;版本升级到4.6.0 **之前的**&#x200B;的说明（升级到&#x200B;**4.4.0**，包括此版本）。

如果您使用的是3.8.5 **之前的**&#x200B;版本，请参阅&#x200B;**Experience Manager Guides帮助PDF存档**&#x200B;上提供的产品特定安装指南中的[升级Adobe Experience Manager Guides](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)部分。

有关较新版本的升级说明，请参阅[升级Adobe Experience Manager Guides 4.6.0及更高版本](./upgrade-aemg-latest-version.md)。

## 开始之前

>[!NOTE]
>
> 在升级AEM版本之前，必须升级特定于您的产品许可版本的说明并安装Experience Manager Guides Service Pack。

>[!IMPORTANT]
>
> 在开始升级之前，请进行&#x200B;**完整的系统备份**&#x200B;以避免任何数据丢失。

## 本文中涉及的升级路径

本文包括以下过程：

- [升级到版本4.4.0](#upgrade-to-version-440)
- [升级到版本4.3.1.5](#upgrade-to-version-4315)
- [升级到版本4.3.1](#upgrade-to-version-431)
- [升级到版本4.3.0](#upgrade-to-version-430)
- [升级到版本4.2.1](#upgrade-to-version-421)
- [升级到版本4.2](#upgrade-to-version-42)
- [从3.8.5升级到版本4.0](#upgrade-from-version-385-to-version-40)


## 全局先决条件（适用于所有升级，除非过程另有说明）

在运行升级过程之前，请完成以下任务：

1. 在打开供审阅的主题中导入审阅注释。
2. 关闭所有活动审阅。
3. 关闭所有翻译任务。
4. 卸载在以前的版本（主要版本或修补程序版本）之上安装的所有Experience Manager Guides修补程序。

某些升级还要求将翻译升级类的日志级别设置为`INFO`并记录到单独的文件；这些要求将在相关升级过程中列出。

## 从版本3.8.5升级到版本4.0

>[!NOTE]
>
> 此升级过程仅适用于&#x200B;**从** 3.8.5 **到** 4.0 **的**。 有关从&#x200B;**3.4或更高版本**&#x200B;升级到&#x200B;**3.8.5**&#x200B;的信息，请参阅[Adobe Experience Manager Guides帮助PDF存档](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)上提供的产品特定安装指南。

如果您使用的是Experience Manager Guides版本&#x200B;**3.8.5**，则可以升级到版本&#x200B;**4.0**&#x200B;而不卸载以前的版本。

### 安装版本4.0之前

1. 确保Experience Manager Guides的版本为&#x200B;**3.8.5**。
2. 下载升级脚本包：在XML Documentation软件分发门户上搜索&#x200B;**“Adobe solution 4.0升级包”**（下载`.zip`）。
3. 通过&#x200B;**包管理器**&#x200B;将包上载到AEM并进行安装。
4. 安装升级软件包后，请按下述顺序运行脚本。

**检查升级兼容性API**

此API旨在评估当前系统状态，并报告是否可以进行升级。 要运行此脚本，请触发以下给定的端点：

| 终点 | /bin/dxml/upgrade/3xto4x/report |
| --- | --- |
| 请求类型 | **GET** <br> **注意**：您可以使用Web浏览器，在该浏览器中，您以管理员身份登录到AEM实例。 |
| 预期响应 | -   如果可以移动所有需要的节点，您将获得一个通过检查。 <br>-   如果目标位置中存在节点，您将收到相关错误。 清理存储库\（删除节点/var/dxml\）并重新安装升级包，然后再次触发此端点。 <br>**注意：**&#x200B;这不是常见的错误，因为3.x Experience Manager Guides之前未使用目标位置。 <br> -   如果此脚本不成功，请不要继续，并报告给您的客户成功团队。 |

**系统数据迁移API**

此API用于迁移&#x200B;**迁移映射**&#x200B;部分中提到的系统数据。

1. 如果Check upgrade compatibility API失败，请勿执行此脚本\（不继续\）。
1. 一旦Check upgrade compatibility API返回成功，您就可以运行升级脚本了。

| 终点 | /bin/dxml/upgrade/3xto4x |
| --- | --- |
| 请求类型 | **POST** <br>**注意**：此脚本是POST请求，因此应通过Postman等代理执行。 |
| 预期响应 | -   成功迁移后，您可以安装XML Documentation解决方案版本4.0.<br>-   如果出现错误，请还原到最后一个检查点，并与您的客户成功团队共享错误日志以及API输出。 |


**迁移映射**

此API会将源位置下的所有数据迁移到目标位置。

| 源 | Target |
|------|------|
| /content/fmdita | /var/dxml |
| /content/dxml | /var/dxml |
| /etc/fmdita | /libs/fmdita |

### 安装版本4.0

1. 仅当升级步骤成功时，才安装版本4.0。
1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.0版本包：

   - 如果您使用的是UUID版本的软件，请搜索“适用于AEM 6.5的XML Documentation解决方案的4.0 UUID版本”。
   - 如果您使用的是非UUID版本的软件，请搜索“适用于AEM 6.5的XML Documentation解决方案的4.0非UUID版本”。
使用AEM包管理器将包上传到现有CRX服务器实例并进行安装。

     >[!NOTE]
     >
     > 等待所有系统组件启动。

1. 安装包后清除浏览器缓存。
1. 如果在AEM创作实例上配置了Dispatcher，请执行以下步骤：
   - 确保在Dispatcher规则中处理以下内容：
   - URL模式/home/users/\*/preferences已列入白名单。
   - 不缓存URL模式/libs/cq/security/userinfo.json 。
1. 清除Dispatcher缓存\（以清除缓存的任何`clientlibs`\）。

## 升级到版本4.2

如果您使用的是版本&#x200B;**4.0**、**4.1**&#x200B;或&#x200B;**4.1.x**，则可以直接升级到版本&#x200B;**4.2**。

### 安装版本4.2之前

在开始Experience Manager Guides 4.2升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides **4.0**、**4.1**&#x200B;或&#x200B;**4.1.x**。
2. 已关闭所有翻译任务。
3. 将`INFO`的日志级别设置为`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`并登录到新日志文件（例如，`logs/translation_upgrade.log`）。

   >[!NOTE]
   > 
   > 您应该关闭所有活动审阅。 如果在升级到4.2时审阅未关闭，则旧版进行中的审阅任务可以继续打开旧版审阅页面；升级后创建的新审阅任务会显示最新的功能更新。

### 安装版本4.2

1. 从&#x200B;**Adobe软件分发门户**&#x200B;下载[4.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)包。
2. 安装4.2包。
3. 安装后，请等待日志中显示以下消息：

   `Completed the post deployment setup script`

   上述消息指示所有安装步骤均已完成。

   如果您遇到以下任何错误，请向客户成功报告这些错误：

   - `Error in post deployment setup script`
   - `Exception while porting the translation MAP`
   - `Unable to port translation map from v1 to v2 for property`

4. （可选）随版本4.2一起发布的升级氧气连接器插件。
5. 安装包后清除浏览器缓存。
6. 继续升级自定义项，如下一节所述。

### 安装版本4.2后

>[!IMPORTANT]
>
> 升级后的服务器上未显示高科技模板。 要在您的服务器上包括高科技模板，您可以复制该模板： Source： `/libs/fmdita/pdf/Hi-Tech`目标： `/content/dam/dita-templates/pdf`。

然后在[常见升级后任务（所有版本）](#common-postupgrade-tasks-all-versions)中继续共享升级后任务。

## 升级到版本4.2.1

>[!TIP]
>
> 建议在版本&#x200B;**4.2.14.2.1.3**&#x200B;之上安装&#x200B;**修补程序**。

如果您使用的是&#x200B;**4.1**、**4.1.x**&#x200B;或&#x200B;**4.2**，则可以直接升级到版本&#x200B;**4.2.1**。

>[!NOTE]
>
> 后期处理和索引可能需要几个小时。 在非高峰时间开始升级。

### 安装版本4.2.1之前

1. 升级到Experience Manager Guides **4.1**、**4.1.x**&#x200B;或&#x200B;**4.2**。
2. 关闭所有翻译任务。
3. 将`INFO`的日志级别设置为`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`并登录到新文件（例如，`logs/translation_upgrade.log`）。

>[!NOTE]
>
> 您应该关闭所有活动审阅（与4.2相同的行为）。

### 安装版本4.2.1

1. 从&#x200B;**Adobe软件分发门户**&#x200B;下载[4.2.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)包。
2. 安装4.2.1包。
3. （可选）触发翻译映射升级作业。 有关详细信息，请参阅[通过Servlet启用脚本触发器](#enable-trigger-of-script-via-a-servlet)。

4. 安装后，等待日志中的`Completed the post deployment setup script`。

   向客户成功报告这些错误：

   - `Error in post deployment setup script`
   - `Exception while porting the translation MAP`
   - `Unable to port translation map from v1 to v2 for property`
5. （可选）随版本&#x200B;**4.2**&#x200B;一起发布的升级氧气连接器插件
6. 清除浏览器缓存。
7. 继续执行[常见升级后任务（所有版本）](#common-postupgrade-tasks-all-versions)。

### 安装版本4.2.1之后

>[!IMPORTANT]
>
> 升级后的服务器上未显示高科技模板。 要在您的服务器上包括高科技模板，您可以复制该模板： Source： `/libs/fmdita/pdf/Hi-Tech`目标： `/content/dam/dita-templates/pdf`。

继续执行[常见升级后任务（所有版本）](#common-postupgrade-tasks-all-versions)和（如果需要）[为映射查找和替换的现有内容编制索引](#index-existing-content-for-map-find-and-replace)。


## 升级到版本4.3.0

升级到版本4.3.0取决于Experience Manager Guides的当前版本。 如果您使用的是版本4.2或4.2.x ，则可以直接升级到版本4.3.0。

>[!NOTE]
>
>后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

### 安装版本4.3.0之前

在开始Experience Manager Guides 4.3.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.2或4.2.x并完成了各自的安装步骤。
1. 已关闭所有翻译任务。

### 安装版本4.3.0

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.3.0版本包。
1. 安装版本4.3.0包。
1. 安装包后清除浏览器缓存。
1. 从文件夹配置文件的`ui_config.json`XML编辑器配置&#x200B;**选项卡中升级**&#x200B;文件。

### 安装版本4.3.0之后

继续：

- [常见升级后任务（所有版本）](#common-postupgrade-tasks-all-versions)
- 如果适用： [后处理断开链接报告的现有内容](#post-process-existing-content-for-broken-link-report)

## 升级到版本4.3.1

升级到版本4.3.1取决于Experience Manager Guides的当前版本。 如果您使用的是版本4.3.0、4.2或4.2.1，则可以直接升级到版本4.3.1。

>[!NOTE]
>
>后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

### 安装版本4.3.1之前

在开始Experience Manager Guides 4.3.1升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.3.0、4.2或4.2.1，并完成了各自的安装步骤。
1. （可选）已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。

### 安装版本4.3.1

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.3.1版本包。
1. 安装版本4.3.1包。
1. （可选）触发翻译映射升级作业。 有关详细信息，请参阅[通过Servlet启用脚本触发器](#enable-trigger-of-script-via-a-servlet)。
1. 安装后，等待日志中的`Completed the post deployment setup script`。
向客户成功报告这些错误：\
   `Error in post deployment setup script`、`Exception while porting the translation MAP`、`Unable to port translation map from v1 to v2 for property`
1. （可选）随版本&#x200B;**4.2**&#x200B;一起发布的升级氧气连接器插件。
1. 清除浏览器缓存。

### 安装版本4.3.1后

继续：

- [常见升级后任务（所有版本）](#common-postupgrade-tasks-all-versions)
- 如果适用： [为映射查找和替换的现有内容编制索引](#index-existing-content-for-map-find-and-replace)
- 如果适用： [后处理断开链接报告的现有内容](#post-process-existing-content-for-broken-link-report)


## 升级到版本4.3.1.5

如果您使用的是版本&#x200B;**4.3.1.5** 4.3.1 **，则可以直接升级到**。

### 安装版本4.3.1.5

1. 从&#x200B;**4.3.1.5** Adobe软件分发门户[下载](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)包。
2. 安装4.3.1.5包。
3. 等待安装过程成功完成。
4. 继续升级自定义项，如下一节所述。

## 安装版本4.3.1.5后

>[!NOTE]
>
>如果要使用org.apache.velocity包，请在上传该包之前执行以下步骤：
> 1. 转到`<server>:<port>/system/console/bundles`
> 1. 搜索org.apache.velocity。
> 1. 卸载搜索捆绑包。
> 1. 安装所需的Velocity包。

1. 升级完成后，请确保验证并更新任何自定义项/叠加图，以匹配新的应用程序代码。 下面给出了一些示例：
   - 任何从`/libs/fmdita`或` /libs`叠加的组件都应与新的产品代码进行比较，并且更新应在`/apps`下的叠加文件中完成。
   - 应审查产品中使用的任何clientlib类别是否有更改。 任何覆盖的配置\（见以下示例\）应与最新的配置进行比较，以获取最新的功能：
   - `elementmapping.xml`
   - `ui\_config.json\` （可能已在文件夹配置文件中设置\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`


## 升级到版本4.4.0

如果您正在使用&#x200B;**4.3.1**、**4.3.0**、**4.2**&#x200B;或&#x200B;**4.2.1 （修补程序**）**，则可以直接升级到4.2.1.34.4.0**。

>[!NOTE]
>
>后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

### 安装版本4.4.0之前

在开始Experience Manager Guides 4.4.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.3.1、4.3.0或4.2.1（修补程序4.2.1.3），并完成了各自的安装步骤。
1. （可选）已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。

### 安装版本4.4.0

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.4.0版本包。
2. 安装4.4.0包。
3. （可选）触发翻译映射升级作业。 有关详细信息，请参阅[通过Servlet启用脚本触发器](#enable-trigger-of-script-via-a-servlet)。
4. 完成软件包安装后，请等待日志中显示以下消息：

   `Completed the post deployment setup script`

   上述消息指示所有安装步骤均已完成。

   如果您遇到以下任何错误前缀，请将其报告给您的客户成功团队：

   - `Error in post deployment setup script`
   - `Exception while porting the translation MAP`
   - `Unable to port translation map from v1 to v2 for property`
5. （可选）随版本&#x200B;**4.4.0**&#x200B;一起发布的升级氧气连接器插件。
6. 清除浏览器缓存。
7. 继续：

   - [常见升级后任务（所有版本）](#common-ppostupgrade-tasks-all-versions)
   - [为地图查找和替换现有内容编制索引](#index-existing-content-for-map-find-and-replace)（仅在适用的情况下）
   - [后处理断开链接报告的现有内容](#post-process-existing-content-for-broken-link-report)（仅在适用时）
   - [翻译映射升级（servlet触发器）](#translation-map-upgrade-servlet-trigger)（仅适用时）


## 常见升级后任务（所有版本）

安装Experience Manager Guides后，您可能需要将适用于从新安装的版本到设置的配置合并。

>[!NOTE]
>
> 可以自定义&#x200B;**DAM更新资产**&#x200B;工作流模型。 如果您有自定义项，请将其与模型工作副本中的Experience Manager Guides更改同步。

### 验证DAM更新资产工作流（后处理更改）

1. 打开AEM工作流模型UI（源中显示的示例）：\
   `http://<host>:4502/libs/cq/workflow/admin/console/content/models.html`
2. 选择&#x200B;**DAM更新资产工作流**。
3. 选择&#x200B;**编辑**。
4. 如果&#x200B;**DXML后处理启动器**&#x200B;组件存在，请确保已同步自定义项。
5. 如果该组件不存在，请插入该组件：
   1. 单击&#x200B;**插入组件**（负责将Guides后处理作为最后一步）。
   2. 配置&#x200B;**进程步骤**：
      **常用选项卡**
 — 标题： `DXML Post Process Initiator`
 — 描述： `DXML post process initiator step which will trigger a sling job for DXML post-processing of the modified/created asset`
      **进程选项卡**
 — 进程：选择`DXML Post Process Initiator`
 — 选择`Handler Advance`
 — 选择`Done`
   3. 完成更改后，单击右上角的&#x200B;**同步**。 您将收到成功通知。

>[!NOTE]
>
> 刷新并验证最终工作流模型中是否存在自定义更改和Experience Manager Guides后处理步骤。

### 验证启动器配置

1. 转到AEM工作流界面并打开&#x200B;**启动器**。

```http
    http://localhost:4502/libs/cq/workflow/content/console.html
```

1. 查找并更改对应于&#x200B;**DAM更新资产工作流**&#x200B;的以下两个启动器\（如果必要\）：

1. 已为&#x200B;*DAM更新资产工作流*&#x200B;创建“**节点**”的启动器 — 对于条件`"jcr:content/jcr:mimeType!=video"`，“通配”值应为：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList`应具有`"event-user-data:changedByWorkflowProcess"`。
   - 已为&#x200B;*DAM更新资产工作流 —*&#x200B;修改的&#x200B;**节点**&#x200B;的启动器，对于条件“`jcr:content/jcr:mimeType!=video`”，“通配”值应为：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList`应具有`"event-user-data:changedByWorkflowProcess"`。

### 验证叠加图和自定义项

升级完成后：

1. 升级完成后，请确保验证并更新任何自定义项/叠加图，以匹配新的应用程序代码。 下面给出了一些示例：
   - 任何来自/libs/fmditor/libsis的叠加组件都应与新的产品代码进行比较，并且更新应在/apps下的叠加文件中完成。
   - 应审查产品中使用的任何clientlib类别是否有更改。 任何覆盖的配置\（见以下示例\）应与最新的配置进行比较，以获取最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在文件夹配置文件中设置\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您在damAssetLucene中添加了任何自定义项，则可能需要再次应用它们。 完成这些更改后，将reindex设置为true。 这将使用自定义项重新索引所有现有节点。 完成后，重新索引标志将再次设置为false。 这可能需要几个小时，具体取决于系统中的资源数量。

## 为地图查找和替换编制现有内容的索引

本节整合了用于启用新的&#x200B;**映射级别查找和替换**&#x200B;功能的重复&#x200B;**索引**&#x200B;过程。

**何时可以跳过索引**

该源包含根据您的升级路径编写的“跳过”说明（例如，“如果您从4.3.0或4.3.1升级，则无需执行这些步骤”以及类似说明）。 按照升级部分中所述的跳过说明进行操作。

执行以下步骤来索引现有内容，并在映射级别使用新的查找和替换文本：

1. 运行POST请求（使用身份验证）：

```http
POST http://<server:port>/bin/guides/map-find/indexing
```

源中支持的可选参数：

- 索引特定的映射路径（默认为索引所有映射）：

  ```http
  POST http://<server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>
  ```

- 在根文件夹（及其子文件夹）下索引DITA映射：

  ```http
  POST http://<server:port>/bin/guides/map-find/indexing?root=/content/dam/test
  ```

  >[!NOTE]
  >
  > 如果同时传递了`paths`和`root`，则只考虑`paths`。

1. API返回`jobId`。 要检查状态，请发送GET请求：

   ```http
   GET http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}
   ```

   预期完成行为：

   - 完成后，GET会做出成功响应，并指示是否有任何映射失败。
   - 在服务器日志中确认已成功索引映射。

### 确保damAssetLucene索引完整（如果适用）

源注释，damAssetLucene索引可能需要几个小时，具体取决于数据大小，并且您可以在`reindex`位于以下位置时`false`确认完成：

`http://<server:port>/oak:index/damAssetLucene`

如果您在`damAssetLucene`中添加了自定义项，则可能需要在重新索引完成后再次应用它们。

### “查询读取或遍历超过100000个节点”的解决方法（如果作业失败）

如果索引作业失败，并且错误显示：

“查询读取或遍历了100000个以上的节点。 为了避免影响其他任务，处理已停止。”

请从源尝试此解决方法：

1. 在`damAssetLucene` oak索引中，在`indexNodeName=true`中添加布尔属性`/oak:index/damAssetLucene/indexRules/dam:Asset`。
2. 在`excerpt`下添加名为`/oak:index/damAssetLucene/indexRules/dam:Asset/properties`的新节点，并设置源中显示的属性：
   - `name=rep:excerpt`
   - `propertyIndex=true`
   - `notNullCheckEnabled=true`
3. 通过设置`damAssetLucene`重新索引`reindex=true`并等待它再次变为`false`（可能需要几个小时）。
4. 再次重新运行索引脚本（重复POST和作业跟踪）。

## 为断开的链接报告后处理现有内容

本节整合了用于启用&#x200B;**断开链接报表**&#x200B;的重复&#x200B;**后处理**&#x200B;过程。

**何时可以跳过后处理**

该源根据您的升级路径包含“跳过”说明（例如，“如果您从4.3.0升级”、“从4.3.0或4.3.1”升级，则无需执行这些步骤）。 按照升级部分中所述的跳过说明进行操作。

执行以下步骤以启用断开链接报表：

1. （可选）增加适用于大型存储库的Oak queryLimitReads

   如果存在超过&#x200B;**100,000个DITA文件**，请将`queryLimitReads`下的`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`更新为大于资产数的值（例如： `200000`），重新部署，然后继续。

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitRead | 值： 200000 <br>默认值： 100000 |

1. 执行以下API以对所有文件运行后处理：

   | 终点 | /bin/guides/reports/upgrade |
   |---|---|
   | 请求类型 | **POST**&#x200B;此脚本是POST请求，因此应通过Postman等代理执行。 |
   | 预期响应 | 该API将返回作业ID。 要检查作业的状态，您可以向同一端点发送一个带有作业ID的GET请求。<br>示例URL： `http://<server:port>/bin/guides/reports/upgrade` |

   | 终点 | /bin/guides/reports/upgrade |
   |---|---|
   | 请求类型 | **GET** |
   | 参数 | jobId：传递从上一个post请求收到的jobId。 |
   | 预期响应 |  — 作业完成后，GET请求将做出成功响应。 <br> — 如果出现错误，请与您的客户成功团队共享错误日志以及API输出。  <br>示例URL： `http://<server:port>/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678` |

1. 如果您在步骤1中更改了`queryLimitReads`的值，请恢复为默认或以前的现有值。

## 通过Servlet启用脚本触发器

多个版本包括一个可选步骤，用于通过servlet触发翻译映射升级作业。 本节整合了重复的过程，并包含源中提供的所有详细信息。


>[!NOTE]
>
> 如果从4.3.0或4.3.1升级，则无需执行这些步骤。

发帖：

```
http://localhost:4503/bin/guides/script/start?jobType=translation-map-upgrade
```

响应：

```
{
"msg": "Job is successfully submitted and lock node is created for future reference",
"lockNodePath": "/var/dxml/executor-locks/translation-map-upgrade/1683190032886",
"status": "SCHEDULED"
}
```

在上述响应JSON中，键`lockNodePath`保存指向存储库中创建的指向已提交作业的节点的路径。 作业完成后该节点会被自动删除，在此之前，您可以引用此节点以获取作业的当前状态。

在继续后续步骤之前，请查找`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2`和`com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2`。

>[!NOTE]
>
> 您应该检查节点是否仍然存在以及作业的状态。

**GET**： `http://<aem_domain>/var/dxml/executor-locks/translation-map-upgrade/1683190032886.json`


### 处理“fmdita重写器”冲突的步骤

Experience Manager Guides包含用于处理为跨映射链接生成的链接的自定义Sling重写器模块(`fmditarewriter`)。

如果您的代码库中有另一个自定义Sling重写器：

- 使用大于50`order`的&#x200B;**值**，因为指南使用的是`order=50`。
- 在此升级过程中，`order`值从`1000`更改为`50`，因此您必须将现有的自定义重写器（如果有）与`fmditarewriter`合并。

