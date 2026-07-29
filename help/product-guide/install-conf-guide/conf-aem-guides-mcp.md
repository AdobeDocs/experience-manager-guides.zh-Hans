---
title: 将MCP与Adobe Experience Manager Guides结合使用
description: 了解如何将模型上下文协议(MCP)与AEM Guides结合使用，以通过AI助手使用主题、地图、基线和报告
feature: Authoring, Publishing
role: User
source-git-commit: c724946a3426e28a1270ba01cdf2646bbf5f2a0d
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 0%

---


# 使用Adobe Experience Manager Guides MCP服务器

模型上下文协议(MCP)是AI助手连接到外部工具和数据的标准方法，而不是您切换上下文以自己操作这些工具。

Adobe Experience Manager Guides MCP服务器将此功能引入Experience Manager Guides。 它允许启用了MCP的AI助手（如Anthropic Claude）连接到您的Experience Manager Guides环境，并在您自己的AEM权限下代表您执行操作。 连接后，您可以使用纯自然语言在Experience Manager Guides as a Cloud Service中处理地图、主题、基线和报表。

本文说明了MCP对Experience Manager Guides有用的原因、MCP服务器涵盖的内容、它使用的应用程序、如何设置以及如何使用它。

## Experience Manager Guides的MCP为何有用

文档团队经常将大量时间花费在重复、导航繁重的任务上，例如在大地图中查找主题、检查文档状态、跟踪断开的链接、为版本创建基线或导出报表。 使用Experience Manager Guides MCP服务器，您可以要求AI助手直接处理这些内容，而无需切换到Experience Manager Guides UI。

例如：

- 请助理列出主题及其状态，而不是打开地图并逐一检查每个主题的状态。
- 要求助手运行报表并告知您报表创建时间，而不是手动启动断开链接报表并等待Experience Manager Guides UI。
- 要求助理为特定映射创建基线，而不是导航到基线屏幕。

## Experience Manager Guides提供的MCP服务器

Experience Manager Guides通过单个HTTP端点公开其MCP功能。

| MCP服务器 | 端点 | 描述 |
| --- | --- | --- |
| **Experience Manager Guides** | `https://mcp.adobeaemcloud.com/adobe/mcp/guides` | 在Experience Manager Guides中使用主题和地图、基线和报表。 |

此一个端点涵盖四个区域：

- **主题和映射** — 创建、读取、更新、删除、版本和锁定主题和映射。
- **基线** — 创建、列出、导出、复制、重建和标签基线。
- **报告** — 主题列表、元数据、断开的链接和多媒体使用。
- **系统** — 包版本、包运行状况和环境诊断。

确切的可用工具可能会随着时间的推移而改变。 请让您的助理向您显示可用内容，而不是依赖固定列表：

```
List all Experience Manager Guides tools available from the author https://author-pXXXX-eXXXX.adobeaemcloud.com and describe what they do.
```

## 为您的组织请求访问权限

对Experience Manager Guides MCP服务器的访问是每个组织&#x200B;**选择加入**。 在您组织中的任何人都可以连接之前：

- 必须在AEM as a Cloud Service环境中启用Experience Manager Guides。
- 贵组织的IMS组织ID （组织ID）必须由Adobe Guides团队列入允许列表。

要请求获取访问权限，请联系您的Adobe客户成功团队。

## 支持的应用程序

Experience Manager Guides MCP服务器是&#x200B;**远程**&#x200B;服务器。 它可与任何支持远程服务器的MCP客户端配合使用，包括：

### 聊天应用程序

- Anthropic Claude（Web和桌面）

### 开发人员工具

- 光标
- Visual Studio代码
- 其他支持MCP的IDE

## 设置

您不会在本机安装任何内容。 您将客户端指向服务器URL，并通过Adobe IMS登录流进行身份验证。

### 克洛德

遵循官方演练：[为AEM MCP设置Claude](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/ai-in-aem/mcp-support/chat-applications/setup-claude)。 添加自定义连接器时，请使用Experience Manager Guides端点：

```
https://mcp.adobeaemcloud.com/adobe/mcp/guides
```

### 光标/Visual Studio代码

将服务器添加到MCP配置。 对于游标，将其添加到`.cursor/mcp.json`：

```json
{
  "mcpServers": {
    "aem-guides": {
      "url": "https://mcp.adobeaemcloud.com/adobe/mcp/guides"
    }
  }
}
```

对于仅支持本地(stdio)服务器的客户端，使用[`mcp-remote`](https://www.npmjs.com/package/mcp-remote)桥接到远程终结点：

```json
{
  "mcpServers": {
    "aem-guides": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.adobeaemcloud.com/adobe/mcp/guides"]
    }
  }
}
```

## 身份验证

Experience Manager Guides MCP服务器使用&#x200B;**Adobe IMS**&#x200B;进行身份验证。

- 首次连接时，您的客户端会打开一个浏览器登录窗口。 使用您的Adobe ID登录以完成连接。
- 登录后，每个操作都将在您现有的AEM权限下运行。 如果您没有权限使用AEM中的操作，则相同的操作将通过MCP失败。

## 使用Experience Manager Guides MCP服务器

连接后，以简单的语言描述您想要的内容。 该助理选择适当的刀具并填充其参数，如映射路径或基线名称。

>[!IMPORTANT]
>
>涉及多个步骤或需要一段时间才能完成的请求（例如导出、基线构建和批量更新）最适合用于思维模型。 这些命令在后台运行：助手将启动作业，然后检查其状态，直到结果或下载链接准备就绪为止。

### 示例提示

以下提示说明了典型请求，每个请求都会触发不同的工具：

1. **检查地图中的主题状态**

   > 在`/content/dam/docs/user-guide.ditamap`处列出地图中的所有主题，并显示其标题和文档状态。

1. **创建基线**

   > 创建标题为“版本3.2”的`/content/dam/docs/user-guide.ditamap`的静态基线。

1. **运行报告**

   > 运行用户指南的断开链接报表，并在准备就绪后提供下载链接。

## 期望管理

- **验证结果** — 助理可能会出错，如选择错误的地图或主题。 在使用报告或新基线之前对其进行复查。
- **随着时间的推移它会逐渐改善** — 随着助理变得越来越好，今天需要一些提示的任务稍后可能需要一个提示。
- **您仍然进行呼叫** — 助理可以告知您主题的状态或列表断开的链接，但决定内容是否准备好发布仍由审阅者或发布者决定。
- **请小心自动批准** — 某些MCP客户端（包括Claude）允许您自动批准操作而不是确认每个操作。 对于只读操作（如运行报告），这是可以接受的。 对于创建、更改或锁定内容的操作，请确认每个操作，以便在内容生效之前对其进行查看。

有关Experience Manager Guides MCP的问题，请联系您的Adobe客户成功团队。


