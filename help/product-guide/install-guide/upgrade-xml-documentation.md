---
title: 升级Adobe Experience Manager Guides
description: 了解如何升级Adobe Experience Manager Guides
exl-id: f058b39f-7408-4874-942b-693e133886cf
feature: Installation
role: Admin
level: Experienced
source-git-commit: 479794862cec667baecbdb513e48a2979ef631a7
workflow-type: tm+mt
source-wordcount: '9160'
ht-degree: 0%

---

# 升级Adobe Experience Manager Guides {#id224MBE0M0XA}

>[!NOTE]
>
> 按照特定于您的产品的许可版本的升级说明进行操作。

您可以将当前版本的Experience Manager Guides升级到版本5.1.0 Service Pack 3：

- 如果您使用的是版本5.1.0或5.1.x ，则可以直接升级到版本5.1.0 Service Pack 3。
- 如果您使用的是版本4.6.0、4.6.x、5.0.0或5.0.x，则需要升级到版本5.1.0。
- 如果您使用的是版本4.6.3、4.6.1、4.6或4.4，则需要升级到版本5.0.0。
- 如果您使用的是版本4.3.x、4.2、4.2.1（修补程序4.2.1.3）、4.1或4.1.x，则需要在升级到版本5.0.0之前升级到版本4.4。
- 如果您使用的是版本4.0，则需要先升级到版本4.2，然后再升级到版本4.3.x。
- 如果您使用的是版本3.8.5，则在升级到版本4.2之前需要升级到版本4.0。
- 如果您使用的版本低于3.8.5，请参阅[Adobe Experience Manager Guides帮助Experience Manager Guides存档](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)上提供的产品特定安装指南中的“升级PDF”部分。


>[!NOTE]
>
> 在升级AEM版本之前，必须安装Experience Manager Guides Service Pack。

有关更多详细信息，请参阅以下过程：

