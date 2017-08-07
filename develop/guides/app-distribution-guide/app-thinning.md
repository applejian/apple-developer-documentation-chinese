# 按需资源（iOS，tvOS）

按需资源是诸如图片和声音资源，这些资源可以通过关键词标记，并且可以通过标记按组请求的。应用商店将这些资源存储到 Apple 服务器，并为你管理这些内容的下载。按需资源可以实现更快的下载和更小的应用大小，提升初次启动的体验。例如，游戏应用可能会根据游戏等级来拆分资源，并且仅当应用预料到用户会到达这个等级的时候，才会请求下一个等级的资源。类似的，仅当用户有应用内购买的相关操作的时候，才去请求应用内购买的资源。

当按需资源不再需要或者磁盘空间低的时候，操作系统会清除这些资源。如果你想要在应用商店之外导出你的应用来测试或者发布的时候，你需要自己存储相关的按需资源。请注意：可执行的按需资源是不支持的。商店也会切分按需资源，如 [“切分（iOS，tvOS）”所述](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/AppThinning/AppThinning.html#//apple_ref/doc/uid/TP40012582-CH35-SW1)，进一步的提高用户体验。

对于用户来说，按需资源在后台透明的工作，当用户探索你应用的功能时，提供所需资源。

![](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/Art/on_demand_resources_2x.png)

要在你应用程序中设置按需资源，请阅读“[按需资源向导](https://developer.apple.com/library/content/documentation/FileManagement/Conceptual/On_Demand_Resources_Guide/index.html#//apple_ref/doc/uid/TP40015083)”和“ [NSBundleResourceRequest 类参考](https://developer.apple.com/documentation/foundation/nsbundleresourcerequest)”。

![](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/Art/app_thinning_2x.png)

在你的常规开发和发布工作流程期间被切分执行，通常如下进行:

1.在 Xcode 中，指定目标设备，并在资源管理目录中提供多种分辨率的图片。  
你必须使用资源管理目录，以便资源能够被切分。

2.在模拟器或设备上构建并运行应用程序。  
Xcode 为所选择的设备类型构建应用安装包，改进调试构建时间，并允许你在测试本地安装包。

3.创建应用程序的存档，并为目标设备导出本地安装包。  
测试您在目标设备上导出的所有安装包，以便及早发现配置问题。

4.上传应用到 iTunes Connect。  
商店从存档创建单独的应用程序安装包。安装包的大小取决于 Xcode 项目中指定的体系结构和资源。

5.在 iTunes Connect 中，将应用程序的预发行版本分发给指定的测试人员。  
测试人员在支持的设备上使用 TestFlight 安装了预发布版本。TestFlight 为特定的用户设备下载了一款安装包。

```
注意：要测试商店在将应用程序分发给用户之前构建的安装包，请仅邀请内部测试人员（您的团队的 iTunes Connect 用户），并使用 TestFlight 下载安装包。
如果您邀请外部测试人员（仅指定其电子邮件地址的用户），外部测试人员必须等待 Beta App Review 批准该应用程序才能下载安装包。
```
 
6.在 iTunes Connect，发布应用。  
用户可以在支持的设备上安装该应用，商店应用会为特定的用户设备下载应用程序的安装包。


## Bitcode  

Bitcode 是编译程序的中间表示形式，你上传到 iTunes Connect 里包含 bitcode 的的应用将会被编译和链接到商店。包含 bitcode 的应用将允许苹果重新优化你的应用二进制包，而无须将新版本的应用程序提交到应用商店。

默认情况下，Xcode 会隐藏在构建时生成的符号，因此它们不可读取。 只有当您将应用程序上传到 iTunes Connect 时选择包含符号，才能将符号发送给 Apple。 您必须包含符号以从 Apple 收到崩溃报告。

**注意：**对于iOS应用程序，bitcode 是默认的，但可选。 对于 watchOS 和 tvOS 应用程序，需要使用 bitcode 。 如果您提供 bitcode，则应用程序包中的所有应用程序和框架（项目中的所有目标）都需要包含 bitcode。   
使用 iTunes Connect 发布应用程序后，您可以下载“构建”的 dSYMs 文件，[如“设备窗口”中的“查看和导入崩溃”中所述](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/AnalyzingCrashReports/AnalyzingCrashReports.html#//apple_ref/doc/uid/TP40012582-CH21-SW3)。