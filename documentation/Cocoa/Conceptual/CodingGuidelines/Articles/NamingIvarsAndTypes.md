# Naming Properties and Data Types  
# 属性和数据类型的命名

This section describes the naming conventions for declared properties, instance variables, constants, notifications, and exceptions.  
这个部分介绍了声明的属性、实例变量、常量、通知和异常。

## Declared Properties and Instance Variables  
## 声明的属性和实例变量

A declared property effectively declares accessor methods for a property, and so conventions for naming a declared property are broadly the same as those for naming accessor methods (see [Accessor Methods](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-1004202)). If the property is expressed as a noun or a verb, the format is:  
属性的声明实际上是声明属性的读写方法，所以声明属性的命名约定大体上和读写方法的命名约定相同(参见[读写方法](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-1004202))。如果属性是一个名词或者动词，格式是：

`@property (…) type nounOrVerb;`

For example:  
例如：

`@property (strong) NSString *title;`  
`@property (assign) BOOL showsAlpha;`

If the name of a declared property is expressed as an adjective, however, the property name omits the “is” prefix but specifies the conventional name for the get accessor, for example:  
如果声明属性是一个形容词，然而需要注意的是，属性名忽略掉“is”前缀，但是指定约定的get读取方法名，例如：

`@property (assign, getter=isEditable) BOOL editable;`

In many cases, when you use a declared property you also synthesize a corresponding instance variable.  
大多数情况下，当你使用一个声明的属性的时候，你同样需要 synthesize 一个相对应的实例变量。

Make sure the name of the instance variable concisely describes the attribute stored. Usually, you should not access instance variables directly; instead you should use accessor methods (you do access instance variables directly in init and dealloc methods). To help to signal this, prefix instance variable names with an underscore (_), for example:  
确保实例变量的名字简明的描述存储的属性。通常情况下，你不能直接访问实例变量；而是要通过读写方法来访问（你可以在init和dealloc方法中直接访问实例变量）。为了更加显著，可以采用下划线来命名实例变量，例如：

    @implementation MyClass {
    BOOL _showsTitle;
    }

If you synthesize the instance variable using a declared property, specify the name of the instance variable in the @synthesize statement.  
如果你通过使用一个声明属性来synthesize一个实例变量的话，在@synthesize语句中指定实例变量的名字。

    @implementation MyClass
    @synthesize showsTitle=_showsTitle;
    
There are a few considerations to keep in mind when adding instance variables to a class:  
当向类中添加实例变量的时候，需要考虑以下几点：

+ Avoid explicitly declaring public instance variables.Developers should concern themselves with an object’s interface, not with the details of how it stores its data. You can avoid declaring instance variables explicitly by using declared properties and synthesizing the corresponding instance variable.  
+ 避免直接声明公共的实例变量。开发者应当关注的是对象的接口，而不是如何存储数据的细节。你可以通过使用声明属性以及synthesize相关的实例变量。  
+ If you need to declare an instance variable, explicitly declare it with either @private or @protected.If you expect that your class will be subclassed, and that these subclasses will require direct access to the data, use the @protected directive.  
+ 如果你需要声明一个实例变量，避免用 @private 或者 @protected来声明。如果你想在子类中直接访问数据，可以使用@protected。  
+ If an instance variable is to be an accessible attribute of instances of the class, make sure you write accessor methods for it (when possible, use declared properties).  
+ 如果一个实例变量是一个类实例的可访问属性，确保你给他写了读写方法（如果可能，请使用声明属性）。

## Constants  
## 常量

The rules for constants vary according to how the constant is created.  
常量的命名规则与这个常量如何创建的有关。

### Enumerated constants  
### 枚举常量

+ Use enumerations for groups of related constants that have integer values.  
+ 对于有整型常量的组来说，我们可以用枚举。

