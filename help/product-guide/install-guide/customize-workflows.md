---
title: 配置和自定义工作流
description: 了解如何配置和自定义工作流
exl-id: 3be387b9-6ac2-4b61-afdf-fbe9d8b6cc1e
feature: Workflow Configuration
role: Admin
level: Experienced
source-git-commit: 01efb1f17b39fcbc48d78dd1ae818ece167f4fe5
workflow-type: tm+mt
source-wordcount: '1854'
ht-degree: 2%

---

# 配置和自定义工作流 {#id181AI0OJ0RO}

借助工作流，您可以自动化Adobe Experience Manager \(AEM\)活动。 工作流包含一系列按特定顺序执行的步骤。 您可以定义要在每个步骤中执行的不同活动。 例如，您可以在创建主题审阅时向组中的所有审阅人发送电子邮件通知。 或者，在输出生成任务完成时向发布者发送通知。

有关AEM中工作流的详细信息，请参阅：

- [管理工作流](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/workflows.html)

- 应用和参与工作流： [使用工作流](https://helpx.adobe.com/experience-manager/6-5/sites/authoring/using/workflows.html)。

- 创建工作流模型和扩展工作流功能： [开发和扩展工作流](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/workflows.html)。

- 提高使用重要服务器资源的工作流的性能： [并发工作流处理](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/configuring-performance.html#ConfiguringforPerformance)。


本主题中的部分将指导您逐步完成AEM Guides中提供的默认工作流中可以进行的各种自定义设置。

## 自定义审核工作流 {#id176NE0C00HS}

每个组织的内容创作团队都以特定的方式工作，以满足其业务要求。 有些组织设有专门的编辑人员，而有些其他组织则设有自动编辑审查系统。 例如，在组织中，典型的创作和发布工作流程可能包括以下任务 — 每当作者完成创作内容时，它会自动发送给审阅人，审阅完成后会发送给发布者，以生成最终输出。 在AEM中，您可以采用流程的形式组合对内容和资产执行的活动并将其映射到AEM工作流。 有关AEM中工作流的详细信息，请参阅AEM文档中的[管理工作流](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/workflows.html)。

AEM Guides允许您自定义默认审核工作流。 您可以将以下四个与自定义审阅相关的流程用于其他创作或发布工作流。

- **创建审核**：此进程准备创建审核任务所需的元数据。 例如，它将为审阅人分配审阅权限、将主题的状态设置为审阅、设置审阅时间表等。 在四个流程中，这是必须包含在自定义工作流中的唯一强制流程。 在工作流中，您可以选择包括或排除其他三个流程。

- **分配审阅任务**：此进程创建审阅任务并将任务通知发送给发起者和审阅者。

- **发送审阅电子邮件**：此进程将审阅电子邮件发送给发起人和审阅人。

- **将作业计划为关闭审阅**：此进程确保审阅进程在到达截止日期时完成。


创建自定义审阅工作流时，第一项任务是设置“创建审阅”进程所需的元数据。 为此，您可以创建一个ECMA脚本。 下面提供了用于分配元数据的ECMA脚本示例，其中既包括主题，也包括映射。

主题&#x200B;**的**

```json
var workflowdata=workItem.getWorkflowData();
workflowdata.getMetaDataMap().put("initiator","admin");
workflowdata.getMetaDataMap().put("operation","AEM_REVIEW");
workflowdata.getMetaDataMap().put("orgTopics","/content/dam/xml-solution/review.xml");
workflowdata.getMetaDataMap().put("payloadJson","{\"base\":\"/content/dam/xml-solution\",\"asset\":[\"/content/dam/xml-solution/review.xml\"],\"referrer\":\""}");
workflowdata.getMetaDataMap().put("deadline","2017-06-27T13:19:00.000+05:30");
workflowdata.getMetaDataMap().put("title","Review through custom workflow");
workflowdata.getMetaDataMap().put("description","Initiate this review process using the AEM workflow");
workflowdata.getMetaDataMap().put("assignee","user-one", "user-two");
workflowdata.getMetaDataMap().put("status","1");
workflowdata.getMetaDataMap().put("projectPath","/content/projects/review");
workflowdata.getMetaDataMap().put("startTime", System.currentTimeMillis());
workflowdata.getMetaDataMap().put("reviewType", "AEM");
workflowdata.getMetaDataMap().put("versionJson", "[{\"path\":\"GUID-ca6ae229-889a-4d98-a1c6-60b08a820bb3.dita\",\"review\":true,\"version\":\"1.0\",\"reviewers\":[\"projects-samplereviewproject-owner\"]}]");
workflowdata.getMetaDataMap().put("isDitamap","false");
```

地图&#x200B;**的**

```json
var workflowdata = workItem.getWorkflowData();
workflowdata.getMetaDataMap().put("initiator", "admin");
workflowdata.getMetaDataMap().put("operation", "AEM_REVIEW");
workflowdata.getMetaDataMap().put("orgTopics", "GUID-ae42f13c-7201-4453-9a3a-c87675a5868e.dita|GUID-28a6517b-1b62-4d3a-b7dc-0e823225b6a5.dita|GUID-dd699e10-118d-4f1b-bf19-7f1973092227.dita|");
var payloadJson = "{\"referrer\":\"\",\"rootMap\":\"GUID-17feb385-acf3-4113-b838-77b11fd6988d.ditamap\",\"asset\":[\"GUID-17feb385-acf3-4113-b838-77b11fd6988d.ditamap\"],\"base\":\"/content/dam\"}";
workflowdata.getMetaDataMap().put("payloadJson", payloadJson);
workflowdata.getMetaDataMap().put("deadline", "2047-06-27T13:19:00.000+05:30");
workflowdata.getMetaDataMap().put("title", "Review task via workflow with map");
workflowdata.getMetaDataMap().put("description", "Review task via workflow with map Description");
workflowdata.getMetaDataMap().put("assignee", "user-one");
workflowdata.getMetaDataMap().put("status", "1");
workflowdata.getMetaDataMap().put("projectPath", "/content/projects/review_project_via_workflow");
workflowdata.getMetaDataMap().put("startTime", new Date().getTime());
var versionJson = "[{\"path\":\"GUID-ae42f13c-7201-4453-9a3a-c87675a5868e.dita\",\"version\":\"1.0\",\"review\":true,\"reviewers\":[\"starling-regression-user\"]},{\"path\":\"GUID-28a6517b-1b62-4d3a-b7dc-0e823225b6a5.dita\",\"version\":\"1.0\",\"review\":true,\"reviewers\":[\"starling-regression-user\"]},{\"path\":\"GUID-dd699e10-118d-4f1b-bf19-7f1973092227.dita\",\"version\":\"1.0\",\"review\":true,\"reviewers\":[\"starling-regression-user\"]}]";
workflowdata.getMetaDataMap().put("versionJson", versionJson);
workflowdata.getMetaDataMap().put("notifyViaEmail", "true");
workflowdata.getMetaDataMap().put("allowAllReviewers", "false");
workflowdata.getMetaDataMap().put("isDitamap", "true");
workflowdata.getMetaDataMap().put("ditamap", "GUID-17feb385-acf3-4113-b838-77b11fd6988d.ditamap");
var ditamapHierarchy = "[{\"path\":\"GUID-17feb385-acf3-4113-b838-77b11fd6988d.ditamap\",\"items\":[{\"path\":\"GUID-db5787bb-5467-4dc3-b3e5-cfde562ee745.ditamap\",\"items\":[{\"path\":\"GUID-ae42f13c-7201-4453-9a3a-c87675a5868e.dita\",\"items\":[],\"title\":\"\"},{\"path\":\"GUID-28a6517b-1b62-4d3a-b7dc-0e823225b6a5.dita\",\"items\":[],\"title\":\"\"}],\"title\":\"\"},{\"path\":\"GUID-dd699e10-118d-4f1b-bf19-7f1973092227.dita\",\"items\":[],\"title\":\"\"}]}]";
workflowdata.getMetaDataMap().put("ditamapHierarchy", ditamapHierarchy);
```

您可以在`/etc/workflows/scripts`节点中创建此脚本。 下表描述了此ECMA脚本所分配的属性：

| 属性 | 类型 | 描述 |
|--------|----|-----------|
| `initiator` | 字符串 | 启动审阅任务的用户的用户ID。 |
| `operation` | 字符串 | 静态值设置为`AEM_REVIEW`。 |
| `orgTopics` | 字符串 | 共享以供审核的主题路径。 指定多个以逗号分隔的主题。 |
| `payloadJson` | JSON 对象 | 指定以下值： <br> - `base`：包含已发送以供审阅主题的父文件夹的路径。<br>- `asset`：发送以供审阅的主题路径。 <br>- `referrer`：将其留空。 |
| `deadline` | 字符串 | 以`yyyy-MM-dd'T'HH:mm:ss.SSSXXX`格式指定时间。 |
| `title` | 字符串 | 输入审核任务的标题。 |
| `description` | 字符串 | 输入审核任务的说明。 |
| `assignee` | 字符串 | 要向其发送主题以供审阅的用户的用户ID。 |
| `status` | 整数 | 静态值设置为1。 |
| `startTime` | 长 | 使用`System.currentTimeMillis()`函数获取当前系统时间。 |
| `projectPath` | 字符串 | 将为其分配审阅任务的审阅项目的路径，例如： /content/projects/samplereviewproject。 |
| `reviewType` | 字符串 | 静态值“AEM”。 |
| `versionJson` | JSON 对象 | versionJson是审核中的主题列表，其中每个主题对象具有以下结构[ { &quot;path&quot;： &quot;/content/dam/1-topic.dita&quot;， &quot;version&quot;： &quot;1.1&quot;， &quot;review&quot;： true， &quot;reviewers&quot;： [&quot;projects-we_retail-editor&quot;] } ] |
| `isDitamap` | 布尔值 | false/true |
| `ditamapHierarchy` | JSON 对象 | 如果发送了映射以供审查，则此处的值应如下所示：[ { &quot;path&quot;： &quot;GUID-f0df1513-fe07-473f-9960-477d4df29c87.ditamap&quot;， &quot;items&quot;： [ { &quot;path&quot;： &quot;GUID-9747e8ab-8cf1-45dd-9e20-d47d482f667d.dita&quot;， &quot;title&quot;： “”，“items”： [] } ] ]。 |
| `ditamap` | 字符串 | 指定审核任务的日期映射的路径 |
| `allowAllReviewers` | 布尔值 | false/true |
| `notifyViaEmail` | 布尔值 | false/true |


创建脚本后，请在调用工作流中的创建审阅进程之前调用该脚本。 然后，根据您的要求，您可以调用其他审阅工作流流程。

### 从清除配置中删除审核工作流

要提高工作流引擎性能，您可以定期从AEM存储库中清除已完成的工作流实例。 如果您使用默认的AEM配置，则会在特定时间段后清除所有已完成的工作流实例。 这也会导致所有审阅工作流从AEM存储库中清除。

您可以通过从自动清除配置中删除审核工作流模型\(information\)来阻止自动清除审核工作流。 您需要使用&#x200B;**Adobe Granite工作流清除配置**&#x200B;从自动清除列表中删除审核工作流模型。

在&#x200B;**Adobe Granite工作流清除配置**&#x200B;中，确保至少列出一个可安全清除的工作流。 例如，您可以使用由AEM Guides创建的以下任何工作流：

- /etc/workflow/models/publishditamap/jcr:content/model
- /etc/workflow/models/post-dita-project-creation-tasks/ jcr:content/model

在&#x200B;**Adobe Granite工作流清除配置**&#x200B;中添加工作流可确保AEM仅清除配置中列出的那些工作流。 这会阻止AEM清除审核工作流信息。

有关配置&#x200B;**Adobe Granite工作流清除配置**&#x200B;的更多详细信息，请参阅AEM文档中的&#x200B;*管理工作流实例*。

### 自定义电子邮件模板

许多AEM Guides工作流会使用电子邮件通知。 例如，如果您启动审阅任务，则会向审阅人发送电子邮件通知。 但是，要确保电子邮件通知已发送，您必须在AEM中启用此功能。 要在AEM中启用电子邮件通知，请参阅AEM文档中的文章[配置电子邮件通知](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=zh-Hans)。

AEM Guides包含一组您可自定义的电子邮件模板。 执行以下步骤可自定义这些模板：

1. 登录AEM并打开CRXDE Lite模式。

1. 在“导航”选项卡中，转到以下位置：

   `/libs/fmdita/mail`

   >[!NOTE]
   >
   > 请勿在``libs``节点中使用默认配置文件中的任何自定义设置。 您必须在``libs``节点中创建``apps``节点的叠加，并仅更新``apps``节点中的所需文件。

1. 邮件文件夹包含以下可自定义的模板：

   | 模板文件名 | 描述 |
   |-----------------|-----------|
   | closereview.html | 此电子邮件模板在关闭审核任务时使用。 |
   | createreview.html | 创建新审阅任务时使用此电子邮件模板。 |
   | reviewapproval.css | 此CSS文件包含电子邮件模板的样式。 |


## 自定义输出后生成工作流 {#id17A6GI004Y4}

AEM Guides可让您灵活地指定输出后生成工作流程。 您可以对使用AEM Guides生成的输出执行一些后处理任务。 例如，您可能希望在生成的AEM Site输出中应用一些CQ标记，或在PDF输出中设置某些属性，或者在生成输出后向一组用户发送电子邮件。

您可以创建新的工作流模型以用作输出后生成工作流。 触发输出后生成工作流时，输出生成工作流通过工作流元数据映射共享上下文信息，您可以使用这些上下文信息对生成的输出执行处理。 下表描述了作为元数据共享的上下文信息：

| 属性 | 类型 | 描述 |
|--------|----|-----------|
| ``outputName`` | 字符串 | 用于生成输出的输出预设的名称。 |
| `generatedPath` | 字符串 | DAM中存储生成的输出的路径。 |
| `outputType` | com.adobe.fmdita.output.OutputType | 输出预设的类型。 |
| `outputTitle` | 字符串 | 输出预设的标题。 |
| `outputHistoryPath` | 字符串 | 历史记录节点的存储库路径。 |
| `isSuccess` | 布尔值 | 描述输出生成过程的最终状态（成功或失败）的标志。 |
| `logPath` | 字符串 | DAM中保存输出生成日志的路径。 |
| `generatedTime` | 长 | 触发输出生成过程的时间。 |
| `initiator` | 字符串 | 触发输出生成工作流的用户的用户ID。 |

要利用输出生成元数据，您可以创建ECMA脚本或OSGi捆绑包。 下面给出了使用元数据的ECMA脚本示例：

>[!NOTE]
>
> 您可以在``/etc/workflows/scripts``节点中创建此脚本。

```json
var session = workflowSession.getSession(); // Obtain session object to read/write the repository.
var payload = workItem.getWorkflowData().getPayload().toString(); // Get the workflow payload (the ditamap file on which the generation was triggered)
var metadata = workItem.getWorkflowData().getMetaDataMap(); // Get the workflow metadata object
var generatedPath = metadata.get("generatedPath"); // supplied by AEM Guides
var username = metadata.get("initiator"); // supplied by AEM Guides
var successful = metadata.get("isSuccess"); // supplied by AEM Guides
var title = metadata.get("outputTitle"); // supplied by AEM Guides
var subject = "Output Generation Finished";
var message = "Generation of output " + title + " just finished " + 
(successful ? "successfully. " : "unsuccessfully. ");
    message += "It was triggered by " + username;    
if (successful) {
    message += "<br/><br/>The path to the generated output is " + 
generatedPath;
}
/*
    MailerAPI.sendMail("dl-docs-authors", subject, message);
*/
```

创建脚本后，在工作流中调用自定义脚本。 然后，根据您的要求，您可以调用其他工作流进程。 设计自定义工作流后，调用&#x200B;*完成帖子生成*&#x200B;作为工作流进程的最后一步。 *最终确定后生成*&#x200B;步骤可确保输出生成任务的状态在输出生成过程完成时更新为&#x200B;*已完成*。 创建自定义输出后生成工作流后，您可以将其配置为使用任何输出生成预设。 在所需预设的&#x200B;*运行生成后工作流*&#x200B;属性中选择所需的工作流。 使用配置的输出预设运行输出生成任务时，\（在“输出”选项卡中\）任务状态将更改为&#x200B;*后处理*。

## 自定义更新资产工作流 {#id18C3D0I0B5Z}

默认情况下，每当您创建或更新任何AEM资源\（XML或非XML\）时，*DAM更新资源*&#x200B;工作流都会触发。 例如，当您创建或更新主题时，将执行&#x200B;*DAM更新资产*&#x200B;工作流。 *DAM更新资产*&#x200B;工作流尝试从Assets中提取相关元数据。 现成的&#x200B;*资产更新工作流*&#x200B;没有从DITA文件提取任何相关元数据的任何步骤，并且&#x200B;*DAM更新资产*&#x200B;工作流在执行时生成大量日志。 如果要避免额外的日志，可以配置工作流以跳过处理所有XML文件。

执行以下步骤以自定义&#x200B;*DAM更新资产*&#x200B;工作流：

1. 打开&#x200B;**工作流启动器**&#x200B;页面。

   访问“工作流启动器”页面的默认URL为：

   ```http
   http://<server name>:<port>/libs/cq/workflow/admin/console/content/launchers.html
   ```

1. 从工作流启动器列表中，打开&#x200B;**DAM更新资产**&#x200B;工作流的属性。

1. 使用以下表达式添加条件：

   ```json
   jcr:content/metadata/dc:format!=application/xml
   ```

1. 点击&#x200B;**保存并关闭**


## 配置后处理XML工作流 {#id18CJB03J0Y4}

AEM Guides创建了一系列工作流，这些工作流允许您在AEM中使用DITA内容。 例如，有些工作流会在您上传DITA内容或更新现有内容时执行。 这些工作流解析DITA文档并执行各种任务，例如设置元数据、将默认输出预设添加到新的DITA映射以及其他相关任务。

>[!NOTE]
>
> Adobe Experience Manager Guides要自定义或扩展默认的后处理工作流，您可以使用&#x200B;*API参考*&#x200B;中所述的后处理事件处理程序。

以下属性控制AEM Guides执行后处理工作流的方式：

>[!NOTE]
>
> 可通过Web控制台访问以下属性： http://&lt;服务器名称\>：&lt;端口\>/system/console/configMgr。

| 属性 | 包名称 | 描述 |
|--------|-----------|-----------|
| 动态外置 | `com.adobe.fmdita.postprocess.PostProcessObservation` | 对于尚未对其执行后处理的所有文件，它通过解析主题文件来检索出站引用。 建议禁用此选项，因为如果要处理的文件数量很大，此选项可能会使系统过载。 |
| 后处理Threads | `com.adobe.fmdita.config.ConfigManager` | 设置用于后处理工作流的后处理线程数。 <br>默认值为1。 |
