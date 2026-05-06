---
title: 关于在Adobe Experience Manager Guides中发布性能和可扩展性的常见问题解答
description: 了解有关在Adobe Experience Manager Guides中发布性能和可扩展性的常见问题解答。
source-git-commit: f188c2827a9e27249d0162c9f9913e090b29672d
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 1%

---


# 资产处理

资产处理是一个关键的工作流，负责确保内容资产在平台内结构化、验证、索引并可供访问。 随着可扩展性需求和云原生需求的不断发展，体系结构经历了从单线程的分层处理模型到分布式的、支持图形的多线程系统的重大转变。

## 当前资产处理工作流

### 处理概述

将资产导入Experience Manager Guides时，将执行以下顺序处理步骤：

- 唯一键值分配：为每个文档分配一个唯一标识符，以确保可跟踪性和引用完整性。
- 解析：将内容（例如DITA XML）解析为结构化组件，以便进行系统级别的理解。
- 验证：结构和架构验证确保符合文档标准。
- 引用分辨率：跨资源解析交叉引用（链接、图像、依赖项）。
- 元数据提取：提取诸如标题、作者和自定义属性等元数据以用于索引和搜索。
- 修改时的重新处理：增量重新处理可确保内容更新后的一致性。

### 体系结构特性

- **单线程处理**：防止依赖于B-Tree实现的JCR （Java内容存储库）结构损坏。这可以确保数据的完整性，但在批量摄取期间会引入处理瓶颈。

- **父映射依赖关系**：使用图形遍历维护资源之间的分层关系。 这是一项密集操作，在大规模处理过程中具有高延迟，增加了计算开销，并且由于遍历密集型操作而带来负担。

## 新资产处理流程

核心处理步骤在功能上保持一致，但现在是在分布式和并行框架中执行的，显着提高了吞吐量。

### 体系结构增强

- **图形数据库集成**：
   - 从分层JCR过渡到本机图形数据库
   - 支持高效地处理关系和依赖关系
   - 消除了在分层存储上模拟图形操作的复杂性
- **多线程分布式处理**：
   - 在云环境中跨多个Pod执行处理
   - 删除对单个前导节点的依赖关系
   - 支持水平可扩展性和并行执行
- **父映射依赖关系已清除：**
   - 消除显式图形遍历的需要
   - 减少I/O操作和处理延迟
   - 简化处理管道
- **同步的唯一ID分配**
   - 集中协调确保：
   - 文档ID不重复
   - 跨分布式节点的一致性
   - 在并发环境中维护引用完整性
- **云原生可伸缩数据库（托管AWS）**
   - 高可用性和可复原的数据库层
   - 支持基于工作负载的弹性扩展
   - 提高整体系统可靠性和性能

![](images/workflow.png)

## 新架构的优势

- 性能改进：
   - 并行执行可显着缩短处理时间
   - 消除大量遍历操作可降低滞后
   - 优化的图形处理提高了依赖关系解析速度
- 可扩展性：
   - 跨Pod水平缩放允许处理较大的摄取卷
   - 云原生基础架构可动态适应工作负载需求
- 可靠性和可用性：
   - 分布式处理可消除单点故障
   - AWS托管数据库可确保高可用性和容错性
- 效率提升：
   - 由于消除了父映射遍历而降低了I/O开销
   - 跨计算节点提高资源利用率
- 数据完整性：
   - 同步的ID分配可维护分布式系统间的一致性
   - 在启用并发性的同时保持稳健性

## 配置数据库

Experience Manager Guides可以为AEM Cloud环境简化数据库配置。 要为AEM Cloud实例设置数据库，请执行以下步骤：

1. 访问AEM Cloud Manager：使用以下URL导航到Adobe Experience Cloud Manager，将占位符替换为您的组织、项目和环境详细信息： `https://experience.adobe.com/#/${orgName}/cloud-manager/environments.html/program/${programId}/environment/${envId}`

1. 配置环境：通过Cloud Manager打开环境配置页面后，您将能够调整特定于实例的设置，包括设置所需的数据库配置。

这种简化的方法确保了Adobe云基础架构中AEM环境的轻松访问和配置。

1. 配置以下属性：


