---
title: 技术要求
description: 了解使用Adobe Experience Manager Guides的技术要求
feature: Introduction, Installation
role: Admin
level: Experienced
exl-id: 7e0894ef-f1d4-47a8-9bb8-fe63e3968260
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
  - id: c5fd2af0-6cbb-4746-ab0d-40ecb093af12
    internal-label: Introduction
  - id: e557051c-ff02-4ff8-9421-cf452af0edd5
    internal-label: Installation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%
---
# 技术要求 {#id213BCG003XA}

AEM Guides可通过Adobe软件分发门户获取。 您可以从Adobe软件分发门户帐户下载AEM Guides，并将其安装到安装程序中的所有Adobe Experience Manager (AEM)实例上。 通常，您的AEM创作实例和生产实例将托管在不同服务器上。 您必须在要使用的所有AEM实例上安装AEM Guides。

在安装Adobe Experience Manager Guides for On-Premise之前，请确保您的系统满足下面提及的给定版本的技术要求。

**支持的浏览器**

- Google Chrome


>[!NOTE]
>
> 了解有关[Experience Manager Guides版本的更多信息并下载内部版本](../release-info/latest-release-info.md)。


| [!DNL AEM Guides]版本 | 技术规范 |
|---|---|
| **AEM Guides 5.2.0** | **UUID 5.2.0** <ul><li> AEM 6.5 LTS SP2<br><ul><li>Java：17或21</li></ul> <li> AEM 6.5 SP24、SP23或SP22 <br> <ul><li>Java：11或8 </li></ul> <li>操作系统：<ul><li>Microsoft Windows Server 2012 R2 <br> <li>Red Hat Linux 7和6</ul> |
| **AEM Guides 5.1.0** | **UUID 5.1.0** <ul><li> AEM 6.5 LTS SP1<br><ul><li>Java：17或21</li></ul> <li> AEM 6.5 SP23、SP22或SP21 <br> <ul><li>Java：11或8 </li></ul> <li>操作系统：<ul><li>Microsoft Windows Server 2012 R2 <br> <li>Red Hat Linux 7和6</ul> |
| **AEM Guides 5.0.0** | **UUID 5.0.0** <ul><li> AEM 6.5 SP 22、SP21或SP20<br> <li>   Java： 11或8 <br><li>操作系统： <ul><li>Microsoft Windows Server 2012 R2 <br> <li>Red Hat Linux 7和6</ul> |
| **AEM Guides 4.6.0** | **非UUID和UUID 4.6.0** <ul><li> AEM 6.5 SP 21、SP20或SP19<br> <li>   Java： 11或8 <br><li>操作系统： <ul><li>Microsoft Windows Server 2012 R2 <br> <li>Red Hat Linux 7和6</ul> |
| **AEM Guides 4.4.0** | **非UUID和UUID 4.4.0** <ul><li> AEM 6.5 SP20、SP19、SP18或SP17 <br> <li> Java： 11或8 <br><li>操作系统： <ul><li> Windows Server 2012 R2 <br> <li>Red Hat Linux 7和6</ul> |
| **AEM Guides 4.2** | **非UUID和UUID 4.2.1**<br><ul> <li>AEM 6.5 SP15、SP14、SP13或SP12 <br><li>Java： 11或8 <br><li> 操作系统： <ul><li>Windows Server 2012 R2  <li>Red Hat Linux 7和6</ul></ul>**非UUID和UUID 4.2**<br><ul> <li>AEM 6.5 SP15、SP14、SP13或SP12 <br><li>Java： 11或8<br><li> 操作系统： <ul><li>Windows Server 2012 R2 <br> <li>Red Hat Linux 7和6</ul> |
| **AEM Guides 4.1** | **非UUID和UUID 4.1.2**<br><ul><li>AEM 6.5 SP13、SP12、SP11或SP10 <br><li>Java： 11或8<br><li>操作系统： <ul><li>Windows Server 2012 R2 <br><li> Red Hat Linux 7和6 </ul></ul> **非UUID和UUID 4.1**<br><ul> <li>AEM 6.5 SP13、SP12、SP11或SP10 <br><li>Java：11或8<li>操作系统： <ul><li>Windows Server 2012 R2 <br> <li> Red Hat Linux 7和6 |
| **AEM Guides 4.0** | **非UUID和UUID 4.0.3**<br><ul><li> AEM 6.5 SP12、SP11、SP10或SP9 <br><li>Java： 11或8 <br><li>操作系统：<ul><li>Windows Server 2012 R2 <br> <li>Red Hat Linux 7和6<br></ul></ul>**非UUID和UUID 4.0.2** <br><ul><li> AEM 6.5 SP12、SP11、SP10或SP9 <br><li>Java： 11或8 <br><li>操作系统： <ul><li>Windows Server 2012 R2 <br> <li>Red Hat Linux 7和6<br> </ul></ul>**非UUID和UUID 4.0**<br><ul><li>AEM 6.5 SP11、SP10或SP9 <br><li>Java： 11或8<br><li> 操作系统： <ul><li>Windows Server 2012 R2 <br> <li> Red Hat Linux 7和6 |
| **AEM Guides 3.8.5** <br>3.8.5是3.8之上的SP版本。 不能单独安装<br> 3.8版本<br>，因为3.8.5 SP包含<br>关键修复。<br> 客户必须先安装3.8 <br>，然后再安装SP 3.8.5。 | **非UUID** <br> <ul><li>AEM 6.5 SP9或SP8 <br> AEM 6.4 SP8 <br> AEM 6.3 SP3 <br><li>操作系统： <ul><li>Windows Server 2012 R2 <br> <li> Red Hat Linux 7和6</ul>**UUID** <br><li> AEM 6.5 SP9或SP8 <br><li> 操作系统： <ul><li>Windows Server 2012 R2 <br> <li>Red Hat Linux 7和6 |
