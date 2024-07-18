---
title: 自定义
description: 自定义审核应用程序
role: User, Admin
exl-id: 9f6a4e9f-fc13-40b5-a30f-151c94faff81
source-git-commit: 492f72768e0de74a91eb7acc9db8264e21bfc810
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# 自定义审核应用程序

为了简化审阅应用程序的自定义，我们提供了一些挂钩，如下所述：

## Review-Comment

- ID： `review_comment`
- 挂接： `this.next('updateExtraProps')`：

如[此处](../../aem_guides_framework/basic-customisation.md)所述，自定义期间添加的任何新属性都位于`this.model.extraProps`下。 方法`updateExtraProps`允许您向审阅评论添加属性，并处理服务器上所添加属性的更新和存储。

### 使用示例

例如，您想要将字段`commentRationale`和`severity`添加到评论中。
让我们将`commentRationale`更新为“这是一个重要句子”。 以及`severity`到“关键”。
可以使用语法执行此操作：

```typescript
  this.next('updateExtraProps', {
    'commentRationale': 'This is an important sentence.',
    'severity': 'CRITICAL'
  })
```

上述代码片段将处理值的更新和保存。 通过定义视图，保存的值可以在UI中呈现。

```JSON
{
    "component" : "label",
    "label": "@extraProps.commentRationale"
}
```

## 内联审核面板

- ID： `inline_review_panel`

1. 挂钩： `onNewCommentEvent`
挂钩`onNewCommentEvent`允许您针对新评论或回复事件抛出事件或调用方法。
`onNewCommentEvent`中收到的参数包括：
   - 事件：已调度的评论/回复事件。
   - newComment：布尔型
如果调度的事件是新评论事件，即`highlight`、`insertion`、`deletion`、`sticky note comment`
   - newReply：布尔值
如果调度的事件是新回复事件。

2. 挂钩： `sendExtraProps`

如果要扩展`event`并从内联审核面板发送`extraProps`，此挂接很有用。 下面我们将解释这两个钩子的用法。

### 内联审阅面板示例

假设我们要发送额外的Prop `userInfo`，每次发送新评论或回复时。 现在，这将通过内联审阅面板完成，但我们没有对新生成评论的commentId的引用，因此要实现此目的，我们可以编写以下代码。

```typescript
    onNewCommentEvent(args){
      const events = _.get(args, "events")
      const currTopicIndex = tcx.model.getValue(tcx.model.KEYS.REVIEW_CURR_TOPIC) || this.getValue('currTopicIndex') || "0"
      const event = _.get(_.get(events, currTopicIndex), '0')
      const newComment = _.get(args, 'newComment')
      const newReply = _.get(args, 'newReply')
      if ((newComment || newReply) && event) {
        this.next('setUserInfo', event)
      }
    },
```

在上述代码片段中，我们正在检查已调度的事件是新注释还是回复。 如果存在新的评论或回复，我们将调用方法`setUserInfo`

```typescript
    const getUserInfo = (userId) => {
      return $.ajax({
        url: '/bin/dxml/xmleditor/userinfo',
        data: {
          username: userId,
        },
        success: (data) => {
          return data
        }
      })
    }

    setUserInfo(event) {
      getUserInfo(event.user).done(userData => {
        const extraProps = {
          "userFirstName": userData?.givenName || '',
          "userLastName": userData?.familyName || '',
          "userTitle": userData?.title || '',
          "userJobTitle": userData?.jobTitle || '',
          'userEmail': userData?.email || '',
        }
        const data = {... event, extraProps}
        this.next(
          'sendExtraProps',
          data
        )
      })
    },
```

在上述方法中，我们将扩展事件以发送extraProp，包括用户的名字、电子邮件、标题等。 通过此方式扩展事件可确保使用正确的commentId发送extraProp，并确保它们附加到正确的注释中。

挂接`updateExtraProps`本身会调用挂接`sendExtraProps`，因此何时使用什么？

我们在`review_comment`控制器中使用`updateExtraProps`，该控制器已具有评论的`id`，因此您只需提及`extraProps.`

但是，`inline_review_panel`无权访问评论的ID，因此无论何时需要从内联审核面板调度事件，`sendExtraProps`都会派上用场。