- [升级到版本5.1.0](#upgrade-to-version-510)
- [升级到版本5.0.0](#upgrade-to-version-500)
- [升级到版本4.6.0](#upgrade-to-version-460)
- [升级到版本4.4.0](#upgrade-to-version-440)
- [升级到版本4.3.1.5](#upgrade-to-version-4315)
- [升级到版本4.3.1](#upgrade-to-version-431)
- [升级到版本4.3.0](#upgrade-to-version-430)
- [升级到版本4.2.1](#upgrade-to-version-421)
- [升级到版本4.2](#upgrade-to-version-42)
- [从3.8.5升级到版本4.0](#upgrade-from-version-385-to-version-40)


>[!IMPORTANT]
>
> 在开始升级之前，请进行完整的系统备份以避免任何数据丢失。

## 从版本3.8.5升级到版本4.0

如果您使用的是Experience Manager Guides版本3.8.5，则可以升级到Experience Manager Guides版本4.0。 使用升级功能，您无需卸载以前版本的Experience Manager Guides。

在运行进程之前，必须完成某些任务。 以下子部分将指导您完成先决条件、报告生成和迁移过程。 此外，安装Experience Manager Guides版本4.0后，您可以根据客户设置自定义各种配置。

>[!NOTE]
>
> 此升级过程仅适用于版本3.8.5到版本4.0。有关从版本3.4或更高版本升级到3.8.5的过程，请参阅&#x200B;*Experience Manager Guides帮助PDF存档*&#x200B;上提供的产品特定安装指南中的[升级Adobe Experience Manager Guides](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)部分。



****先决条件****

在开始Experience Manager Guides升级过程之前，请确保您已：

1. 在打开供审阅的主题中导入审阅注释。
1. 已关闭所有活动审核。
1. 已关闭所有翻译任务。
1. 卸载Experience Manager Guides先前版本\（主要版本或修补程序版本\）顶部安装的所有Experience Manager Guides修补程序。

**安装版本4.0**&#x200B;之前

在安装版本4.0之前，请执行以下步骤：

1. 此时，请确保Experience Manager Guides使用的是版本3.8.5。
1. 下载升级脚本包。 为此，请在[XML Documentation软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)上搜索将下载zip文件的“Adobe解决方案4.0升级包”。
1. 通过包管理器将此包上传到AEM并安装此包。
1. 安装升级软件包后，请按照相同的顺序运行以下给定脚本，然后按照给定说明操作：

**检查升级兼容性API**

此API旨在评估当前系统状态，并报告是否可以进行升级。 要运行此脚本，请触发以下给定的端点：

| 终点 | /bin/dxml/upgrade/3xto4x/report |
| --- | --- |
| 请求类型 | **GET**&#x200B;您可以使用Web浏览器，在该浏览器中，您以管理员身份登录到AEM实例。 |
| 预期响应 | -   如果可以移动所有需要的节点，您将获得一个通过检查。 <br>-   如果目标位置中存在节点，您将收到相关错误。 清理存储库\（删除节点/var/dxml\）并重新安装升级包，然后再次触发此端点。 <br>**注意：**&#x200B;这不是常见的错误，因为3.x Experience Manager Guides之前未使用目标位置。 <br> -   如果此脚本不成功，请不要继续，并报告给您的客户成功团队。 |

**系统数据迁移API**

此API用于迁移&#x200B;**迁移映射**&#x200B;部分中提到的系统数据。

1. 如果Check upgrade compatibility API失败，请勿执行此脚本\（不继续\）。
1. 一旦Check upgrade compatibility API返回成功，您就可以运行升级脚本了。

| 终点 | /bin/dxml/upgrade/3xto4x |
| --- | --- |
| 请求类型 | **POST**&#x200B;此脚本是POST请求，因此应通过Postman等代理执行。 |
| 预期响应 | -   成功迁移后，您可以安装XML Documentation解决方案版本4.0.<br>-   如果出现错误，请还原到最后一个检查点，并与您的客户成功团队共享错误日志以及API输出。 |

**迁移映射**：上述API将源位置下的所有数据迁移到目标位置。

| 源 | Target |
|------|------|
| /content/fmdita | /var/dxml |
| /content/dxml | /var/dxml |
| /etc/fmdita | /libs/fmdita |

## 安装版本4.0 {#id23598G006XA}

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

升级到版本4.2取决于当前版本的Experience Manager Guides。

如果您使用的是版本4.0、4.1或4.1.x，则可以直接升级到版本4.2。

****先决条件****

在开始Experience Manager Guides 4.2升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.0、4.1或4.1.x。
1. 已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为**&#x200B;信息`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新日志文件中，例如`logs/translation_upgrade.log.`

>[!NOTE]
>
> 您应该关闭所有活动审阅。 如果在升级到4.2时未关闭审阅任务，则旧版进行中的审阅任务将继续让用户访问旧版审阅页面，并且升级后创建的审阅任务将显示功能中的最新更新。

## 安装版本4.2 {#id2245IK0E0EV}

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.2版本包。
1. 安装版本4.2包。
1. 完成软件包安装后，请等待日志中显示以下消息：

   `Completed the post deployment setup script`

   上述消息指示所有安装步骤均已完成。

   如果您遇到以下任何错误前缀，请将其报告给您的客户成功团队：

   - 部署后设置脚本出错
   - 移植翻译映射时出现异常
   - 无法为属性将翻译映射从v1端口转换为v2
1. 升级随版本4.2一起发布的氧气连接器插件\（如果需要\）。
1. 安装包后清除浏览器缓存。
1. 继续升级自定义项，如下一节所述。

## 安装版本4.2之后 {#id2326F02004K}

>[!IMPORTANT]
>
> 升级后的服务器上未显示高科技模板。 要在服务器上包含高科技模板，您可以复制该模板： Source： /libs/fmdita/pdf/Hi-Tech Destination： /content/dam/dita-templates/pdf

安装Experience Manager Guides后，您可以将适用于从新安装的版本到设置的各种配置合并到一起。

>[!NOTE]
>
> 可以自定义dam-update-asset模型。 因此，如果已完成任何自定义设置，那么我们需要将自定义设置和Experience Manager Guides同步到模型的工作副本中。

1. **DAM更新资产工作流\（后处理更改\）：**

1. 打开URL：

   ```http
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html
   ```

1. 选择&#x200B;**DAM更新资产工作流**。
1. 单击&#x200B;**编辑**。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件存在，请确保已同步自定义项。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件不存在，请执行以下步骤以插入该组件：

1. 单击&#x200B;**插入组件** \(作为流程的最后一步负责Experience Manager Guides后处理\)。
1. 使用以下详细信息配置&#x200B;**流程步骤**：

   **常用选项卡**

   **标题：** DXML后处理发起程序

   **描述**： DXML后处理发起程序步骤，它将触发用于已修改/创建的资产的DXML后处理的Sling作业

   **进程选项卡**

   - 从&#x200B;**进程**&#x200B;下拉列表中选择&#x200B;**DXML后处理启动器**

   - 选择&#x200B;**处理程序前进**

   - 选择&#x200B;**完成**

1. 完成更改后，单击右上角的&#x200B;**同步**。 您将收到成功通知。

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
   - 针对&#x200B;*DAM更新资产工作流 —*&#x200B;的“**节点已修改**”的启动器（适用于条件“`jcr:content/jcr:mimeType!=video`”），
   - “通配”值应为：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - “excludeList”应具有`"event-user-data:changedByWorkflowProcess"`。
1. 升级完成后，请确保验证并更新任何自定义项/叠加图，以匹配新的应用程序代码。 下面给出了一些示例：
   - 任何来自/libs/fmditor/libsis的叠加组件都应与新的产品代码进行比较，并且更新应在/apps下的叠加文件中完成。
   - 应审查产品中使用的任何clientlib类别是否有更改。 任何覆盖的配置\（见以下示例\）应与最新的配置进行比较，以获取最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在文件夹配置文件中设置\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`
   - 检查是否有任何自定义代码使用任何旧路径\（如[迁移映射](#id2244LE040XA)部分中所述\） — 应更新为新路径，以便自定义项也能按预期工作。
1. 阅读当前版本中引入的任何新配置\（查看[发行说明](../release-info/release-notes-4-3.md)\），了解是否有任何功能受到影响，然后采取适当措施。 例如，可以使用4.0版中引入的“改进的文件和版本处理”，您需要启用该版本的配置。

## 为现有内容编制索引以使用新的查找和替换的步骤：

执行以下步骤来索引现有内容，并在映射级别使用新的查找和替换文本：

- 对服务器运行POST请求\（使用正确的身份验证\） - `http://<server:port\>/bin/guides/map-find/indexing`。 \(可选：您可以传递映射的特定路径来索引它们，默认情况下，所有映射都将索引\|\| 例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`\)

- 该API将返回作业ID。 要检查作业的状态，您可以将带有作业ID的GET请求发送到同一端点 — 

`http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）

- 作业完成后，上述GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。

如果升级作业失败，并且错误日志显示以下错误：

“*查询*&#x200B;读取或遍历了超过&#x200B;*100000个节点*。 为了避免影响其他任务，处理已停止。”

发生这种情况的原因是，没有为升级中使用的查询正确设置索引。 您可以尝试以下解决方法：

1. 在damAssetLucene Oak索引中，将布尔属性`indexNodeName`添加为节点中的`true`。
   `/oak:index/damAssetLucene/indexRules/dam:Asset`
1. 在节点下添加名称为摘录的新节点。

   `/oak:index/damAssetLucene/indexRules/dam:Asset/properties`
并在节点中设置以下属性：

   ```
   name - rep:excerpt
   propertyIndex - {Boolean}true
   notNullCheckEnabled - {Boolean}true
   ```

   `damAssetLucene`的结构应如下所示：

   ```
   <damAssetLucene compatVersion="{Long}2" async="async, nrt" jcr:primaryType="oak:QueryIndexDefinition" evaluatePathRestrictions="{Boolean}true" type="lucene">
   <indexRules jcr:primaryType="nt:unstructured">
     <dam:Asset indexNodeName="{Boolean}true" jcr:primaryType="nt:unstructured">
       <properties jcr:primaryType="nt:unstructured">
         <excerpt name="rep:excerpt" propertyIndex="{Boolean}true" jcr:primaryType="nt:unstructured" notNullCheckEnabled="{Boolean}true"/>
       </properties>
       </dam:Asset>
     </indexRules>
   </damAssetLucene>    
   ```


   （以及其他现有节点和属性）

1. 重新索引`damAssetLucene`索引(通过将重新索引标志设置为`true`，在
并等待它重新`false`（这表示重新索引已完成）。 请注意，根据索引的大小，这可能需要几个小时。
1. 通过执行上述步骤，再次运行索引脚本。


## 升级到版本4.2.1

>[!TIP]
>
>建议在版本4.2.1的基础上安装修补程序4.2.1.3。

升级到版本4.2.1取决于Experience Manager Guides的当前版本。 如果您使用的是版本4.1、4.1.x或4.2，则可以直接升级到版本4.2.1。

>[!NOTE]
>
>后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

****先决条件****

在开始Experience Manager Guides 4.2.1升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.1、4.1.x或4.2。
1. 已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为**&#x200B;信息`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新日志文件中，例如`logs/translation_upgrade.log.`

>[!NOTE]
>
> 您应该关闭所有活动审阅。 如果在升级到4.2时未关闭审阅任务，则旧版进行中的审阅任务将继续让用户访问旧版审阅页面，并且升级后创建的审阅任务将显示功能中的最新更新。

## 安装版本4.2.1

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.2.1版本包。
1. 安装版本4.2.1包。
1. 您可以选择点击触发器以启动翻译图升级作业。 有关详细信息，请参阅[通过Servlet启用脚本触发器](#enable-trigger-of-script-via-a-servlet-for-421)。


1. 完成软件包安装后，请等待日志中显示以下消息：

   `Completed the post deployment setup script`

   上述消息指示所有安装步骤均已完成。

   如果您遇到以下任何错误前缀，请将其报告给您的客户成功团队：

   - 部署后设置脚本出错
   - 移植翻译映射时出现异常
   - 无法为属性将翻译映射从v1端口转换为v2
1. 升级随版本4.2一起发布的氧气连接器插件\（如果需要\）。
1. 安装包后清除浏览器缓存。
1. 继续升级自定义项，如下一节所述。

### 通过Servlet启用脚本触发器（对于4.2.1）

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

示例日志：
以下是触发脚本后日志文件中显示的日志示例。

```
04.05.2023 14:17:12.876 *INFO* [[0:0:0:0:0:0:0:1] [1683190032736] POST /bin/guides/script/start HTTP/1.1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Acquiring lock for job : translation-map-upgrade
04.05.2023 14:17:12.897 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Starting the thread to upgrade translation map from V1 to V2
04.05.2023 14:17:12.899 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Initiating lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.901 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Starting porting of translation map from V1 to V2
04.05.2023 14:17:12.904 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Memory increase is of : 764 kB
04.05.2023 14:17:12.906 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2
04.05.2023 14:17:12.907 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Releasing lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.909 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2
```

在继续后续步骤之前，请查找`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2`和`com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2`。



## 安装版本4.2.1之后

>[!IMPORTANT]
>
> 升级后的服务器上未显示高科技模板。 要在服务器上包含高科技模板，您可以复制该模板： Source： /libs/fmdita/pdf/Hi-Tech Destination： /content/dam/dita-templates/pdf

安装Experience Manager Guides后，您可以将适用于从新安装的版本到设置的各种配置合并到一起。

>[!NOTE]
>
> 可以自定义dam-update-asset模型。 因此，如果已完成任何自定义设置，那么我们需要将自定义设置和Experience Manager Guides同步到模型的工作副本中。

1. **DAM更新资产工作流\（后处理更改\）：**

1. 打开URL：

   ```http
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html
   ```

1. 选择&#x200B;**DAM更新资产工作流**。
1. 单击&#x200B;**编辑**。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件存在，请确保已同步自定义项。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件不存在，请执行以下步骤以插入该组件：

1. 单击&#x200B;**插入组件** \(作为流程的最后一步负责Experience Manager Guides后处理\)。
1. 使用以下详细信息配置&#x200B;**流程步骤**：

   **常用选项卡**

   **标题：** DXML后处理发起程序

   **描述**： DXML后处理发起程序步骤，它将触发用于已修改/创建的资产的DXML后处理的Sling作业

   **进程选项卡**

   - 从&#x200B;**进程**&#x200B;下拉列表中选择&#x200B;**DXML后处理启动器**

   - 选择&#x200B;**处理程序前进**

   - 选择&#x200B;**完成**

1. 完成更改后，单击右上角的&#x200B;**同步**。 您将收到成功通知。

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
   - 任何来自/libs/fmditor/libsis的叠加组件都应与新的产品代码进行比较，并且更新应在/apps下的叠加文件中完成。
   - 应审查产品中使用的任何clientlib类别是否有更改。 任何覆盖的配置\（见以下示例\）应与最新的配置进行比较，以获取最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在文件夹配置文件中设置\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`
   - 检查是否有任何自定义代码使用任何旧路径\（如[迁移映射](#id2244LE040XA)部分中所述\） — 应更新为新路径，以便自定义项也能按预期工作。
1. 阅读当前版本中引入的任何新配置\（查看[发行说明](../release-info/release-notes-4-2-1.md)\），了解是否有任何功能受到影响，然后采取适当措施。 例如，可以使用4.0版中引入的“改进的文件和版本处理”，您需要启用该版本的配置。

## 为现有内容编制索引以使用新的查找和替换的步骤：

执行以下步骤来索引现有内容，并在映射级别使用新的查找和替换文本：

- 确保`damAssetLucene`索引已完成。 这可能需要几个小时，具体取决于服务器上存在的数据量。 您可以通过检查中的重新索引字段是否设置为false来确认重新索引已完成
  `http://<server:port>/oak:index/damAssetLucene`。  此外，如果您已在`damAssetLucene`中添加任何自定义项，则可能需要再次应用它们。

- 对服务器运行POST请求\（使用正确的身份验证\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (可选：您可以传递映射的特定路径以对其进行索引，默认情况下，所有映射都将进行索引\|\| 例如：`https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 您还可以传递根文件夹来索引特定文件夹（及其子文件夹）的DITA映射。 例如，`http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。请注意，如果同时传递了路径参数和根参数，则只考虑路径参数。

- 该API将返回作业ID。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）


- 作业完成后，上述GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。


## 升级到版本4.3.0

升级到版本4.3.0取决于Experience Manager Guides的当前版本。 如果您使用的是版本4.2或4.2.x ，则可以直接升级到版本4.3.0。

>[!NOTE]
>
>后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

****先决条件****

在开始Experience Manager Guides 4.3.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.2或4.2.x并完成了各自的安装步骤。
1. 已关闭所有翻译任务。



## 安装版本4.3.0

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.3.0版本包。
1. 安装版本4.3.0包。
1. 安装包后清除浏览器缓存。
1. 从文件夹配置文件的`ui_config.json`XML编辑器配置&#x200B;**选项卡中升级**&#x200B;文件。


## 安装版本4.3.0之后

安装Experience Manager Guides后，您可以将适用于从新安装的版本到设置的各种配置合并到一起。

## 后处理现有内容以使用断开链接报表的步骤


执行以下步骤后处理现有内容并使用新的断开链接报表：

1. （可选）如果系统中有超过100,000个dita文件，请将`queryLimitReads`下的`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`更新为更大的值（任何大于现有资产数的值，例如200,000），然后重新部署。

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



## 升级到版本4.3.1

升级到版本4.3.1取决于Experience Manager Guides的当前版本。 如果您使用的是版本4.3.0、4.2或4.2.1，则可以直接升级到版本4.3.1。

>[!NOTE]
>
>后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

****先决条件****

在开始Experience Manager Guides 4.3.1升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.3.0、4.2或4.2.1，并完成了各自的安装步骤。
1. （可选）已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。


## 安装版本4.3.1

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.3.1版本包。
1. 安装版本4.3.1包。
1. 您可以选择点击触发器以启动翻译图升级作业。 有关详细信息，请参阅[通过Servlet启用脚本触发器](#enable-trigger-of-script-via-a-servlet-for-431)。


1. 完成软件包安装后，请等待日志中显示以下消息：

   `Completed the post deployment setup script`

   上述消息指示所有安装步骤均已完成。

   如果您遇到以下任何错误前缀，请将其报告给您的客户成功团队：

   - 部署后设置脚本出错
   - 移植翻译映射时出现异常
   - 无法为属性将翻译映射从v1端口转换为v2
1. 升级随版本4.2一起发布的氧气连接器插件\（如果需要\）。
1. 安装包后清除浏览器缓存。
1. 继续升级自定义项，如下一节所述。

### 通过Servlet启用脚本触发器（对于4.3.1）

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

示例日志：
以下是触发脚本后日志文件中显示的日志示例。

```
04.05.2023 14:17:12.876 *INFO* [[0:0:0:0:0:0:0:1] [1683190032736] POST /bin/guides/script/start HTTP/1.1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Acquiring lock for job : translation-map-upgrade
04.05.2023 14:17:12.897 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Starting the thread to upgrade translation map from V1 to V2
04.05.2023 14:17:12.899 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Initiating lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.901 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Starting porting of translation map from V1 to V2
04.05.2023 14:17:12.904 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Memory increase is of : 764 kB
04.05.2023 14:17:12.906 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2
04.05.2023 14:17:12.907 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Releasing lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.909 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2
```

在继续后续步骤之前，请查找`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2`和`com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2`。

## 安装版本4.3.1之后



安装Experience Manager Guides后，您可以将适用于从新安装的版本到设置的各种配置合并到一起。

>[!NOTE]
>
> 可以自定义dam-update-asset模型。 因此，如果已完成任何自定义设置，那么我们需要将自定义设置和Experience Manager Guides同步到模型的工作副本中。

1. **DAM更新资产工作流\（后处理更改\）：**

1. 打开URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 选择&#x200B;**DAM更新资产工作流**。
1. 单击&#x200B;**编辑**。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件存在，请确保已同步自定义项。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件不存在，请执行以下步骤以插入该组件：

1. 单击&#x200B;**插入组件** \(作为流程的最后一步负责Experience Manager Guides后处理\)。
1. 使用以下详细信息配置&#x200B;**流程步骤**：

   **常用选项卡**

   **标题：** DXML后处理发起程序

   **描述**： DXML后处理发起程序步骤，它将触发用于已修改/创建的资产的DXML后处理的Sling作业

   **进程选项卡**

   - 从&#x200B;**进程**&#x200B;下拉列表中选择&#x200B;**DXML后处理启动器**

   - 选择&#x200B;**处理程序前进**

   - 选择&#x200B;**完成**

1. 完成更改后，单击右上角的&#x200B;**同步**。 您将收到成功通知。

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
   - 任何来自/libs/fmditor/libsis的叠加组件都应与新的产品代码进行比较，并且更新应在/apps下的叠加文件中完成。
   - 应审查产品中使用的任何clientlib类别是否有更改。 任何覆盖的配置\（见以下示例\）应与最新的配置进行比较，以获取最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在文件夹配置文件中设置\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`


## 索引现有内容的步骤

>[!NOTE]
>
> 如果从4.3.0或4.2.1升级，则无需执行这些步骤。

执行以下步骤来索引现有内容，并在映射级别使用新的查找和替换文本：


- 对服务器运行POST请求\（使用正确的身份验证\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (可选：您可以传递映射的特定路径以对其进行索引，默认情况下，所有映射都将进行索引\|\| 例如：`https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)


- 该API将返回作业ID。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）


- 作业完成后，上述GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。

## 后处理现有内容以使用断开链接报表的步骤

>[!NOTE]
>
> 如果从4.3.0升级，则无需执行这些步骤

执行以下步骤后处理现有内容并使用新的断开链接报表：

1. （可选）如果系统中有超过100,000个dita文件，请将`queryLimitReads`下的`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`更新为更大的值（任何大于现有资产数的值，例如200,000），然后重新部署。

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



## 升级到版本4.3.1.5

升级到版本4.3.1.5依赖于Experience Manager Guides的当前版本。 如果您使用的是版本4.3.1，则可以直接升级到版本4.3.1.5。



## 安装版本4.3.1.5

1. 从4.3.1.5Adobe软件分发门户[下载](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)版本包。
1. 安装版本4.3.1.5包。

1. 等待安装过程成功完成。
1. 继续升级自定义项，如下一节所述。


## 安装版本4.3.1.5后


>[!NOTE]
>
>如果要使用org.apache.velocity包，请在上传该包之前执行以下步骤：
> 1. 转到 `<server>:<port>/system/console/bundles`.
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

升级到版本4.4.0取决于Experience Manager Guides的当前版本。 如果您使用的是版本4.3.1、4.3.0、4.2或4.2.1（修补程序4.2.1.3），则可以直接升级到版本4.4.0

>[!NOTE]
>
>后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

****先决条件****

在开始Experience Manager Guides 4.4.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.3.1、4.3.0或4.2.1（修补程序4.2.1.3），并完成了各自的安装步骤。
1. （可选）已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。


## 安装版本4.4.0

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.4.0版本包。
1. 安装版本4.4.0包。
1. 您可以选择点击触发器以启动翻译图升级作业。 有关详细信息，请参阅[通过Servlet启用脚本触发器](#enable-trigger-of-script-via-a-servlet)。

1. 完成软件包安装后，请等待日志中显示以下消息：

   `Completed the post deployment setup script`

   上述消息指示所有安装步骤均已完成。

   如果您遇到以下任何错误前缀，请将其报告给您的客户成功团队：

   - 部署后设置脚本出错
   - 移植翻译映射时出现异常
   - 无法为属性将翻译映射从v1端口转换为v2
1. 升级氧气连接器插件，随版本4.4.0一起发布\（如果需要\）。
1. 安装包后清除浏览器缓存。
1. 继续升级自定义项，如下一节所述。


## 安装版本4.4.0之后

安装Experience Manager Guides后，您可以将适用于从新安装的版本到设置的各种配置合并到一起。

>[!NOTE]
>
> 可以自定义dam-update-asset模型。 因此，如果已完成任何自定义设置，那么我们需要将自定义设置和Experience Manager Guides同步到模型的工作副本中。

1. **DAM更新资产工作流\（后处理更改\）：**

1. 打开URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 选择&#x200B;**DAM更新资产工作流**。
1. 单击&#x200B;**编辑**。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件存在，请确保已同步自定义项。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件不存在，请执行以下步骤以插入该组件：

1. 单击&#x200B;**插入组件** \(作为流程的最后一步负责Experience Manager Guides后处理\)。
1. 使用以下详细信息配置&#x200B;**流程步骤**：

   **常用选项卡**

   **标题：** DXML后处理发起程序

   **描述**： DXML后处理发起程序步骤，它将触发用于已修改/创建的资产的DXML后处理的Sling作业

   **进程选项卡**

   - 从&#x200B;**进程**&#x200B;下拉列表中选择&#x200B;**DXML后处理启动器**

   - 选择&#x200B;**处理程序前进**

   - 选择&#x200B;**完成**

1. 完成更改后，单击右上角的&#x200B;**同步**。 您将收到成功通知。

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
   - 任何来自/libs/fmditor/libsis的叠加组件都应与新的产品代码进行比较，并且更新应在/apps下的叠加文件中完成。
   - 应审查产品中使用的任何clientlib类别是否有更改。 任何覆盖的配置\（见以下示例\）应与最新的配置进行比较，以获取最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在文件夹配置文件中设置\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您在damAssetLucene中添加了任何自定义项，则可能需要再次应用它们。 完成这些更改后，将reindex设置为true。 这将使用自定义项重新索引所有现有节点。 完成后，重新索引标志将再次设置为false。 这可能需要几个小时，具体取决于系统中的资源数量。

## 索引现有内容的步骤

>[!NOTE]
>
> 如果从4.3.0或4.3.1升级，则无需执行这些步骤。

执行以下步骤来索引现有内容，并在映射级别使用新的查找和替换文本：

- 对服务器运行POST请求\（使用正确的身份验证\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (可选：您可以传递映射的特定路径以对其进行索引，默认情况下，所有映射都将进行索引\|\| 例如：`https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 该API将返回作业ID。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）

- 作业完成后，上述GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。

## 后处理现有内容以使用断开链接报表的步骤

>[!NOTE]
>
> 如果从4.3.0或4.3.1升级，则无需执行这些步骤。

执行以下步骤后处理现有内容并使用新的断开链接报表：

1. （可选）如果系统中有超过100,000个dita文件，请将`queryLimitReads`下的`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`更新为更大的值（任何大于现有资产数的值，例如200,000），然后重新部署。

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

### 通过Servlet启用脚本触发器

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



## 处理`'fmdita rewriter'`冲突的步骤

Experience Manager Guides有一个&#x200B;[**自定义sling重写器**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模块，用于处理在交叉映射（两个不同映射的主题之间的链接）情况下生成的链接。

如果您的代码库中有另一个自定义sling重写器，请使用大于50的`'order'`值，因为Experience Manager Guides sling重写器使用`'order'` 50。  要覆盖此值，您需要一个大于50的值。 有关详细信息，请查看[输出重写管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升级过程中，由于`'order'`值从1000更改为50，因此您需要将现有的自定义重写器（如果有）与`'fmdita-rewriter'`合并。


**父主题：**[&#x200B;下载并安装](download-install.md)


## 升级到版本4.6.0

>[!TIP]
>
> 建议在版本4.6.0、4.6.0 Service Pack 1或4.6.0 Service Pack 3的基础上安装4.6.0 Service Pack 4。 4.6.0 Service Pack 4版本的升级过程与4.6.0版本遵循的步骤相同。

升级到版本4.6.0取决于Experience Manager Guides的当前版本。 如果您使用的是版本4.4.0、4.3.1、4.3.0、4.2或4.2.1（修补程序4.2.1.3），则可以直接升级到版本4.6.0。

>[!NOTE]
>
> 后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

****先决条件****

在开始Experience Manager Guides 4.6.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.3.1、4.3.0或4.2.1（修补程序4.2.1.3），并完成了各自的安装步骤。
1. （可选）已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。


## 安装版本4.6.0

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载4.6.0版本包。
1. 安装版本4.6.0包。
1. 您可以选择点击触发器以启动翻译图升级作业。 有关详细信息，请参阅[通过Servlet启用脚本触发器](#enable-trigger-of-script-via-a-servlet)。

1. 完成软件包安装后，请等待日志中显示以下消息：

   `Completed the post deployment setup script`

   上述消息指示所有安装步骤均已完成。

   如果您遇到以下任何错误前缀，请将其报告给您的客户成功团队：

   - 部署后设置脚本出错
   - 移植翻译映射时出现异常
   - 无法为属性将翻译映射从v1端口转换为v2
1. 升级随版本4.6.0一起发布的氧气连接器插件\（如果需要\）。
1. 安装包后清除浏览器缓存。

## 安装版本4.6.0之后

安装Experience Manager Guides后，您可以将适用于从新安装的版本到设置的各种配置合并到一起。

>[!NOTE]
>
> 可以自定义dam-update-asset模型。 因此，如果已完成任何自定义设置，那么我们需要将自定义设置和Experience Manager Guides同步到模型的工作副本中。

1. **DAM更新资产工作流\（后处理更改\）：**

1. 打开URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 选择&#x200B;**DAM更新资产工作流**。
1. 单击&#x200B;**编辑**。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件存在，请确保已同步自定义项。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件不存在，请执行以下步骤以插入该组件：

1. 单击&#x200B;**插入组件** \(作为流程的最后一步负责Experience Manager Guides后处理\)。
1. 使用以下详细信息配置&#x200B;**流程步骤**：

   **常用选项卡**

   **标题：** DXML后处理发起程序

   **描述**： DXML后处理发起程序步骤，它将触发用于已修改/创建的资产的DXML后处理的Sling作业

   **进程选项卡**

   - 从&#x200B;**进程**&#x200B;下拉列表中选择&#x200B;**DXML后处理启动器**

   - 选择&#x200B;**处理程序前进**

   - 选择&#x200B;**完成**

1. 完成更改后，单击右上角的&#x200B;**同步**。 您将收到成功通知。

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
   - 任何来自/libs/fmditor/libsis的叠加组件都应与新的产品代码进行比较，并且更新应在/apps下的叠加文件中完成。
   - 应审查产品中使用的任何clientlib类别是否有更改。 任何覆盖的配置\（见以下示例\）应与最新的配置进行比较，以获取最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在文件夹配置文件中设置\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您在damAssetLucene中添加了任何自定义项，则可能需要再次应用它们。 完成这些更改后，将reindex设置为true。 这将使用自定义项重新索引所有现有节点。 完成后，重新索引标志将再次设置为false。 这可能需要几个小时，具体取决于系统中的资源数量。

## 重新索引Experience Manager Guides索引的步骤

1. 打开`crx/de`并导航到索引路径： `/oak:index/guidesAssetProperties`
2. 将重新索引属性设置为`true` （默认为`false`），然后单击&#x200B;**全部保存**。
3. 重新索引完成后，重新索引属性再次设置为`false`，并且重新索引计数以1为单位递增。

   >[!NOTE]
   >
   > 这可能需要几分钟的时间，具体取决于存在的数据量。
4. 对其他添加或修改的索引执行相同的步骤： `guidesBulkActivation`、`guidesPeerLinkIndex`和`guidesKonnectTemplateIndex`。

## 索引现有内容的步骤



执行以下步骤来索引现有内容：

- 对服务器运行POST请求\（使用正确的身份验证\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (可选：您可以传递映射的特定路径来对其进行索引，默认情况下，所有映射都将进行索引 || 示例：`https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 该API将返回作业ID。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： ` http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

- 作业完成后，上述GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。


>[!NOTE]
>
> 如果使用自定义架构，则必须在&#x200B;**集成目录**&#x200B;选项中定义AEM存储库中自定义DTD和XSD catalog.xml文件的路径。




## 处理`'fmdita rewriter'`冲突的步骤

Experience Manager Guides有一个&#x200B;[**自定义sling重写器**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模块，用于处理在交叉映射（两个不同映射的主题之间的链接）情况下生成的链接。

如果您的代码库中有另一个自定义sling重写器，请使用大于50的`'order'`值，因为Experience Manager Guides sling重写器使用`'order'` 50。  要覆盖此值，您需要一个大于50的值。 有关详细信息，请查看[输出重写管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升级过程中，由于`'order'`值从1000更改为50，因此您需要将现有的自定义重写器（如果有）与`'fmdita-rewriter'`合并。


## 升级到版本5.0.0

>[!TIP]
>
> 升级到5.0.0版Service Pack 3取决于当前版本的Experience Manager Guides。 如果您使用的是版本5.0.0 Service Pack 2、5.0.0 Service Pack 1或5.0.0，则可以直接升级到版本5.0.0 Service Pack 3。

>[!NOTE]
>
> 后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

****先决条件****

在开始Experience Manager Guides 5.0.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.6.3、4.6.1、4.6.0或4.4，并完成了各自的安装步骤。
1. （可选）已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。


## 安装版本5.0.0

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载5.0.0版本包。
1. 安装版本5.0.0包。
1. 您可以选择点击触发器以启动翻译图升级作业。 有关详细信息，请参阅[通过Servlet启用脚本触发器](#enable-trigger-of-script-via-a-servlet)。

1. 完成软件包安装后，请等待日志中显示以下消息：

   `Completed the post deployment setup script`

   上述消息指示所有安装步骤均已完成。

   如果您遇到以下任何错误前缀，请将其报告给您的客户成功团队：

   - 部署后设置脚本出错
   - 移植翻译映射时出现异常
   - 无法为属性将翻译映射从v1端口转换为v2
1. 升级随版本5.0.0一起发布的氧气连接器插件\（如果需要\）。
1. 安装包后清除浏览器缓存。

## 安装版本5.0.0之后

安装Experience Manager Guides后，您可以将适用于从新安装的版本到设置的各种配置合并到一起。

>[!NOTE]
>
> 可以自定义dam-update-asset模型。 因此，如果已完成任何自定义设置，那么我们需要将自定义设置和Experience Manager Guides同步到模型的工作副本中。

1. **DAM更新资产工作流\（后处理更改\）：**

1. 打开URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 选择&#x200B;**DAM更新资产工作流**。
1. 单击&#x200B;**编辑**。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件存在，请确保已同步自定义项。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件不存在，请执行以下步骤以插入该组件：

1. 单击&#x200B;**插入组件** \(作为流程的最后一步负责Experience Manager Guides后处理\)。
1. 使用以下详细信息配置&#x200B;**流程步骤**：

   **常用选项卡**

   **标题：** DXML后处理发起程序

   **描述**： DXML后处理发起程序步骤，它将触发用于已修改/创建的资产的DXML后处理的Sling作业

   **进程选项卡**

   - 从&#x200B;**进程**&#x200B;下拉列表中选择&#x200B;**DXML后处理启动器**

   - 选择&#x200B;**处理程序前进**

   - 选择&#x200B;**完成**

1. 完成更改后，单击右上角的&#x200B;**同步**。 您将收到成功通知。

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
   - 任何来自/libs/fmditor/libsis的叠加组件都应与新的产品代码进行比较，并且更新应在/apps下的叠加文件中完成。
   - 应审查产品中使用的任何clientlib类别是否有更改。 任何覆盖的配置\（见以下示例\）应与最新的配置进行比较，以获取最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在文件夹配置文件中设置\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您在damAssetLucene中添加了任何自定义项，则可能需要再次应用它们。 完成这些更改后，将reindex设置为true。 这将使用自定义项重新索引所有现有节点。 完成后，重新索引标志将再次设置为false。 这可能需要几个小时，具体取决于系统中的资源数量。

## 重新索引Experience Manager Guides索引的步骤

1. 打开`crx/de`并导航到索引路径： `/oak:index/guidesAssetProperties`
2. 将重新索引属性设置为`true` （默认为`false`），然后单击&#x200B;**全部保存**。
3. 重新索引完成后，重新索引属性再次设置为`false`，并且重新索引计数以1为单位递增。

   >[!NOTE]
   >
   > 这可能需要几分钟的时间，具体取决于存在的数据量。
4. 对其他添加或修改的索引执行相同的步骤： `guidesBulkActivation`、`guidesPeerLinkIndex`和`guidesKonnectTemplateIndex`。

## 索引现有内容的步骤



执行以下步骤来索引现有内容：

- 对服务器运行POST请求\（使用正确的身份验证\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (可选：您可以传递映射的特定路径来对其进行索引，默认情况下，所有映射都将进行索引 || 示例：`https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 该API将返回作业ID。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： ` http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

- 作业完成后，上述GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。


>[!NOTE]
>
> 如果使用自定义架构，则必须在&#x200B;**集成目录**&#x200B;选项中定义AEM存储库中自定义DTD和XSD catalog.xml文件的路径。




## 处理`'fmdita rewriter'`冲突的步骤

Experience Manager Guides有一个&#x200B;[**自定义sling重写器**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模块，用于处理在交叉映射（两个不同映射的主题之间的链接）情况下生成的链接。

如果您的代码库中有另一个自定义sling重写器，请使用大于50的`'order'`值，因为Experience Manager Guides sling重写器使用`'order'` 50。  要覆盖此值，您需要一个大于50的值。 有关详细信息，请查看[输出重写管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升级过程中，由于`'order'`值从1000更改为50，因此您需要将现有的自定义重写器（如果有）与`'fmdita-rewriter'`合并。



## 重新索引damAssetLucene的步骤

带有指南的damAssetLucene的索引定义已更新。 请参阅[本文](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-16460)，了解在升级到5.0.0版本后如何重新索引damAssetLucene。

>[!NOTE]
>
> 在遵循文档操作时，请确保通过保存操作同时更新两个属性（对于/oak:index/damAssetLucene，reindex=true和reindex-async=true）。

## 升级到版本5.1.0

>[!IMPORTANT]
>
> 如果您当前使用AEM 6.5，并计划迁移到AEM 6.5 LTS，请确保先完成AEM升级，然后再继续进行Experience Manager Guides 5.1.0升级。 有关详细信息，请查看[升级到Adobe Experience Manager (AEM) 6.5 LTS](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/implementing/deploying/upgrading/upgrade)。

**先决条件**

>[!NOTE]
>
>如果您要升级到5.1.0 Service Pack 3，则需要使用Experience Manager Guides的5.1.0或5.1.x版本。

在开始Experience Manager Guides 5.1.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本4.6.3、4.6.4、5.0.0或5.0.0 Service Pack 1，并完成了各自的安装步骤。
1. （可选）已关闭所有翻译任务。
1. 已将&#x200B;**类的日志级别更改为** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。

>[!NOTE]
>
> 后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

## 安装版本5.1.0

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载5.1.0版本包。
1. 安装版本5.1.0包。
1. 您可以选择点击触发器以启动翻译图升级作业。 有关详细信息，请参阅[通过Servlet启用脚本触发器](#enable-trigger-of-script-via-a-servlet)。

1. 完成软件包安装后，请等待日志中显示以下消息：

   `Completed the post deployment setup script`

   上述消息指示所有安装步骤均已完成。

   如果您遇到以下任何错误前缀，请将其报告给您的客户成功团队：

   - 部署后设置脚本出错
   - 移植翻译映射时出现异常
   - 无法为属性将翻译映射从v1端口转换为v2
1. 升级随版本5.1.0一起发布的氧气连接器插件\（如果需要\）。
1. 安装包后清除浏览器缓存。

## 安装版本5.1.0之后

安装Experience Manager Guides后，您可以将适用于从新安装的版本到设置的各种配置合并到一起。

>[!NOTE]
>
> 可以自定义dam-update-asset模型。 因此，如果已完成任何自定义设置，那么我们需要将自定义设置和Experience Manager Guides同步到模型的工作副本中。

1. **DAM更新资产工作流\（后处理更改\）：**

1. 打开URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 选择&#x200B;**DAM更新资产工作流**。
1. 选择&#x200B;**编辑**。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件存在，请确保已同步自定义项。
1. 如果&#x200B;**DXML后处理启动器**&#x200B;组件不存在，请执行以下步骤以插入该组件：

1. 选择&#x200B;**插入组件** \(负责将Experience Manager Guides后处理作为流程的最后一步\)。
1. 使用以下详细信息配置&#x200B;**流程步骤**：

   **常用选项卡**

   **标题：** DXML后处理发起程序

   **描述**： DXML后处理发起程序步骤，它将触发用于已修改/创建的资产的DXML后处理的Sling作业

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
   - 任何来自/libs/fmditor/libsis的叠加组件都应与新的产品代码进行比较，并且更新应在/apps下的叠加文件中完成。
   - 应审查产品中使用的任何clientlib类别是否有更改。 任何覆盖的配置\（见以下示例\）应与最新的配置进行比较，以获取最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在文件夹配置文件中设置\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您在damAssetLucene中添加了任何自定义项，则可能需要再次应用它们。 完成这些更改后，将reindex设置为true。 这将使用自定义项重新索引所有现有节点。 完成后，重新索引标志将再次设置为false。 这可能需要几个小时，具体取决于系统中的资源数量。

## 重新索引Experience Manager Guides索引的步骤

1. 打开`crx/de`并导航到索引路径： `/oak:index/guidesAssetProperties`
2. 将重新索引属性设置为`true` （默认为`false`），然后单击&#x200B;**全部保存**。
3. 重新索引完成后，重新索引属性再次设置为`false`，并且重新索引计数以1为单位递增。

   >[!NOTE]
   >
   > 这可能需要几分钟的时间，具体取决于存在的数据量。
4. 对其他添加或修改的索引执行相同的步骤： `guidesBulkActivation`、`guidesPeerLinkIndex`和`guidesKonnectTemplateIndex`。

## 索引现有内容的步骤



执行以下步骤来索引现有内容：

- 对服务器运行POST请求\（使用正确的身份验证\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (可选：您可以传递映射的特定路径来对其进行索引，默认情况下，所有映射都将进行索引 || 示例：`https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 该API将返回作业ID。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： ` http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

- 作业完成后，上述GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。


>[!NOTE]
>
> 如果使用自定义架构，则必须在&#x200B;**集成目录**&#x200B;选项中定义AEM存储库中自定义DTD和XSD catalog.xml文件的路径。




## 处理`'fmdita rewriter'`冲突的步骤

Experience Manager Guides有一个&#x200B;[**自定义sling重写器**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模块，用于处理在交叉映射（两个不同映射的主题之间的链接）情况下生成的链接。

如果您的代码库中有另一个自定义sling重写器，请使用大于50的`'order'`值，因为Experience Manager Guides sling重写器使用`'order'` 50。  要覆盖此值，您需要一个大于50的值。 有关详细信息，请查看[输出重写管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升级过程中，由于`'order'`值从1000更改为50，因此您需要将现有的自定义重写器（如果有）与`'fmdita-rewriter'`合并。



## 重新索引damAssetLucene的步骤

带有指南的damAssetLucene的索引定义已更新。 请参阅[本文](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-16460)，了解在升级到5.1.0版本后如何重新索引damAssetLucene。

>[!NOTE]
>
> 在遵循文档操作时，请确保通过保存操作同时更新两个属性（对于/oak:index/damAssetLucene，reindex=true和reindex-async=true）。



**父主题：** [下载并安装](download-install.md)
