# App Distribution Guide  
# APP发布指南

This guide contains everything you need to know to distribute an app through the App Store or Mac App Store.  
此指南包含所有在 App Store 或 Mac App Store 上发布应用所有的内容。

+ Get step-by-step guidance for enrolling in an Apple Developer Program and building, testing, and submitting your app.
+ Configure services that are available only to apps submitted to the App Store or Mac App Store.
+ Test your app on multiple devices and system versions, or offer testers a preview of your next release.
+ Upload metadata about your app so the store can present it to customers.
+ Verify that you’ve prepared your app correctly, and submit it to the store.
+ Learn how to release and maintain your app after submission.  
+ 针对 Apple Developer Program 的登记以及构建、测试和提交你的应用的逐步引导。
+ 对仅提交到 App Store 或 Mac App Store 的应用配置可用服务。
+ 在多设备和多系统版本上测试你的应用，以及提供给测试人员你下一个发布版本的预览。
+ 上传你应用的元数据，以便 Store 可以呈献给客户。
+  验证你已经正确的准备好你的应用，并且提交到 Store。
+ 学习在提交应用之后如何发布和维护你的应用。

![](https://raw.githubusercontent.com/ifeegoo/ifeegoo-developer-documentation-translation-chinese-ios/master/documentation/IDEs/Conceptual/AppDistributionGuide/Introduction/apple-app-enroll-develop-distribute-workflow.png "Apple App Enroll Develop Distribute Workflow")


You perform these tasks using Xcode features and several web tools available only to members of an Apple Developer Program. Before you use certain app services, such as iCloud and Game Center, you must join an Apple Developer Program. Join a program even if you distribute an application outside of the store so that customers know your application comes from a known source.  
你可以通过Xcode特性和一些可用的Web工具来执行以上任务，当然，这仅针对于 Apple Developer Program 成员。在你使用某一应用服务之前，例如 iCloud 和 Game Center 之前，你必须加入一个 Apple Developer Program。即使你在Store之外发布一个应用，也需要加入一个 Program，因为这样可以让客户知道你的应用的来源。

*Note: If you just want to use Xcode to run an app on a device or write code that uses a service, read [App Distribution Quick Start](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013839) first and then return to this document for additional tasks you’ll perform throughout the lifetime of your app.*   
*备注：如果你想要使用 Xcode 在设备上运行应用或者通过服务来写代码，请先阅读[App Distribution Quick Start](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013839)，然后返回到这个文档来处理那些在你的应用的整个生命周期都需要处理的额外的工作。*

## At a glance  
## 概览

This guide explains how to develop, test, submit, and release your iOS and Mac apps. By understanding your tools and the distribution process, you’ll be able to get your new app and updates to your customers faster.  
此指南说明了如何开发、测试、提交和发布你的iOS和Mac应用。通过理解你的工具和发布流程，你会更快的获取和更新你的应用。

### Enroll in an Apple Developer Program to Distribute Your App  
### 登记 Apple Developer Program 并发布你的应用。

Joining an Apple Developer Program is the first step to submit your apps on the App Store and Mac App Store, to distribute iOS in-house apps, or to sign apps that you distribute outside the Mac App Store with a Developer ID. As a member, you have access to the resources you need to configure app services and to submit new apps and updates.  
加入 Apple Developer Program 是在 Apple Store 和 Mac App Store 上提交你的应用，以及发布iOS内部应用和你通过一个开发者ID来签名你要在 Mac App Store外发布的应用的第一步。作为一个成员，你有权访问你需要配置应用服务和提交新的应用和更新的资源。

**Related Chapter**: [Managing Accounts](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW1)  
**相关章节**：[账号管理](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingAccounts/ManagingAccounts.html#//apple_ref/doc/uid/TP40012582-CH24-SW1)

### Add Services to Your App  
### 给你的APP添加服务

Apple provides advanced, integrated services for certain types of apps, such as games and Newsstand apps, and for additional sources of revenue, such as In-App Purchase and iAd Network. These app services require additional configuration—both during development and later, when you submit your app to the App Store or Mac App Store. Good examples are Game Center and iCloud. In this guide, you’ll learn how to add these capabilities to your app.  
Apple为某一类型的应用提供了高级和集成的服务，例如游戏应用和报摊应用，还有诸如应用内购买和 iAd 网络服务的额外收入来源。在开发的过程中还有当你将你的应用提交到App Store或Mac App Store时，这些应用服务需要额外的配置。比较好的例子就是 Game Center 和 iCloud。你将会了解如何添加这些功能到你的应用中。

**Related Chapter**: [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html#//apple_ref/doc/uid/TP40012582-CH26-SW1), [Configuring Push Notifications](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringPushNotifications/ConfiguringPushNotifications.html#//apple_ref/doc/uid/TP40012582-CH32-SW1)  
**相关章节**：[添加功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html#//apple_ref/doc/uid/TP40012582-CH26-SW1), [配置推送通知](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringPushNotifications/ConfiguringPushNotifications.html#//apple_ref/doc/uid/TP40012582-CH32-SW1)

### Prepare Your App for Distribution  
### 应用发布准备

Before you distribute your app for testing or submit it to the store for approval, complete the configuration of your Xcode project. Your final Xcode project should contain required app icons and launch images, contain additional entitlements for app services you enable, and specify which devices and operating systems your app supports.  
在你进行应用发布测试或者提交你的应用到商店审批之前，你需要完成你Xcode工程的配置。你的最终Xcode工程需要包含必要的应用图标和启动图片，包含你启用的应用服务的额外授权，以及指定你的应用支持哪种设备和操作系统。

**Related Chapter**: [Configuring Your Xcode Project for Distribution](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)   
**相关章节**：[发布需要配置你的Xcode项目](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ConfiguringYourApp/ConfiguringYourApp.html#//apple_ref/doc/uid/TP40012582-CH28-SW1)

### Test iOS Apps Across Numerous Devices  
### 在大量设备上测试iOS应用

If you have an iOS app, make sure you test it not only in iOS Simulator but on all the devices and releases that your app supports. Testing on more than one kind of device ensures that your app operates exactly as you thought it would, no matter which device it’s running on. You can register up to 100 devices per membership year for development and testing. After testing an app yourself, distribute a beta release of your app to testers. You can distribute a beta app yourself or use iTunes Connect to manage beta testing. For iOS apps distributed through TestFlight and the App Store, Apple provides a service that collects and aggregates crash logs that you can download and analyze in Xcode.  
如果你有iOS应用，确保你不仅在iOS模拟器上测试，而且还要在你的应用支持的所有的设备和版本上测试。在超过一款设备上测试，可以确保你的应用像你想象的一样正常运行，而不用管在哪一台设备上运行。一个年会员最多可以注册100个设备用来开发和测试。你自己测试完应用之后，发布一个beta版本的引用给你的测试者。你可以自己发布一个beta的应用，或者使用iTunes Connect来管理beta测试。对于通过TestFlight和App store发布的iOS应用来说，Apple提供了手机和统计崩溃日志的服务，你可以通过Xcode来下载和分析。

**Related Chapters**: [Beta Testing iOS Apps](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/TestingYouriOSApp/TestingYouriOSApp.html#//apple_ref/doc/uid/TP40012582-CH8-SW1), [Analyzing Crash Reports ](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AnalyzingCrashReports/AnalyzingCrashReports.html#//apple_ref/doc/uid/TP40012582-CH21-SW1)   
**相关章节**：[iOS应用beta测试](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/TestingYouriOSApp/TestingYouriOSApp.html#//apple_ref/doc/uid/TP40012582-CH8-SW1)，[崩溃报告分析](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AnalyzingCrashReports/AnalyzingCrashReports.html#//apple_ref/doc/uid/TP40012582-CH21-SW1)

### Submit and Release Your App on the Store  
### 将你的应用提交和发布到App store上

Submitting your app to the App Store or Mac App Store is a multistep process. First, you sign in to iTunes Connect to create an app record and enter necessary information. If you’re selling your app on the store, you also enter the information for your reimbursement in iTunes Connect. In Xcode, you create an archive and sign it with your distribution certificate. Then you upload your app using Xcode or Application Loader. Use iTunes Connect to submit your app to the store. When your app is approved, use iTunes Connect to release it by setting the date when the app will be available to customers.  
将你的应用提交到App Store或者 Mac App Store上是一个多步操作流程。首先，你需要注册到iTunes Connect，然后创建一个应用记录然后输入必要的信息。如果你打算在App store上出售你的应用，你还需要在iTunes Connect中输入你的偿付信息。你在Xcode里面将你的应用打包并且通过发布证书来签名。然后你通过Xcode或者Application Loader来上传你的应用。通过iTunes Connect 来将你的应用提交到App store上。当你的应用被审核通过了之后，可以通过iTunes来设置发布日期。

**Related Chapters**: [Submitting Your App to the Store](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SubmittingYourApp/SubmittingYourApp.html#//apple_ref/doc/uid/TP40012582-CH9-SW1), [Releasing and Updating Your App on the Store](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ShippingandUpdatingYourApp/ShippingandUpdatingYourApp.html#//apple_ref/doc/uid/TP40012582-CH19-SW1), [Managing Your App in iTunes Connect](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/UsingiTunesConnect/UsingiTunesConnect.html#//apple_ref/doc/uid/TP40012582-CH22-SW3), [Distributing Apple Developer Enterprise Program Applications](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1), [Distributing Applications Outside the Mac App Store](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingApplicationsOutside/DistributingApplicationsOutside.html#//apple_ref/doc/uid/TP40012582-CH12-SW2)  
**相关章节**: [将你的应用提交到Store](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SubmittingYourApp/SubmittingYourApp.html#//apple_ref/doc/uid/TP40012582-CH9-SW1), [发布和更新你Store上的应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/ShippingandUpdatingYourApp/ShippingandUpdatingYourApp.html#//apple_ref/doc/uid/TP40012582-CH19-SW1), [在iTunes Connect 上管理你的应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/UsingiTunesConnect/UsingiTunesConnect.html#//apple_ref/doc/uid/TP40012582-CH22-SW3), [发布Apple Developer Enterprise Program应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1), [在Mac App Store以外发布应用](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingApplicationsOutside/DistributingApplicationsOutside.html#//apple_ref/doc/uid/TP40012582-CH12-SW2)  

### Distribute Your App Outside the Store  
### 在Store外发布你的应用

Alternatively, join the Apple Developer Enterprise Program and distribute your in-house applications directly to employees. To distribute a Mac app outside of the Mac App Store, request and sign your application with a Developer ID certificate. If you’re distributing your application outside the store, you follow a slightly different process. You don’t have access to iTunes Connect and some app services so can skip those steps.  
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

First choose a type of account (individual or company) and a developer program. If needed, create an Apple ID and join a developer program, as described in Managing Accounts. If you enroll in a developer program as an individual, you’re the team agent for a one-person team. If you enroll in a developer program as a company, you’re the team agent and can invite other people to join your team, as described in Inviting Team Members. You specify whether a person is a team admin, who can perform most of the same tasks as a team agent, or a team member who can’t create assets in Member Center. To learn more about team roles, read About Apple Developer Program Team Roles and Privileges.  
首先选择一个账号类型(个人还是企业)和一个开发者计划。






























