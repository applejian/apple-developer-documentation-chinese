# 关于核心蓝牙


核心蓝牙框架给你的 iOS 和 Mac 应用与装备了蓝牙低功耗无线技术的设备通信提供了相关的类。例如，你的应用可以发现、扫描以及可以与低功耗外围设备交互，例如心率显示器和数字温控器。从 OS X v10.9 和 iOS 6 之后的系统，Mac 和 iOS 设备同样可以作为蓝牙低功耗外围设备，给其他设备提供数据，包括其他 Mac 和 iOS 设备。

![](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/CoreBluetooth_concepts/Art/CBTechnologyFramework_2x.png)

## 快速预览


蓝牙低功耗无线技术是基于蓝牙 4.0 规范，此外，还定义了低功耗设备之间的通信协议。核心蓝牙框架是蓝牙低功耗协议栈抽象化。也就是说，它为你隐藏了很多规范的底层细节，对于开发者来说，你可以更容易的开发与蓝牙低功耗设备交互的应用。

### 中心设备和外围设备是核心蓝牙的核心成员

在蓝牙低功耗通信中，有两个核心成员，中心设备和外围设备。每一个成员都有不同的角色。外围设备通常有其他设备需要的数据。中心设备通常使用外围设备提供的信息来完成某些任务。例如配备蓝牙低功耗技术的温控计可以将房间中的温度信息提供给 iOS 应用，然后以一种用户友好的方式来显示。


Each player performs a different set of tasks when carrying out its role. Peripherals make their presence known by advertising the data they have over the air. Centrals scan for nearby peripherals that might have data they’re interested in. When a central discovers such a peripheral, the central requests to connect to the peripheral and begins exploring and interacting with the peripheral’s data. The peripheral is responsible for responding to the central in appropriate ways.

Relevant Chapters: Core Bluetooth Overview