| 属性名称 | 值 | 已应用服务 | 类型 |
|----------------------------------|--------------------------------|-----------------|----------|
| 数据库URL | `<host>:<port>/<db_name>` | 创作 | 变量 |
| GUIDES_ENABLE_DATABASE | `true` | 创作 | 变量 |
| DATABASE_PASSWORD | `password` | 创作 | 密钥 |
| 数据库用户名 | `username` | 创作 | 变量 |
| RUN_POSTPROCESS_IN_PHACES | `true` | 创作 | 变量 |
| DATABASE_CONNECTION_POOL_SIZE | `10` | 创作 | 变量 |


![](images/environment-config.png){width="350"}

1. 保存更改：进行配置更改后，请确保在Cloud Manager界面中&#x200B;**保存**&#x200B;更改。

1. 系统可用性：完全应用配置后，打开GET `http://host/bin/guides/v1/system/status`并检查以下属性：
   - `<isDatabase>`：必须为true
   - `<databaseConnectionCheck>`：必须传递

   如果上述值在响应中正确，则系统可用于新配置的数据库。

通过遵循此流程，您将会获得一个正确设置且随时可用的AEM云环境。

>[!NOTE]
>
> 如果要迁移到具有现有内容的现有环境，则必须先执行阶段2（迁移现有内容），然后再引入任何新内容。 这是为了确保为新内容正确分配临时GUID。

## 在AEM DAM（云环境）中摄取数据（第1阶段）

要在AEM DAM (Digital Asset Manager)中设置新文件夹，请摄取数据并将其与基于JCR的环境进行比较，请执行以下步骤。

1. 在DAM中创建新文件夹。

2. 使用数据上传工具摄取数据：有关详细信息，请查看&#x200B;**将Assets上传到AEM Cloud**。

3. 验证系统
   - 上传完成后，验证资产是否存在DAM中。
   - 确保已提取元数据（例如文件类型、描述和标记）并将其与资源关联。
   - 检查Experience Manager Guides处理（多线程），确认所有引用、元数据提取和验证均成功。
   - 测试访问和编辑文档以确认系统完整性。

4. 与基于JCR的环境进行比较
   - 比较各种测试案例的结果。
   - 评估摄取速度。


要迁移在将Experience Manager Guides切换到基于数据库的设置之前上传和处理的内容，可以使用迁移脚本。 该脚本利用一组API来启动和监控迁移过程。 以下步骤概述了推荐的方法。

## 将内容从JCR迁移到数据库（阶段2）

要迁移在将Experience Manager Guides切换到基于数据库的设置之前上传和处理的内容，您必须使用迁移脚本。 该脚本利用一组API来启动和监控迁移过程。 以下步骤概述了推荐的方法。

1. 使用任何REST客户端触发迁移API。
2. 检查迁移进度。
3. 监控迁移直至完成：继续监控，直到进度API报告100%完成。 完成后，以前从JCR存储库上传和处理的所有内容都将迁移到数据库。

   >[!NOTE]
   >
   > - 确保包含所需的授权标头（例如OAuth令牌、API密钥或来自开发人员控制台的访问令牌），以便对AEM的请求进行身份验证。
   > - 迁移持续时间取决于内容存储库的大小。 建议定期检查进度，并监控错误或中断情况。
   > - 查看迁移日志（如果可用），以评估迁移性能并识别任何问题。

4. 要支持大型存储库的迁移，请遵循以下配置

   >[!NOTE]
   >
   > 仅在迁移期间遇到存储库遍历错误时应用此配置。

   `file name: `org.apache.jackrabbit.oak.query.QueryEngineSettingsService.xml”

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0"
         xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
         jcr:primaryType="sling:OsgiConfig"
         queryLimitInMemory="5000000"
         queryLimitReads="1000000"
   />
   ```


## 迁移API

### 开始迁移

- 终结点： `POST /bin/guides/v1/assets/process`
- 请求正文： (`application/json`)：

```json
  {
    "path": "/content/dam/dita-templates",
    "excludedPaths": [
      "/content/dam/demo",
      "/content/dam/demo1"
    ],
    "type": "ASSET_PROCESSING"
  }
