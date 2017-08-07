## Bitcode  

Bitcode 是编译程序的中间表示形式，你上传到 iTunes Connect 里包含 bitcode 的应用将会在商店中进行编译和链接。包含 bitcode 的应用将允许苹果在将来重新优化你的应用二进制包，而无须将新版本的应用程序提交到应用商店。

默认情况下，Xcode 会隐藏在构建时生成的符号，因此它们不可读取。 只有当您将应用程序上传到 iTunes Connect 时选择包含符号，才能将符号发送给 Apple。 您必须包含符号以从 Apple 收到崩溃报告。

**注意：**对于 iOS 应用程序，bitcode 是默认的，但可选。 对于 watchOS 和 tvOS 应用程序，bitcode 是必须的。 如果您提供 bitcode，则应用程序包中的所有应用程序和框架（项目中的所有目标）都需要包含 bitcode。   
使用 iTunes Connect 发布应用程序后，您可以下载构建的 dSYMs 文件，[如在设备窗口查看和导入崩溃中所述](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/AnalyzingCrashReports/AnalyzingCrashReports.html#//apple_ref/doc/uid/TP40012582-CH21-SW3)。