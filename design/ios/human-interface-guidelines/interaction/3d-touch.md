
#3D Touch

3D Touch 补充了一种基于触摸式的交互方式。在支持 3D Touch 设备上，人们可以通过对触摸屏施加不同级别的压力，来获得额外的功能。应用可以响应诸如菜单显示、展示额外内容、或者播放一个动画。人们并不需要针对 3D Touch 来学习新的交互手势。当他们轻按屏幕得到响应时，他们会很快发现这个新增的交互方式。

##主屏幕的交互


On the Home screen, pressing the icon of an app that supports 3D Touch displays an action view. This view lets you quickly perform common app-specific tasks and see interesting information. Calendar, for example, provides a shortcut for creating an event. It also shows the next event on your schedule. For design guidance, see Home Screen Actions and Widgets.

在主屏幕上，按下一个支持 3D Touch 的应用图标就会显示一个可操作的视图。这个视图能让你快速的执行指令来完成程序特定的任务和查看你感兴趣的信息。例如日历，提供了能快速的创建一个行程的快捷方式。同时也可以在你的日程安排表上显示下一个行程。对于设计指南，详细内容请参见[主屏幕操作](https://developer.apple.com/ios/human-interface-guidelines/extensions/home-screen-actions/)和[窗口](https://developer.apple.com/ios/human-interface-guidelines/extensions/widgets/)。

##Peek 和 Pop

Peek 让人们使用3D Touch预览项目，如网页，链接，或文件，在这个视图上会短暂的出现在当前的上下文上。
要查看支持此功能的项目，只需用手指向该项目轻轻一按。手指抬起时候退出 Peek。为了打开项目并且查看更多的详情，稍微用力按下，直到该内容弹出并且铺满整个屏幕。在某些 Peek 视图，你可以通过向上滑动出现相关操作按钮。例如，当查看 Safari 中的一个链接，你可以通过向上轻扫，则会出现用于后台打开链接的按钮，添加并拷贝该链接到你的阅读清单。

**使用 Peek 来提供新富内容的实时预览。**理想情况下，Peek 交互会提供足够多的信息，用于当前新增任务，或者用于帮助你决定是否完全参与项目。例如，在决定是是否将当前邮件信息中的链接在 Safari 中打开或者分享给好友之前，进行一个预览。在表视图中，Peek 交互经常被用来在单行被选择之前，向用户展示行内容详情。

**设计足够大的 Peek 视图。**设计一个足够大的 Peek 视图，这样手指就不会掩盖内容。让人们根据足够详细的 Peek 来决定是否按的更用力，来完全打开（弹出）项目。

Adopt Peek and Pop consistently. If you support Peek and Pop in some places but not others, people won’t know where they can use the feature and may think there’s a problem with your app or their device.

**Peek 和 Pop 的使用，请保持一致性。**如果你在某些地方支持 Peek 和 Pop，在某些地方不支持，人们不知道那些地方可以使用，他们就会认为是他们的设备或者你的应用出了问题。

**为每一个 Peek 提供 Pop 功能。**???

Avoid displaying button-like elements in a peek view. If a user lifts a finger to tap an element that looks like a button, the peek disappears.

**在 Peek 视图中，避免视图内的元素设计的像一个按钮。**用户往往很想点击看起来像按钮的元素，这样手指离开了屏幕，Peek 视图会消失。

**不要呢针对同一个条目，既启用 Peek 交互，又提供编辑功能。** 它可能会使使用者混淆，并且使得系统很难判断用户的意图，当一个项目启用了这两个特性时。额外的详细指导，请参见[编辑菜单](https://developer.apple.com/ios/human-interface-guidelines/ui-controls/edit-menus/)。

**适当时提供操作按钮。**不是每个 Peek 都需要动作按钮，但它们恰恰是针对常见任务提供快捷方式的一个很好的方法。 如果你的应用程序已经为操作项目提供了自定义触摸方式，同时再使用 Peek 交互，是一个良好的习惯。

**避免给一个已经。**为了打开一个peek项目，人们通常会按的重一点，结果通常不需要为他们提供明显的打开按钮。

不要把使用Peek作为项目具体行动的唯一方法。并非每个设备都支持Peek视图和Pop视图，有些用户也许会关闭3D触控功能。所以你的应用在这种情况下，应该提供其它方式来触发项目具体行动。例如，你的应用可以提供类似于在项目中触发和点击Peek视图中一样的快捷操作






