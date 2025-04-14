---
title: AEM Guides版本
description: 最新的 AEM Guides 版本和必备 AEM 版本
exl-id: 780697a9-bdc6-40c2-b258-64639fe30f88
feature: Release Notes
role: Leader
source-git-commit: a78209390f71239c9d884a75ec7d3d386e560e78
workflow-type: tm+mt
source-wordcount: '953'
ht-degree: 1%

---

# [!DNL AEM Guides]版本

[!DNL Adobe Experience Manager Guides]是部署在AEM上的应用程序。 这是一个功能强大、企业级组件内容管理解决方案(CCMS)，可在Adobe Experience Manager中启用原生DITA支持，使AEM能够处理基于DITA的内容创建和交付。

AEM Guides包有两种变体可用 — UUID内部版本和非UUID内部版本。

## UUID和非UUID内部版本

UUID和非UUID内部版本之间的主要区别如下：

|  | 非UUID版本 | UUID版本 |
|---|---|---|
| **资源标识** | 所有资源都使用存储库中资源的路径进行标识。 | 所有资产均使用其UUID（首次上传资产时系统生成的唯一ID）进行标识。 |
| **引用创建** | 所有内容引用都是根据其路径创建的。 | 所有内容引用都是基于其UUID创建的。 |

### UUID构建的优势

* UUID安装的性能更高：
   * 参照是独立于路径的：参照管理系统在参照基于UUID而不是路径创建时可识别链接。
   * 移动/更新操作高效：即使资产迁移到存储库中的其他路径，UUID仍保持不变。 因此，在移动/更新操作中，无需处理即可修补资源之间的引用。
* UUID构建具有前瞻性，因为我们也将此框架用于AEM Guides的云设置。


### 在两个内部版本之间进行选择

* 如果您是新客户，我们建议您使用UUID内部版本。
* 如果您是现有客户，则可以选择迁移到UUID内部版本，因为现在可以从非UUID内部版本迁移到UUID内部版本。 有关更多详细信息，请参阅&#x200B;**安装和配置Adobe Experience Manager Guides**&#x200B;中的&#x200B;*从Non-UUID迁移到UUID内容*&#x200B;部分。

>[!NOTE]
>
>* 在首次设置时，客户将需要在UUID和非UUID模式之间进行选择（如果您需要帮助，请联系客户成功经理，帮助您根据用例做出决策）。
>* 从一种版本的AEM Guides升级到较新版本时，客户将需要确保选择相同的模式（UUID/非UUID）以匹配其现有模式。 非UUID内部版本不应直接升级到UUID内部版本。 从非UUID内部版本迁移到UUID内部版本将需要内容迁移。

**正在升级内部版本**

当您从较旧版本升级到[!DNL AEM Guides]的较新版本时，您可能需要执行迁移脚本。 有关升级说明，请参阅发行说明和特定于版本的文档。

并非所有升级路径都直接受支持。 例如，只有从版本3.8直接升级到版本4.0才可行。
If you are on a version prior to 3.8, then refer to your version-specific documentation for upgrade instructions [Help Archive](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html).
请联系您的客户成功经理以验证升级路径。

**[!DNL AEM Guides]内部版本**

>[!NOTE]
>
>联系您的客户成功经理以访问AEM as a Cloud Service的[!DNL AEM Guides]内部版本。

以下列表包含可用于在AMS或内部部署上安装的最新[!DNL AEM Guides]软件包、软件包的下载链接以及其他有用信息。 在安装Experience Manager Guides之前，请确保您的系统符合[技术要求](../install-guide/download-install-technical-requirements.md)。 此外，建议仅使用[!DNL AEM Guides]的最新内部版本。 如果由于某种原因，您需要访问旧版本，请联系您帐户的客户成功经理。

>[!NOTE]
>
> 从Experience Manager Guides的5.0.0版本开始，将不再支持非UUID版本。 如果您使用的是低于AEM 5.0.0版本的非UUID内部版本，请联系您的客户成功经理，以了解从非UUID内部版本迁移到UUID内部版本所需的过程。

