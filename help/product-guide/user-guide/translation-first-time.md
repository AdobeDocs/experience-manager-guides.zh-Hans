---
title: 内容翻译的最佳实践
description: 了解AEM Guides中内容翻译的最佳实践。 了解如何配置翻译服务、创建新翻译项目以及启动翻译作业。
exl-id: f2a4df86-bba7-434c-b7f9-3587b8a4f9bc
feature: Translation
role: User
source-git-commit: ac83f613d87547fc7f6a18070545e40ad4963616
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 0%

---

# 内容翻译的最佳实践 {#id1678G0S702F}

翻译内容时请考虑以下几点：

- 文件夹和文件名必须符合文件命名标准，例如 — 不应有空格、撇号、大括号、等号、特殊或非ASCII字符。

- 如果您翻译不同语言的内容，则必须创建与每种语言对应的文件夹。 其中每个语言文件夹都将包含与该语言对应的内容。 例如，您可以使用语言指示符创建文件夹，例如`de`用于德语，`fr`用于法语等等。 或者，您也可以使用语言和区域指示符（如`fr-FR`用于法国使用的法语，或`fr-CA`用于加拿大使用的法语）来创建文件夹。
- 目标语言还应根据其实例上的目标语言文件夹选择实际区域设置。
- 云配置应与源文件夹的云配置相同，并且一个文件夹中应该只有一个云配置。 如果要使用多个翻译连接器，则可以在/conf下创建多个文件夹。
- 一个文件夹中的文件不应超过1000个。
- 确保负责启动翻译流程的用户对源语言文件夹和目标语言文件夹具有读取、修改、创建和删除权限。
- 由于翻译内容需要创建翻译项目，因此用户必须有权在Adobe Experience Manager中创建项目。
- 如果要在映射中使用条件预设，则必须在启动翻译过程之前创建这些预设。 由于条件预设也捆绑在映射的翻译版本中，因此在启动翻译过程之前创建预设，可以确保它们在翻译版本中可用。
- 内容翻译过程必须从DITA映射控制台而不是Adobe Experience Manager Assets UI启动。
- 如果通过人工翻译来翻译内容，则不得使用基于组件的DITA翻译工作流。 但是，此选项必须用于机器翻译。
- 不需要本地化的全局使用内容和媒体应放在语言副本之外。
- 所有必须本地化的常用内容都应保存在语言文件夹下的公用文件夹中。

下图显示了一个例子，说明了当您全局使用内容和三个语言副本时，Adobe Experience Manager中的文件夹结构。

![](images/aem-directory_structure.png){align="left"}

## 配置翻译服务

执行以下步骤以配置要使用的人工翻译服务或机器翻译服务：

1. 在Assets UI中，选择源语言文件夹。

1. 打开文件夹属性，然后转到&#x200B;**云服务**&#x200B;选项卡。

1. 在&#x200B;**云服务**&#x200B;选项卡中，配置要使用的翻译服务。

   您可以配置机器翻译或人工翻译。

   确保一个文件夹中只有翻译连接器的一个配置。 如果有多个翻译连接器，则可以在/conf下创建多个文件夹。 在开始翻译过程之前，源语言文件夹必须选择云配置。

   >[!NOTE]
   >
   > 查看Adobe Experience Manager文档中的[配置翻译集成框架](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/integration-framework.html?lang=zh-Hans)，了解有关与第三方翻译服务集成的详细信息。

1. 选择&#x200B;**保存并关闭**&#x200B;以保存更新的文件夹属性。


## 开始翻译作业 {#id225IK030OE8}

执行以下步骤以启动翻译作业：

1. 在&#x200B;**项目**&#x200B;控制台中，导航到为本地化而创建的项目文件夹。

1. 选择本地化项目以打开详细信息页面。

1. 选择&#x200B;**翻译作业**&#x200B;拼贴上的箭头，然后从列表中选择&#x200B;**开始**&#x200B;以启动翻译工作流。

   >[!NOTE]
   >
   > 如果您使用的是人工翻译服务，则需要导出内容以供翻译。 获得已翻译内容后，您需要将其导入回翻译项目。

1. 要查看翻译作业的状态，请选择&#x200B;**翻译作业**&#x200B;拼贴底部的省略号。


翻译完成后，翻译作业的状态将更改为&#x200B;*准备好审查*。 要完成翻译过程，您需要在项目控制台中接受翻译作业拼贴中的已翻译副本和资产元数据。 如果要启动新的翻译项目，请查看[创建翻译项目](translate-documents-web-editor.md#create-a-translation-project)。

>[!NOTE]
>
>- 如果您拒绝翻译作业中一个或多个主题的翻译，则所有被拒绝主题的&#x200B;**正在进行**&#x200B;翻译状态将恢复到其原始状态。 将根据最新翻译状态检查并还原所引用主题的状态。 此外，即使拒绝在目标语言文件夹中创建的翻译文件，也不会删除这些文件。
>- 如果您拒绝、删除或取消在多个项目（针对任何一个项目）中存在的主题的翻译作业，则不会还原该主题的&#x200B;**正在进行**&#x200B;翻译状态，但会从该给定资产的&#x200B;**正在进行**&#x200B;项目列表中删除该项目。
>- 此外，如果您取消或删除翻译作业或删除整个项目，则&#x200B;**正在进行**&#x200B;翻译状态将恢复到其原始状态。

**父主题：**&#x200B;[&#x200B;内容翻译概述](translation.md)
