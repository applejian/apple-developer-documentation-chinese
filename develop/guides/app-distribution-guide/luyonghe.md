![](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/Art/app_thinning_2x.png)

在你的常规开发和发布工作流程期间被切分执行，通常如下进行:

1.在 Xcode 中，指定目标设备，并在资源管理目录中提供多种分辨率的图片。 <br /> 
为了资源被切分，你必须使用资源管理目录。

2.在模拟器或设备上构建并运行应用程序。 <br />
   Xcode 为所选择的设备类型构建应用安装包，改进调试构建时间，并允许你在测试本地安装包。

3.创建应用程序的存档，并为目标设备导出本地安装包 <br />
测试您在目标设备上导出的所有安装包，以便及早发现配置问题。

4.上传应用到 iTunes Connect 。 <br />
  商店从存档创建单独的应用程序安装包。安装包的大小取决于 Xcode 项目中指定的体系结构和资源。

5.在 iTunes Connect 中，将应用程序的预发行版本分发给指定的测试人员。 <br />
测试人员在支持的设备上使用 TestFlight 安装了预发布版本。TestFlight 为特定的用户设备下载了一款安装包。
   
     注意：要测试商店在将应用程序分发给用户之前构建的安装包，请仅邀请内部测试人员（您的团队的 iTunes Connect 用户），并使用 TestFlight 下载安装包。
     如果您邀请外部测试人员（仅指定其电子邮件地址的用户），外部测试人员必须等待 Beta App Review 批准该应用程序才能下载安装包。
 
6.在 iTunes Connect， 发布应用。 <br />
用户可以在支持的设备上安装该应用，商店应用会为特定的用户设备下载应用程序的安装包。
