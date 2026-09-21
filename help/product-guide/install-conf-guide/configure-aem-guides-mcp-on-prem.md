---
title: 为AEM Guides内部部署配置MCP连接设置
description: 了解如何为AEM Guides内部部署配置MCP连接设置。
meta-feature: Authoring
meta-product: Experience Manager, Experience Manager Guides
meta-role: Admin
meta-type: Documentation
source-git-commit: e234425f1e277990de25057971f3e2453c93360f
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 3%
---

# 为Experience Manager Guides（内部部署）配置MCP连接设置

Claude、Cursor和Codex等AI工具可以使用模型上下文协议(MCP)连接到Experience Manager Guides。 您可以在Adobe Experience Manager Web控制台的“配置”页中配置MCP连接和身份验证设置。

可用配置可控制令牌处理、不含反向链接信息的请求以及AEM创作实例的外部URL。

## 配置登录令牌处理

要配置登录令牌处理，请执行以下步骤：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```
   http://<server name>:<port>/system/console/configMgr
   ```

2. 搜索并选择&#x200B;**AEM Guides OAuth PKCE令牌包装器**。

3. 配置以下属性：

   | 属性 | 默认 | 描述 |
   |---|---|---|
   | Granite基本URL | `http://localhost:4502` | 指定AEM在身份验证期间用于与创作实例通信的URL。 仅当创作实例使用其他端口时，才更改默认端口4502。 |
   | Granite超时（毫秒） | `5000` | 指定等待身份验证请求完成的最长时间（以毫秒为单位）。 |

4. 选择&#x200B;**保存**。

## 配置没有反向链接信息的请求

>[!NOTE]
>
> 仅当使用“光标”时，才需要配置此设置。

某些MCP客户端（包括Cursor）可能会发送没有反向链接信息的请求。 要允许这些请求，请按照以下方式配置Apache Sling反向链接过滤器：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```
   http://<server name>:<port>/system/console/configMgr
   ```

2. 搜索并选择&#x200B;**Apache Sling引用过滤器**。

3. 在&#x200B;**允许为空**&#x200B;属性中，将该值设置为`true`。

   此设置允许在身份验证期间不包含反向链接信息的请求。

4. 选择&#x200B;**保存**。

## 为创作实例配置外部URL

**Day CQ Link Externalizer**&#x200B;服务允许您集中定义用于为资源路径添加前缀的外部URL，包括AEM创作实例的URL。

要配置外部URL，请执行以下步骤：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```
   http://<server name>:<port>/system/console/configMgr
   ```

2. 搜索并选择&#x200B;**Day CQ Link Externalizer**。

3. 在&#x200B;**域**&#x200B;下，使用以下格式添加或更新`author`映射：

   ```
   author [scheme://]server[:port][/contextpath]
   ```

   例如：

   ```
   author https://author.mycompany.com
   ```

4. 选择&#x200B;**保存**。