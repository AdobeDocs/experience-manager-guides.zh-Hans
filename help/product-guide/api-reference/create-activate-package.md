---
title: 用于创建和激活包的REST API
description: 了解用于创建和激活包的REST API
exl-id: 90686f77-a769-44bc-90eb-116cf9d0341e
feature: Rest API Packages
role: Developer
level: Experienced
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# 用于创建和激活包的REST API {#id198CF0260Y4}

以下REST API允许您创建和激活CRX包。

## 创建和激活包

创建并激活CRX包的POST方法。

**请求URL**：
http://*&lt;aem-guides-server\>*： *&lt;port-number\>*/bin/fmdita/activate

**参数**：
请求查询包含JSON规则字符串。 POST请求的内容类型必须设置为`application/json; charset=UTF-8`。

**示例**：
以下示例演示了使用curl命令的API调用：

```XML
curl -u <*username*>:<*password*> -H "Content-Type: application/json; charset=UTF-8"  -k -X POST -d "{[JSON rules string](create-activate-package-java.md#example-create-activate-package-id198JH0B905Z)}" http://<*aem-guides-server*>:<*port-number*>/bin/fmdita/activate
```


**可选参数**

`activationTarget`

**有效值**

Cloud Service的`preview`或`publish`，内部部署软件的`publish`

- 对于Cloud Service，如果参数包含无效值，则包激活失败。

- 对于内部部署软件，如果参数包含无效值，将记录错误，并使用默认值`publish`完成发布。

如果未定义可选参数`activationTarget`，则它会使用Cloud Service和On-premise Software的默认发布代理来激活。



以下示例显示使用带有可选参数的curl命令的API调用：


```XML
curl -u <*username*>:<*password*> -H "Content-Type: application/json; charset=UTF-8"  -k -X POST -d "{[JSON rules string](create-activate-package-java.md#example-create-activate-package-id198JH0B905Z)}" http://<*aem-guides-server*>:<*port-number*>/bin/fmdita/activate?activationTarget=`<validActivationTargetValue>`
```
