---
title: 了解Experience Manager Guides中的会话超时
description: 了解Experience Manager Guides中的会话超时。
feature: Authoring, Publishing
role: User
exl-id: f09b1215-4753-4dfd-89ef-1629257e5efe
TQID: https://experienceleague.adobe.com/nrxkVxSUooy2-08PaUp1pjiH8w2kBBNGC9efarvepbQ
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 249
ht-degree: 0%

---

# 为何Experience Manager Guides会在特定时间段后注销我？

Experience Manager Guides会在用户会话达到定义的不活动期（空闲超时）后结束该会话。 此自动注销功能是在Adobe Experience Manager中配置的。 会话过期时，会显示一个弹出警报，通知用户会话已过期。 此警报会限制用户进一步更改内容。

**会话超时的工作原理是什么？**

Experience Manager Guides每30秒发送一次后台请求`token.json`以验证会话。 如果会话仍处于活动状态，则会返回有效令牌。 如果会话因非活动状态而过期，则会返回空令牌，并将会话视为非活动。

**会话过期后会发生什么情况？**

检测到非活动会话时：

- 此时会出现一个弹出警报，通知您已注销。

  ![](images/sign-out-prompt.png)

- 该警报将禁用与应用程序的所有交互。

- 选择&#x200B;**确定**&#x200B;将刷新浏览器并将您重定向到登录页面。
- 登录后，您将被重定向到Experience Manager Guides的最后一个打开页面。

**后续步骤**

会话到期警报通过限制您在非活动会话期间对应用程序进行更改，有助于防止数据丢失。 为避免意外丢失内容，建议定期在编辑器中保存您所做的工作，特别是在长时间离开系统之前。