+ Enumerated constants and the typedef under which they are grouped follow the naming conventions for functions (see [Naming Functions](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingFunctions.html#//apple_ref/doc/uid/20001283-BAJGGCAD)). The following example comes from NSMatrix.h :  
+ 枚举常量和类型定义组的命名约定遵循函数的命名（参见[函数的命名](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingFunctions.html#//apple_ref/doc/uid/20001283-BAJGGCAD)）。以下例子来自 NSMatrix.h：

<pre><code>typedef enum _NSMatrixMode {
    NSRadioModeMatrix           = 0,
    NSHighlightModeMatrix       = 1,
    NSListModeMatrix            = 2,
    NSTrackModeMatrix           = 3
} NSMatrixMode;
</code></pre>

Note that the typedef tag (_NSMatrixMode in the above example) is unnecessary.  
注意类型定义的标签（例如上面的_NSMatrixMode）是不需要的。

+ You can create unnamed enumerations for things like bit masks, for example:  
+ 你可以创建一个诸如位掩码的没有名字的枚举类型。例如：

<pre><code>enum {
    NSBorderlessWindowMask      = 0,
    NSTitledWindowMask          = 1 << 0,
    NSClosableWindowMask        = 1 << 1,
    NSMiniaturizableWindowMask  = 1 << 2,
    NSResizableWindowMask       = 1 << 3
 
};
</pre></code>

### Constants created with const   
### 通过const创建的常量

+ Use const to create constants for floating point values. You can use const to create an integer constant if the constant is unrelated to other constants; otherwise, use enumeration.  
+ 通过const创建浮点型值的常量。如果你的整型常量与其它常量无关的话，你可以使用const创建一个整型的值；否则请使用枚举类型。
+ The format for const constants is exemplified by the following declaration:  
+ 下面是一个const常量的命名格式的例子：

<pre><code>const float NSLightGray;</pre></code>

As with enumerated constants, the naming conventions are the same as for functions (see [Naming Functions](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingFunctions.html#//apple_ref/doc/uid/20001283-BAJGGCAD)).  
如同常量枚举一样，对于函数的命名约定也是一样的（参见[函数命名](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingFunctions.html#//apple_ref/doc/uid/20001283-BAJGGCAD)）。

### Other types of constants  
### 其它类型的常量

+ In general, don’t use the #define preprocessor command to create constants. For integer constants, use enumerations, and for floating point constants use the const qualifier, as described above.  
+ 一般来说，不要使用#define预处理器命令来创建常量。对于整型常量，请使用枚举。对于浮点型常量，请使用const修饰符。

+ Use uppercase letters for symbols that the preprocessor evaluates in determining whether a block of code will be processed. For example:  
+ 可以用大写符号做标记，这样预处理器就可以判断代码是否需要被处理。例如：

<pre><code>#ifdef DEBUG</pre></code>

+ Note that macros defined by the compiler have leading and trailing double underscore characters. For example:  
+ 注意，由编译器定义的宏在头部和尾部有双下划线。例如：

<pre><code>__MACH__</pre></code>

+ Define constants for strings used for such purposes as notification names and dictionary keys. By using string constants, you are ensuring that the compiler verifies the proper value is specified (that is, it performs spell checking). The Cocoa  frameworks provide many examples of string constants, such as:  
+ 对于通知名和字典键，我们可以定义字符串常量。通过字符串常量，你可以确保编译器检验指定的正确的值（是指执行拼写检查）Cocoa框架提供许多字符串常量的例子，例如：

<pre><code>APPKIT_EXTERN NSString *NSPrintCopies;</pre></code>

The actual NSString value is assigned to the constant in an implementation file. (Note that the APPKIT_EXTERN macro evaluates to extern for Objective-C.)  
实际上，NSString的值是赋值给一个实现文件中的常量的。（请注意，在Objective-C中，APPKIT_EXTERN宏是全局变量。）

### Notifications and Exceptions  
### 通知和异常

The names for notifications and exceptions follow similar rules. But both have their own recommended usage patterns.  
通知和异常的命名约定遵守同样的规则。但是又有他们自己推荐的使用规则。

#### Notifications
#### 通知

If a class has a delegate, most of its notifications will probably be received by the delegate through a defined delegate method. The names of these notifications should reflect the corresponding delegate method. For example, a delegate of the global `NSApplication` object is automatically registered to receive an `applicationDidBecomeActive:` message whenever the application posts an `NSApplicationDidBecomeActiveNotification`.  
如果一个类有一个代理，大多数的通知有可能通过代理中定义的代理方法来接收的。这些通知的名字应当显示相关的代码方法。例如，一个全局的 `NSApplication`代理对象自动注册接收一个`applicationDidBecomeActive:` 的消息，当application任何时候发送一个`NSApplicationDidBecomeActiveNotification`。

Notifications are identified by global NSString objects whose names are composed in this way:  
通知是通过全局的NSString对象来标识的，以以下方式来组合名字：

<pre><code>[Name of associated class] + [Did | Will] + [UniquePartOfName] + Notification</pre></code>

For example:  
例如：

<pre><code>NSApplicationDidBecomeActiveNotification
NSWindowDidMiniaturizeNotification
NSTextViewDidChangeSelectionNotification
NSColorPanelColorDidChangeNotification
</pre></code>

#### Exceptions  
#### 异常

Although you are free to use exceptions (that is, the mechanisms offered by the NSException class and related functions) for any purpose you choose, Cocoa reserves exceptions for programming errors such an array index being out of bounds. Cocoa does not use exceptions to handle regular, expected error conditions. For these cases, use returned values such as nil, NULL, NO, or error codes. For more details, see [Error Handling Programming Guide](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/ErrorHandlingCocoa/ErrorHandling/ErrorHandling.html#//apple_ref/doc/uid/TP40001806).  
尽管你可以选择任意意图来使用异常（就是说NSException类和相关函数提供的机制）但是Cocoa保留一些编程错误的异常，例如：数组索引越界异常。Cocoa不实用异常来处理普通的、可预料的异常。对于这种情况，会使用诸如nil、NULL、NO或者其他错误代码的返回值。更多细节，请参见 [Error Handling Programming Guide](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/ErrorHandlingCocoa/ErrorHandling/ErrorHandling.html#//apple_ref/doc/uid/TP40001806).   

Exceptions are identified by global NSString objects whose names are composed in this way:  
异常是通过全局的NSString对象来标识的，以以下方式来组合名字：

<pre><code>[Prefix] + [UniquePartOfName] + Exception</pre></code>

The unique part of the name should run constituent words together and capitalize the first letter of each word. Here are some examples:  
名字唯一的部分，应当将组合的名字连在一起，并且每个单词的首字母大写，以下是一些例子：

<pre><code>NSColorListIOException
NSColorListNotEditableException
NSDraggingException
NSFontUnavailableException
NSIllegalSelectorException</pre></code>








