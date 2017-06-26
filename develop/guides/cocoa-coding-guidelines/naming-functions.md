# 函数的命名

Objective-C 允许你通过函数来实现和方法一样的功能。当潜在的对象总是一个单例或者当你要处理明显的功能性的子系统，你可以使用函数，而不是类中的方法。

有以下一些一般的函数命名规则你需要遵循：

+ 函数的命名格式有点类似方法的命名，但是有一些例外：

函数名以你使用的类或者常量前缀开始。  
前缀后面的第一个单词首字母大写。

+ 大多数的函数名以动词打头，用来表示这个函数的作用：

`NSHighlightRect`  
`NSDeallocateObject`

如果这个函数是用来查询属性的话，还有一套其它的规则：

+ 如果你的函数返回的是第一个参数的属性，请忽略掉动词。

`unsigned int NSEventMaskFromType(NSEventType type)`  
`float NSHeight(NSRect aRect)`

+ 如果返回的是引用类型，请使用“Get”。

`const char *NSGetSizeAndAlignment(const char *typePtr, unsigned int *sizep, unsigned int *alignp)`

+ 如果返回的是布尔类型，函数应该以一个变化动词打头。

`BOOL NSDecimalIsNotANumber(const NSDecimal *decimal)`