# Tips and Techniques for Framework Developers  
# 框架开发者的技巧和小结

Developers of frameworks have to be more careful than other developers in how they write their code. Many client applications could link in their framework and, because of this wide exposure, any deficiencies in the framework might be magnified throughout a system. The following items discuss programming techniques you can adopt to ensure the efficiency and integrity of your framework.  
框架开发者应当比其他开发者在对待代码上面，应当更加小心。很多的客户端应用都会链接到他们的框架中，正是因为这样广泛的暴露，任何框架的缺陷，都会放大到整个系统。下面的内容讨论一些你可以采纳的编程技巧，用来确保你的框架的效率和集成。

***Note**: Some of these techniques are not limited to frameworks. You can productively apply them in application development.*  
***备注**: 一些技巧不仅仅局限于框架。你也可以应用到应用开发中。*

## Initialization  
## 初始化

The following suggestions and recommendations cover framework initialization.  
以下是包含了框架初始化的意见和建议。

### Class Initialization  
### 类初始化

The initialize  class method gives you a place to have some code executed once, lazily, before any other method of the class is invoked. It is typically used to set the version numbers of classes (see [Versioning and Compatibility](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/FrameworkImpl.html#//apple_ref/doc/uid/20001286-1001777)).  
初始化类方法给你一个可以在任何其它类的方法执行之前，执行一次代码。通常被用来设置类的版本号（参见[版本与兼容](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/FrameworkImpl.html#//apple_ref/doc/uid/20001286-1001777)）。

The runtime sends `initialize` to each class in an inheritance chain, even if it hasn’t implemented it; thus it might invoke a class’s initialize method more than once (if, for example, a subclass hasn’t implemented it). Typically you want the initialization code to be executed only once. One way to ensure this happens is to use `dispatch_once()`:  
运行时会给继承链中的每一个类发送初始化信息，及时没有实现它；所以类初始化方法可能不止被调用一次（例如，一个子类没有实现它）。通常情况下，你希望初始化代码仅执行一次。有一种方式可以确保这样，就是使用dispatch_once()：

<pre><code>+ (void)initialize {
    static dispatch_once_t onceToken = 0;
    dispatch_once(&onceToken, ^{
        // the initializing code
    }
}
</code></pre>

Note: Because the runtime sends initialize to every class, it's possible that `initialize` will be called in the context of a subclass—if the subclass doesn't implement `initialize`, then the invocation will fall through to the superclass. If you specifically need to perform initialization within the context of the relevant class, you can perform the following check rather than using `dispatch_once()`:  
备注：因为运行时会发送初始化给每一个类，很有可能`initialize`在子类的上下文环境中调用。如果子类没有实现`initialize`，然后这个调用会传到父类。如果你需要在相关的类的上下文中执行初始化，你可以用一下检查替代 `dispatch_once()`的使用会更好：

<pre><code>if (self == [NSFoo class]) {
    // the initializing code
}</code></pre>

You should never invoke the initialize method explicitly. If you need to trigger the initialization, invoke some harmless method, for example:  
绝不要显示的调用`initialize`方法。如果你想要触发初始化，调用一些无害的方法，例如：

`[NSImage self];`

### Designated Initializers  
### 指定的初始化器

A designated initializer is an `init` method of a class that invokes an `init` method of the superclass. (Other initializers invoke the init methods defined by the class.) Every public class should have one or more designated initializers. As examples of designated initializers there is `NSView`’s `initWithFrame:` and `NSResponder`’s `init` method. Where `init` methods are not meant to be overridden, as is the case with `NSString` and other abstract classes fronting class clusters, the subclass is expected to implement its own.  
指定的初始化器是一个类的实例方法，它会调用父类的初始化方法。（其它初始化器调用类定义的初始化方法）每一个公共类都需要有一个或者多个指定的初始化器。指定初始化器的一个例子有：`NSView`类的`initWithFrame:`和`NSResponder`的`init`方法。`init`方法并不意味着需要重写，比如`NSString`类和其它类集合中的抽象类，子类来自己实现。

Designated initializers should be clearly identified because this information is important to those who want to subclass your class. A subclass can just override the designated initializer and all other initializers will work as designed.  
指定的初始化器应当明确的指定，因为这对于想要依据你的类创建子类来说非常重要。子类仅重写指定的初始化器。

When you implement a class of a framework, you often have to implement its archiving methods as well: `initWithCoder:` and `encodeWithCoder:`. Be careful not to do things in the initialization code path that doesn’t happen when the object is unarchived. A good way to achieve this is to call a common routine from your designated initializers and `initWithCoder:` (which is a designated initializer itself) if your class implements archiving.  
当你要实现一个框架的类时，你经常需要也实现它的存档方法：`initWithCoder:` 和 `encodeWithCoder:`。注意不要当在对象解归档的时候，在初始化的代码中执行不会发生的事情。一个好的解决这个问题的方式就是，如果你的类实现了归档，可以从你指定的初始化器和`initWithCoder:`方法中实现一个普通的调用。

### Error Detection During Initialization  
### 初始化过程中的错误检测

A well-designed initialization method should complete the following steps to ensure the proper detection and propagation of errors:  
一个设计比较好的初始化方法应当通过完成以下几部来确保正确的检测和错误输出：

1.Reassign self by invoking super’s designated initializer.  
1.通过调用父类的指定初始化器来重新分配自己。  
2.Check the returned value for nil, which indicates that some error occurred in the superclass initialization.  
2.检查nil返回值，这个表明在父类初始化的过程中发生了错误。  
3.If an error occurs while initializing the current class, release the object and return nil.  
3.如果在初始化当前类对象的时候，发生错误，释放这个对象并返回nil。

Listing 1 illustrates how you might do this.  
列表 1 阐明了你可能会这样做。

Listing 1  Error detection during initialization
列表1 初始化过程中的错误检测

<pre><code>- (id)init {
    self = [super init];  // Call a designated initializer here.
    if (self != nil) {
        // Initialize object  ...
        if (someError) {
            [self release];
            self = nil;
        }
    }
    return self;
}</code></pre>

## Versioning and Compatibility  
## 版本和兼容性

When you add new classes or methods to your framework, it is not usually necessary to specify new version numbers for each new feature group. Developers typically perform (or should perform) Objective-C runtime checks such as `respondsToSelector:` to determine if a feature is available on a given system. These runtime tests are the preferred and most dynamic way to check for new features.  
当你向你的框架中添加新的类或者方法的时候，一般来说，没有必要给每一个新增的特性组都指定一个新的版本号。开发者通常会执行（或可能执行）Objective-C运行时检查，例如`respondsToSelector:`来检测对于一个给定的系统是有新特性。这些运行时测试是检查新特性时候所优先采取的大多数动态方式。

However, you can employ several techniques to make sure each new version of your framework are properly marked and made as compatible as possible with earlier versions.  
然而，你可以雇佣一些技术人员来确保你每一个框架的新版本被正确的标注了，尽可能的与早期的版本兼容。

### Framework Version  
### 框架版本

When the presence of a new feature or bug fix isn’t easily detectable with runtime tests, you should provide developers with some way to check for the change. One way to achieve this is to store the exact version number of the framework and make this number accessible to developers：  
当有一个新增特性或者bug被修复时，通过运行时测试是不容易检测出来的，你应当以某种方式告知开发者来检测这种变化。一种方式就是以归档的形式来存储框架的确切版本号，同时需要让开发者可见这些内容：

+ Document the change (in a release note, for instance) under a version number.  
+ 在每一个版本号下做文档记录变化（例如，在发布备注中）。
+ Set the current version number of your framework and provide some way to make it globally accessible. You might store the version number in your framework’s information property list (Info.plist) and access it from there.  
+ 设置你框架当前的版本号并且提供一些方式让它能够全局访问。你可以通过plist文件来存储你框架的版本号，然后可以通过这种方式来访问。

### Keyed Archiving  
### 归档关键

If the objects of your framework need to be written to nib file, they must be able to archive themselves. You also need to archive any documents that use the archiving mechanisms to store document data.  
如果你的框架对象需要写入nib文件，他们必须能够自归档。你同样需要通过使用归档机制存储文档数据来归档任何文档。

You should consider the following issues about archiving:  
你应当考虑以下关于归档方面的问题：

+ If a key is missing in an archive, asking for its value will return nil, NULL, NO, 0, or 0.0, depending on the type being asked for. Test for this return value to reduce the data that you write out. In addition, you can find out whether a key was written to the archive.  
+ 如果归档中的key丢失了，请求对应的值的话，将会返回nil、NULL、NO、0或0.0等，取决于请求的数据类型。通过判断这个返回值，可以减少你的数据输出。另外，你可以确认这个key有没有被写入归档。
+ Both the encode and decode methods can do things to ensure backwards compatibility. For instance, the encode method of a new version of a class might write new values using keys but can still write out older fields so that older versions of the class can still understand the object. In addition, decode methods might want to deal with missing values in some reasonable way to maintain some flexibility for future versions.
+ 编码和解码方法可以确保向后的兼容性。例如一个类的新版本的编码方法可能会通过使用key写入新的值，但是可能仍然返回旧的字段以便旧版本的类仍然知道这个对象。另外，解码方法想要通过一些可能的方式来处理丢失的值来保持新版本的灵活性。  
+ A recommended naming convention for archive keys for framework classes is to begin with the prefix used for other API elements of the framework and then use the name of the instance variable. Just make sure that names cannot conflict with the names of any superclass or subclass.  
+ 对于框架类的归档key的一个推荐的命名约定就是以针对于其他框架API元素的前缀并且使用实例变量的名字。这样确保命名不会和其他任何父类或子类的名字冲突。  
+ If you have a utility function that writes out a basic data type (in other words, a value that isn’t an object), be sure to use a unique key. For example, if you have an “archiveRect” routine that archives a rectangle should take a key argument, and either use that; or, if it writes out multiple values (for instance, four floats), it should append its own unique bits to the provided key.  
+ 如果你有一个工具函数输出一个基本的数据类型（换言之，这个值不是对象），确保使用一个唯一的key。例如，如果你有一个archiveRect程序来归档举行，需要传入key参数，你可以使用它。或者，如果它输出多个值（例如，四个浮点数据），应当在给定的key上追加自己唯一的位。
+ Archiving bitfields as-is can be dangerous due to compiler and endianness dependencies. You should archive them only when, for performance reasons, a lot of bits need to be written out, many times. See Bitfields for a suggestion.  
+ 按照原样来归档位字段是很危险的，因为这个和编译器以及字节顺序依赖有关。你仅能在对于优化的原因的情况下归档位字段，例如，需要大量多次的的位输出。参见位字段。

## Exceptions and Errors  
## 异常和错误

Most Cocoa framework methods do not force developers to catch and handle exceptions. That is because exceptions are not raised as a normal part of execution, and are not typically used to communicate expected runtime or user errors. Examples of these errors include:  
大多数Cocoa框架方法不强制开发者捕获和处理异常。那是引文异常作为执行的一个不同的部分，并不会增加，而且一般不会用在运行时的通信或者用户错误。这些错误的包括以下例子：  

+ File not found  
+ 文件没有找到  
+ No such user  
+ 没有此用户  
+ Attempt to open a wrong type of document in an application  
+ 在应用中试图打开一个错误的文档类型
+ Error in converting a string to a specified encoding  
+ 转换String到特定编码格式错误

However, Cocoa does raise exceptions to indicate programming or logic errors such as the following:  
然而，Cocoa对于以下情况会产生异常来指明程序或者逻辑错误：

+ Array index out of bounds  
+ 数组越界异常
+ Attempt to mutate immutable objects  
+ 尝试变化不可变的对象
+ Bad argument type  
+ 错误的参数类型

The expectation is that the developer will catch these kinds of errors during testing and address them before shipping the application; thus the application should not need to handle the exceptions at runtime. If an exception is raised and no part of the application catches it, the top-level default handler typically catches and reports the exception and execution then continues. Developers can choose to replace this default exception-catcher with one that gives more detail about what went wrong and offers the option to save data and quit the application.  
期望开发者在应用发布之前能够捕获这种类型的错误；所以应用不需要在运行时处理这些异常。如果一个异常往外扩散，应用没有捕获它，高级别的默认处理器通常会处理它，并且会报告异常，然后让它们继续执行。开发者可以选择用一个能够提供更多关于错误的信息，并且提供一个可选项来保存数据并且退出应用的默认异常捕获器来处理。

Errors are another area where Cocoa frameworks differ from some other software libraries. Cocoa methods generally do not return error codes. In cases where there is one reasonable or likely reason for an error, the methods rely on a simple test of a boolean or object (nil/non-nil) returned value; the reasons for a NO or nil returned value are documented. You should not use error codes to indicate programming errors to be handled at runtime, but instead raise exceptions or in some cases simply log the error without raising an exception.  
错误是处于Cocoa框架中的另外一个与其他一些软件开发库不同的区域。Cocoa方法一般不会返回错误代码。万一有错误的理由，这些方法依赖于一个简单的布尔或者对象（空/非空）返回值的简单测试；返回NO或者nil的原因是记录的。你不能在运行时使用错误代码来显示程序错误，但是有些情况下，你可以听哦你不敢过打印简单的错误信息而不用抛出异常。  

For instance, `NSDictionary`’s `objectForKey`: method either returns the found object or nil if it can’t find the object. NSArray’s objectAtIndex: method can never return nil (except for the overriding general language convention that any message to nil results in a nil return), because an NSArray object cannot store nil values, and by definition any out-of-bounds access is a programming error that should result in an exception. Many init methods return nil when the object cannot be initialized with the parameters supplied.  
例如，`NSDictionary`的`objectForKey: `方法返回发现的对象或者当没有发现返回对象的时候返回空。`NSArray`的`objectAtIndex: `方法不会返回nil（除非重写一般语言约定，将任何信息转换成nil，导致返回nil），因为一个NSArray对象不能存储nil值，并且通过定义任何越界方法是一个会导致异常的程序错误。许多初始化方法会因为通过提供的参数不能够初始化，从而导致返回nil。  

In the small number of cases where a method has a valid need for multiple distinct error codes, it should specify them in a by-reference argument that returns either an error code, a localized error string, or some other information describing the error. For example, you might want to return the error as an NSError object; look at the NSError.h header file in Foundation for details. This argument might be in addition to a simpler BOOL or nil that is directly returned. The method should also observe the convention that all by-reference arguments are optional and thus allow the sender to pass NULL for the error-code argument if they do not wish to know about the error.  
在少数情况下，一个方法有一个返回多个不同的错误代码，应当用引用参数来指定它，返回一个错误的代码，一个本地话的错误字符串，或者其他的描述错误的信息。例如，你肯能需要返回一个NSError对象来表示错误；可以查看框架中的NSError.h头文件来获取细节。这个参数一般来说是一个直接返回的BOOL或者nil。这个方法同样应当遵循引用参数是可选的并且允许将错误代码参数传入null，如果它们不期望知道这个错误。

## Framework Data  
## 框架数据

How you handle framework data has implications for performance, cross-platform compatibility, and other purposes. This section discusses techniques involving framework data.  
你如何处理框架数据会对性能，跨平台兼容性和其它方面有影响。这部分讨论涉及的框架数据的技巧。

### Constant Data  
### 常量数据

For performance reasons, it is good to mark as constant as much framework data as possible because doing so reduces the size of the __DATA segment of the Mach-O binary. Global and static data that is not const ends up in the __DATA section of the __DATA segment. This kind of data takes up memory in every running instance of an application that uses the framework. Although an extra 500 bytes (for example) might not seem so bad, it might cause an increment in the number of pages required—an additional four kilobytes per application.  
处于性能的考虑，尽可能的将常量数据作为框架数据，因为这样可以减少Mach-O二进制文件的__DATA段的大小。这种数据会在每一个使用这个框架应用的运行实例中占用内存。尽管额外的500字节（举个例子）看起来还好，但是它可能会导致页要求的数量的增加-每个应用有一个额外的4kB。

You should mark any data that is constant as const. If there are no char * pointers in the block, this will cause the data to land in the __TEXT segment (which makes it truly constant); otherwise it will stay in the __DATA segment but will not be written on (unless prebinding is not done or is violated by having to slide the binary at load time).  
你应当用const标记任何常量数据。如果在block中没有char指针，会导致数据处于 __TEXT段（这里会使之成为真正的常量）；否则的话，它处于__DATA段，但是却不能输出（除非预绑定没有完成或者通过在加载时二进制的偏移来改变它）。

You should initialize static variables to ensure that they are merged into the __data section of the __DATA segment as opposed to the __bss section. If there is no obvious value to use for initialization, use 0, NULL, 0.0, or whatever is appropriate.  
你应当初始化静态变量来确保他们被合并到__DATA段中的__data部分，而不是__bss部分。如果没有明显的值来初始化，请使用0,NULL,0.0或者其他任何恰当的值。

### Bitfields  
### 位段

Using signed values for bitfields, especially one-bit bitfields, can result in undefined behavior if code assumes the value is a boolean. One-bit bitfields should always be unsigned. Because the only values that can be stored in such a bitfield are 0 and -1 (depending on the compiler implementation), comparing this bitfield to 1 is false. For example, if you come across something like this in your code:  
针对位段请使用有符号的值，特别是一位的位段，这样会导致如果代码将这个值作为boolean值，会出现未定义行为。一位的位段应当使用无符号类型。因为单个位段能够存储的值，只是0和-1（取决于编译器的实现），对比这个位段，1是false。例如：如果你在代码中遇到这些：

<pre><code>BOOL isAttachment:1;
int startTracking:1;</code></pre>

You should change the type to unsigned int.  
你应当将类型改为无符号整型值。

Another issue with bitfields is archiving. In general, you shouldn’t write bitfields to disk or archives in the form they are in, as the format might be different when they are read again on another architecture, or on another compiler.  
另外一个和位段相关的内容是归档。一般来说，你不能以位段本身的格式来写入到磁盘或者归档中，因为当在另外一个架构或者其它编译器上读取的时候，格式可能不同。

### Memory Allocation  
### 内存分配

In framework code, the best course is to avoid allocating memory altogether, if you can help it. If you need a temporary buffer for some reason, it’s usually better to use the stack than to allocate a buffer. However, stack is limited in size (usually 512 kilobytes altogether), so the decision to use the stack depends on the function and the size of the buffer you need. Typically if the buffer size is 1000 bytes (or MAXPATHLEN) or less, using the stack is acceptable.  
在框架代码中，避免全部内存分配是最好的课程。如果在某种情况下，你需要一个临时的buffer，通常使用栈要好过于buffer的分配。然而，stack有大小限制（通常全部大小为512kb)，所以使用栈的这个决定取决于函数和你需要的buffer的大小。通常，如果buffer大小是1000bytes（或者MAXPATHLEN）或者更小，可以使用stack。

One refinement is to start off using the stack, but switch to a malloc’ed buffer if the size requirements go beyond the stack buffer size. Listing 2 presents a code snippet that does just that:  
一个改进就是使用stack开启偏移，但是如果大小超过了栈buffer大小，请切换到内存分配的buffer中。以下有例子：

<pre><code>#define STACKBUFSIZE (1000 / sizeof(YourElementType))
 YourElementType stackBuffer[STACKBUFSIZE];
 YourElementType *buf = stackBuffer;
 int capacity = STACKBUFSIZE;  // In terms of YourElementType
 int numElements = 0;  // In terms of YourElementType
 
while (1) {
    if (numElements > capacity) {  // Need more room
        int newCapacity = capacity * 2;  // Or whatever your growth algorithm is
        if (buf == stackBuffer) {  // Previously using stack; switch to allocated memory
            buf = malloc(newCapacity * sizeof(YourElementType));
            memmove(buf, stackBuffer, capacity * sizeof(YourElementType));
        } else {  // Was already using malloc; simply realloc
            buf = realloc(buf, newCapacity * sizeof(YourElementType));
        }
        capacity = newCapacity;
    }
    // ... use buf; increment numElements ...
  }
  // ...
  if (buf != stackBuffer) free(buf);
</code></pre>

## Object Comparison  
## 对象比较

You should be aware of an important difference between the generic object-comparison method isEqual: and the comparison methods that are associated with an object type, such as isEqualToString:. The isEqual: method allows you to pass arbitrary objects as arguments and returns NO if the objects aren’t of the same class. Methods such as isEqualToString: and isEqualToArray: usually assume the argument is of the specified type (which is that of the receiver). They therefore do not perform type-checking and consequently they are faster but not as safe. For values retrieved from external sources, such as an application’s information property list (Info.plist) or preferences, the use of isEqual: is preferred because it is safer; when the types are known, use isEqualToString: instead.  
你应当意识到泛型的对象比较方法isEqual: 和对象相关的比较方法，例如isEqualToString:方法之间的重要区别。isEqual: 方法允许你传入任意对象作为参数，并且如果对象不是同一个类会返回NO。诸如isEqualToString: 和isEqualToArray:方法通常假设参数是指定的类型（也就是接收者的类型）。所以它们不执行类型检查，从而它们运行会更快，但却不安全。对于从内部资源取回的值，例如应用信息属性列表（Info.plist）或者偏好设置，更倾向于使用
 isEqual: ，因为它更安全。当类型未知的时候，使用isEqualToString:。
 
 A further point about isEqual: is its connection to the hash method. One basic invariant for objects that are put in a hash-based Cocoa collection such as an NSDictionary or NSSet is that if [A isEqual:B] == YES, then [A hash] == [B hash]. So if you override isEqual: in your class, you should also override hash to preserve this invariant. By default isEqual: looks for pointer equality of each object’s address, and hash returns a hash value based on each object’s address, so this invariant holds.  
和isEqual:方法相关的一点就是它和hash方法有关。对象一个最基本的不变的地方就是被放入一个基于哈希的例如NSDictionary 或 NSSetCocoa集合中，如果[A isEqual:B] == YES，那么[A hash] == [B hash]。如果你重写你的类的isEqual:方法，你应当也要重写hash方法来维持这一个不变的条件。默认的isEqual:方法寻找和每一个对象地址相等的指针，并且hash方法返回的hash值是基于每一个对象的地址，所以还是保持了这个不变性。
















