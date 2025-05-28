---
title: 了解Experience Manager Guides中的会话超时
description: 了解Experience Manager Guides中的会话超时。
feature: Authoring, Publishing
role: User
source-git-commit: a6e015817bc9a964e3ca6a83c50089e7fabcdd94
workflow-type: tm+mt
source-wordcount: '247'
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





