

## 文件处理
人们不需要考虑文件系统在创建、阅览以及修改文件的时候。如果你的应用需要文件协同工作，应尽可能的忽略文件操作。

**逐渐形成一种观念，文件总是被保存起来的，除非它被取消了或者是被删除了**。通常情况下，不要特意的使人去保存文件。相反地，打开或关闭文件或者切换到其他应用时，自动的在一定时间间隔内段内自动保存修改。在许多情况下，你如当编辑已经存在的文件，保存和取消选项的存在对用户是否要保存编辑内容将是合乎情理的。

**不提供创建仅保存本地的接口选项**。用户总是期望他们所有的文件在他们的其他设备上都可用。任何时候，在可能的情况下，你的应用应该支持云端文件存储比如 iCloud.

**实现一个既有知觉又生动的浏览接口** 观念上，用户使用系统的文档选择器来浏览文档。如果你实现了一歌自定义文件浏览器，确信它是生动且有效的。文件浏览器在文件高效的绘制并呈现出来时会发挥出最好的状态。为了提高导航能力，最小化手势，考略到提供一个按钮，所以人们不需要到其他地方去创建文件。
![](https://developer.apple.com/ios/human-interface-guidelines/images/file_handling.png)

**让用户预览文件在没有离开你的应用的情况下**，你可以使用 Quick Look 让人们预览 Keynote 、Numbers 、 Page 文档，PDF、图片以及其他类型的文件 ,即使你的应用不真正的打开他们。见 [Quick Look](https://developer.apple.com/ios/human-interface-guidelines/features/quick-look/).


**在适当的时候和其他人分享文件**。如果有意思，你的应用通过一个 [文件提供推广](https://developer.apple.com/ios/human-interface-guidelines/extensions/document-providers/) 提和其他应用进行文件分享。你的应用同样可以打开浏览和打开别的应用的文件。更多的实现细节，请查看[Document Picker Programming Guide](https://developer.apple.com/library/content/documentation/FileManagement/Conceptual/DocumentPickerProgrammingGuide/Introduction/Introduction.html)。

