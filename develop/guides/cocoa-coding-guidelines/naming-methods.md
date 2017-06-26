# 方法的命名

方法或许是你编程接口中最常见的元素，因此在它们的命名方面应当特别小心。这部分讨论方法命名方面的内容：

## 一般规则

有一些在方法命名方面的一些一般指南你应当记住：

+ 方法名应该以小写字母打头，然后紧接着后面每一个单词的首字母大写。不要使用前缀。参见[排版约定](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-1002931)。对于以上指南，有两个特别的例外，你可能用一个很有名的大写缩写词为方法名打头（例如 TIFF或PDF），而且你可能会使用前缀来标记组以及私有方法（参见[私有方法](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-1003829)）。

+ 当一个方法表示一个对象执行的动作的话，请以一个动词打头：

`- (void)invokeWithTarget:(id)target;  `  
`- (void)selectTabViewItem:(NSTabViewItem *)tabViewItem`

不要使用“do”或者“does”作为方法名的一部分，因为这些辅助的动词很少能够增强意思。同样，绝不要在动词前面使用副词或者形容词。

+ 如果一个方法返回给调用者一个属性的话，用这个属性命名方法。没有必要使用“get”。除非不是直接返回一个或多个返回值。

*译者注：[ifeegoo](http://www.ifeegoo.com)，一直以来不是很喜欢Objective-C的Get方法的命名不带get。感觉不够明了。但是这个大家都习以为常。上面也说了，如果方法不是直接返回的，可以使用get，比如通过回调才能获取的属性。*

|方法命名|评述
|-----|-----
|- (NSSize)cellSize;|正确。
|- (NSSize)calcCellSize;|错误。
|- (NSSize)getCellSize;|错误。

+ 在所有参数前面使用关键词。

|方法命名|评述
|-----|-----
|- (void)sendAction:(SEL)aSelector toObject:(id)anObject forAllCells:(BOOL)flag;|正确。
|- (void)sendAction:(SEL)aSelector :(id)anObject :(BOOL)flag;|错误。

+ 在参数之前描述这个参数。

|方法命名|评述
|-----|-----
|- (id)viewWithTag:(NSInteger)aTag;|正确。
|- (id)taggedView:(int)aTag;|错误。

+ 当你想要创建一个比继承的方法更加明确的方法的时候，请在方法结束之后，添加一些关键词。

|方法命名|评述
|-----|-----
|- (id)initWithFrame:(CGRect)frameRect;|NSView, UIView.
|- (id)initWithFrame:(NSRect)frameRect mode:(int)aMode cellClass:(Class)factoryId numberOfRows:(int)rowsHigh numberOfColumns:(int)colsWide;|NSMatrix, NSView的子类

+ 不要在描述属性的关键词上使用“and”。

|方法命名|评述
|-----|-----
|- (int)runModalForDirectory:(NSString *)path file:(NSString *) name types:(NSArray *)fileTypes;|正确。
|- (int)runModalForDirectory:(NSString *)path andFile:(NSString *)name andTypes:(NSArray *)fileTypes;|错误。

尽管在这个例子中，采用“and”看起来还可以，但是当你创建越来越多关键词方法的时候，会出问题。

+ 如果一个方法描述了两个单独的动作，可以使用“and”来连接他们。

|方法命名|评述
|-----|-----
|- (BOOL)openFile:(NSString *)fullPath withApplication:(NSString *)appName andDeactivate:(BOOL)flag;|NSWorkspace.

## 存取方法

存取方法是用来设置和返回一个对象的属性值。有推荐的格式，取决于这个属性表达方式：

+ 如果这个属性是名词的话，格式是这样的：  
`- (type)noun;`  
`- (void)setNoun:(type)aNoun;`

例如：  
`- (NSString *)title;`   
`- (void)setTitle:(NSString *)aTitle;`

+ 如果这个属性是形容词，格式是这样的：  
`- (BOOL)isAdjective;`  
`- (void)setAdjective:(BOOL)flag;`

例如：  

`- (BOOL)isEditable;`  
`- (void)setEditable:(BOOL)flag;`

+ 如果这个属性是一个动词，格式是这样的：  
`- (BOOL)verbObject;`  
`- (void)setVerbObject:(BOOL)flag;`

例如：

`- (BOOL)showsAlpha;`  
`- (void)setShowsAlpha:(BOOL)flag;`

动词应当使用简单的现在时。

+ 不要通过分词形式将动词转换成形容词：

|方法命名|评述
|-----|-----
|- (void)setAcceptsGlyphInfo:(BOOL)flag;|正确。
|- (BOOL)acceptsGlyphInfo;|正确。
|- (void)setGlyphInfoAccepted:(BOOL)flag;|错误。
|- (BOOL)glyphInfoAccepted;|错误。

+ 你可能会使用情态动词来阐述意思，但是不用使用“do” 或“does”。

|方法命名|评述
|-----|-----
|- (void)setCanHide:(BOOL)flag;|正确。
|- (BOOL)canHide;|正确。
|- (void)setShouldCloseDocument:(BOOL)flag;|正确。
|- (BOOL)shouldCloseDocument;|正确。
|- (void)setDoesAcceptGlyphInfo:(BOOL)flag;|错误。
|- (BOOL)doesAcceptGlyphInfo;|错误。

+ 仅当方法间接返回对象和值的时候，使用“get”命名。而且仅当对个条目需要返回的时候。

|方法命名|评述
|-----|-----
|- (void)getLineDash:(float *)pattern count:(int *)count phase:(float *)phase;|NSBezierPath.

在以上这些方法中，方法的实现应当考虑针对这些输入输出参数可接受NULL值，来指明调用者不必对一个或者多个返回值感兴趣。

## 代理方法

代理方法是指在某一事件发生的时候，一个对象调用它的代理（如果实现了这个代理）。它们有独特的格式，同样适用于对象数据源的方法调用。

+ 方法打头请标明是哪个类的对象发送信息的：

`- (BOOL)tableView:(NSTableView *)tableView shouldSelectRow:(int)row;`  
`- (BOOL)application:(NSApplication *)sender openFile:(NSString *)filename;`

类名省略前缀，并且第一个字母小写。  

+ 一个冒号后附带类名（参数是代理对象的实例），除非这个方法只有一个参数，发送者。

`- (BOOL)applicationOpenUntitledFile:(NSApplication *)sender;`

+ 有一个例外就是，方法作为通知被发送的结果来调用。这种情况下，这个单独的参数就是通知对象。

`- (void)windowDidChangeScreen:(NSNotification *)notification;`

+ 在方法名上使用“did” 或 “will”用来通知代理，有事情已经发生或者即将发生。

`- (void)browserDidScroll:(NSBrowser *)sender;`  
`- (NSUndoManager *)windowWillReturnUndoManager:(NSWindow *)window;`

+ 尽管你可以在方法名上使用“did” 或“will”，在方法被调用的时候，请求代理为另外一个对象做些事情，还是推荐“should”。

`- (BOOL)windowShouldClose:(id)sender;`

## 方法集合

对于那些管理对象集合的对象（每一个被称为集合的元素），约定为以下方法格式：

`- (void)addElement:(elementType)anObj;`  
`- (void)removeElement:(elementType)anObj;`  
`- (NSArray *)elements;`

例如：

`- (void)addLayoutManager:(NSLayoutManager *)obj;`  
`- (void)removeLayoutManager:(NSLayoutManager *)obj;`  
`- (NSArray *)layoutManagers;`

以下是对这个指南的限制和改进：

+ 如果这个集合的确是无序的，返回一个NSSet对象，而不是一个NSArray对象。  
+ 如果向一个集合中指定位置插入一个元素非常重要，采用以下形式的方法:

`- (void)insertLayoutManager:(NSLayoutManager *)obj atIndex:(int)index;`  
`- (void)removeLayoutManagerAtIndex:(int)index;`

对于集合方法来说，这里有两个实现的细节需要注意：

+ 这些方法都显示的持有插入的对象，所以代码中添加或插入它们的时候，必须retain，移除它们的时候，必须release。  
+ 如果插入的对象需要有一个反向指针指向主对象，你可以使用（通常情况下）一个 set方法设置方向指针，但是不要retain。至于insertLayoutManager:atIndex:方法， NSLayoutManager类已经在这些方法中处理了：

`- (void)setTextStorage:(NSTextStorage *)textStorage;`  
`- (NSTextStorage *)textStorage;`

你一般不会直接去调用setTextStorage:方法，但是可能需要重写它。对于上面关于集合方法约定的另外一个例子来自NSWindow类：

`- (void)addChildWindow:(NSWindow *)childWin ordered:(NSWindowOrderingMode)place;`  
`- (void)removeChildWindow:(NSWindow *)childWin;`  
`- (NSArray *)childWindows;`
 
`- (NSWindow *)parentWindow;`  
`- (void)setParentWindow:(NSWindow *)window;`

## 方法参数

这里有一些设计方法参数命名的一般规则：

+ 和方法一样，参数要以一个小写字母打头，并且后续每一个单词的首字母要大写（例如： removeObject:(id)anObject）。  
+ 不要在参数名中使用“pointer” 或“ptr”。使用参数类型，而不是声明它是不是一个指针。  
+ 避免1-2个字母的参数名字。  
+ 避免缩写。

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

## 私有方法

大多数情况下，私有方法的命名遵循公共方法命名的一些规则。然而，一个常见的约定就是给私有方法一个前缀，以便它很容易与公共方法进行区分。如果你不遵循这个约定，私有方法的命名会导致奇怪的问题。当你设计一个Cocoa框架类的子类的时候，你可能会无意识的使用了一个与框架内部私有方法名一样的名字。

大多数Cocoa框架中的私有方法有一个下划线前缀（例如：_fooData ），用来标记它是私有方法。基于这个事实，有以下两个建议：

+ 不要在你的私有方法前使用下划线字符做为前缀。Apple保留这个约定。  
+ 如果你要完全确保你的一个很大的Cocoa框架类（例如NSView 或 UIView）的子类中的私有方法的命名与父类中的私有方法的命名不同，你可以在你的私有方法前面加上一个你自己的前缀。这个前缀尽可能的唯一，或许基于你的公司或者项目，诸如“XX_”格式。所以，若你的项目叫做Byte Flogger，那么这个方法名可以是BF_addObject:  。

尽管给私有方法加上前缀的命名方式看起来像是与先前的提出的方法以类为区分的命名空间存在矛盾之处，但是这里的意图在于：防止无意识的重写了父类的私有方法。
