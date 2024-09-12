---
title: 为数据源配置自定义连接器
description: 了解如何为数据源配置自定义连接器。
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: fdd19363c6768860ffa2f70c934b6f71c811c08b
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 0%

---

# 配置自定义数据源连接器

Experience Manager Guides允许您根据自己的要求自定义连接器，然后将它们用于不同的数据源。 要自定义连接器，您需要实施连接器接口及其重要功能，然后配置接口。 您还可以随自定义连接器一起提供资源。


- [自定义Experience Manager Guides的连接器](#customize-connector)
- [实施连接器接口](#implement-interface)
- [重要函数](#important-functions)
- [默认连接器实施的类型](#default-connectors)
   - [配置界面](#config-interface)
   - [默认配置实施的类型](#default-config-types)
   - [具体配置实施](#concrete-config-implementation)
   - [其他资源](#resources)



## 自定义Experience Manager Guides的连接器 {#customize-connector}

可以使用预定义的接口和抽象类为数据源定制或配置连接器。 整个源代码位于[https://github.com/adobe/guides-data-source-connectors/tree/main/konnect-definitions](https://github.com/adobe/guides-data-source-connectors/tree/main/konnect-definitions)。


有关konnect定义，请参阅[![javadoc](https://javadoc.io/badge2/com.adobe.aem.addon.guides/konnect-definitions/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem.addon.guides/konnect-definitions)。

## 实施连接器接口 {#implement-interface}

执行以下步骤，根据您的要求实施接口及其功能：

1. 为连接器定义与系统集成的标准化方式，以允许执行查询、验证连接和检索元数据。
1. 通过提供用于配置模板、徽标、查询和其他设置的默认方法来促进UI集成。
1. 请确保连接器已正确验证，并且在与数据源交互时可以处理错误(`KonnectException`)。

该界面充当实施各种类型Data Connectors的蓝图，确保连接器满足大型软件生态系统内的任何特定集成和操作要求。

## 重要函数 {#important-functions}

实施以下重要功能：

| 方法 | 必填 | 描述 |
|---|---|---|
| getLogoUrl |  | <ul><li> 此方法将返回用作连接器徽标的URL。 <li> 默认情况下，它会返回一个空字符串，指示除非覆盖否则不提供任何徽标URL。 <br><b>其他注释</b>： <br> <ul><li> 如果您同时提供徽标URL和徽标类名称，则徽标URL用于在用户界面中显示徽标。 <li> 如果通过配置设置指定徽标URL，它将覆盖方法实施中设置的URL。 |
| validateConnection | 是 | <ul><li> 使用此方法验证连接器是否可以建立与其数据源的连接。 <li> 它将`ConfigDto`对象作为参数，其中包含配置设置，如连接凭据和端点URL。 <li> 如果验证（连接测试）成功，则方法返回true，指示连接器可以连接到其数据源。 |
| 执行 | 是 | <ul><li>使用此方法执行与数据源交互的单一连接器查询。 <li> 支持此操作的连接器可处理查询执行、解析响应并根据需要将其转换为JSON字符串。 <li> 在`QueryInfoDto`对象中封装要在此方法中执行的查询，该对象包含查询字符串和参数等详细信息。 <li> 方法会返回一个JSON字符串，以表示执行查询所产生的响应。 <br><b>其他注释</b>： <li>此方法的实施因特定连接器及其与数据源的交互而异。 <li> 使用`KonnectException`处理在执行或连接到数据源期间发生的任何异常或错误。 |
| executeWithLimit | 是 | <ul><li> 使用此方法的目的与`execute()`相同，但具有应用限制查询的附加功能，通常用于显示UI组件中的预览。 <li> 支持此操作的连接器可处理查询执行、解析响应并在必要时将其转换为JSON字符串。 <li> 在`QueryInfoDto`对象中封装要在此方法中执行的查询，与上一个方法类似。 <br><b>其他注释</b>： <ul><li> `QueryResultDto`是封装查询执行结果的自定义类或数据传输对象，包括有关查询及其执行状态的元数据。 |
| getsamplequery | | <ul><li>此方法返回一个示例查询字符串，该字符串可以显示在UI中，例如，用户可以在其中插入或编辑查询的对话框中。 <li>默认情况下，它返回一个空字符串，指示除非覆盖否则不提供示例查询。 <br><b>其他注释</b>： <ul> <li> 如果未定义示例查询，并且方法返回空字符串，则在UI插入查询对话框中不会显示任何示例查询。 |
| getTemplates | | <ul> <li> 此方法会返回与连接器关联的模板列表。 <li> 默认情况下，它返回一个空列表，指示除非覆盖否则不提供任何模板。 |
| getLogoClassName | | <ul> <li> 此方法将类名作为连接器的徽标返回。 默认情况下，它返回一个空字符串，指示除非覆盖否则不提供徽标类名称。 <br><b>其他注释</b>： <ul><li> 如果您同时提供徽标URL和徽标类名称，则徽标URL用于在用户界面中显示徽标。 <li> 如果通过配置设置指定徽标类名，它将覆盖方法实现中设置的类名。 |
| 已启用 | 是 | <ul><li> 此方法检查是否已启用`connector`。 <li> 默认情况下，该方法返回false，这意味着除非实现此方法的类覆盖该连接器，否则不会启用该连接器。 |
| getDescription | | <ul><li>使用此方法可返回可在UI中显示的描述字符串。 <li> 默认情况下，它返回一个空字符串，指示除非覆盖否则不提供任何描述。 |
| getAuthor | | <ul><li> 此方法提供一种检索创建或负责连接器的作者的名称的方法。 <li> 它通常有助于识别并确认系统或框架中的连接器创建者或维护者。 |
| getName | 是 | <ul><li>此方法提供了一种检索分配给连接器的唯一名称的方法。 <li>返回的名称对于在用户界面(UI)上下文中标识连接器至关重要，尤其是在连接器的配置设置未明确指定名称的情况下。 <li>此名称用于各种UI组件中，以用户友好的方式显示或管理连接器。 |
| getGroup | 是 | <ul> <li>此方法提供了一种检索与连接器关联的组名称的方法。 <li>组名称通常用于根据连接器的功能、用途或类型将连接器组织或分类为逻辑组。 <li> 这允许在配置UI中更轻松地管理和显示连接器。 |
| getDefaultTemplatePath |  | <ul><li> 此方法返回与此连接器关联的模板的默认路径。 <li> 默认情况下，它返回一个空字符串，指示除非覆盖否则不设置默认路径。 |
| getlogesvg |  | <ul><li>使用此方法可返回连接器徽标的SVG表示形式。 <li> 默认情况下，它返回一个空字符串，指示除非覆盖，否则不提供任何的SVG数据。 |
| getMaxNoRowsForPreviewQuery | | <ul><li>此方法返回在UI预览中查询或显示的最大行数。 <li> 缺省情况下，它会返回DEFAULT_LIMIT_PREVIEW值，该常量表示预览行的缺省限制。 |
| getConfigClass | 是 | <ul><li>此方法提供有关实现Config接口并受此连接器支持的类的信息。 <li> 它允许应用程序或框架动态发现和使用与连接器兼容的配置。 |

## 默认连接器实施的类型 {#default-connectors}

*konnect-definitions*&#x200B;库提供了抽象连接器实现并具有预定义函数以运行查询。 这些连接器实施充当模板，可以直接扩展并按原样使用。 如果需要自定义实施，则可以覆盖其函数。

除了实现默认连接器外，您还可以实现以下默认抽象类之一：

- Rest连接器
- 文件连接器
- GraphQL连接器
- SQL连接器
- NoSQL连接器


如果连接器适合这些类型之一，请将连接器扩展到相应的基类。 否则，通过实施连接器接口从头开始创建。

## 配置界面 {#config-interface}

`Config`接口设计用于使用特定的身份验证方法配置数据源，从而让您精确控制创建连接的方式。

`Config`接口在如何处理和实施身份验证详细信息方面提供了灵活性。 不同的实施可以提供多种验证数据源的方式。 连接器使用配置实例对数据源执行和验证查询，从而形成完整的工作流。
连接器使用`Config`实例对数据源执行和验证查询，从而形成完整的工作流。

配置实施定义如何处理身份验证以连接到数据源。 然后，连接器实施使用此配置与数据源交互，确保正确执行和验证查询。

总体而言，`Config`接口是连接到数据源的工作流的重要组成部分，尤其侧重于身份验证配置。

### 默认配置实施的类型 {#default-config-types}

有三种类型的默认抽象配置实现用于身份验证：

- RestConfig
- SqlConfig
- NoSqlConfig

如果配置与其中一种类型一致，则可以扩展相应的基类。 否则，可以通过实施Config接口从头开始创建它。

### 具体配置实施 {#concrete-config-implementation}

*konnect-definitions*&#x200B;库附带预定义的Config接口实现，用于一些广泛使用的身份验证配置。 您可以直接在连接器中使用这些配置，或使用“配置”界面定义新配置。 这些实施包括：

- API密钥身份验证配置
- 基于身份验证令牌的基本配置
- 基本身份验证配置
- 持有者令牌配置
- SQL的用户名密码配置
- NoSQL的连接字符串身份验证配置

### 其他资源{#resources}

Experience Manager Guides还允许您为徽标和模板以及实施提供自定义资源。 您可以将这些资源保留在`resources`文件夹中。
要使连接器能够使用它们，必须实施以下连接器功能：


- `getLogoSvg` — 以字符串形式返回徽标SVG。

- `getTemplates` — 返回给定格式的模板列表。