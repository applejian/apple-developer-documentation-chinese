# 快速查看

在您的应用程序中，快速查看可让人们预览 Keynote、Numbers、Pages 和 PDF 文档，以及图像和其他类型的文件，即使您的应用程序不支持这些文件格式。邮件使用快速查看来查看附件。下载附件后，邮件会在消息中显示附件的图标和文件名。点击图标显示附件的预览。

![邮件](https://developer.apple.com/ios/human-interface-guidelines/images/QuickLook-Screen_2x.png)


**针对当前上下文适当地进行预览。** 在 iPhone 上，如果您的应用程序有导航栏，请将预览视图像应用程序的层次结构中的任何其他视图一样滑动到位。在 iPad 上，或者如果您的应用没有自己的导航栏，请在包含导航栏的全屏模式视图中打开预览。使用这两种方法，导航栏应包括用于退出快速查看的按钮，以及用于执行例如共享和标记等操作的预览专用按钮。如果您的应用程序包含工具栏，则任何预览专用按钮都会显示在此处，而不是导航栏中。

有关开发人员的指导，请参阅 [Document Interaction Programming Topics for iOS](https://developer.apple.com/library/content/documentation/FileManagement/Conceptual/DocumentInteraction_TopicsForIOS/Introduction/Introduction.html) 和 [Quick Look](https://developer.apple.com/documentation/quicklook) 。