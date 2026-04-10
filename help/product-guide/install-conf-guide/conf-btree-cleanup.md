---
title: 为云服务配置B树清理作业
description: 为云服务配置B树清理作业
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 3%

---

# 配置B树清理

设置B树清理作业并管理`Guides BTree deletion`设置以保持系统优化和存储清洁。

## 配置B树清理作业

以下选项卡提供了有关根据Experience Manager Guides设置配置B树清理作业的说明：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[配置覆盖](download-install-config-override.md)中提供的说明创建配置文件。

1. 在配置文件中，提供以下（属性）详细信息：

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | `com.adobe.guides.utils.schedulers.GuidesBTreesCleanupSchedulerJob` | `cronExpression` | **默认值：** &quot;0 0 0 * * ？&quot; |

>[!TAB 内部部署]

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;*com.adobe.guides.utils.schedulers.GuidesBTreesCleanupSchedulerJob*&#x200B;捆绑包。

1. 更新cron表达式以设置B树清理计划程序作业运行频率。

1. 配置B树清理计划程序，如下所示。

   ![](assets/btree-cleanup-config.png){align="left"}

1. 选择&#x200B;**保存**。

>[!ENDTABS]

## 配置指南B树删除启用设置

以下选项卡提供了根据Experience Manager Guides设置启用该设置的说明：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[配置覆盖](download-install-config-override.md)中提供的说明创建配置文件。

1. 在配置文件中，提供以下（属性）详细信息：

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `btree.deletion.enabled` | **默认值：** &quot;True&quot; |

>[!TAB 内部部署]

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;包。
1. 启用设置`Guides btree deletion enabled`。

   ![](assets/btree-cleanup-setting.png){align="left"}

1. 选择&#x200B;**保存**。

>[!ENDTABS]