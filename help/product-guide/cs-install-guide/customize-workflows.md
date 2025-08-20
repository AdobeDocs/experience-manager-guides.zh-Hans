---
title: 配置和自定义工作流
description: 了解如何配置和自定义工作流
exl-id: a5742082-cc0b-49d9-9921-d0da1b272ea5
feature: Workflow Configuration
role: Admin
level: Experienced
source-git-commit: 01efb1f17b39fcbc48d78dd1ae818ece167f4fe5
workflow-type: tm+mt
source-wordcount: '1762'
ht-degree: 2%

---

# 配置和自定义工作流 {#id181AI0OJ0RO}

借助工作流，您可以自动化Adobe Experience Manager \(AEM\)活动。 工作流包含一系列按特定顺序执行的步骤。 您可以定义要在每个步骤中执行的不同活动。 例如，您可以在创建主题审阅时向组中的所有审阅人发送电子邮件通知。 或者，在输出生成任务完成时向发布者发送通知。

有关AEM中工作流的详细信息，请参阅：

- [管理工作流实例](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html)

- 应用和参与工作流： [使用项目工作流](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/projects/workflows.html)。


本主题中的部分将指导您逐步完成AEM Guides中提供的默认工作流中可以进行的各种自定义设置。

## 自定义审核工作流 {#id176NE0C00HS}

每个组织的内容创作团队都以特定的方式工作，以满足其业务要求。 有些组织设有专门的编辑人员，而有些其他组织则设有自动编辑审查系统。 例如，在组织中，典型的创作和发布工作流程可能包括以下任务 — 每当作者完成创作内容时，它会自动发送给审阅人，审阅完成后会发送给发布者，以生成最终输出。 在AEM中，您可以采用流程的形式组合对内容和资产执行的活动并将其映射到AEM工作流。 有关AEM中工作流的详细信息，请参阅AEM文档中的[管理工作流](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html)。

AEM Guides允许您自定义默认审核工作流。 您可以将以下四个与自定义审阅相关的流程用于其他创作或发布工作流。

- **创建审核**：此进程准备创建审核任务所需的元数据。 例如，它将为审阅人分配审阅权限、将主题的状态设置为审阅、设置审阅时间表等。 在四个流程中，这是必须包含在自定义工作流中的唯一强制流程。 在工作流中，您可以选择包括或排除其他三个流程。

- **分配审阅任务**：此进程创建审阅任务并将任务通知发送给发起者和审阅者。

- **发送审阅电子邮件**：此进程将审阅电子邮件发送给发起人和审阅人。

- **将作业计划为关闭审阅**：此进程确保审阅进程在到达截止日期时完成。


创建自定义审阅工作流时，第一项任务是设置“创建审阅”进程所需的元数据。 为此，您可以创建一个ECMA脚本。 下面提供了用于分配元数据的ECMA脚本示例，其中既包括主题，也包括映射。

主题&#x200B;**的**

```javascript
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
workflowdata.getMetaDataMap().put("reviewVersion","3.0");
```

地图&#x200B;**的**

```javascript
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
workflowdata.getMetaDataMap().put("reviewVersion","3.0");
```

您可以在`/etc/workflows/scripts`节点中创建这些脚本。 下表描述了上述两个ECMA脚本所分配的属性。

| 属性 | 类型 | 描述 |
|--------|----|-----------|
| `initiator` | 字符串 | 启动审阅任务的用户的用户ID。 |
| `operation` | 字符串 | 静态值设置为`AEM_REVIEW`。 |
| `orgTopics` | 字符串 | 共享以供审核的主题路径。 指定多个以逗号分隔的主题。 |
| `payloadJson` | JSON 对象 | 指定以下值： -   `base`：包含已发送以供审阅主题的父文件夹的路径。 <br> -   `asset`：发送供审阅的主题路径。 <br> -   `referrer`：将其留空。 |
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
| `ditamapHierarchy` | JSON 对象 | 如果发送了映射以供审查，则此处的值应如下所示：[ &lbrace; &quot;path&quot;： &quot;GUID-f0df1513-fe07-473f-9960-477d4df29c87.ditamap&quot;， &quot;items&quot;： [ { &quot;path&quot;： &quot;GUID-9747e8ab-8cf1-45dd-9e20-d47d482f667d.dita&quot;， &quot;title&quot;： “”，“items”： [] } ] ]。 |
| `ditamap` | 字符串 | 指定审核任务的日期映射的路径 |
| `allowAllReviewers` | 布尔值 | false/true |
| `notifyViaEmail` | 布尔值 | false/true |
| `reviewVersion` | 字符串 | 指定审阅工作流的当前版本。 默认值设置为`3.0` 。<br>要为[作者](../user-guide/review-close-review-task.md)和[审阅人](../user-guide/review-complete-review-tasks.md)启用新的审阅工作流功能，请确保`reviewVersion`设置为`3.0`。 |


