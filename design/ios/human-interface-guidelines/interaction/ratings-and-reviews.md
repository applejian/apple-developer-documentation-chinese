# 评分和评论

评分和评论能够帮助用户在考虑是否试用你的应用时做出明确的决定。积极的评分和评论意味着你应用有更多的下载，并且客户反馈让你深入了解现实世界的使用情况，能够对将来的开发有帮助。

提供良好的整体体验是鼓励积极评分和评论的最佳方式，但是在恰当的时间请求反馈同样重要。当请求用户为你的应用打分的时候，请牢记这些注意事项。

**只有当用户有意愿参与你应用互动的时候，才去请求评分。**例如，在完成一个游戏级别或者生产力任务的时候提醒用户。千万不要在第一次启动或者加载的时候请求评分。允许充足的时间来形成意见。

**不要打断用户，尤其是当他们执行时间敏感或者有压力的任务。**寻找逻辑暂停或停止点，这个时候的评分请求最有意义。

**不要做一个害虫。** 重复的评分提醒可能会让人感觉烦躁，而且还会对用户对你应用的评价造成负面影响。在评分请求之间应当至少一到两周的时间间隔，并且仅当用户与你的应用有了进一步互动之后，才再次提醒评分。

## 系统评分和评论提醒

<img src="https://developer.apple.com/ios/human-interface-guidelines/images/AppRating.png"/>

系统为应用提供了一致的非侵入式的方式来请求评分和评论。要使用此功能，你只需要在应用用户体验中确认需要反馈意见的位置。如果用户尚未提供反馈，并且最近没有提出请求，系统会显示一个应用内提示，来请求评分和撰写评论的可选项。用户可以通过单击提供反馈或者关闭提醒。（在设置中，用户来可以选择不接受所有已安装应用的评分提醒）系统会针对每个应用在 365 天的周期内，将自动限制提醒的展示次数在 3 次。

**系统提供的提示优先。**系统的评分提醒提供了一个熟悉、有效的的体验，这种体验最小化了对用户的影响。

**不要使用按钮或其他控制器请求反馈。**因为系统限制了评分提醒的频率，如果尝试通过响应控制来请求反馈的话，可能会导致评分提醒不会显示。

For developer guidance, see SKStoreReviewController in StoreKit.

更多开发者指导，参见 [StoreKit](https://developer.apple.com/reference/storekit) 中的 [SKStoreReviewController](https://developer.apple.com/reference/storekit/skstorereviewcontroller)。

Responding to reviews is a great way to communicate with users, address concerns, and potentially improve your app’s rating. For best practices, see Responding to Reviews on the App Store.

>小提示  
>对评论的回复是与用户交流、解决问题的很好的方式，并且可能提升你的应用评分。有关最佳做法，参见 [App Store 上的评论回复](https://developer.apple.com/app-store/responding-to-reviews/)。

