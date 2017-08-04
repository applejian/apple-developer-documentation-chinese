# Quartz Composer 基本概念

Quartz Composer 是  OS X v10.5 提供的用来处理和渲染图解数据的开发工具。他的可视化编程环境适合以下情况：

+ 无需一行代码即可开发图像处理模块。

+ 无需专门针对相关技术学习编程接口，从而从容的探索在 OS X 已有的可视化技术。

在 OS X v10.5 中安装系统提供的开发者工具之后，你可以从以下路径找到 Quartz Composer 开发工具：

`/Developer/Applications`

Quartz Composer 带来了一整套丰富的图解和非图解的技术，包括 Quartz 2D，核心图像，核心适配，OpenGL，QuickTime，MIDI 系统服务，RSS (真正简单整合) 和 XML 等。

这章阐述了你需要了解的 Quartz Composer 的基本概念。定义了基本元素（组成与快），阐述了组成中的数据流，举例说明了坐标系，介绍了组成仓库。

## 组成

你可以使用 Quartz Composer 编辑器来创建 Quartz 组成，这是通过在数据处理和渲染的工作流中组装预先存在的模块（称为块）来创建的运动图形程序。图 1-1 展示的是一个简单的组成。

图 1-1 Quartz 组成

![](https://developer.apple.com/library/content/documentation/GraphicsImaging/Conceptual/QuartzComposerUserGuide/art/patch_title_colors.jpg)



组成可以处理有输入参数和处理输出结果。图 1-1 中通过组成产生的输出是一个旋转的立方体，立方体的表面展示的是连接到电脑上的相机拍摄的视频（参见图 1-2）。


图 1-2 通过组合产生的动态图形

![](https://developer.apple.com/library/content/documentation/GraphicsImaging/Conceptual/QuartzComposerUserGuide/art/live_video.jpg)

组合可以自主操作，但是针对任何 Mac 应用都可以与组合通信并且将组合集成到现有的工作流中。（更多细节请参见《Quartz Composer 编程指南》中关于应用集成组合的细节。）组合存储为以 `.qtz` 为文件后缀的  Quartz Composer 文件。

## 块

Quartz Composer 的基本元素是块。和传统的编程语言的程序类似，块是基本处理单元。他们执行并且产生一个结果。块相当于：

`结果 = 功能 (时间, {0 or 多个输入参数)`

不像传统的程序，块是添加到可视编程环境中的可视的实体（参见图 1-3）。块中的圆圈表示端口，左侧圆圈表示输入端口，右侧圆圈表示输出端口。端口通过他们来传输数据-你可以将端口当做参数。

图 1-3

![](https://developer.apple.com/library/content/documentation/GraphicsImaging/Conceptual/QuartzComposerUserGuide/art/sample_patches.jpg)

和程序类似，并不是所有的块都需要输入参数。图 1-3 展示的是三个块中的端口可以具备不同的配置。低频率振荡器（LFO）块同时有输入和输出端口。类型，周期，相，振幅，偏移量和 PWM 比，提供用来计算振荡器在指定时间的振幅。计算得到的振幅值可以在块的输出端口得到。

图片导入器和 Quartz Composer 信息块没有任何的输入端口，但是每一个都有一个输出端口。图片导入器产生图片，Quartz Composer 信息块产生指定的运行在系统中的 Quartz Composer 版本值。精灵块，有很多输入端口，但是没有输出端口。而精灵块将其结果呈现到目的地。端口之间的连接定义了组成运行时数据流。

