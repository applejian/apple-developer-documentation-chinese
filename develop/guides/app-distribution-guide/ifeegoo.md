# 按需资源（iOS，tvOS）

按需资源是诸如图片和声音资源，这些资源可以通过关键词标记，并且可以通过标记按组请求的。应用商店将这些资源存储到 Apple 服务器，并为你管理这些内容的下载。按需资源可以实现更快的下载和更小的应用大小，提升初次启动的体验。例如，游戏应用可能会根据游戏等级来拆分资源，并且仅当应用预料到用户会到达这个等级的时候，才会请求下一个等级的资源。类似的，仅当用户有应用内购买的相关操作的时候，才去请求应用内购买的资源。

当按需资源不再需要或者磁盘空间低的时候，操作系统会清除这些资源。如果你想要在应用商店之外导出你的应用来测试或者发布的时候，你需要自己存储相关的按需资源。请注意：可执行的按需资源是不支持的。商店也会切分按需资源，如 [“切分（iOS，tvOS）”所述](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/AppThinning/AppThinning.html#//apple_ref/doc/uid/TP40012582-CH35-SW1)，进一步的提高用户体验。

对于用户来说，按需资源在后台透明的工作，当用户探索你应用的功能时，提供所需资源。

![](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/Art/on_demand_resources_2x.png)

要在你应用程序中设置按需资源，请阅读“[按需资源向导](https://developer.apple.com/library/content/documentation/FileManagement/Conceptual/On_Demand_Resources_Guide/index.html#//apple_ref/doc/uid/TP40015083)”和“ [NSBundleResourceRequest 类参考](https://developer.apple.com/documentation/foundation/nsbundleresourcerequest)”。

