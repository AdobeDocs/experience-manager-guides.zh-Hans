---
title: 基本疑难解答
description: 解决AEM Guides中的基本故障诊断问题。 了解如何在文本编辑器中查看、复制和检查日志文件并解决JSP编译错误。
feature: Publishing, Troubleshooting
role: User
hide: true
exl-id: f85fee0f-30d1-453f-8700-781e0be8f616
source-git-commit: 26fa1e52920c1f1abd5655b9ca7341600a9bca67
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# 基本疑难解答 {#id1821I0Y0G0A}

使用AEM Guides时，在发布或打开文档时可能会遇到错误。 此类错误可能位于DITA映射、主题或AEM Guides进程本身中。 本节提供了有关如何访问和分析输出生成日志文件中的信息的信息。 此外，如果DITA主题太大，则可能会看到JSP编译错误。 本节还提供了有关如何解决JSP编译错误的信息。

## 查看并检查日志文件 {#id1822G0P0CHS}

执行以下步骤以查看并检查输出生成日志文件：

1. 启动输出生成过程后，在DITA映射控制台中单击&#x200B;**输出**。

   **生成的输出**&#x200B;的&#x200B;**常规**&#x200B;列显示一些图标，以直观提示输出生成的成功或失败。

   ![](images/output-general-settings.png){width="300" align="left"}

   在上面的屏幕快照中，第一个和第三个图标显示生成的输出失败。 第二个图标显示成功的输出生成，但显示消息。 最后一种是没有任何消息的成功输出生成。

1. 作业完成后，单击&#x200B;**生成时间**&#x200B;列中的链接。

   日志文件将在新选项卡中打开。

   ![](images/log-file.png){width="800" align="left"}

1. 应用以下筛选器以高亮显示日志文件中的文本：
   - 致命：以粉红色突出显示日志文件中的致命错误。
   - 错误：以橙色突出显示日志文件中的错误。
   - 警告：以紫色突出显示日志文件中的警告。
   - 信息：以蓝色突出显示日志文件中的信息消息。
   - 异常：以黄色突出显示日志文件中的异常。
1. 使用向上和向下导航按钮跳转到日志文件中突出显示的文本。

   或者，滚动浏览日志文件并检查消息。


## 在文本编辑器中复制并检查日志文件

执行以下步骤，在文本编辑器中复制并检查输出生成日志文件：

1. 启动输出生成过程后，在DITA映射控制台中单击&#x200B;**输出**。

1. 作业完成后，单击&#x200B;**生成时间**&#x200B;列中的链接。

   日志文件将在新选项卡中打开。

1. 单击&#x200B;**复制日志**&#x200B;按钮。 日志文件将复制到剪贴板中。
1. 打开文本编辑器并在编辑器中粘贴日志文件。

1. 滚动浏览日志文件并检查消息。

   以下信息将帮助您确定DITA文件或AEM Guides进程中是否存在错误：

   - *与DITA映射文件相关的错误*：如果在DITA映射文件或DITA映射中包含的任何其他文件中发现错误，则日志文件将包含字符串“BUILD FAILED”。 您可以检查日志文件中提供的信息以找到错误文件并修复问题。

   在以下示例日志文件片段中，您可以看到`BUILD FAILED`消息以及错误原因。

   ![](images/dita-error-in-log-file.png){width="650" align="left"}

   - *与AEM Guides相关的错误*：您可以在日志文件中识别的其他错误类型与AEM Guides进程本身相关。 在这种情况下，已成功解析DITA映射文件，但输出生成过程会由于AEM Guides中的一些内部错误而失败。 对于此类错误，您必须寻求技术支持团队的帮助。

   在以下示例日志文件片段中，您可以看到`BUILD SUCCESSFUL`消息，随后是其他技术错误。

   ![](images/process-error-in-log-file.png){width="650" align="left"}


## 解决JSP编译错误

如果DITA主题过大，则您可能会在浏览器中看到JSP编译错误\(`org.apache.sling.api.request.TooManyCallsException`\)。 打开主题进行编辑、审阅或发布时，可能会显示此错误。

执行以下步骤以解决此问题：

1. 在“全局导航”中，选择“工具”，然后选择“操作”\>“Web控制台”。

   此时将显示“Adobe Experience Manager Web控制台配置”页面。

1. 搜索并单击&#x200B;*Apache Sling主Servlet*&#x200B;组件。

   此时将显示Apache Sling主Servlet的可配置选项。

1. 根据您的要求，增加每个请求&#x200B;*调用数*&#x200B;参数的值。


**父主题：**&#x200B;[&#x200B;输出生成](generate-output.md)
