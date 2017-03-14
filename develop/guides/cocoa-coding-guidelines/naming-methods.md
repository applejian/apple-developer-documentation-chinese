# Naming Methods  
# 方法的命名

Methods are perhaps the most common element of your programming interface, so you should take particular care in how you name them. This section discusses the following aspects of method naming:  
方法或许是你编程接口中最常见的元素，因此在它们的命名方面应当特别小心。这部分讨论方法命名方面的内容：

## General Rules  
## 一般规则

Here are a few general guidelines to keep in mind when naming methods:  
有一些在方法命名方面的一些一般指南你应当记住：

+ Start the name with a lowercase letter and capitalize the first letter of embedded words. Don’t use prefixes. See [Typographic Conventions](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-1002931).There are two specific exceptions to these guidelines. You may begin a method name with a well-known acronym in uppercase (such as TIFF or PDF)), and you may use prefixes to group and identify private methods (see [Private Methods](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-1003829)).  
+ 方法名应该以小写字母打头，然后紧接着后面每一个单词的首字母大写。不要使用前缀。参见[排版约定](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-1002931)。对于以上指南，有两个特别的例外，你可能用一个很有名的大写缩写词为方法名打头（例如 TIFF或PDF），而且你可能会使用前缀来标记组以及私有方法（参见[私有方法](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-1003829)）。

+ For methods that represent actions an object takes, start the name with a verb:  
+ 当一个方法表示一个对象执行的动作的话，请以一个动词打头：

`- (void)invokeWithTarget:(id)target;  `  
`- (void)selectTabViewItem:(NSTabViewItem *)tabViewItem`

Do not use “do” or “does” as part of the name because these auxiliary verbs rarely add meaning. Also, never use adverbs or adjectives before the verb.  
不要使用“do”或者“does”作为方法名的一部分，因为这些辅助的动词很少能够增强意思。同样，绝不要在动词前面使用副词或者形容词。

+ If the method returns an attribute of the receiver, name the method after the attribute. The use of “get” is unnecessary, unless one or more values are returned indirectly.  
+ 如果一个方法返回给调用者一个属性的话，用这个属性命名方法。没有必要使用“get”。除非不是直接返回一个或多个返回值。

