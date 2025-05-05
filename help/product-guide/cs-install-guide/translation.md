---
title: 翻译内容
description: 了解如何翻译内容
exl-id: 5af78233-343e-47ba-b60c-b7f4789e2406
feature: Translation
role: Admin
level: Experienced
source-git-commit: ea3083542e955a56c27cd833600370a7962c6b8d
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 9%

---

# 翻译内容 {#id181GB0400UI}

自动翻译页面内容、资产和用户生成的内容，以创建和维护多语言网站。 要自动化翻译工作流，您可以将翻译服务提供商与 AEM 集成并创建项目以将内容翻译成多种语言。AEM 支持人工翻译工作流和机器翻译工作流。

- 人工翻译：内容将发送给您的翻译提供商并由专业翻译人员进行翻译。 完成后，将返回翻译的内容并将其导入 AEM。当您的翻译提供商与AEM集成时，内容会在AEM和翻译提供商之间自动交换

- 机器翻译：机器翻译服务将立即翻译您的内容


翻译内容涉及以下步骤：

1. 将AEM与您的[翻译服务提供商](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/integration-framework.html?lang=zh-Hans)连接并创建翻译集成框架配置。

1. 将语言母版页面关联到翻译服务和框架配置。

1. 标识要翻译的[内容的类型](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/rules.html?lang=zh-Hans)。

1. 通过创作语言母版并创建语言副本的根页面来[准备内容以进行翻译](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/preparation.html?lang=zh-Hans)。

1. 创建[翻译项目](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/managing-projects.html?lang=zh-Hans)以收集要翻译的内容并准备翻译过程。

1. 使用翻译项目[管理内容翻译](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/managing-projects.html?lang=zh-Hans)进程。


如果翻译服务提供商不提供连接器来与AEM集成，则AEM支持以XML格式手动导出和导入已翻译内容。

>[!TIP]
>
> 有关翻译内容的最佳实践，请参阅最佳实践指南中的&#x200B;*翻译*&#x200B;部分。

## 在DITA映射仪表板上配置翻译选项卡

要在DITA map操控板上隐藏翻译选项卡，请执行以下步骤：

1. 使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。
1. 在配置文件中，提供以下\（属性\）详细信息以在映射功能板上配置翻译选项卡：

   | PID | 属性键 | 属性值 |
   |---|------------|--------------|
   | `com.adobe.fmdita.config.ConfigManager` | `tabs.translation` | 布尔值\( true/ false\)。<br> **默认值**： `true` |

   >[!NOTE]
   >
   > 默认情况下，此配置处于启用状态，并且翻译选项卡在映射功能板上不可用。


## 配置基于组件的翻译工作流

如果翻译供应商的连接器不支持DITA内容，则需要启用基于组件的翻译工作流。 启用后，可翻译内容将作为资产元数据发送。 但是，连接器需要支持此工作流的资产元数据翻译才能正常工作。

根据设置中使用的翻译工作流，应配置基于组件的翻译工作流选项。 使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\（属性\）详细信息以配置基于组件的翻译工作流：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `component.translation` | 布尔值： <br> -   如果您使用的是人工翻译，则&#x200B;*禁用* \( `false`\) **基于组件的翻译工作流**&#x200B;选项。 <br> -   如果您正在使用机器翻译，则&#x200B;*启用\( `true`\)* **基于组件的翻译工作流**&#x200B;选项。 |



## 配置旧版翻译工作流

>[!IMPORTANT]
>
> 建议您使用AEM Guides 2024.06.0及更高版本中提供的最新翻译工作流以提高性能。 但是，如果您在翻译流程中启用了任何自定义设置，并且它受新工作流的影响，请考虑还原旧版翻译工作流作为解决方法。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下（属性）详细信息以配置旧版翻译工作流：


| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `translation.workflow.version.legacy` | 布尔值： <br> — 如果您使用最新的翻译工作流，则&#x200B;*禁用* \(`false`\) **运行旧版翻译工作流**&#x200B;选项。  <br> -   如果使用旧版翻译，则&#x200B;*启用\( `true`\)* **运行旧版翻译工作流**&#x200B;选项。<br> **默认值**： false |




>[!NOTE]
>
> 如果您使用的是翻译连接器，请确保已按照Adobe Experience Manager文档中的&#x200B;*[配置翻译集成框架](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/integration-framework.html?lang=zh-Hans)*&#x200B;主题中所述配置连接器。

>[!IMPORTANT]
>
> 设置翻译配置后，请确保在语言文件夹上设置适当的云配置。

## 配置临时语言副本的后处理

启动翻译工作流时，系统会创建源内容的临时语言副本。 您可以选择对这些临时文件启用或禁用后处理操作。 在后处理操作中，解析来自文件的传入和传出引用，设置文档状态以及其他操作。 如果对这些临时文件启用后处理，则翻译过程可能需要更长的时间才能完成。 因此，建议禁用后处理选项。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以配置临时语言副本的后处理：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `postprocess.temporary.langcopies` | 布尔值： <br> -   如果不想对临时文件运行后处理操作，则&#x200B;*禁用* \( false\) **后处理语言副本**&#x200B;选项。<br> -   如果要对临时文件运行后处理操作，请&#x200B;*启用* \( true\) **后处理语言副本**&#x200B;选项。<br> **默认值**： false |

