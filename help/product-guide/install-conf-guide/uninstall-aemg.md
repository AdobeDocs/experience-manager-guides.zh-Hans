---
title: 卸载AEM Guides
description: 了解如何卸载AEM Guides
feature: Installation
role: Admin
level: Experienced
exl-id: 84b248da-af7b-4811-a184-4ab17838faaa
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
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
source-wordcount: '151'
ht-degree: 0%
---
# 卸载适用于内部部署的AEM Guides{#id21BHG0C0SXA}

您可以使用AEM Guides包管理器卸载CRX for On-Premise。 在卸载过程中，存储库的内容将恢复到紧接着软件包安装之前创建的快照。

执行以下步骤可卸载AEM Guides for On-Premise：

1. 登录AEM实例并导航到CRX包管理器。 访问包管理器的默认URL为：

   ```http
   http://<server name>:<port>/crx/packmgr/index.jsp
   ```

1. 搜索`com.adobe.fmdita`包。
1. 单击包以将其展开。
1. 单击&#x200B;**更多**&#x200B;以打开下拉菜单。
1. 单击&#x200B;**卸载**，然后等待卸载完成。
1. 如果不再需要此包，请在卸载包后单击&#x200B;**删除**。

## 卸载后

要在卸载后清除剩余文件，请执行以下步骤：

1. 使用以下方式清除脚本缓存：

   ```http
   http://<host>:<port>/system/console/scriptcache
   ```

1. 您可以使用以下代码使缓存失效：

   ```http
   http://<host>:<port>/libs/granite/ui/content/dumplibs.rebuild.html?back=true
   ```

1. 单击&#x200B;**使缓存失效**。
1. 清理浏览器的缓存。
