---
title: 为Adobe Experience Manager Guides设置MCP
description: 了解如何将AI助手连接到Experience Manager Guides MCP服务器，以便进行Cloud Service和内部部署
meta-feature: Authoring
meta-product: Experience Manager, Experience Manager Guides
meta-role: User
meta-type: Documentation
source-git-commit: 6841c373b75770e8691a2cac4d56aeb368b09480
workflow-type: tm+mt
source-wordcount: '1557'
ht-degree: 1%
---

# 设置Experience Manager Guides MCP服务器

本文介绍了有关连接到Experience Manager Guides MCP服务器的特定于环境的详细信息。 根据您的Experience Manager Guides实例是运行as a Cloud Service还是内部部署，安装程序会有所不同。 选择与您的环境匹配的选项卡。

>[!BEGINTABS]

>[!TAB Cloud Service]

## MCP服务器端点

Experience Manager Guides通过单个HTTP端点公开其MCP功能。

| MCP服务器 | 端点 | 描述 |
|---|---|---|
| **Experience Manager Guides** | `https://mcp.adobeaemcloud.com/adobe/mcp/guides` | 在Experience Manager Guides中使用主题和地图、[新基线](../user-guide/web-editor-baseline-v2.md)以及报告。 |

要了解环境的当前工具列表，请询问您的助手：

```
List all Experience Manager Guides tools available from the author https://author-pXXXX-eXXXX.adobeaemcloud.com and describe what they do.
```

## 为您的组织请求访问权限

对Experience Manager Guides MCP服务器的访问是每个组织&#x200B;**选择加入**。 在您组织中的任何人都可以连接之前：

- 必须在AEM as a Cloud Service环境中启用Experience Manager Guides。
- 贵组织的IMS组织ID （组织ID）必须由Adobe Guides团队列入允许列表。

要请求获取访问权限，请联系您的Adobe客户成功团队。

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

>[!TAB 内部部署]

您可以使用模型上下文协议(MCP)将受支持的AI客户端连接到Experience Manager Guides本地实例。 建立连接后，客户端可以访问您的AEM用户帐户可用的Experience Manager Guides操作。

使用&#x200B;**您的AEM标识和权限**&#x200B;执行所有操作。 连接的客户端只能查看或修改您的AEM帐户有权访问的内容和资源。

身份验证使用带有Proof Key for Code Exchange (PKCE)的OAuth 2.0授权代码流。 首次连接客户端时，您可以使用AEM进行身份验证。 成功验证后，连接会自动刷新访问令牌。

您可以连接以下客户端：

| 客户端 | 连接方法 | AEM实例要求 |
| ------------------ | ----------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **克劳德桌面** | 桌面扩展(`.mcpb`) | 支持HTTP和HTTPS端点，包括可从公司网络访问的内部主机。 |
| **ChatGPT（Web和桌面）** | 自定义连接器 | 需要具有有效、公开受信任的TLS证书的公开可访问HTTPS端点。 |
| **游标** | `~/.cursor/mcp.json`中的MCP配置 | 支持HTTP和HTTPS端点，包括可从公司网络访问的内部主机。 |

## 先决条件

在连接客户端之前，请与AEM管理员合作以验证以下配置：

1. **验证是否已部署MCP功能。**：确保已部署MCP功能并在Experience Manager Guides实例上运行。

2. **配置Granite基本URL。**：在AEM Web控制台配置管理器(`/system/console/configMgr`)中，找到&#x200B;**Experience Manager Guides OAuth PKCE令牌包装器**&#x200B;配置，并验证是否已配置Granite基本URL。 如果Granite基本URL配置不正确，则客户端无法建立连接。

3. **配置Day CQ链接外部化器。**：在AEM Web控制台配置管理器中，找到&#x200B;**Day CQ链接外部化器**&#x200B;配置，并验证外部创作URL是否指向正确的AEM创作实例。 在OAuth发现期间使用外部作者URL。 URL不正确可能会阻止客户端完成连接。

   有关更多详细信息，请查看[配置AEM Guides内部部署的MCP连接设置](./configure-aem-guides-mcp-on-prem.md)

