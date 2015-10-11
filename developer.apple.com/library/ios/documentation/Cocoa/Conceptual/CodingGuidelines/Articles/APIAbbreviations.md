# Acceptable Abbreviations and Acronyms  
# 可接受的缩写词和首字母缩写词

In general, you shouldn’t abbreviate names when you design your programmatic interface (see [General Principles](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-1001751)). However, the abbreviations listed below are either well established or have been used in the past, and so you may continue to use them. There are a couple of additional things to note about abbreviations:  
一般来说，你在设计你的编程接口的时候，不应当缩写名字（参见[一般原则](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-1001751)）。然而，以下列举的缩写词已经创建并且在过去使用了很久，所以你可以继续使用他。这里有额外的两件事情需要注意：

+ Abbreviations that duplicate forms long used in the standard C library—for example, “alloc” and “getc”—are permitted.  
+ 简写格式和在标准的C库中长期使用的格式相同的，例如：“alloc”和“getc”是允许的。

+ You may use abbreviations more freely in argument names (for example, “imageRep”, “col” (for “column”), “obj”, and “otherWin”).  
+ 你在参数名中可以更加自由的使用简写（例如：imageRep”, “col” (“column”的简写), “obj”, 和 “otherWin”）。

|Abbreviation|Meaning and comments
|---|---
|alloc|Allocate.
|alt|Alternate.
|app|Application. For example, NSApp the global application object. However, “application” is spelled out in delegate methods, notifications, and so on.
|calc|Calculate.
|dealloc|Deallocate.
|func|Function.
|horiz|Horizontal.
|info|Information.
|init|Initialize (for methods that initialize new objects).
|int|Integer (in the context of a C int—for an NSInteger value, use integer).
|max|Maximum.
|min|Minimum.
|msg|Message.
|nib|Interface Builder archive.
|pboard|Pasteboard (but only in constants).
|rect|Rectangle.
|Rep|Representation (used in class name such as NSBitmapImageRep).
|temp|Temporary.
|vert|Vertical.

|缩写词|意思和评注
|---|---
|alloc|Allocate. 分配。
|alt|Alternate. 轮流的。
|app|Application. 应用。例如，全局的应用对象NSApp。然而在代理方法、通知等地方，还是用全拼“application”。
|calc|Calculate.计算。
|dealloc|Deallocate.重新分配。
|func|Function.函数。
|horiz|Horizontal.水平。
|info|Information.信息。
|init|Initialize.初始化。用于初始化对象方法中。
|int|Integer.整型。对于C来说，可以用int。对于NSInteger来说，用Integer。
|max|Maximum.最大。
|min|Minimum.最小。
|msg|Message.消息。
|nib|Interface Builder archive.界面生成器归档文件。
|pboard|Pasteboard 。剪贴板（仅在常量中使用）。
|rect|Rectangle.矩形。
|Rep|Representation .表现（在类名中使用，例如NSBitmapImageRep）。
|temp|Temporary.临时的。
|vert|Vertical.垂直的。

You may use abbreviations and acronyms that are common in the computer industry in place of the words they represent. Here are some of the better-known acronyms:  
你可以使用已经在计算机工业领域非常常见的缩写词和首字母大写词。以下是一些比较有名的缩写词：

ASCII
PDF
XML
HTML
URL
RTF
HTTP
TIFF
JPG
PNG
GIF
LZW
ROM
RGB
CMYK
MIDI
FTP
