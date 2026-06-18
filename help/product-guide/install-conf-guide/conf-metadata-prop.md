---
title: 配置元数据属性的忽略列表
description: 了解如何在AEM Guides中为元数据属性配置忽略列表。
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# 配置元数据属性的忽略列表

编辑文件时，对&#x200B;**文件属性**&#x200B;下可用或后端应用的元数据字段所做的任何更改都会触发文档版本的星号(*)。 要防止系统生成的元数据更新影响此指示器，管理员可以为元数据属性配置忽略列表。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[配置覆盖](download-install-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下（属性）详细信息以配置脏版本&#x200B;**的**&#x200B;忽略元数据属性。


| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.dirtychecker.ignoremetadata` | `<comma-separated list / array of metadata properties>` |

>[!TAB 内部部署]

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;包。

1. 在&#x200B;*XmlEditorConfig*&#x200B;设置中，导航到&#x200B;**忽略已更新版本的元数据属性**&#x200B;选项。

   查看当前配置为忽略的默认元数据属性的列表。

1. 根据要求添加或删除元数据属性。
1. 选择&#x200B;**保存**&#x200B;以保存更新的配置。


>[!ENDTABS]

## 忽略列表中的默认元数据属性

AEM Guides在忽略列表中包含一组默认的元数据属性。 您可以根据需要修改此列表以添加或删除元数据属性。

* “jcr:mixinTypes”，
* “jcr:primaryType”，
* “jcr:frozenMixinTypes”，
* “jcr:frozenPrimaryType”，
* “jcr:frozenUuid”，
* “jcr:uuid”，
* “dam:extracted”，
* “jcr:lastModified”，
* “jcr:lastModifiedBy”，
* &quot;dc:modified&quot;，
* “dam:sha1”，
* “dam:size”，
* &quot;指南:wordCount&quot;，
* “dam:scene7UploadTimeStamp”，
* &quot;dam:scene7LastModified&quot;

只有未包括在忽略列表中的元数据属性才考虑将文档的版本标记为已修改。

**父主题：**[&#x200B;自定义编辑器](customize-overview.md)