| [!DNL AEM Guides]版本 | 发行说明 | 生成下载链接 |
|---|---|---|
| **AEM Guides 5.0.0** | [5.0.0已修复问题](./fixed-issues-5-0-0.md)<br><br>[5.0.0升级说明](./upgrade-instructions-5-0-0.md) | **UUID AEM 6.5** <br> [5.0.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F5-0%2Fcom.adobe.fmdita-6.5-uuid-5.0.0.211.zip) |
| **AEM Guides 4.6.0** | [4.6.0 Service Pack 4已修复问题](./fixed-issues-4-6-0-sp4.md)<br><br>[4.6.0 Service Pack 4升级说明](upgrade-instructions-4-6-0-sp4.md)<br><br>[4.6.0 Service Pack 3已修复问题](./fixed-issues-4-6-0-sp2.md)<br><br>[4.6.0 Service Pack 3升级说明](upgrade-instructions-4-6-0-sp2.md)<br><br>[4.6.0 Service Pack 1升级说明](upgrade-instructions-4-6-0-sp1.md)<br><br>[4.6.0升级说明](./upgrade-instructions-4-6-0.md)<br><br>[4.6.0新增功能](./whats-new-4-6.md)<br><br> [4.6.0已修复问题](./fixed-issues-4-6-0.md) | **非UUID AEM 6.5** <br> [4.6.0 Service Pack 4](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-6-4%2Fcom.adobe.fmdita-6.5-hotfix-4.6.0.4.5.zip)<br> [4.6.0 Service Pack 3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-6-3%2Fcom.adobe.fmdita-6.5-hotfix-4.6.0.3.9.zip)<br>[4.6.0 Service Pack 1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-6-1%2Fcom.adobe.fmdita-6.5-hotfix-4.6.0.1.10.zip) <br> [4.6.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-6%2Fcom.adobe.fmdita-6.5-4.6.0.164.zip) <br> **UUID AEM 6.5** <br> [4.6.0 Service Pack 4](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-6-4%2Fcom.adobe.fmdita.uuid-6.5-hotfix-4.6.0.4.5.zip)<br> [4.6.0 Service Pack 3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-6-3%2Fcom.adobe.fmdita.uuid-6.5-hotfix-4.6.0.3.9.zip)<br>[4.6.0 Service Pack 1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-6-1%2Fcom.adobe.fmdita.uuid-6.5-hotfix-4.6.0.1.10.zip) <br> [4.6.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-6%2Fcom.adobe.fmdita-6.5-uuid-4.6.0.164.zip) |
| **AEM Guides 4.4.0** | [4.4.0升级说明](./upgrade-instructions-4-4.md)<br><br>[4.4.0新增内容](./whats-new-4-4.md)<br><br> [4.4.0已修复问题](./fixed-issues-4-4.md) | **非UUID AEM 6.5** <br> [4.4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-4%2Fcom.adobe.fmdita-6.5-4.4.0.40.zip) <br> **UUID AEM 6.5** <br>[4.4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-4%2Fcom.adobe.fmdita-6.5-uuid-4.4.0.40.zip) |
| **AEM Guides 4.3.0** | [4.3.1.5升级说明](./upgrade-instructions-4-3-1-5.md)<br><br> [4.3.1发行说明](./release-notes-4-3-1.md)<br><br>[4.3.0发行说明](./release-notes-4-3.md) | **非UUID AEM 6.5** <br>[4.3.1.5](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3-1-5%2Fcom.adobe.fmdita-6.5-hotfix-4.3.1.5.1.zip)<br> [4.3.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3-1%2Fcom.adobe.fmdita-6.5-4.3.1.390.zip) <br> [4.3.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3%2Fcom.adobe.fmdita-6.5-4.3.0.347.zip)<br> **UUID AEM 6.5** <br>[4.3.1.5](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3-1-5%2Fcom.adobe.fmdita.uuid-6.5-hotfix-4.3.1.5.1.zip)<br> [4.3.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3-1%2Fcom.adobe.fmdita-6.5-uuid-4.3.1.390.zip)<br>[4.3.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-3%2Fcom.adobe.fmdita-6.5-uuid-4.3.0.347.zip) |
| **AEM Guides 4.2** | [4.2.1发行说明](release-notes-4-2-1.md)<br> <br> [4.2发行说明](./release-notes-4-2.md) | **非UUID**： <br> **AEM 6.5** <br>[4.2.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-2-1%2F4-2-1-non-uuid%2Fcom.adobe.fmdita-6.5-4.2.1.270.zip)<br>[4.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-2%2F4-2-non-uuid%2Fcom.adobe.fmdita-6.5-4.2.229.zip)<br><br> **UUID** <br>**AEM 6.5** <br>[4.2.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-2-1%2F4-2-1-uuid%2Fcom.adobe.fmdita-6.5-uuid-4.2.1.270.zip)<br>[4.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-2%2F4-2-uuid%2Fcom.adobe.fmdita-6.5-uuid-4.2.229.zip)<br> |
| **AEM Guides 4.1** | [4.1.x发行说明](release-notes-4-1.md) | **非UUID**： <br> **AEM 6.5** <br>[4.1.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-3%2F4-1-3-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.1.3.2.zip)<br>[4.1.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-2%2F4-1-2-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.1.2.11.zip)<br>[4.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1%2F4-1-non-uuid%2Fcom.adobe.fmdita-6.5-4.1.159.zip)<br><br> **UUID** <br>**AEM 6.5** <br>[4.1.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-3%2F4-1-3-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.1.3.2.zip)<br>[4.1.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1-2%2F4-1-2-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.1.2.11.zip)<br>[4.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-1%2F4-1-uuid%2Fcom.adobe.fmdita-6.5-uuid-4.1.159.zip) |
| **AEM Guides 4.0** | [4.0.x发行说明](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-4-0.html) | **非UUID**： <br> **AEM 6.5** <br>[4.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-3%2F4-0-2-non-uuid%2Fcom.adobe.fmdita-6.5-hotfix-4.0.3.1.zip)<br>[4.0.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-2%2F4-0-2-non-uuid%2Fcom.adobe.fmdita-6.5-sp-4.0.2.10.zip) <br> [4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/4-0/4-0-non-uuid/com.adobe.fmdita-6.5-4.0.70.zip) <br><br> **UUID** <br>**AEM 6.5** <br>[4.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-3%2F4-0-3-uuid%2Fcom.adobe.fmdita.uuid-6.5-hotfix-4.0.3.1.zip) <br>[4.0.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faemdox%2F4-0-2%2F4-0-2-uuid%2Fcom.adobe.fmdita.uuid-6.5-sp-4.0.2.10.zip)<br> [4.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/4-0/4-0-uuid/com.adobe.fmdita-6.5-uuid-4.0.70.zip) |
| **AEM Guides 3.8.5** <br> 3.8.5是3.8之上的SP版本。由于3.8.5 SP包含关键修复，因此不能单独安装<br>3.8发行版。 <br>客户必须先安装3.8，然后再安装SP 3.8.5。 | [3.8.x发行说明](https://helpx.adobe.com/xml-documentation-for-experience-manager/release-note/release-notes-xml-documentation-solution-3-8.html) | **非UUID**： <br> **AEM 6.5** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.5-hotfix-3.8.5.2.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.5-3.8.166.zip)<br> **AEM 6.4** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.4-hotfix-3.8.5.1.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.4-3.8.166.zip) <br> **AEM 6.3** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5/com.adobe.fmdita-6.3-hotfix-3.8.5.1.zip) <br>[3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8/com.adobe.fmdita-6.3-3.8.166.zip) <br><br> **UUID** <br>**AEM 6.5** <br> [3.8.5 SP](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8-5uuid/com.adobe.fmdita.uuid-6.5-hotfix-3.8.5.2.zip) <br> [3.8](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/3-8uuid/com.adobe.fmdita.uuid-6.5-3.8.168.zip) |
