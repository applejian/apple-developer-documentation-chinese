# Introduction to Coding Guidelines for Cocoa  
# Cocoa代码规范指南介绍

Developing a Cocoa framework, plug-in, or other executable with a public API requires some approaches and conventions that are different from those used in application development. The primary clients of your product are developers, and it is important that they are not mystified by your programmatic interface. This is where API naming conventions come in handy, for they help you to make your interfaces consistent and clear. There are also programming techniques that are special to—or of greater importance with—frameworks, such as versioning, binary compatibility, error-handling, and memory management. This topic includes information on both Cocoa naming conventions and recommended programming practices for frameworks.  
用公共API开发一个Cocoa框架、插件或者其他可执行程序，需要采取与那些应用开发不同的方法和约定。你产品的初始客户端是开发者，非常重要的一点就是不要让他们为你的编程接口感到困惑。以下便是API的命名约定，能够帮助你让你的接口保持一致和清晰，这些对于你来说，迟早排得上用场。同样还有比较特殊的针对更重要的与框架有关的编程技术，例如，版本标注、二进制兼容性、错误处理和内存管理。此篇文章同样包含Cocoa命名约定和推荐的框架编程实践。

## Organization of This Document  
## 文档结构

The articles contained in this topic fall into two general types. The first and larger group presents naming conventions for programmatic interfaces. These are the same conventions (with some minor exceptions) that Apple uses for its own Cocoa frameworks. These articles on naming conventions include the following:  
此主题包含的文章分为两种类型。第一个大的类型是编程接口的命名约定。这些约定和Apple在自己的Cocoa框架上使用的约定是一样的（少数除外）。这些关于命名约定的文章如下：

[Code Naming Basics](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-BBCHBFAH)  
[Naming Methods](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-BCIGIJJF)  
[Naming Functions](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingFunctions.html#//apple_ref/doc/uid/20001283-BAJGGCAD)  
[Naming Properties and Data Types](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingIvarsAndTypes.html#//apple_ref/doc/uid/20001284-BAJGIIJE)  
[Acceptable Abbreviations and Acronyms](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/APIAbbreviations.html#//apple_ref/doc/uid/20001285-BCIHCGAE)  
[基础的代码命名](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-BBCHBFAH)  
[方法命名](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-BCIGIJJF)  
[函数命名](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingFunctions.html#//apple_ref/doc/uid/20001283-BAJGGCAD)  
[属性和数据类型的命名](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingIvarsAndTypes.html#//apple_ref/doc/uid/20001284-BAJGIIJE)  
[可接受的缩略词和首字母缩略词](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/APIAbbreviations.html#//apple_ref/doc/uid/20001285-BCIHCGAE)  

The second group (currently with a membership of one) discusses aspects of framework programming:  
第二部分是关于框架编程方面的讨论：

Tips and Techniques for Framework Developers  
框架开发者的技巧和方法
















