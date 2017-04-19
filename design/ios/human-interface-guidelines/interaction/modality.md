# 模态

模态创建焦点，通过防止人们做其他事情直到他们完成任务或关闭消息或视图。行动表，警报框和活动视图提供模态体验。当屏幕上出现模态视图时，用户必须通过点按按钮或以其他方式退出模态体验来进行选择，例如在日历中编辑事件或在 Safari 中选择书签时。 模式视图可以占据整个屏幕，整个父视图（如弹出框）或屏幕的一部分。模态视图通常包括退出视图的完成和取消按钮。


![警告框](https://developer.apple.com/ios/human-interface-guidelines/images/modality_alert_2x.png)

![模态视图](https://developer.apple.com/ios/human-interface-guidelines/images/ModalView-Screen_2x.png)


**最小化模态的使用。** 一般来说，人们更喜欢以非线性方式与应用程序进行交互。考虑创建一个模态的上下文，只有当关键是获得人们的注意时，当一个任务必须被完成或放弃继续使用该应用程序，或者保存重要的数据时。

**提供一种明显而安全的方式来退出模式任务。** 确保人们在退出模态视图的时候总是知道他们行为的结果。

**保持模态任务简单，简短，精细集中。**不要在你的应用程序中创建一个应用程序。如果模态任务太复杂，人们可能会忽略他们进入模态语境所时暂停的任务。特别注意创建涉及层次结构视图的模态任务，因为用户可能会迷路，并且忘记如何回溯其步骤。如果模态任务必须包含子视图，请提供通过层次结构的单一路径和一个明确的完成路径。避免在完成任务之外的事件中使用完成按钮。

**如果合适，显示标识任务的标题。**您还可以在视图的其他部分提供更完整的任务描述或提供指导。

**预留警报来传递要点和和理想的可操作信息。**警报框中断了体验，并且需要轻按关闭，所以让人们感觉入侵是有必要的至关重要。要了解更多信息，请参阅[警报](https://developer.apple.com/ios/human-interface-guidelines/ui-views/alerts/)。

**遵守通知偏好。**在设置中，用户可以指定他们想要如何从您的应用程序接收通知。遵守这些偏好设置，以避免他们完全关闭您的应用的通知。

**不要在弹出框上显示模态视图。**除了警报有可能例外，没有任何东西可能出现在弹出框之上。在罕见的情况下，当您需要在弹出框中执行操作后呈现一个模态视图，请在显示模态视图之前关闭该弹出框。

**与您的应用程序协调模态视图外观。**
模式视图可以包括例如导航栏。在这种情况下，请使用与您应用中导航栏相同的外观。

**选择适当的模态视图样式。** 您可以使用以下任何一种样式：

![](https://developer.apple.com/ios/human-interface-guidelines/images/fullScreen_modality_2x.png)

**全屏。** 覆盖整个屏幕。 用于可以在模态视图的上下文中完成的潜在复杂任务。


![](https://developer.apple.com/ios/human-interface-guidelines/images/pageSheet_modality_2x.png)

**单页面**部分涵盖了以横向为主的大型设备的底层内容。 所有未覆盖的区域变暗，以防止与它们的相互作用。 在较小的设备上以纵向方向覆盖整个屏幕。 用于可以在模态视图的上下文中完成的潜在复杂任务。


![](https://developer.apple.com/ios/human-interface-guidelines/images/formSheet_modality_2x.png)

**表单。**以屏幕为中心，但如果键盘可见，则可能会重新定位。 所有未覆盖的区域变暗，以防止与它们的相互作用。 在较小的设备上可能会覆盖整个屏幕。 用于收集信息。


![](https://developer.apple.com/ios/human-interface-guidelines/images/currentContext_modality_2x.png)

**当前上下文。**显示为与其父视图相同的大小。 用于在分割视图窗格，弹出框或非全屏的其他视图中显示模态内容。


**选择适当的过渡风格来显示模态视图。**使用与您的应用程序协调的过渡风格，并提高临时上下文转换的意识。默认的转换从屏幕底部向上垂直滑动模态视图，并且一旦关闭就会退回。翻转式转换似乎是水平翻转视图以显示模态视图。视觉上，模态视图看起来像当前视图的背面。一旦关闭，它就会翻转。 在您的应用程序中使用一致的模态转换样式。

有关模态视图的开发人员指导，请参阅 [UIViewController](https://developer.apple.com/reference/uikit/uiviewcontroller) 和 [UIPresentationController](https://developer.apple.com/reference/uikit/uipresentationcontroller) 。
