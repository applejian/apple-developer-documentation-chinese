# 属性和数据类型的命名

这个部分介绍了声明的属性、实例变量、常量、通知和异常。

## 声明的属性和实例变量

属性的声明实际上是声明属性的读写方法，所以声明属性的命名约定大体上和读写方法的命名约定相同(参见[读写方法](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-1004202))。如果属性是一个名词或者动词，格式是：

`@property (…) type nounOrVerb;`

例如：

`@property (strong) NSString *title;`  
`@property (assign) BOOL showsAlpha;`

如果声明属性是一个形容词，然而需要注意的是，属性名忽略掉“is”前缀，但是指定约定的get读取方法名，例如：

`@property (assign, getter=isEditable) BOOL editable;`

大多数情况下，当你使用一个声明的属性的时候，你同样需要 synthesize 一个相对应的实例变量。

确保实例变量的名字简明的描述存储的属性。通常情况下，你不能直接访问实例变量；而是要通过读写方法来访问（你可以在init和dealloc方法中直接访问实例变量）。为了更加显著，可以采用下划线来命名实例变量，例如：

    @implementation MyClass {
    BOOL _showsTitle;
    }

如果你通过使用一个声明属性来synthesize一个实例变量的话，在@synthesize语句中指定实例变量的名字。

    @implementation MyClass
    @synthesize showsTitle=_showsTitle;
    
当向类中添加实例变量的时候，需要考虑以下几点：

+ 避免直接声明公共的实例变量。开发者应当关注的是对象的接口，而不是如何存储数据的细节。你可以通过使用声明属性以及synthesize相关的实例变量。  
+ 如果你需要声明一个实例变量，避免用 @private 或者 @protected来声明。如果你想在子类中直接访问数据，可以使用@protected。  
+ 如果一个实例变量是一个类实例的可访问属性，确保你给他写了读写方法（如果可能，请使用声明属性）。

## 常量

常量的命名规则与这个常量如何创建的有关。

### 枚举常量

+ 对于有整型常量的组来说，我们可以用枚举。

+ 枚举常量和类型定义组的命名约定遵循函数的命名（参见[函数的命名](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingFunctions.html#//apple_ref/doc/uid/20001283-BAJGGCAD)）。以下例子来自 NSMatrix.h：

<pre><code>typedef enum _NSMatrixMode {
    NSRadioModeMatrix           = 0,
    NSHighlightModeMatrix       = 1,
    NSListModeMatrix            = 2,
    NSTrackModeMatrix           = 3
} NSMatrixMode;
</code></pre>

注意类型定义的标签（例如上面的_NSMatrixMode）是不需要的。

+ 你可以创建一个诸如位掩码的没有名字的枚举类型。例如：

<pre><code>enum {
    NSBorderlessWindowMask      = 0,
    NSTitledWindowMask          = 1 << 0,
    NSClosableWindowMask        = 1 << 1,
    NSMiniaturizableWindowMask  = 1 << 2,
    NSResizableWindowMask       = 1 << 3
 
};
</pre></code>

### 通过const创建的常量

+ 通过const创建浮点型值的常量。如果你的整型常量与其它常量无关的话，你可以使用const创建一个整型的值；否则请使用枚举类型。
+ 下面是一个const常量的命名格式的例子：

<pre><code>const float NSLightGray;</pre></code>

如同常量枚举一样，对于函数的命名约定也是一样的（参见[函数命名](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingFunctions.html#//apple_ref/doc/uid/20001283-BAJGGCAD)）。

### 其它类型的常量

+ 一般来说，不要使用#define预处理器命令来创建常量。对于整型常量，请使用枚举。对于浮点型常量，请使用const修饰符。

+ 可以用大写符号做标记，这样预处理器就可以判断代码是否需要被处理。例如：

<pre><code>#ifdef DEBUG</pre></code>

+ 注意，由编译器定义的宏在头部和尾部有双下划线。例如：

<pre><code>__MACH__</pre></code>

+ 对于通知名和字典键，我们可以定义字符串常量。通过字符串常量，你可以确保编译器检验指定的正确的值（是指执行拼写检查）Cocoa框架提供许多字符串常量的例子，例如：

<pre><code>APPKIT_EXTERN NSString *NSPrintCopies;</pre></code>

实际上，NSString的值是赋值给一个实现文件中的常量的。（请注意，在Objective-C中，APPKIT_EXTERN宏是全局变量。）

### 通知和异常

通知和异常的命名约定遵守同样的规则。但是又有他们自己推荐的使用规则。

#### 通知

如果一个类有一个代理，大多数的通知有可能通过代理中定义的代理方法来接收的。这些通知的名字应当显示相关的代码方法。例如，一个全局的 `NSApplication`代理对象自动注册接收一个`applicationDidBecomeActive:` 的消息，当application任何时候发送一个`NSApplicationDidBecomeActiveNotification`。

通知是通过全局的NSString对象来标识的，以以下方式来组合名字：

<pre><code>[Name of associated class] + [Did | Will] + [UniquePartOfName] + Notification</pre></code>

例如：

<pre><code>NSApplicationDidBecomeActiveNotification
NSWindowDidMiniaturizeNotification
NSTextViewDidChangeSelectionNotification
NSColorPanelColorDidChangeNotification
</pre></code>

#### 异常

尽管你可以选择任意意图来使用异常（就是说NSException类和相关函数提供的机制）但是Cocoa保留一些编程错误的异常，例如：数组索引越界异常。Cocoa不实用异常来处理普通的、可预料的异常。对于这种情况，会使用诸如nil、NULL、NO或者其他错误代码的返回值。更多细节，请参见 [Error Handling Programming Guide](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/ErrorHandlingCocoa/ErrorHandling/ErrorHandling.html#//apple_ref/doc/uid/TP40001806).   

异常是通过全局的NSString对象来标识的，以以下方式来组合名字：

<pre><code>[Prefix] + [UniquePartOfName] + Exception</pre></code>

名字唯一的部分，应当将组合的名字连在一起，并且每个单词的首字母大写，以下是一些例子：

<pre><code>NSColorListIOException
NSColorListNotEditableException
NSDraggingException
NSFontUnavailableException
NSIllegalSelectorException</pre></code>








