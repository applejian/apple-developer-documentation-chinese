# 可接受的缩写词和首字母缩写词

一般来说，你在设计你的编程接口的时候，不应当缩写名字（参见[一般原则](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-1001751)）。然而，以下列举的缩写词已经创建并且在过去使用了很久，所以你可以继续使用他。这里有额外的两件事情需要注意：

+ 简写格式和在标准的C库中长期使用的格式相同的，例如：“alloc”和“getc”是允许的。

+ 你在参数名中可以更加自由的使用简写（例如：imageRep”, “col” (“column”的简写), “obj”, 和 “otherWin”）。

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
