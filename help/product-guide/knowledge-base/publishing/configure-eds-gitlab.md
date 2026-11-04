---
title: 为Edge Delivery Services设置和配置GitLab
description: 了解如何配置GitLab存储库、访问令牌、Cloud Manager、Webhook和使用您自己的Git将内容从Experience Manager Guides发布到Edge Delivery Services。
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 380089cbcfc56b23a9cb494d49c0e39e1813eabd
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 3%
---

# 为Edge Delivery Services设置和配置GitLab

要使用GitLab将内容从Experience Manager Guides发布到Edge Delivery Services (EDS)，请通过Cloud Manager的&#x200B;*自带Git* (BYOG)功能将GitLab存储库连接到EDS站点。 本文列出了按顺序执行的步骤。 有关每个步骤的详细信息，请访问链接的文档。

## 工作原理

- **GitHub存储库**&#x200B;通过AEM代码同步应用程序创建EDS站点。
- **GitLab存储库**&#x200B;存储从Experience Manager Guides发布的内容。
- **Cloud Manager**&#x200B;通过接收GitLab推送事件(webhook)并将它们同步到EDS网站来链接这两者。

## 先决条件

- 访问GitHub和GitLab（GitLab.com或自托管）以创建存储库和令牌。
- 访问Cloud Manager，其角色允许添加存储库（部署管理员或业务负责人）。
- 系统管理员或API开发人员角色（在Adobe组织中），用于创建Cloud Manager API集成。
- 在配置服务中注册了`aem.live`组织。 在[配置服务设置](https://www.aem.live/docs/config-service-setup)中了解详情。

## 为Edge Delivery Services配置GitLab

要配置GitLab以用于Edge Delivery Services，请按照指定的顺序执行以下步骤，以确保正确设置和集成。

### &#x200B;1. 使用GitHub创建EDS站点

从AEM Guides样板创建GitHub存储库，并在其上安装AEM代码同步应用程序。 保存生成的&#x200B;**实时URL** (`https://<branch>--<github-repo>--<github-username>.aem.live`)供以后使用。

有关步骤，请查看[为EDS创建GitHub存储库](./configure-eds.md#create-a-github-repository-for-eds)和[通过AEM代码同步将GitHub连接到Adobe](./configure-eds.md#connect-github-to-adobe-via-aem-code-sync)。

>[!IMPORTANT]
>
> 请勿使用Cloud Manager中的一键单击选项创建EDS站点。 通过这种方式创建的站点不会为您提供后续步骤所需的管理员权限。 在[准备Edge Delivery Services网站](https://www.aem.live/developer/byo-git#1.-prepare-your-edge-delivery-services-site)中了解详情。

### &#x200B;2. 创建GitLab存储库

从同一AEM Guides样板创建单独的GitLab存储库（例如，`my-eds-gitlab`）。 Experience Manager Guides将生成的输出发布到此存储库。 EDS需要`main`分支。

要创建存储库，请创建一个空白项目并将[aem-guides-boilerplate](https://github.com/adobe/aem-guides-boilerplate)的内容推送到其中，或将样板导入新项目中。 有关步骤，请查看GitLab文档中的[创建项目](https://docs.gitlab.com/user/project/)和[将项目从GitHub导入到GitLab](https://docs.gitlab.com/user/project/import/github/)。

### &#x200B;3. 配置装载点URL

在GitHub存储库中，更新`fstab.yaml`，使内容源指向GitLab存储库，并将更改提交到`main`。

```text
https://<worker URL>/gitlab/<git acc domain>/<git username>/<git repo>/main/docs
```

| 参数 | 描述 |
|---|---|
| `<worker URL>` | 由Adobe提供的工作节点URL。 |
| `<git acc domain>` | GitLab域（如`gitlab.com`）或您的自托管域。 |
| `<git username>` | 您的GitLab用户名。 |
| `<git repo>` | GitLab存储库的名称。 |
| `main` / `docs` | 分支和根文件夹。 Experience Manager Guides的默认值。 |

### &#x200B;4. 创建GitLab访问令牌

创建以下所需的访问令牌：

- **Cloud Manager**，用于验证和访问存储库。 在Cloud Manager[&#128279;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/managing-code/external-repositories)中添加外部存储库中了解更多信息。
- **Experience Manager Guides发布配置文件**，以提交已发布的输出。 创建具有&#x200B;**开发人员**&#x200B;角色和`api`作用域的GitLab项目访问令牌。 请参阅[GitLab文档](https://docs.gitlab.com/ee/user/project/settings/project_access_tokens.html)以了解详情。

>[!NOTE]
>
> 在令牌过期前续订令牌。 如果发布配置文件中的令牌已过期，则发布失败。 要更新Cloud Manager使用的令牌，请查看[管理外部存储库的访问令牌](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/managing-code/manage-access-tokens)。

### &#x200B;5. 将GitLab存储库添加到Cloud Manager

在Cloud Manager中，转到&#x200B;**存储库** > **添加存储库**，选择&#x200B;**专用存储库**，然后使用访问令牌验证所有权。 等待存储库状态为&#x200B;**就绪**。 BYOG选项仅在至少一个外部存储库准备就绪后可用。

有关步骤，请查看[在Cloud Manager中添加外部存储库](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/managing-code/external-repositories)。

### &#x200B;6. 生成Cloud Manager API密钥

在Adobe Developer Console中创建API集成（**Cloud Manager** API，**OAuth服务器到服务器**），并复制&#x200B;**客户端ID （API密钥）**。

有关步骤，请查看[创建API集成项目](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration)。

### &#x200B;7. 配置GitLab webhook

在Cloud Manager中，为存储库选择&#x200B;**配置Webhook**，并复制&#x200B;**Webhook URL**&#x200B;和&#x200B;**密钥**。 将API密钥附加到URL (`<webhook URL>&api-key=<CLIENT_ID>`)。 在GitLab中，转到&#x200B;**设置** > **Webhooks**，添加URL和密钥，选择`main`分支，并启用&#x200B;**推送事件**。

有关详细信息，请查看[在Cloud Manager中配置外部存储库](https://www.aem.live/developer/byo-git#2.-configure-your-external-repository-in-cloud-manager)。

### &#x200B;8. 将EDS站点添加到Cloud Manager

在Cloud Manager中，转到&#x200B;**Edge Delivery** > **添加Edge Delivery站点**，然后输入在第1步中保存的实时URL。 完成所有权验证。

有关步骤，请查看[添加Edge Delivery站点](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/edge-delivery-sites/add-edge-delivery-site)。

### &#x200B;9. 使用自带Git连接存储库

在Cloud Manager的EDS网站上，选择&#x200B;**自带Git (BYOG)**，选择GitLab存储库，然后进行确认。 复制并安全存储生成的密钥。 它只会显示一次，如果您重新配置站点，则会生成一个新的密钥。

有关详细信息，请查看[在Cloud Manager中配置Edge Delivery站点](https://www.aem.live/developer/byo-git#3.-configure-your-edge-delivery-site-in-cloud-manager)。

### &#x200B;10. 配置EDS站点以使用Cloud Manager

使用webhook URL中的&#x200B;**程序ID** (`/program/<PROGRAM_ID>/`)和&#x200B;**存储库ID** (`/repo/<REPO_ID>/`)，将EDS网站的代码源设置为Cloud Manager存储库。 然后，使用步骤9中的密码创建一个名为`cm-byog`的密码。

对于管理员API调用，请查看[将您的AEM站点配置为使用Cloud Manager](https://www.aem.live/developer/byo-git#4.-configure-your-aem-site-to-use-cloud-manager)。

### &#x200B;11. 同步和验证

在Cloud Manager中，从网站的菜单中选择&#x200B;**同步代码**，然后选择`main`分支。 然后打开`https://main--<site>--<org>.aem.page`以验证站点。

有关详细信息，请查看[触发您的第一个同步](https://www.aem.live/developer/byo-git#5.-trigger-your-first-sync)和[验证您的AEM网站](https://www.aem.live/developer/byo-git#6.-verify-your-aem-site)。

### &#x200B;12. 从Experience Manager Guides发布

使用步骤4中的项目访问令牌创建一个EDS发布配置文件，其中将&#x200B;**Git帐户类型**&#x200B;设置为&#x200B;**GitLab**。 然后在EDS输出预设中选择此配置文件并生成输出。 输出已提交到GitLab存储库的`docs`文件夹。

有关步骤，请查看[创建EDS发布配置文件](./configure-eds.md#create-the-eds-publish-profile-for-github-or-gitlab)和[创建EDS的输出预设并生成输出](./configure-eds.md#create-an-output-preset-for-eds-and-generate-output)。

## 疑难解答

- **站点在推送后显示旧内容：**&#x200B;验证webhook是否正在向Cloud Manager传递事件，然后检查最新同步作业的状态。
- **同步错误`Unable to fetch hlxignore: 401`：** `cm-byog`密码不正确。 使用步骤9中的秘密重新创建。
- **链接到其他站点的存储库：** Cloud Manager存储库一次只能链接到一个站点。 要跨站点共享存储库，请使用[Repoless](https://www.aem.live/docs/repoless)。

有关更多详细信息，请参阅自带Git [&#128279;](https://www.aem.live/developer/byo-git#troubleshooting)中的疑难解答。
