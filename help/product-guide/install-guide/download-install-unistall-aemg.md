---
title: 卸载AEM Guides
description: 了解如何卸载AEM Guides
exl-id: 6c6b9692-cdec-426f-bc3b-f09d0091da39
feature: Installation
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/W6cpFBqAnriNXNYqP6r-GZm7tJhPWnlSI53q33iduvE
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 0%

---

# 卸载AEM Guides {#id21BHG0C0SXA}

您可以使用AEM Guides包管理器卸载CRX。 在卸载过程中，存储库的内容将恢复到紧接着软件包安装之前创建的快照。

执行以下步骤卸载AEM Guides：

1. 登录AEM实例并导航到CRX包管理器。 访问包管理器的默认URL为：

   ```http
   http://<server name>:<port>/crx/packmgr/index.jsp
   ```

1. 搜索com.adobe.fmdita包。
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

**父主题：**&#x200B;[&#x200B;下载并安装](download-install.md)
