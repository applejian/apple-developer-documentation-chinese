
# 设置
有一些应用可能一开始就需要让用户进行设置或者配置选择，但是大部分应用都会避免或者延迟这么做。成功的应用能够一开始就让用户很好地使用，同时提供了一个方便的方式去调整体验。当你的应用被设计成满足大部分用户的需求，你就可以减少他们对设置的需要。   

 **推断你可以从系统中得到什么。** 如果你需要知道关于用户、设备或是环境的信息，尽可能的向系统请求来代替向用户的询问。例如，可以向用户请求获取他们的当前位置来提供本地的选项，而不是要求用户输入他们的邮政编码。    

 **在你的应用程序中优先考虑配置选项。** 你应用的主屏是一个放置关键或是常用选项的绝佳位置。次要的屏幕更适合放置只偶尔才更改的选项。    

 **适当时提供去设置的快捷方式。** 如果你的应用包含引导用户去设置的文本，如“去设置>我的应用>隐私>定位服务”，提供一个自动打开定位设置界面的按钮。想了解如何实现这个行为，请参阅 [UIApplication](https://developer.apple.com/reference/uikit/uiapplication) 中的 [Settings Launch URL](https://developer.apple.com/reference/uikit/uiapplication/settings_launch_url) 部分。        

 **在系统设置中放置不经常更改的配置选项。** 系统设置应用是更改系统配置的核心地带，但是人们必须离开你的应用才能到达那里。而在你的应用中直接更改设置更加方便。如果你的应用必须提供很少改动的设置选项，请参阅 [Preferences and Settings Programming Guide](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/UserDefaults/Introduction/Introduction.html) 中的 [Implementing an iOS Settings Bundle](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/UserDefaults/Preferences/Preferences.html) 部分。
