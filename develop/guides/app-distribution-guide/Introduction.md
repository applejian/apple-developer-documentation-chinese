
# APP发布指南

此指南包含所有在 App Store 或 Mac App Store 上发布应用所有的内容。
 
+ 针对 Apple Developer Program 的登记以及构建、测试和提交你的应用的逐步引导。
+ 对仅提交到 App Store 或 Mac App Store 的应用配置可用服务。
+ 在多设备和多系统版本上测试你的应用，以及提供给测试人员你下一个发布版本的预览。
+ 上传你应用的元数据，以便 Store 可以呈献给客户。
+  验证你已经正确的准备好你的应用，并且提交到 Store。
+ 学习在提交应用之后如何发布和维护你的应用。

![](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Art/1_administration_tasks_2x.png "Apple App Enroll Develop Distribute Workflow")

你可以通过Xcode特性和一些可用的Web工具来执行以上任务，当然，这仅针对于 Apple Developer Program 成员。在你使用某一应用服务之前，例如 iCloud 和 Game Center 之前，你必须加入一个 Apple Developer Program。即使你在Store之外发布一个应用，也需要加入一个 Program，因为这样可以让客户知道你的应用的来源。

*备注：如果你想要使用 Xcode 在设备上运行应用或者通过服务来写代码，请先阅读[App Distribution Quick Start](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013839)，然后返回到这个文档来处理那些在你的应用的整个生命周期都需要处理的额外的工作。*

## 概览

此指南说明了如何开发、测试、提交和发布你的iOS和Mac应用。通过理解你的工具和发布流程，你会更快的获取和更新你的应用。

### 登记 Apple Developer Program 并发布你的应用。

加入 Apple Developer Program 是在 Apple Store 和 Mac App Store 上提交你的应用，以及发布iOS内部应用和你通过一个开发者ID来签名你要在 Mac App Store外发布的应用的第一步。作为一个成员，你有权访问你需要配置应用服务和提交新的应用和更新的资源。

**相关章节**：[账号管理](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW1)

### 给你的APP添加服务

Apple为某一类型的应用提供了高级和集成的服务，例如游戏应用和报摊应用，还有诸如应用内购买和 iAd 网络服务的额外收入来源。在开发的过程中还有当你将你的应用提交到App Store或Mac App Store时，这些应用服务需要额外的配置。比较好的例子就是 Game Center 和 iCloud。你将会了解如何添加这些功能到你的应用中。