4. **获取MCP服务器URL。**： MCP服务器URL使用以下格式：

   ```
   http(s)://<AEM-HOST>/bin/guides/v1/mcp/sse
   ```

   >[!NOTE]
   >
   > 配置客户端时使用完整的SSE端点。 请勿在URL中添加结尾斜杠。

   例如：

   **内部AEM创作实例：**

   ```
   http://10.42.42.20:4502/bin/guides/v1/mcp/sse
   ```

   **公共AEM创作实例：**

   ```
   https://author.example.com/bin/guides/v1/mcp/sse
   ```



5. **验证您的AEM凭据和权限。**：您必须拥有有效的AEM实例帐户。 使用您用于登录到AEM用户界面的相同凭据。 通过MCP可用的操作取决于分配给此帐户的权限。

## 连接克劳德桌面

Claude Desktop支持桌面扩展(`.mcpb`)。 Experience Manager Guides MCP扩展将打包连接配置，因此您无需手动编辑MCP JSON配置。

1. 获取[`aem-guides-mcp.mcpb`](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/aemdox/other-packages/guides-mcp/aem-guides-mcp.zip)扩展文件。

2. 打开&#x200B;**Claude Desktop**&#x200B;并导航到&#x200B;**设置>扩展**。

3. 通过双击文件或将其拖到“扩展”窗口中来安装`aem-guides-mcp.mcpb`。

   在“安装”对话框中显示&#x200B;**Adobe Experience Manager Guides MCP**。

4. 选择&#x200B;**安装**。

5. 在&#x200B;**Experience Manager Guides MCP服务器URL**&#x200B;字段中，输入AEM实例的完整SSE端点。

   例如：

   ```
   http://<AEM-HOST>:4502/bin/guides/v1/mcp/sse
   ```

6. 选择&#x200B;**保存**&#x200B;并确保该扩展已启用。

## 连接ChatGPT

您可以在ChatGPT中将Experience Manager Guides MCP服务器配置为自定义连接器。

>[!IMPORTANT]
>
> ChatGPT要求MCP服务器可通过具有有效、公开受信任的TLS证书&#x200B;**的**&#x200B;可公开访问的HTTPS端点使用。
>
> 不支持HTTP端点、`localhost`、私有IP地址和自签名证书。 AEM实例必须通过HTTPS主机公开，例如负载平衡器、反向代理或配置了TLS的Dispatcher。
>
> 在&#x200B;**Day CQ Link Externalizer**&#x200B;中配置的外部作者URL还必须指向公共HTTPS地址。 否则，OAuth发现元数据可能会通告不正确的身份验证端点并阻止登录。

1. 验证您的MCP服务器在公共HTTPS URL上是否可用，格式如下：

   ```
   https://<PUBLIC-AEM-HOST>/bin/guides/v1/mcp/sse
   ```

   在浏览器中打开端点，并验证您是否可以在没有证书警告或连接错误的情况下访问主机。

2. 在ChatGPT中，打开&#x200B;**设置>插件**。

   >[!NOTE]
   >
   > 连接器的可用性取决于您的ChatGPT计划和工作区配置。 工作区管理员可能需要启用自定义连接器或开发人员连接器。

3. 选择选项以添加或创建插件。

4. 指定连接器详细信息：

   * **名称：**&#x200B;输入`Experience Manager Guides`或其他描述性名称。
   * **MCP服务器URL：**&#x200B;输入公共HTTPS SSE终结点。
   * **身份验证：**&#x200B;选择&#x200B;**OAuth**。

   您无需提供OAuth客户端ID或客户端密钥。 MCP服务器支持自动客户端注册。

5. 创建连接器。

## 连接光标

