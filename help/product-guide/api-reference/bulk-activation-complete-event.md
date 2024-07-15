---
title: 批量激活完成事件处理程序
description: 了解批量激活完成事件处理程序
feature: Bulk Activation Event Handler
role: Developer
level: Experienced
exl-id: 08b153d7-3d13-4804-9e3e-38790dbea1f3
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 1%

---

# 批量激活完成事件处理程序

Experience Manager Guides公开`com/adobe/fmdita/replication/complete`事件，用于在批量激活过程完成后执行任何操作。 每当批量激活过程完成时，就会触发此事件。 例如，如果您运行批量激活地图的AEM站点预设，则会在激活过程结束后调用此事件。

您需要创建一个AEM事件处理程序来读取此事件中可用的属性并进行进一步处理。

活动详情说明如下：

**事件名称**：

```
com/adobe/fmdita/replication/complete 
```

**参数**：

|Name|Type|Description|
|----|----|-----------|
|`path`|String|The path of the file that triggered this event. <br> For example, `/content/output/sites/ditamap1-ditamap`. <br> It is a list of paths serialized as a JSON array.|
|`messageType`|String|The type of a message. <br>Possible option : `REPLICATION`|
|`action`|String|This is the action performed. <br>Possible option : `BulkReplicate`|
|`user`|String|The user who started the operation.|
|`result`|String|The result of the Bulk Activation. It is a serialized JSON Object: <br>`{"success":boolean,"code":integer,"message":"" }`|
|`agentId`|String|The agentId used in the replication. For example, `"publish"`.|
|`importMode`|String|Import mode used in Activation. The possible options are: <br>`REPLACE, MERGE, UPDATE`.|


**示例事件侦听器**：

```XML
@Component(service = EventHandler.class,
        immediate = true,
        property = {
                EventConstants.EVENT_TOPIC + "=" + "com/adobe/fmdita/replication/complete",
        })
 
public class SampleEventHandler implements EventHandler {
 
    protected final Logger log = LoggerFactory.getLogger(this.getClass());
 
    @Override
    public void handleEvent(final Event event) {
        Map<String, String> properties = new HashMap<>();
        properties.put("paths", (String) event.getProperty("paths"));
        properties.put("messageType", (String) event.getProperty("messageType"));
        properties.put("action", (String) event.getProperty("action"));
        properties.put("result", (String) event.getProperty("result"));
        properties.put("user", (String) event.getProperty("user"));
        properties.put("agentId", (String) event.getProperty("agentId"));
        properties.put("importMode", (String) event.getProperty("importMode"));
 
        String eventTopic = event.getTopic();
        log.debug("eventTopic {}", eventTopic);
        for(Map.Entry entry:properties.entrySet()) {
            log.debug(entry.getKey() + " : " + entry.getValue());
        }
 
    }
}
```
