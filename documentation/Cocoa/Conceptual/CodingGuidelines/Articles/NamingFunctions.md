# Naming Functions  
# 函数的命名

Objective-C allows you to express behavior through functions as well as methods. You should use functions rather than, say, class methods, when the underlying object is always a singleton or when you are dealing with obviously functional subsystems.  
Objective-C 允许你通过函数来实现和方法一样的功能。当潜在的对象总是一个单例或者当你要处理明显的功能性的子系统，你可以使用函数，而不是类中的方法。

Functions have some general naming rules that you should follow:  
有以下一些一般的函数命名规则你需要遵循：

+ Function names are formed like method names, but with a couple exceptions:  
+ 函数的命名格式有点类似方法的命名，但是有一些例外：

They start with the same prefix that you use for classes and constants.  
The first letter of the word after the prefix is capitalized.  
函数名以你使用的类或者常量前缀开始。  
前缀后面的第一个单词首字母大写。

+ Most function names start with verbs that describe the effect the function has:  
+ 大多数的函数名以动词打头，用来表示这个函数的作用：

`NSHighlightRect`  
`NSDeallocateObject`

Functions that query properties have a further set of naming rules:  
如果这个函数是用来查询属性的话，还有一套其它的规则：

+  If the function returns the property of its first argument, omit the verb.  
+ 如果你的函数返回的是第一个参数的属性，请忽略掉动词。

`unsigned int NSEventMaskFromType(NSEventType type)`  
`float NSHeight(NSRect aRect)`

+ If the value is returned by reference, use “Get”.  
+ 如果返回的是引用类型，请使用“Get”。

`const char *NSGetSizeAndAlignment(const char *typePtr, unsigned int *sizep, unsigned int *alignp)`

+ If the value returned is a boolean, the function should begin with an inflected verb.  
+ 如果返回的是布尔类型，函数应该以一个变化动词打头。

`BOOL NSDecimalIsNotANumber(const NSDecimal *decimal)`