创建脚本后，请在调用工作流中的创建审阅进程之前调用该脚本。 然后，根据您的要求，您可以调用其他审阅工作流流程。

### 从清除配置中删除审核工作流

要提高工作流引擎性能，您可以定期从AEM存储库中清除已完成的工作流实例。 如果您使用默认的AEM配置，则会在特定时间段后清除所有已完成的工作流实例。 这也会导致所有审阅工作流从AEM存储库中清除。

您可以通过从自动清除配置中删除审核工作流模型\(information\)来阻止自动清除审核工作流。 您需要使用&#x200B;**Adobe Granite工作流清除配置**&#x200B;从自动清除列表中删除审核工作流模型。

在&#x200B;**Adobe Granite工作流清除配置**&#x200B;中，确保至少列出一个可安全清除的工作流。 例如，您可以使用由AEM Guides创建的以下任何工作流：

- /etc/workflow/models/publishditamap/jcr:content/model
- /etc/workflow/models/post-dita-project-creation-tasks/ jcr:content/model

在&#x200B;**Adobe Granite工作流清除配置**&#x200B;中添加工作流可确保AEM仅清除配置中列出的那些工作流。 这会阻止AEM清除审核工作流信息。

有关配置&#x200B;**Adobe Granite工作流清除配置**&#x200B;的更多详细信息，请参阅AEM文档中的&#x200B;*管理工作流实例*。

### 自定义电子邮件和AEM通知

许多AEM Guides工作流会使用电子邮件通知。 例如，如果您启动审阅任务，则会向审阅人发送电子邮件通知。 但是，要确保电子邮件通知已发送，您必须在AEM中启用此功能。 要在AEM中启用电子邮件通知，请参阅AEM文档中的文章[发送电子邮件](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#sending-email)。

AEM Guides包含一组用于审核工作流的电子邮件和AEM通知，您可以对这些通知进行自定义。 执行以下步骤以自定义这些通知：

1. 使用包管理器下载`/libs/fmdita/mail/review`文件夹。

   >[!NOTE]
   >
   > 请勿在``libs``节点中使用默认配置文件中的任何自定义设置。 您必须在``libs``节点中创建``apps``节点的叠加，并仅更新``apps``节点中的所需文件。

1. `review`文件夹包含以下子文件夹：

   - `aem-notification`
   - `CSS`
   - `email-notification`

   这些子文件夹的详细说明如下：

   | 查看子文件夹 | 描述 |
   |-----------------|-----------|
   | `aem-notification` | 包含可供自定义的其他AEM通知类型。<br> `closed` <br> `content-updated` <br> `feedback-addressed` <br> `feedback-provided` <br> `requested` <br> `reviewer-removed` <br> `tag-mention` <br>在这些子文件夹中，找到`primary.vm`和`secondary.vm`个分别允许您自定义AEM通知标题和描述的文件。 |
   | `CSS` | 包含用于自定义电子邮件通知样式的`email-notification.css`文件。 |
   | `email-notification` | 包含可供自定义的不同电子邮件通知类型。<br> `closed` <br> `content-updated` <br> `feedback-addressed` <br> `feedback-provided` <br> `requested` <br> `reviewer-removed` <br> `tag-mention` <br>在这些子文件夹中，找到`primary.vm`和`secondary.vm`个分别允许您自定义电子邮件通知主题和正文的文件。 |

每种通知类型的定义概述如下：

- `closed`：审核任务关闭时触发。
- `content-updated`：作者或发起人更新内容时触发。
- `feedback-addressed`：作者或发起者处理注释并请求审阅者重新审阅时触发。
- `feedback-provided`审阅者通过向审阅任务的作者或发起者提供任务级注释，将任务标记为完成时触发。
- `requested`：作者或发起者创建审核任务时触发。
- `reviewer-removed`：从审核任务中取消分配审核者时触发。
- `tag-mention`：在审核评论中提及或标记用户时触发。

在自定义电子邮件或AEM通知时，请确保仅使用在`primary.vm`和`secondary.vm`文件中使用的以下预定义变量集。


| **变量名称** | **描述** | **数据类型** |
|-------------------------|---------------------------------------------------------------|---------------|
| `projectPath` | 包含审阅任务的项目的路径 | 字符串 |
| `reviewTitle` | 审核任务的标题 | 字符串 |
| `projectName` | 项目名称 | 字符串 |
| `commentator` | 添加评论的用户的名称 | 字符串 |
| `commentExcerpt` | 添加的评论片段 | 字符串 |
| `taskLink` | 审阅任务的直接链接 | URL |
| `authorName` | 创建或更新审阅任务的作者的姓名 | 字符串 |
| `dueDate` | 审核任务的截止日期 | 日期 |
| `reviewerName` | 分派给任务的审阅者姓名 | 字符串 |
| `user` | 审阅任务中涉及的用户，如作者、审阅者，甚至管理员。 | 字符串 |
| `recipient` | 接收通知的特定用户 | 字符串 |


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

```javascript
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