**相关章节**：[添加功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html#//apple_ref/doc/uid/TP40012582-CH26-SW1), [配置推送通知](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringPushNotifications/ConfiguringPushNotifications.html#//apple_ref/doc/uid/TP40012582-CH32-SW1)

### 应用发布准备

在你进行应用发布测试或者提交你的应用到商店审批之前，你需要完成你Xcode工程的配置。你的最终Xcode工程需要包含必要的应用图标和启动图片，包含你启用的应用服务的额外授权，以及指定你的应用支持哪种设备和操作系统。

**相关章节**：[发布需要配置你的Xcode项目](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)

### 在大量设备上测试iOS应用
 
如果你有iOS应用，确保你不仅在iOS模拟器上测试，而且还要在你的应用支持的所有的设备和版本上测试。在超过一款设备上测试，可以确保你的应用像你想象的一样正常运行，而不用管在哪一台设备上运行。一个年会员最多可以注册100个设备用来开发和测试。你自己测试完应用之后，发布一个beta版本的引用给你的测试者。你可以自己发布一个beta的应用，或者使用iTunes Connect来管理beta测试。对于通过TestFlight和App store发布的iOS应用来说，Apple提供了手机和统计崩溃日志的服务，你可以通过Xcode来下载和分析。
  
**相关章节**：[iOS应用beta测试](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/TestingYouriOSApp/TestingYouriOSApp.html#//apple_ref/doc/uid/TP40012582-CH8-SW1)，[崩溃报告分析](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AnalyzingCrashReports/AnalyzingCrashReports.html#//apple_ref/doc/uid/TP40012582-CH21-SW1)

### 将你的应用提交和发布到App store上

将你的应用提交到App Store或者 Mac App Store上是一个多步操作流程。首先，你需要注册到iTunes Connect，然后创建一个应用记录然后输入必要的信息。如果你打算在App store上出售你的应用，你还需要在iTunes Connect中输入你的偿付信息。你在Xcode里面将你的应用打包并且通过发布证书来签名。然后你通过Xcode或者Application Loader来上传你的应用。通过iTunes Connect 来将你的应用提交到App store上。当你的应用被审核通过了之后，可以通过iTunes来设置发布日期。

**相关章节**: [将你的应用提交到Store](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SubmittingYourApp/SubmittingYourApp.html#//apple_ref/doc/uid/TP40012582-CH9-SW1), [发布和更新你Store上的应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ShippingandUpdatingYourApp/ShippingandUpdatingYourApp.html#//apple_ref/doc/uid/TP40012582-CH19-SW1), [在iTunes Connect 上管理你的应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/UsingiTunesConnect/UsingiTunesConnect.html#//apple_ref/doc/uid/TP40012582-CH22-SW3), [发布Apple Developer Enterprise Program应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1), [在Mac App Store以外发布应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingApplicationsOutside/DistributingApplicationsOutside.html#//apple_ref/doc/uid/TP40012582-CH12-SW2)  

### 在Store外发布你的应用

另外一个方法，就是加入Apple Developer Enterprise Program，然后可以直接向雇员发布企业内部应用。在Mac App store之外发布一个Mac应用，需要将你的应用用开发者ID证书签名。如果你准备在Store外发布你的应用，你需要遵循一个略微不同的流程。你不需要访问iTunes Connect，并且可以跳过一些应用服务。

Related Chapters: [Distributing Apple Developer Enterprise Program Applications](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1), [Distributing Applications Outside the Mac App Store](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingApplicationsOutside/DistributingApplicationsOutside.html#//apple_ref/doc/uid/TP40012582-CH12-SW2)  
Related Chapters: [发布Apple Developer Enterprise Program应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1), [在Mac App Store外发布应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingApplicationsOutside/DistributingApplicationsOutside.html#//apple_ref/doc/uid/TP40012582-CH12-SW2)

### Maintain Your Certificates, Identifiers, and Profiles  
### 维护你的 Certificate,Identifier,Profile文件

Apple implements an underlying security model to protect both user data and your app from being modified and distributed without your knowledge. Throughout the development process, you create assets and enter information that Apple uses to identify you, your devices, and your apps. Xcode automatically creates many certificates, identifiers, and profiles for you as you need them. Xcode maintains the App IDs and provisioning profiles it creates for you, but not the other assets. During your Developer Program membership, you may maintain various other certificates, identifiers, and profiles yourself.  
Apple实现了基础的安全模型，用来保护用户数据和防止你的应用在你未知的情况下被修改和发布。在开发过程中，Apple用你创建的资源和输入的信息来标识你，你的设备和你的应用。Xocde会自动的创建许多Certificate,Identifier,Profile文件供你使用。Xcode能够维护App ID和provision profile文件，但是不维护资源文件。在你作为Developer Program会员的时候，你需要管理各种不同的其他的Certificate,Identifier,Profile文件。

**Related Chapters**: [Maintaining Your Signing Identities and Certificates](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html#//apple_ref/doc/uid/TP40012582-CH31-SW1), [Maintaining Identifiers, Devices, and Profiles](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW1)  
**Related Chapters**: [管理你的Signing Identities and Certificates](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html#//apple_ref/doc/uid/TP40012582-CH31-SW1), [维护Identifiers, Devices, and Profiles 文件](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW1)  

### How to Use This Document  
### 如何使用这个文档

How you use this document depends on your Apple Developer Program membership and your role (team agent, admin, or member) in the program. For Mac apps, how you use this document also depends on whether you choose to submit your app to the Mac App Store or distribute it outside of the Mac App Store.  
如何使用这个文档，取决于你的Apple Developer Program会员和你在其中所处的角色(Team创建者，管理员或者成员)。对于Mac应用来说，你如何使用这个文档还取决于你选择提交你的应用到Mac App Store还是将它发布到Mac App Store之外。

First choose a type of account (individual or company) and a developer program. If needed, create an Apple ID and join a developer program, as described in [Managing Accounts](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW1). If you enroll in a developer program as an individual, you’re the team agent for a one-person team. If you enroll in a developer program as a company, you’re the team agent and can invite other people to join your team, as described in [Inviting Team Members](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW17). You specify whether a person is a team admin, who can perform most of the same tasks as a team agent, or a team member who can’t create assets in Member Center. To learn more about team roles, read [About Apple Developer Program Team Roles and Privileges](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW10).  
首先选择一个账号类型(个人还是企业)和一个开发者计划。如若必要，创建一个Apple ID并且加入一个开发者计划，就像在[管理账号](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW1)中描述的一样。如果你以个人身份加入开发者计划的话，你是单人Team的Team创建者。如果你以公司的身份假如开发者计划的话，你就是Team创建者，并且可以邀请其他人加入你的Team，就像在[邀请Team成员](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW17)里面描述的一样。你可以指定一个人为Team的管理员，这个人可以执行大多数Team创建者的任务，或者可以指定一个人作为Team成员，但是这个人不能在会员中心创建内容。如果你想了解更多关于team的规则，请参阅 [About Apple Developer Program Team Roles and Privileges](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW10)。

Then refer to the tables in this section for the tasks you perform depending on your role and developer program membership. (Refer to the glossary for the definitions of terms used in this guide.)

然后依据你的角色和开发者计划成员，参考这部分中的表格来执行你的任务。（参考这个指南中的条目定义的术语表。）

**If you’re a team agent or admin and want to submit your app to the App Store or Mac App Store:**  
**如果你是Team创建者或者管理员的话，你想要提交你的应用到App Store或者Mac App Store：**

| To learn how to        | Read
|-------------|-------------
|Add your Apple ID to Xcode|[Add your Apple ID to Xcode](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW2)
|Set your bundle ID and assign your project to a team| [Configuring Identity and Team Settings](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW2),[Configuring Your Xcode Project for Distribution](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)
|Configure app services|[Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html#//apple_ref/doc/uid/TP40012582-CH26-SW1)
|Launch your app on devices|[Launching Your App on Devices](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/LaunchingYourApponDevices/LaunchingYourApponDevices.html#//apple_ref/doc/uid/TP40012582-CH27-SW1)
|Perform final configuration steps before distributing your app|[Configuring Your Xcode Project for Distribution](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)
|Test your iOS app on different devices|[Beta Testing iOS Apps](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/TestingYouriOSApp/TestingYouriOSApp.html#//apple_ref/doc/uid/TP40012582-CH8-SW1)
|Fix problems during testing|[Analyzing Crash Reports](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AnalyzingCrashReports/AnalyzingCrashReports.html#//apple_ref/doc/uid/TP40012582-CH21-SW1)
|Upload your app to iTunes Connect for approval|[Submitting Your App to the Store](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SubmittingYourApp/SubmittingYourApp.html#//apple_ref/doc/uid/TP40012582-CH9-SW1)
|Release your app by setting the availability date|[Releasing and Updating Your App on the Store](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ShippingandUpdatingYourApp/ShippingandUpdatingYourApp.html#//apple_ref/doc/uid/TP40012582-CH19-SW1),[Managing Your App in iTunes Connect](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/UsingiTunesConnect/UsingiTunesConnect.html#//apple_ref/doc/uid/TP40012582-CH22-SW3)
|Maintain your Apple Developer Program assets|[Maintaining Your Signing Identities and Certificates](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html#//apple_ref/doc/uid/TP40012582-CH31-SW1),[Maintaining Identifiers, Devices, and Profiles](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW1)
|Fix issues with your code signing assets|[Troubleshooting](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Troubleshooting/Troubleshooting.html#//apple_ref/doc/uid/TP40012582-CH5-SW2)

| 如何使用       | 请阅读
|-------------|-------------
|在Xcode里面添加你的Apple ID|[在Xcode里面添加你的Apple ID](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW2)
|设置你的Bundle ID并且分配你的工程到一个组中| [配置Identity和Team设置](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW2),[发布应用之Xcode配置](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)
|配置APP服务|[添加功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html#//apple_ref/doc/uid/TP40012582-CH26-SW1)
|在设备上运行你的应用|[在设备上运行你的应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/LaunchingYourApponDevices/LaunchingYourApponDevices.html#//apple_ref/doc/uid/TP40012582-CH27-SW1)
|发布应用之前，需要执行的最后的配置步骤|[发布应用之前，Xcode工程配置](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)
|在不同设备上测试你的iOS应用|[iOS应用的Beta测试](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/TestingYouriOSApp/TestingYouriOSApp.html#//apple_ref/doc/uid/TP40012582-CH8-SW1)
|测试过程中的问题修复|[奔溃报告分析](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AnalyzingCrashReports/AnalyzingCrashReports.html#//apple_ref/doc/uid/TP40012582-CH21-SW1)
|将你的应用上传到iTunes Connect以获得审批通过|[向Store提交你的应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SubmittingYourApp/SubmittingYourApp.html#//apple_ref/doc/uid/TP40012582-CH9-SW1)
|设置你的应用发布时间|[发布和更新你Store上的应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ShippingandUpdatingYourApp/ShippingandUpdatingYourApp.html#//apple_ref/doc/uid/TP40012582-CH19-SW1),[在iTunes Connect中管理你的应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/UsingiTunesConnect/UsingiTunesConnect.html#//apple_ref/doc/uid/TP40012582-CH22-SW3)
|维护你Apple Developer Program的内容|[维护你的签名 Identities and Certificates](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html#//apple_ref/doc/uid/TP40012582-CH31-SW1),[维护 Identifiers, Devices, and Profiles](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW1)
|修复代码内容签名问题|[疑难解答](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Troubleshooting/Troubleshooting.html#//apple_ref/doc/uid/TP40012582-CH5-SW2)

**If you’re a team agent or admin for a company:**  
**如果你是一个企业Team的创建者或者管理员的话：**

|To learn how to|Read
|----------------------|--------
|Add team members and assign roles for company accounts|[Managing Your Team in Member Center](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW1)

| 如何使用       | 请阅读
|----------------------|--------
|在企业账号中添加Team成员和承担的角色|[Managing Your Team in Member Center](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW1)

**If you’re a team member for a company who is developing an app for the App Store or Mac App Store:**  
**如果你是一个企业的Team成员，为Mac App Store或者App Store开发应用的话：**

|To learn how to|Read
|----------------------|--------
|Add your Apple ID to Xcode|[Add your Apple ID to Xcode](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW2)
|Set your bundle ID and assign your project to a team| [Configuring Identity and Team Settings](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW2),[Configuring Your Xcode Project for Distribution](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)
|Request your development certificate and ask your team agent or admin to approve it|[Approving Development Certificates](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW4)
|Ask your team agent or admin to register your device|[Registering Team Member Devices](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW6)
|Launch your app on devices|[Launching Your App on Devices](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/LaunchingYourApponDevices/LaunchingYourApponDevices.html#//apple_ref/doc/uid/TP40012582-CH27-SW1)
|Fix issues with your code signing assets|[Troubleshooting](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Troubleshooting/Troubleshooting.html#//apple_ref/doc/uid/TP40012582-CH5-SW2)

| 如何使用       | 请阅读
|----------------------|--------
|在Xcode里面添加你的Apple ID|[在Xcode里面添加你的Apple ID](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW2)
|设置你的Bundle ID并且分配你的工程到一个组中| [配置Identity和Team设置](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW2),[发布应用之Xcode配置](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)
|请求你的开发证书，并且请求你的Team创建者或者管理员批准|[开发Certificates的审批](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW4)
|请求Team创建者或者管理员来注册你的设备|[Team成员的设备注册](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW6)
|在设备上运行你的应用|[在设备上运行你的应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/LaunchingYourApponDevices/LaunchingYourApponDevices.html#//apple_ref/doc/uid/TP40012582-CH27-SW1)
|修复代码内容签名问题|[疑难解答](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Troubleshooting/Troubleshooting.html#//apple_ref/doc/uid/TP40012582-CH5-SW2)

**If you’re a team agent or admin in the Apple Developer Enterprise Program:**  
**如果你是Apple Developer Enterprise Program(苹果开发者企业计划)的Team创建者或者管理员的话：**

|To learn how to|Read
|----------------------|--------
|Manage your certificates and distribute your app|[Distributing Apple Developer Enterprise Program Applications](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1)

| 如何使用       | 请阅读
|----------------------|--------
|证书的管理和应用的发布|[Apple Developer Enterprise Program(苹果开发者企业计划)应用的发布](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1)

**If you’re a team agent and want to distribute your Mac application outside of the Mac App Store:**  
**如果你是Team创建者，并且想要在Mac App Store之外发布你的Mac应用的话：**

|To learn how to|Read
|----------------------|--------
|Perform final configuration steps before distributing your app|[Configuring Your Xcode Project for Distribution](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)
|Create a Developer ID-signed application|[Distributing Applications Outside the Mac App Store](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingApplicationsOutside/DistributingApplicationsOutside.html#//apple_ref/doc/uid/TP40012582-CH12-SW2)
|Request additional Developer ID certificates|[Requesting Additional Developer ID Certificates](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html#//apple_ref/doc/uid/TP40012582-CH31-SW32)

| 如何使用       | 请阅读
|----------------------|--------
|发布你的应用之前需要执行的最后的配置步骤|[应用发布之前，配置你的Xcode工程](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)
|开发者ID签名的应用的创建|[在Mac App Store之前发布你的应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingApplicationsOutside/DistributingApplicationsOutside.html#//apple_ref/doc/uid/TP40012582-CH12-SW2)
|请求额外的开发者ID证书|[请求额外的开发者ID证书](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html#//apple_ref/doc/uid/TP40012582-CH31-SW32)

For Mac apps, if you select None as the distribution method, as described in [Choosing a Signing Identity (Mac Only)](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW45), you don’t need to read this guide.  
对于Mac应用，如果你在发布方法中选择无，在[选择一个签名的ID (仅Mac)](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW45)，你不需要阅读此指南。

### See Also  
### 同样参见

This guide assumes you are already familiar with the software and tools you use to write code. If not, start by reading a number of platform-specific tutorials. Next, read the technology overview documents followed by the appropriate human interface guidelines for your platform, and most important, the guidelines for submitting your app to the store.  
这份指南是假设你已经对你写代码用的软件和工具已经很熟悉的前提下。如果不是，首先你需要阅读一些特定平台教程。然后阅读合适你所处平台的人机交互指南的技术概述文档。最重要的就是向Store提交你的应用的指南。

||iOS|Mac
|----------------------|----------------------|----------------------
|To get started . . .|[Start Developing iOS Apps Today](https://developer.apple.com/library/ios/referencelibrary/GettingStarted/RoadMapiOS/index.html#//apple_ref/doc/uid/TP40011343),[App Distribution Quick Start](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013839)|Start Developing Mac Apps Today,[App Distribution Quick Start](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013839)
|To learn more about technologies . . .|[iOS Technology Overview](https://developer.apple.com/library/ios/documentation/Miscellaneous/Conceptual/iPhoneOSTechOverview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007898)[App Programming Guide for iOS](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007072)|Mac Technology Overview,Mac App Programming Guide
|To learn about the user interface guidelines . . .|[iOS Human Interface Guidelines](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/index.html#//apple_ref/doc/uid/TP40006556),[App Store Review Guidelines for iOS Apps](http://developer.apple.com/appstore/resources/approval/guidelines.html)|OS X Human Interface Guidelines,App Store Review Guidelines for Mac Apps
|To learn more about tools . . .|[Xcode Overview](https://developer.apple.com/library/ios/documentation/ToolsLanguages/Conceptual/Xcode_Overview/index.html#//apple_ref/doc/uid/TP40010215),[iTunes Connect Developer Guide](https://developer.apple.com/library/ios/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/About.html#//apple_ref/doc/uid/TP40011225),[iOS Simulator User Guide](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/iOS_Simulator_Guide/index.html#//apple_ref/doc/uid/TP40012848),[Using Application Loader](https://itunesconnect.apple.com/docs/UsingApplicationLoader.pdf)|[Xcode Overview](https://developer.apple.com/library/ios/documentation/ToolsLanguages/Conceptual/Xcode_Overview/index.html#//apple_ref/doc/uid/TP40010215),[iTunes Connect Developer Guide](https://developer.apple.com/library/ios/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/About.html#//apple_ref/doc/uid/TP40011225),[Using Application Loader](https://itunesconnect.apple.com/docs/UsingApplicationLoader.pdf)
|To learn about tools for large teams. . .|[Xcode Server and Continuous Integration Guide](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/xcode_guide-continuous_integration/index.html#//apple_ref/doc/uid/TP40013292),[Testing with Xcode](https://developer.apple.com/library/ios/documentation/DeveloperTools/Conceptual/testing_with_xcode/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014132),[Source Control Management Help](https://developer.apple.com/library/ios/recipes/xcode_help-source_control_management/_index.html#//apple_ref/doc/uid/TP40013353)|[Xcode Server and Continuous Integration Guide](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/xcode_guide-continuous_integration/index.html#//apple_ref/doc/uid/TP40013292),[Testing with Xcode](https://developer.apple.com/library/ios/documentation/DeveloperTools/Conceptual/testing_with_xcode/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014132),[Source Control Management Help](https://developer.apple.com/library/ios/recipes/xcode_help-source_control_management/_index.html#//apple_ref/doc/uid/TP40013353)

||iOS|Mac
|----------------------|----------------------|----------------------
|开端. . .|[今日开始开发iOS应用](https://developer.apple.com/library/ios/referencelibrary/GettingStarted/RoadMapiOS/index.html#//apple_ref/doc/uid/TP40011343),[应用发布快速入门](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013839)|[今日开始开发Mac应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013839)
|了解更多技术. . .|[iOS技术概述](https://developer.apple.com/library/ios/documentation/Miscellaneous/Conceptual/iPhoneOSTechOverview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007898)[iOS应用编程指南](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007072)|Mac技术概述,Mac应用编程指南
|了解关于用户交互指南 . . .|[iOS人机交互指南](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/index.html#//apple_ref/doc/uid/TP40006556),[iOS应用App Store审核指南](http://developer.apple.com/appstore/resources/approval/guidelines.html)|OS X 人机交互指南,Mac应用的App Store审核指南
|工具延伸. . .|[Xcode总览](https://developer.apple.com/library/ios/documentation/ToolsLanguages/Conceptual/Xcode_Overview/index.html#//apple_ref/doc/uid/TP40010215),[iTunes Connect开发者指南](https://developer.apple.com/library/ios/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/About.html#//apple_ref/doc/uid/TP40011225),[iOS模拟器的用户指南](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/iOS_Simulator_Guide/index.html#//apple_ref/doc/uid/TP40012848),[Application Loader的使用](https://itunesconnect.apple.com/docs/UsingApplicationLoader.pdf)|[Xcode总览](https://developer.apple.com/library/ios/documentation/ToolsLanguages/Conceptual/Xcode_Overview/index.html#//apple_ref/doc/uid/TP40010215),[iTunes Connect开发者指南](https://developer.apple.com/library/ios/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/About.html#//apple_ref/doc/uid/TP40011225),[Application Loader的使用](https://itunesconnect.apple.com/docs/UsingApplicationLoader.pdf)
|大型Team工具的使用. . .|[Xcode服务器和持续集成指南](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/xcode_guide-continuous_integration/index.html#//apple_ref/doc/uid/TP40013292),[用Xcode进行测试](https://developer.apple.com/library/ios/documentation/DeveloperTools/Conceptual/testing_with_xcode/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014132),[源代码版本管理帮助](https://developer.apple.com/library/ios/recipes/xcode_help-source_control_management/_index.html#//apple_ref/doc/uid/TP40013353)|[Xcode服务器和持续集成指南](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/xcode_guide-continuous_integration/index.html#//apple_ref/doc/uid/TP40013292),[用Xcode进行测试](https://developer.apple.com/library/ios/documentation/DeveloperTools/Conceptual/testing_with_xcode/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014132),[源代码版本管理帮助](https://developer.apple.com/library/ios/recipes/xcode_help-source_control_management/_index.html#//apple_ref/doc/uid/TP40013353)

更多关于应用审核流程，请参阅[应用审核](https://developer.apple.com/app-store/review/)。






































