---
title: 配置 Dispatcher
description: 了解如何配置Dispatcher
exl-id: 525de1c3-5a79-4d65-89b4-ca05ae660c2c
feature: Installation
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/RTgKeZZYjXP5ebOpTys9RL6-Q9IcPbkLZJ13ueRZwVI
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 310
ht-degree: 6%

---

# 配置 Dispatcher {#id213BCM0M05U}

如果您计划在AEM创作实例上将Dispatcher与AEM Guides结合使用，则需要执行以下其他配置以完成设置：

>[!NOTE]
>
> Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。 有关使用Dispatcher的详细信息，请参阅[Dispatcher概述](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=en)。

## 在URL中启用AllowEncodedSlases

默认情况下，AEM Dispatcher设置中未启用包含编码斜杠的URL，但是在AEM Guides中工作时，您需要启用此功能。 为此，您需要在Apache配置中将AllowEncodedSlashes参数设置为On，如以下代码片段所示：

```XML
<VirtualHost *:80>
                ServerName www.geometrixx-outdoors.com
                **AllowEncodedSlashes On**
                <Directory />
                <IfModule disp_apache2.c>
                SetHandler dispatcher-handler
                </IfModule>
                Options FollowSymLinks
                AllowOverride None
                </Directory>
                </VirtualHost>
            
```

## 为DITA配置mime.types文件

在将Dispatcher与AEM Guides结合使用时，必须确保将DITA映射和主题文件呈现为HTML，以便作者按预期方式查看内容\（而不是原始文本格式\）。

执行以下步骤以更新mime.types文件：

1. 使用SSH连接到Dispatcher服务器并浏览到httpd.conf文件。

1. 检查“ mime.types”文件的路径。

1. 打开mime.types文件并搜索“ text/html ”。 “ text/html ”的默认映射为：

   `text/html html htm`

1. 通过将ditamap和dita扩展添加为来更新映射：

   `text/html html htm ditamap dita`

1. 保存并关闭该文件。


此配置更新可确保Dispatcher渲染的DITA映射和主题文件在Assets UI中显示为HTML。

## 允许用户首选项请求URL

在将Dispatcher与AEM Guides结合使用时，如果您的创作实例前面有调度程序，则进行以下两项更改：

- 将POST请求URL列入白名单。 下面提供了示例“`/filters`”规则 — 将此规则添加到Dispatcher配置文件：

```json
/xxxx {/type "allow" /method "POST" /url "/home/users/*/preferences"}
```

- 确保Author Dispatcher上未缓存URL模式“ /libs/cq/security/userinfo.json”，因此请在author\_dispatcher.any中添加规则\（如下所示\）

```json
/xxxx {
                /glob "/libs/cq/security/userinfo.json"
                /type "deny"
                }
```

**父主题：**[&#x200B;下载并安装](download-install.md)
