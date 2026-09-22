---
title: 为云服务和内部部署配置XML解析实体
description: 了解如何为云服务和内部部署配置XML解析实体
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: e4019ae1e605bd26f7df676a4fab8c632fd8fa8e
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 1%
---
# 配置XML解析器实体大小限制

Experience Manager Guides允许您配置对XML解析器在发布期间接受的总实体大小的限制。 这有助于防止XML实体扩展攻击和处理超大负载等问题。

>[!NOTE]
>
>您可以对XML解析器在发布期间接受的总实体大小配置限制，从而降低XML实体扩展攻击和处理超大负载等风险。 Java 21和Java 25之间的实体大小限制处理有所不同；因此，建议升级到Java 25的环境审查和验证其配置，以确保发布工作流继续运行而不会出错。

此配置涉及两个相关的属性：

* **应用XML解析器实体总大小限制** (`dxml.publish.xml.apply.total.entity.size.limit`)：启用或禁用实体总大小限制检查。
* **XML解析器实体总大小限制** (`dxml.publish.xml.total.entity.size.limit`)：指定启用应用标志时应用于安全XML解析器的JAXP `totalEntitySizeLimit`值（字符）。

以下选项卡提供了根据Experience Manager Guides设置配置这些资产的说明：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[配置覆盖](download-install-config-override.md)中提供的说明创建配置文件。

1. 在配置文件中，提供以下（属性）详细信息：

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService` | `dxml.publish.xml.apply.total.entity.size.limit` | **默认值：** &quot;true&quot; |
   | `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService` | `dxml.publish.xml.total.entity.size.limit` | **默认值：** &quot;50000000&quot; |

>[!TAB 内部部署]

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;*com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService*&#x200B;捆绑包。

1. 根据您的要求配置以下设置：

   * **应用XML分析器实体总大小限制** (`dxml.publish.xml.apply.total.entity.size.limit`)：默认情况下，此设置处于禁用状态。
   * **XML解析器实体总大小限制** (`dxml.publish.xml.total.entity.size.limit`)：默认情况下，此值设置为`50000000`个字符。 此设置仅在启用&#x200B;**应用XML解析器实体总大小限制**&#x200B;设置时生效。

1. 选择&#x200B;**保存**。

>[!ENDTABS]