*译者注：[ifeegoo](http://www.ifeegoo.com)，一直以来不是很喜欢Objective-C的Get方法的命名不带get。感觉不够明了。但是这个大家都习以为常。上面也说了，如果方法不是直接返回的，可以使用get，比如通过回调才能获取的属性。*

|Method Naming|Commentary
|-----|-----
|- (NSSize)cellSize;|Right.
|- (NSSize)calcCellSize;|Wrong.
|- (NSSize)getCellSize;|Wrong.

|方法命名|评述
|-----|-----
|- (NSSize)cellSize;|正确。
|- (NSSize)calcCellSize;|错误。
|- (NSSize)getCellSize;|错误。

+ Use keywords before all arguments.  
+ 在所有参数前面使用关键词。

|Method Naming|Commentary
|-----|-----
|- (void)sendAction:(SEL)aSelector toObject:(id)anObject forAllCells:(BOOL)flag;|Right.
|- (void)sendAction:(SEL)aSelector :(id)anObject :(BOOL)flag;|Wrong.

|方法命名|评述
|-----|-----
|- (void)sendAction:(SEL)aSelector toObject:(id)anObject forAllCells:(BOOL)flag;|正确。
|- (void)sendAction:(SEL)aSelector :(id)anObject :(BOOL)flag;|错误。

+ Make the word before the argument describe the argument.  
+ 在参数之前描述这个参数。

|Method Naming|Commentary
|-----|-----
|- (id)viewWithTag:(NSInteger)aTag;|Right.
|- (id)taggedView:(int)aTag;|Wrong.


|方法命名|评述
|-----|-----
|- (id)viewWithTag:(NSInteger)aTag;|正确。
|- (id)taggedView:(int)aTag;|错误。

+ Add new keywords to the end of an existing method when you create a method that is more specific than the inherited one.  
+ 当你想要创建一个比继承的方法更加明确的方法的时候，请在方法结束之后，添加一些关键词。

|Method Naming|Commentary
|-----|-----
|- (id)initWithFrame:(CGRect)frameRect;|NSView, UIView.
|- (id)initWithFrame:(NSRect)frameRect mode:(int)aMode cellClass:(Class)factoryId numberOfRows:(int)rowsHigh numberOfColumns:(int)colsWide;|NSMatrix, a subclass of NSView

|方法命名|评述
|-----|-----
|- (id)initWithFrame:(CGRect)frameRect;|NSView, UIView.
|- (id)initWithFrame:(NSRect)frameRect mode:(int)aMode cellClass:(Class)factoryId numberOfRows:(int)rowsHigh numberOfColumns:(int)colsWide;|NSMatrix, NSView的子类

+ Don’t use “and” to link keywords that are attributes of the receiver.  
+ 不要在描述属性的关键词上使用“and”。

|Method Naming|Commentary
|-----|-----
|- (int)runModalForDirectory:(NSString *)path file:(NSString *) name types:(NSArray *)fileTypes;|Right.
|- (int)runModalForDirectory:(NSString *)path andFile:(NSString *)name andTypes:(NSArray *)fileTypes;|Wrong.

|方法命名|评述
|-----|-----
|- (int)runModalForDirectory:(NSString *)path file:(NSString *) name types:(NSArray *)fileTypes;|正确。
|- (int)runModalForDirectory:(NSString *)path andFile:(NSString *)name andTypes:(NSArray *)fileTypes;|错误。

Although “and” may sound good in this example, it causes problems as you create methods with more and more keywords.  
尽管在这个例子中，采用“and”看起来还可以，但是当你创建越来越多关键词方法的时候，会出问题。

+ If the method describes two separate actions, use “and” to link them.  
+ 如果一个方法描述了两个单独的动作，可以使用“and”来连接他们。

|Method Naming|Commentary
|-----|-----
|- (BOOL)openFile:(NSString *)fullPath withApplication:(NSString *)appName andDeactivate:(BOOL)flag;|NSWorkspace.

|方法命名|评述
|-----|-----
|- (BOOL)openFile:(NSString *)fullPath withApplication:(NSString *)appName andDeactivate:(BOOL)flag;|NSWorkspace.

## Accessor Methods  
## 存取方法

Accessor methods are those methods that set and return the value of a property of an object. They have certain recommended forms, depending on how the property is expressed:  
存取方法是用来设置和返回一个对象的属性值。有推荐的格式，取决于这个属性表达方式：

+ If the property is expressed as a noun, the format is:  
+ 如果这个属性是名词的话，格式是这样的：  
`- (type)noun;`  
`- (void)setNoun:(type)aNoun;`

For example:  
例如：  
`- (NSString *)title;`   
`- (void)setTitle:(NSString *)aTitle;`

+ If the property is expressed as an adjective, the format is:  
+ 如果这个属性是形容词，格式是这样的：  
`- (BOOL)isAdjective;`  
`- (void)setAdjective:(BOOL)flag;`

For example:  
例如：  

`- (BOOL)isEditable;`  
`- (void)setEditable:(BOOL)flag;`

+ If the property is expressed as a verb, the format is:  
+ 如果这个属性是一个动词，格式是这样的：  
`- (BOOL)verbObject;`  
`- (void)setVerbObject:(BOOL)flag;`

For example:  
例如：

`- (BOOL)showsAlpha;`  
`- (void)setShowsAlpha:(BOOL)flag;`

The verb should be in the simple present tense.   
动词应当使用简单的现在时。

+ Don’t twist a verb into an adjective by using a participle:  
+ 不要通过分词形式将动词转换成形容词：

|Method Naming|Commentary
|-----|-----
|- (void)setAcceptsGlyphInfo:(BOOL)flag;|Right.
|- (BOOL)acceptsGlyphInfo;|Right.  
|- (void)setGlyphInfoAccepted:(BOOL)flag;|Wrong.
|- (BOOL)glyphInfoAccepted;|Wrong.

|方法命名|评述
|-----|-----
|- (void)setAcceptsGlyphInfo:(BOOL)flag;|正确。
|- (BOOL)acceptsGlyphInfo;|正确。
|- (void)setGlyphInfoAccepted:(BOOL)flag;|错误。
|- (BOOL)glyphInfoAccepted;|错误。

+ You may use modal verbs (verbs preceded by “can”, “should”, “will”, and so on) to clarify meaning, but don’t use “do” or “does”.  
+ 你可能会使用情态动词来阐述意思，但是不用使用“do” 或“does”。

|Method Naming|Commentary
|-----|-----
|- (void)setCanHide:(BOOL)flag;|Right.
|- (BOOL)canHide;|Right.
|- (void)setShouldCloseDocument:(BOOL)flag;|Right.
|- (BOOL)shouldCloseDocument;|Right.
|- (void)setDoesAcceptGlyphInfo:(BOOL)flag;|Wrong.
|- (BOOL)doesAcceptGlyphInfo;|Wrong.

|方法命名|评述
|-----|-----
|- (void)setCanHide:(BOOL)flag;|正确。
|- (BOOL)canHide;|正确。
|- (void)setShouldCloseDocument:(BOOL)flag;|正确。
|- (BOOL)shouldCloseDocument;|正确。
|- (void)setDoesAcceptGlyphInfo:(BOOL)flag;|错误。
|- (BOOL)doesAcceptGlyphInfo;|错误。

+ Use “get” only for methods that return objects and values indirectly. You should use this form for methods only when multiple items need to be returned.  
+ 仅当方法间接返回对象和值的时候，使用“get”命名。而且仅当对个条目需要返回的时候。

|Method Naming|Commentary
|-----|-----
|- (void)getLineDash:(float *)pattern count:(int *)count phase:(float *)phase;|NSBezierPath.

|方法命名|评述
|-----|-----
|- (void)getLineDash:(float *)pattern count:(int *)count phase:(float *)phase;|NSBezierPath.

In methods such as these, the implementation should accept NULL for these in–out parameters as an indication that the caller is not interested in one or more of the returned values.  
在以上这些方法中，方法的实现应当考虑针对这些输入输出参数可接受NULL值，来指明调用者不必对一个或者多个返回值感兴趣。

## Delegate Methods  
## 代理方法

Delegate methods (or delegation methods) are those that an object invokes in its delegate (if the delegate implements them) when certain events occur. They have a distinctive form, which apply equally to methods invoked in an object’s data source:  
代理方法是指在某一事件发生的时候，一个对象调用它的代理（如果实现了这个代理）。它们有独特的格式，同样适用于对象数据源的方法调用。

+ Start the name by identifying the class of the object that’s sending the message:  
+ 方法打头请标明是哪个类的对象发送信息的：

`- (BOOL)tableView:(NSTableView *)tableView shouldSelectRow:(int)row;`  
`- (BOOL)application:(NSApplication *)sender openFile:(NSString *)filename;`

The class name omits the prefix and the first letter is in lowercase.  
类名省略前缀，并且第一个字母小写。  

+ A colon is affixed to the class name (the argument is a reference to the delegating object) unless the method has only one argument, the sender.  
+ 一个冒号后附带类名（参数是代理对象的实例），除非这个方法只有一个参数，发送者。

`- (BOOL)applicationOpenUntitledFile:(NSApplication *)sender;`

+ An exception to this are methods that invoked as a result of a notification being posted. In this case, the sole argument is the notification object.  
+ 有一个例外就是，方法作为通知被发送的结果来调用。这种情况下，这个单独的参数就是通知对象。

`- (void)windowDidChangeScreen:(NSNotification *)notification;`

+ Use “did” or “will” for methods that are invoked to notify the delegate that something has happened or is about to happen.  
+ 在方法名上使用“did” 或 “will”用来通知代理，有事情已经发生或者即将发生。

`- (void)browserDidScroll:(NSBrowser *)sender;`  
`- (NSUndoManager *)windowWillReturnUndoManager:(NSWindow *)window;`

+ Although you can use “did” or “will” for methods that are invoked to ask the delegate to do something on behalf of another object, “should” is preferred.  
+ 尽管你可以在方法名上使用“did” 或“will”，在方法被调用的时候，请求代理为另外一个对象做些事情，还是推荐“should”。

`- (BOOL)windowShouldClose:(id)sender;`

## Collection Methods  
## 方法集合

For objects that manage a collection of objects (each called an element of that collection), the convention is to have methods of the form:  
对于那些管理对象集合的对象（每一个被称为集合的元素），约定为以下方法格式：

`- (void)addElement:(elementType)anObj;`  
`- (void)removeElement:(elementType)anObj;`  
`- (NSArray *)elements;`

For example:  
例如：

`- (void)addLayoutManager:(NSLayoutManager *)obj;`  
`- (void)removeLayoutManager:(NSLayoutManager *)obj;`  
`- (NSArray *)layoutManagers;`

The following are some qualifications and refinements to this guideline:  
以下是对这个指南的限制和改进：

+ If the collection is truly unordered, return an NSSet object rather than an NSArray object.  
+ If it’s important to insert elements into a specific location in the collection, use methods similar to the following instead of or in addition to the ones above:  
+ 如果这个集合的确是无序的，返回一个NSSet对象，而不是一个NSArray对象。  
+ 如果向一个集合中指定位置插入一个元素非常重要，采用以下形式的方法:

`- (void)insertLayoutManager:(NSLayoutManager *)obj atIndex:(int)index;`  
`- (void)removeLayoutManagerAtIndex:(int)index;`

There are a couple of implementation details to keep in mind with collection methods:  
对于集合方法来说，这里有两个实现的细节需要注意：

+ These methods typically imply ownership of the inserted objects, so the code that adds or inserts them must retain them, and the code that removes them must also release them.  
+ If the inserted objects need to have a pointer back to the main object, you do this (typically) with a set... method that sets the back pointer but does not retain. In the case of the insertLayoutManager:atIndex: method, the NSLayoutManager class does this in these methods:  
+ 这些方法都显示的持有插入的对象，所以代码中添加或插入它们的时候，必须retain，移除它们的时候，必须release。  
+ 如果插入的对象需要有一个反向指针指向主对象，你可以使用（通常情况下）一个 set方法设置方向指针，但是不要retain。至于insertLayoutManager:atIndex:方法， NSLayoutManager类已经在这些方法中处理了：

`- (void)setTextStorage:(NSTextStorage *)textStorage;`  
`- (NSTextStorage *)textStorage;`

You would normally not call setTextStorage: directly, but might want to override it.Another example of the above conventions for collection methods comes from the NSWindow class:  
你一般不会直接去调用setTextStorage:方法，但是可能需要重写它。对于上面关于集合方法约定的另外一个例子来自NSWindow类：

`- (void)addChildWindow:(NSWindow *)childWin ordered:(NSWindowOrderingMode)place;`  
`- (void)removeChildWindow:(NSWindow *)childWin;`  
`- (NSArray *)childWindows;`
 
`- (NSWindow *)parentWindow;`  
`- (void)setParentWindow:(NSWindow *)window;`

## Method Arguments  
## 方法参数

There are a few general rules concerning the names of method arguments:  
这里有一些设计方法参数命名的一般规则：

+ As with methods, arguments start with a lowercase letter and the first letter of successive words are capitalized (for example, removeObject:(id)anObject).  
+ Don’t use “pointer” or “ptr” in the name. Let the argument’s type rather than its name declare whether it’s a pointer.  
+ Avoid one- and two-letter names for arguments.  
+ Avoid abbreviations that save only a few letters.  
+ 和方法一样，参数要以一个小写字母打头，并且后续每一个单词的首字母要大写（例如： removeObject:(id)anObject）。  
+ 不要在参数名中使用“pointer” 或“ptr”。使用参数类型，而不是声明它是不是一个指针。  
+ 避免1-2个字母的参数名字。  
+ 避免缩写。

Traditionally (in Cocoa), the following keywords and arguments are used together:  
一般来说（在Cocoa中），以下关键词和参数会同时使用：

`...action:(SEL)aSelector`  
`...alignment:(int)mode`  
`...atIndex:(int)index`  
`...content:(NSRect)aRect`  
`...doubleValue:(double)aDouble`  
`...floatValue:(float)aFloat`  
`...font:(NSFont *)fontObj`  
`...frame:(NSRect)frameRect`  
`...intValue:(int)anInt`  
`...length:(int)numBytes`  
`...point:(NSPoint)aPoint`  
`...stringValue:(NSString *)aString`  
`...tag:(int)anInt`  
`...target:(id)anObject`  
`...title:(NSString *)aString`

## Private Methods  
## 私有方法

In most cases, private method names generally follow the same rules as public method names. However, a common convention is to give private methods a prefix so it is easy to distinguish them from public methods. Even with this convention, the names given to private methods can cause a peculiar type of problem. When you design a subclass of a Cocoa framework class, you cannot know if your private methods unintentionally override private framework methods that are identically named.  
大多数情况下，私有方法的命名遵循公共方法命名的一些规则。然而，一个常见的约定就是给私有方法一个前缀，以便它很容易与公共方法进行区分。如果你不遵循这个约定，私有方法的命名会导致奇怪的问题。当你设计一个Cocoa框架类的子类的时候，你可能会无意识的使用了一个与框架内部私有方法名一样的名字。

Names of most private methods in the Cocoa frameworks have an underscore prefix (for example, _fooData ) to mark them as private. From this fact follow two recommendations.  
大多数Cocoa框架中的私有方法有一个下划线前缀（例如：_fooData ），用来标记它是私有方法。基于这个事实，有以下两个建议：

+ Don’t use the underscore character as a prefix for your private methods. Apple reserves this convention.  
+ 不要在你的私有方法前使用下划线字符做为前缀。Apple保留这个约定。  
+ If you are subclassing a large Cocoa framework class (such as NSView or UIView) and you want to be absolutely sure that your private methods have names different from those in the superclass, you can add your own prefix to your private methods. The prefix should be as unique as possible, perhaps one based on your company or project and of the form "XX_". So if your project is called Byte Flogger, the prefix might be BF_addObject:  
+ 如果你要完全确保你的一个很大的Cocoa框架类（例如NSView 或 UIView）的子类中的私有方法的命名与父类中的私有方法的命名不同，你可以在你的私有方法前面加上一个你自己的前缀。这个前缀尽可能的唯一，或许基于你的公司或者项目，诸如“XX_”格式。所以，若你的项目叫做Byte Flogger，那么这个方法名可以是BF_addObject:  。

Although the advice to give private method names a prefix might seem to contradict the earlier claim that methods exist in the namespace of their class, the intent here is different: to prevent unintentional overriding of superclass private methods.  
尽管给私有方法加上前缀的命名方式看起来像是与先前的提出的方法以类为区分的命名空间存在矛盾之处，但是这里的意图在于：防止无意识的重写了父类的私有方法。
