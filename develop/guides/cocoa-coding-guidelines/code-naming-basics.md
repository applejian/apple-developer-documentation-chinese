# 基础的代码命名

对于面向对象软件库的设计，经常忽视的一点是类、方法、函数、常量以及其它编程接口元素的命名。本部分将会讨论对于大多数的Cocoa接口的一些通用的命名约定。

## 总则

简洁

+ 尽可能的简单、明了，但是过于简单，会偏离明了：

|代码 |评注
|-------------|-----------
|insertObject:atIndex:|不错。
|insert:at:|不明了; 插入了什么? “at”表示什么意思?
|removeObjectAtIndex:|不错。
|removeObject:|不错，因为这个方法表明了移除这个参数对象。
|remove:|不明了; 移除什么？

+ 一般来说，不要缩略事物的名字。使用全拼，即使单词比较长：

|代码|评注
|-------------|-----------
|destinationSelection|不错。
|destSel|不明了。
|setBackgroundColor:|不错。
|setBkgdColor:|不明了。

你可以能认为有些缩写比较有名，其实非你所料，尤其是当你的方法或者函数名遇到一个不同文化和语言的开发者。

*译者注：[ifeegoo](http://www.ifeegoo.com)，比如在中国，很多人IT行业人员都知道BAT表示Baidu，Alibaba，Tencent，但是歪果仁不一定知道滴。其实一个缩写词，在不同的语言环境，很有可能表示几十甚至上百种意思，有一个专门查询缩写词网站：[http://www.abbreviations.com/](http://www.abbreviations.com/)。我之前在做Android开发的时候，很喜欢用全拼，这样能够描述的很清楚，也不会让人产生歧义。那又有人说，既然这么推荐全拼，为什么C语言采用这种printf的命名呢？这是一个好的问题。这个在很大一个程度上是因为之前没有强大的IDE，只能靠程序员自己记忆方法名，如果说你记不完全的话，这个代码岂不是无法向下进行呢？*

+ 然而，少数缩写词确实常见，而且有很长的使用历史。你可以继续使用它们；可以参见[可接受的缩略词和首字母缩略词](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/APIAbbreviations.html#//apple_ref/doc/uid/20001285-BCIHCGAE)。

+ 避免模棱两可的API命名，例如具有多种解释的方法名。

|代码|评注
|-------------|-------------
|sendPort|是要发送还是需要返回端口？
|displayName|是需要显示一个名字还是需要返回一个UI的标题？

一致性

+ 在整个Cocoa编程接口中的命名保持一致性。如果你不太确定，请查看当前的头文件或者引用文档。

+ 当你一个类的方法需要利用到多态，这种情况下一致显得尤为重要。方法需要在不同的类中具有相同的作用，并且需要有相同的名字。

|代码|评注
|-------------|-------------
|- (NSInteger)tag|在NSView, NSCell, NSControl中定义。
|- (void)setStringValue:(NSString *)|在许多Cocoa类中定义。

参见[方法参数](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-1001865)。

无自引用

*译者注：[ifeegoo](http://www.ifeegoo.com) 无自引用的意思应该是指不能在当前命名中附带本身的属性，比如一个人叫张三，我们不要把他叫做张三人、人张三。*

+ 名字不能自引用。

|代码|评注
|-------------|-------------
|NSString|可以。
|NSStringObject|自引用。

|Code|Commentary
|-------------|-------------
|NSUnderlineByWordMask|Okay.
|NSTableViewColumnDidMoveNotification|Okay.

|代码|评注
|-------------|-------------
|NSUnderlineByWordMask|可以。
|NSTableViewColumnDidMoveNotification|可以。

## Prefixes  
## 前缀

在编程接口命名中，前缀是一个重要部分。这个是用来区分软件不同的功能范围。这样的不同的范围，通常是一个框架中的包或者（例如基础框架和应用包）相关的框架。前缀能够防止第三方开发者定义的内容与Apple定义的内容相冲突。

+ 前缀有规定的格式。它包含2-3个大写字母，并且不会使用下划线分割或者“子前缀”。下面有些例子：

|前缀|Cocoa框架
|-------------|-------------
|NS|Foundation
|NS|Application Kit
|AB|Address Book
|IB|Interface Builder

+ 在类、协议、函数、常量和定义结构体命名的时候，请使用前缀。不要在方法命名的时候使用前缀；方法是有通过类来定义的命名空间。同样，不要在结构体内的字段上使用前缀。

## 排版约定

在API元素命名的时候，请遵循一些简单的排版约定：

+ 对于由多个单词组成的命名，不要使用标点符号作为名字的一部分，或者作为分隔符（下划线、破折号等）；而且每个单词的首字母要大写，并且连在一起(例如，runTheWordsTogether)-这个被称为驼峰式命名法。然而，要注意以下限制：

对于方法的命名，请一小写字母大头，紧接着后面一个单词的首字母大写。不要使用前缀。

对于方法的命名有一个例外的地方就是以一个有名的首字母缩写词打头，例如NSImage的TIFFRepresentation方法。

对于函数和常量的命名，对于相关的类使用相同的前缀，并且紧接着后面的一个单词首字母大写。

`NSRunAlertPanel`  
`NSCellDisabled`

+ 避免使用下划线字符作为私有方法的命名前缀（对于使用下划线字符作为实例变量的命名前缀是允许的）。Apple保留这种约定的使用权。如果第三方使用，可能会导致命名空间的冲突；可能会在毫不知情的情况下覆盖了其中一个已经存在的私有方法，从而带来灾难性的后果。参见[私有方法](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-1003829)部分来获取对于私有API方法命名的约定建议。

## 类和协议的命名

类的命名中应当包含一个能够清楚的表明这个类（或者类的对象）是什么，或者是做什么的名词。这个名字需要有一个适当的前缀。Foundation框架和应用框架里面到处都是例子；例如： NSString, NSDate, NSScanner, NSApplication, UIApplication, NSButton, and UIButton。

协议应该依据组作用来命名：

+ 一般情况下，大多数协议组相关的方法与任何类都不相关。这种类型的协议应该在命名上与类区分开来。一个常见的约定就是使用动名词（“...ing”）格式：

|代码|评注
|-------------|-------------
|NSLocking|不错。
|NSLock|不是很好 (看起来像一个类的命名)。

+ 一些协议中包含多个不相关的方法(而不是创建多个单独的小的协议)。这些协议与类相关，这是协议最重要的表达方式。在这种情况下，我们约定，保持协议和类名相同的方式。

这种协议的例子就是NSObject协议。可以使用这个协议中的方法来查询任意类层级的对象的位置，可以调用指定方法，增加或减少它的引用数。因为类NSObject提供了这些方法的初始表达式，协议的命名在类名之后。

## 头文件

你如何命名头文件非常重要，因为约定中，你用它来显示这个文件包含的内容：

+ 声明一个单独的类或协议。如果一个类或协议不属于一个组的一部分，将它的声明放在一个单独的文件中，这个文件的名字是已经声明过的类或者协议。

|头文件|声明
|-------------|--------------
|NSLocale.h|NSLocale 类

+ 声明相关的类和协议。对于一个含有相关声明的组（类、分类和协议），将声明放在一个与初始类、分类或协议命名相关的文件中。

|头文件|声明
|-------------|--------------
|NSString.h|NSString和NSMutableString类。
|NSLock.h|NSLocking协议和NSLock, NSConditionLock, 以及 NSRecursiveLock 类。

+ 包含框架头文件。每一个框架应当有一个头文件，在框架后面命名，这个头文件应当包含所有的框架的公共头文件。

|头文件|声明
|-------------|--------------
|Foundation.h|Foundation.framework.

+ 在其它框架中添加API到一个类中。如果你想要在一个框架中中声明一个在其它框架中类的分类中的方法，请在原始类的命名后面追加“Additions”；一个典型的例子就是应用包中的NSBundleAdditions.h 头文件。

+ 相关的函数和数据类型。如果你有一组相关的函数、常量、结构体以及其它数据类型，可以将他们放在一个恰当命名的头文件中，例如 NSGraphics.h（应用包）。
