```

- 返回迁移的processingId。
- 触发产品中内置的资产处理工作流。

### 检查迁移状态

终结点： `GET /bin/guides/v1/assets/process/status?processingId=<processingId>`

### 取消正在运行的迁移

- 终结点： `POST /bin/guides/v1/assets/process/cancel`
- 请求正文(application/json)：

  ```
  {
   "processingId": "processingId"
  }
  ```

### 恢复失败或已取消的迁移

- 终结点： `POST /bin/guides/v1/assets/process/resume`
- 请求正文(application/json)：

  ```
  {
   "processingId": "processingId"
  }
  ```

## 将资源上传到AEM cloud

Adobe Experience Manager (AEM) as a Cloud Service提供了多种批量内容摄取方法。 为了确保获得最佳性能（特别是对于Experience Manager Guides后处理），必须采用受支持和可扩展的摄取策略。

### 使用云存储集成进行批量摄取

AEM支持通过受支持的云存储提供商进行批量内容摄取，从而使组织能够连接其首选存储解决方案并将内容直接导入AEM。 由于以下优势，建议对大规模和性能敏感型摄取使用此方法：

- 可扩展的基础架构：摄取过程在Adobe管理的云基础架构上运行，从而实现基于负载和内容量的自动扩展。 这可确保即使是大型数据集也能获得一致的摄取性能。

- 可预测的摄取计划：用户可以提前估计摄取持续时间，这有助于版本计划、计划以及与依赖团队的协调。

  ![](images/ingestion-time.png){width="350"}

- 全面的日志记录和跟踪：摄取工作流包括详细的日志记录和跟踪功能，提供了整个导入过程中进度、成功状态和潜在问题的可见性。

  ![](images/bulk-import-job.png){width="350"}

- 计划摄取：可以计划内容摄取在预定义的时间段内进行，从而确保对最终用户和持续操作的影响最小或没有。

有关详细信息，请使用“批量导入”查看[&#128279;](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-learn/cloud-service/migration/bulk-import)。

## 使用AEM上传进行批量摄取

AEM还提供[AEM upload](https://github.com/adobe/aem-uploa)，这是一个库和命令行界面(CLI)，允许用户直接从本地文件系统摄取内容。 此选项可以集成到自定义解决方案中，或用作上传内容的独立CLI工具。

由于这种方法运行在用户本地计算机上，因此需要稳定且不间断的网络连接来确保可靠且无缝的摄取体验。


## Experience Manager Guides数据库连接的运行状况检查

配置为使用数据库的Experience Manager Guides部署需要稳定且一致的数据库连接才能可靠运行。 验证数据库连接状态是重要的运行状况检查步骤，可排除可能影响系统功能的连接相关问题。

此运行状况检查允许用户确认数据库是否已配置、可访问以及是否按预期运行。 要检查数据库连接状态，请执行以下步骤。

1. 打开任意浏览器或REST客户端
2. 使用此[URL](https://host:port/bin/guides/v1/system/status)触发GET调用
3. 以下字段可用于确定系统配置和运行状况
   1. isDatabase：
      - true：使用数据库配置了环境。
      - false：环境未使用数据库

   2. databaseConnectionCheck：
      - 通过： Experience Manager Guides将检查连接状态，如果Guides能够与数据库连接，则将返回“通过”状态。
      - 失败：环境无法与数据库通信。 客户应立即停止使用系统，并联系Adobe支持部门。

## 日志监控

带有数据库的Experience Manager Guides可以有效地记录详细信息，以将insight置于系统状态。
在Splunk中使用以下查询获取不同场景的日志。

1. 迁移日志：
   - `index IN ("dx_aem_engineering") aem_service=cm-${programid}-${environmentId} sourcetype=aemerror "AssetProcessingJob" OR "AssetJobProducerDb" NOT "ServiceEvent"`
2. 后处理日志：
   - `index IN ("dx_aem_engineering") aem_service= cm-${programid}-${environmentId} sourcetype=aemerror com.adobe.fmdita.uuid.concrete.Cor*`


>[!NOTE]
>
> 阅读有关[Splunk查询功能](https://www.splunk.com/en_us/blog/learn/splunk-cheat-sheet-query-spl-regex-commands.html)的详细信息，以根据持续时间、日志级别筛选这些日志或搜索某些特定模式。










