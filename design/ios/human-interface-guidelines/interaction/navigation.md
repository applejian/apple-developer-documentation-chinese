## 导航

人们似乎没意识到应用内的导航，直到它导航得不如人们的所预想的那般。你将以一种支持结构化且不带任何刻意调用导航的方式来实现导航。导航应该是令人感觉自然且熟悉的，而不应该从内容上主宰接口元素或刻画的焦点。在 iOS ,导航有三种主要风格。

**分层式导航**。 在到达一个界面之前决定是否应该那么做。为了到另外一个界面，你必须折回或者从头开始做不同的决定。设置和邮件使用的就是这种导航的风格。
![](https://developer.apple.com/ios/human-interface-guidelines/images/NavigationHierarchical-Graphic_2x.png)

**扁平式导航**。 可在两个内容类别不同的界面之间进行切换。Music 和 App Store 使用的就是这种导航模式。

![](https://developer.apple.com/ios/human-interface-guidelines/images/NavigationFlat-Graphic_2x.png)

**内容驱动和体验驱动式导航**。更加自由在内容上进行移动或是内容上自己定义了导航。Games ，books，以及其他沉浸式的应用大多都使用了这种导航的样式。

![](https://developer.apple.com/ios/human-interface-guidelines/images/NavigationExperienceDriven-Graphic_2x.png)

很多应用结合了多种导航样式。例如一个应用使用了扁平导航可能实现分层导航在每一个类别里面。

**一直提供一个清晰的路径**。人们应该知道具体自己处于应用中的哪个位置，以及如何到达下一个目的地。不顾导航的样式，贯穿内容的路径是合乎逻辑的、可预测的且容易跟踪的，这点很重要。总体来说，提供给人到每一个界面的路径。如果他们需要一个界面再多个上下文中，考虑使用 Action Sheets、警告视图、弹出视图、或者模态视图。更多请咨询 [Action Sheets](https://developer.apple.com/ios/human-interface-guidelines/ui-views/action-sheets/), [警告视图](https://developer.apple.com/ios/human-interface-guidelines/ui-views/alerts/), [弹出视图](https://developer.apple.com/ios/human-interface-guidelines/ui-views/popovers/),和 [模态视图](https://developer.apple.com/ios/human-interface-guidelines/interaction/modality/).

**设计一个快速并容易的切合主题的信息结构**。组织你的信息结构在一种需要在屏幕上进行少量的点击、侧滑和界面。

**使用触摸手势创建流利性**。通过最少量的摩擦，使得导航在交互元素中贯穿更加容易。例如，可以让人从屏幕的一侧侧滑返回到上一个界面。

**使用基本的导航元素**。在可能的情况下。使用基础导航原始控制器比如分页控制，标签条（Tab bar），分段控制，列表视图，集合视图，以及分割视图。用户早已经熟悉了这些控制并直观的知道如何在应用内应对它们。

**使用导航条横穿同级数据**。导航条的标题能显示当前层级的位置，并且返回按钮使得它很方便的返回上一个位置。更多的详细的简绍，见[导航条](https://developer.apple.com/ios/human-interface-guidelines/ui-bars/navigation-bars/)。

**使用标签条功能性的呈现同等类别分内的内容**。一个标签条使得人们快速并容易的在每一个类别中进行切换，且不顾及当前的位置。更多关于标签条信息，请查看[标签条（Tab bars）](https://developer.apple.com/ios/human-interface-guidelines/ui-bars/tab-bars/)

**当你有多页相同类型的内容时使用分页控制**。分页控制清晰的阐述了有多少页，且哪一页处于活动状态。天气应用使用了分页控制来展示特定位置的天气页。更多相关内容，请查看[分页控制](https://developer.apple.com/ios/human-interface-guidelines/ui-controls/page-controls/)。

**特别提示**

分段控制和工具条的导航不可用。使用分段控制来组织信息到不同的类别当中。使用工具条来为和当前上下文进行交互并提供控制。更多额外信息，请查看[分段控制](https://developer.apple.com/ios/human-interface-guidelines/ui-controls/segmented-controls/)和[工具条](https://developer.apple.com/ios/human-interface-guidelines/ui-bars/toolbars/)。