通过将服务器详细信息添加到MCP配置，在光标中配置Experience Manager Guides MCP服务器。

1. 在光标中，导航到&#x200B;**自定义> MCP > New**。

   光标打开`~/.cursor/mcp.json`配置文件。

2. 添加Experience Manager Guides MCP服务器配置。

   例如：

   ```json
   {
     "mcpServers": {
       "aem-guides": {
         "url": "http://10.42.34.176:4502/bin/guides/v1/mcp/sse",
         "type": "http"
       }
     }
   }
   ```

3. 将示例URL替换为AEM实例的MCP SSE端点。

4. 保存配置。

5. 启用配置的MCP服务器。

>[!ENDTABS]

## 身份验证和使用Experience Manager Guides

在客户端中配置MCP连接后，使用您的AEM帐户进行身份验证。

1. 从您的客户端启动身份验证过程。

   * **Claude Desktop：**&#x200B;当Claude首次尝试使用Experience Manager Guides连接时，身份验证流程将开始。
   * **ChatGPT：**&#x200B;身份验证在您创建和连接Experience Manager Guides连接器后开始。
   * **游标：**&#x200B;启用配置的MCP服务器并选择&#x200B;**身份验证**。

2. 当AEM登录页面在浏览器中打开时，请使用您的AEM凭据登录。

3. 在出现提示时批准访问请求。

4. 身份验证完成后，返回到您的客户端。

您现在可以使用帐户中可用的Experience Manager Guides操作。 例如，尝试以下提示：

```
List the available Experience Manager Guides operations.
```

```
Get the topic list for my map in Experience Manager Guides.
```

```
Show me the broken-link report for my map.
```

>[!NOTE]
>
> 通过MCP可用的操作和内容由用于身份验证的AEM帐户的权限决定。 MCP连接不提供额外的AEM权限。

成功验证后，客户端会自动刷新身份验证令牌。 除非会话过期或访问权限被撤销，否则您通常不需要再次登录。

## 连接问题疑难解答

使用以下信息解决常见连接和身份验证问题。

| 客户端 | 问题 | 可能的原因和解决方法 |
| -------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 克劳德桌面 | 无法安装或禁用该扩展。 | 您的Claude Desktop版本可能不支持该扩展。 请更新Claude Desktop，然后重试。 |
| 克劳德桌面 | 浏览器未打开进行身份验证，或者连接未完成。 | 验证MCP服务器URL。 它必须以`/bin/guides/v1/mcp/sse`结尾，并且不应包含尾随斜杠。 此外，请验证是否可以从您的计算机访问AEM实例。 |
| ChatGPT | ChatGPT无法访问MCP服务器或不允许您添加连接器。 | 验证端点是否可通过HTTPS公开访问。 不支持HTTP端点、`localhost`、专用IP地址和专用网络端点。 |
| ChatGPT | 显示证书或安全错误。 | 验证服务器是否使用由公开受信任的证书颁发机构颁发的有效未过期证书。 不支持自签名证书。 |
| ChatGPT | 身份验证重定向到不正确的主机，或在发现过程中失败。 | 验证&#x200B;**Day CQ Link Externalizer**&#x200B;中的外部作者URL是否指向公共HTTPS AEM作者地址。 |
| 所有客户端 | 身份验证期间注册失败。 | 向您的AEM管理员验证服务器端OAuth注册配置。 |
| 所有客户端 | 身份验证失败或未完成。 | 验证Granite基本URL、Day CQ Link Externalizer配置、MCP服务器URL以及与AEM实例的连接。 |
| 所有客户端 | 连接成功，但Experience Manager Guides操作或结果不可用。 | 确认经过身份验证的AEM帐户具有所需的Experience Manager Guides权限，并且请求的操作对该帐户可用。 |
| 所有客户端 | 客户端在连接之前工作后请求身份验证。 | 身份验证会话可能已过期或访问权限可能已撤销。 再次使用AEM进行身份验证。 |



