---
layout: post
title:  "Swift 介绍与入门"
tags: [iOS, Swift]
date:   2014-09-08 17:29:43
categories: Tutorial
image:
  feature: abstract-5.jpg
  credit: 
  creditlink: 
---

# 是什么？

## 百科定义

**Swift**是一种编译式编程语言，由[**Apple.Inc**](http://zh.wikipedia.org//wiki/%E8%98%8B%E6%9E%9C%E5%85%AC%E5%8F%B8)推出，用来撰写[OS X](http://zh.wikipedia.org//wiki/OS_X)和[iOS](http://zh.wikipedia.org//wiki/IOS)应用程序。
2014年，在Apple WWDC所发布，设计Swift时，苹果公司有意让Swift与[**Objective-C**](http://zh.wikipedia.org//wiki/Objective-C)共存在苹果公司的操作系统上。

Swift以[**LLVM**](http://zh.wikipedia.org/wiki/LLVM)编译，可以使用现有的Cocoa和Cocoa Touch框架。Xcode Playgrounds功能是Swift为苹果开发工具带来的最大创新，该功能提供强大的互动效果，能让Swift源代码在撰写过程中能实时显示出其运行结果。

Swift运行在XCode 6上：
![Swift运行在XCode 6上](http://ericsensblog.qiniudn.com/whats-new_debug.png)   

![Swift运行在XCode 6上](http://ericsensblog.qiniudn.com/whats-new-2014.png)

## 同类技术有哪些

语法上类似脚本语言：Ruby,Python，但是因为不能跨平台，只能在苹果公司的LLVM上，所以无法比较，不能算作同类技术。

如果需要比较，最佳比较对象应该是**Objective-C语言**，同样是苹果公司推出的语言，都是通过LLVM编译，运行在iOS和OS X上。

总的来说，Swift取消了Objective C的指针及其他不安全访问的使用，并舍弃Objective C早期应用Smalltalk之语法，全面改为句点表示法（dot-notation）。同许多脚本语言一样，Swift可以推断变量类型（var, variant）。同时，它提供了类似Java的命名空间(namespace)、泛型(generic)、运算对象重载（operator overloading）。**Swift被简单的形容为 “没有C的Objective-C”（Objective-C without the C）**

## 相比同类的优缺点是什么？

### 类似 Objective-C之处 

1. 基本数值类型（numeric types）大致相同 (例如Int, UInt, Float, Double)
1. 大量的C运算对象被移出Swift, 但又引入一些新运算对象。
1. 大括号被用于组群陈述（group statements）。
1. 变量之赋值使用等于符号, 但比较则使用“连续两个等于”(==)运算对象。还有一个新的运算对象，“连续三个等于”(===)被用来判断常数或变量之间是否为同一对象之实例(instance)。
1. 中括号([], Square brackets)用于数组的表示, 声明阵例之后, 可以指派索引值(index)来进行元素(element)之访问。
1. 控制陈述（control statement）, for, while, if, switch 与Ojbective-C都十分类似, 但有延伸功能, 像是 for in 用于集合(collection)的轮询, switch 还可以接受非整数的cases条件值, 诸如此类。

### 不同于 Objective-C之处 
1. 陈述句（statement）不须再使用分号 (';')做为退出, 但分号还是可以在一行以内作为两个以上陈述的分隔。
1. 头文件(Header files)不再需要。
1. 注解方式 /* ... */ 可以为嵌套（nested）注解, 意思是指注解内可以再有注解, 过去有些C或C++编译器不支持嵌套注解。
1. 强类型(strong type)
1. 类型推论或隐含类型(Type inference)
1. 支持泛型编程。
1. 函数为第一等类型(first-class object)，这意味着函数可以作为其他函数的参数与返回值。
1. 运算对象可在类型内重新定义 (运算对象重载)。可以生成新的运算对象。
1. 字符串全方面支持 Unicode。某些字符甚至可以成为语言的名称。
1. 许多C语言家族过去恶名昭彰的怪语法（error-prone behaviors）也被改变:
1. 不再存在指针。
1. 指派(Assignments)不再回传值。正确写法是 if (i==0) ，一般容易误写成 if (i=0) 会造成编译时期错误(compile-time error)。
1. 在switch 的区块内不需要再使用 break 叙述句。另外, case后面都需要有可执行的代码（C或C++可连续使用多个case而不需要额外的代码）, 否则会发生编译错误。
1. 变量和常数都要被初始化，而且数组(array)的界限也要确认清楚。
1. 溢出（overflows）的问题。C语言没有强制整数类型（signed integers）的界限, 常常在运行时间发生问题。Swift可以通过整数类型的max或min属性取得最大值或最小值。

# 为什么会出现？ #

## 解决了什么问题？ ##
降低了开发者的门槛，因为相较于语法奇异的Objective-C语言，Swift的语法更通俗易懂，容易上手。详见[**《为什么 Objective-C 很难》**](http://www.oschina.net/question/213217_41058/#tags_nav)。

以下是相同功能分别用Swift和Objective-C实现的代码：
{% highlight Objective-C linenos %}
Person *matt = [[Person alloc] initWithName:@"MatGalloway"];

[matt sayHello];

{% endhighlight %}  

{% highlight Swift linenos %}
var matt = Person(name:"MattGalloway")

matt.sayHello()

{% endhighlight %}  
## 没有这个技术以前怎么做 ##
虽然苹果公司会在iOS8正式版发布（2014.9.9）后开始正式使用Swift，AppStore的绝大多数应用使用的仍然是Objective-C,目前Objective-c在TIOBE语言排行榜上位列**第三**，然而在2010年之前它一直是榜上无名的，尽管它有几十年的历史，促使它上榜的主要原因是iPhone和iOS的问世。

# 怎么学？（Swift语言指南）

<p>这份指南汇集了Swift语言主流学习资源，并以开发者的视角整理编排。</p>

<p>GitHub: <a href="https://github.com/ipader/SwiftGuide">ipader/SwiftGuide</a> ｜ 网站：<a href="http://dev.swiftguide.cn">http://dev.swiftguide.cn</a> ｜ <em>欢迎开发者一起<a href="https://github.com/ipader/SwiftGuide/pulls">维护</a>，或<a href="https://github.com/ipader/SwiftGuide/issues/new">反馈/投稿</a></em></p>

<p><span style="color:lightgray;font-size:12px"><a href="http://weibo.com/swiftlanguage">@SwiftLanguage</a> 更新于 2014-10-27，更新内容详见<a href="https://github.com/ipader/SwiftGuide/blob/master/weekly/2014-10-27.md">《2014-10-27收录周报》</a></span></p>

<h2>Swift文档</h2>

<h3>1. <a href="https://developer.apple.com/library/prerelease/ios/referencelibrary/GettingStarted/LandingPage/index.html">Welcome to Swift</a></h3>

<p>苹果针对Swift开发者官方文档入口。其中包括：
<a href="https://developer.apple.com/library/prerelease/ios/referencelibrary/GettingStarted/LandingPage/index.html">Swift概括</a>,
<a href="https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/index.html">Swift Programming Language</a>,
<a href="https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/BuildingCocoaApps/index.html#//apple_ref/doc/uid/TP40014216">Using Swift with Cocoa and Objective-C</a></p>

<h3>2. <a href="https://developer.apple.com/swift/">Swift Programming Language</a></h3>

<ul>
<li><p>苹果官方文档：
<a href="https://developer.apple.com/library/prerelease/ios/documentation/swift/conceptual/swift_programming_language/index.html">在线版(英文)</a> <a href="https://itunes.apple.com/us/book/swift-programming-language/id881256329?mt=11">iBooks版(英文)</a></p></li>
<li><p>爱好者翻译版：
<a href="http://www.swiftguide.cn">在线版(中文) (By @Swift中文翻译组)</a> ｜
<a href="http://vdisk.weibo.com/s/EhsPPzRRQ5CZ/1402621206">PDF版 (By @CocoaChina)</a> ｜
<a href="http://yuedu.baidu.com/ebook/6f6c3b1ef01dc281e43af000">百度阅读版 (By 小岂子)</a></p></li>
<li><p><a href="https://developer.apple.com/library/prerelease/ios/documentation/swift/conceptual/swift_programming_language/BasicOperators.html#//apple_ref/doc/uid/TP40014097-CH6-XID_109">Basic Operators - Nil Coalescing Operator</a>解读</p>

<ol>
<li> <a href="http://www.devtalking.com/articles/swift-nil-coalescing/">Swift中Nil Coalescing运算符的使用技巧</a>   By <a href="http://weibo.com/jacefu">@DevTalking</a></li>
<li> <a href="http://jamesonquave.com/blog/swifts-nil-coaelescing-operator-in-xcode-6-beta-5/">Swift’s Nil Coalescing Operator In Xcode 6 Beta 5</a> By <a href="http://jamesonquave.com/">Jameson Quave</a></li>
</ol>
</li>
<li><a href="http://swiftist.org/topics/165">Swift 编程风格指南</a>(译文来自 <a href="http://swiftist.org">swiftist.org</a>): 本风格指南的目标是让Swift代码更简洁、可读更强。 原文：<a href="https://github.com/raywenderlich/swift-style-guide">《The Official raywenderlich.com Swift Style Guide》</a></li>
<li><a href="http://hawstein.com/posts/make-thiner-tspl.html">《The Swift Programming Language》读簿</a>: "读书就是要取其精华，去其糟粕、无用、简单和已知的内容。By <a href="http://weibo.com/hawstein">@Hawstein</a>"。站在作者自己的理解能力上，应该是一份很好的去繁求简读薄。不过，每个初学者基础不同，理解能力也千差万别。因此，对于浓缩版，当有不理解时，应该对照原版章节再进一步细读，千万不能蒙混。</li>
</ul>


<h3>3. Using Swift with Cocoa and Objective-C</h3>

<ul>
<li>苹果官方文档：<a href="https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/BuildingCocoaApps/index.html#//apple_ref/doc/uid/TP40014216">在线版(英文)</a> <a href="https://itunes.apple.com/us/book/using-swift-cocoa-objective/id888894773?mt=11&amp;ls=1">iBooks版(英文)</a></li>
<li>爱好者翻译版：<a href="https://github.com/CocoaChina-editors/Welcome-to-Swift/blob/master/UsingSwiftwithCocoaandObjective-C%E4%B8%AD%E6%96%87%E6%89%8B%E5%86%8C.md">在线版(中文) (By @CocoaChina)</a>｜<a href="http://vdisk.weibo.com/s/EhsPPzRRQHNd/1402648326">PDF版 (By @CocoaChina)</a></li>
</ul>


<h3>4. <a href="https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/index.html#//apple_ref/doc/uid/TP40014214">App Extension Programming Guide</a></h3>

<ul>
<li><p>应用扩展要点（App Extension Essentials）</p>

<table>
<thead>
<tr>
<th>译文 </th>
<th> 译者 </th>
<th> 原文</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="http://www.devtalking.com/articles/understand-how-an-extension-works/">应用扩展如何工作</a> </td>
<td> <a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/ExtensionOverview.html#//apple_ref/doc/uid/TP40014214-CH2-SW2">Understand How an Extension Works</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/creating-an-app-extension/">开发应用扩展</a> </td>
<td> <a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/ExtensionCreation.html#//apple_ref/doc/uid/TP40014214-CH5-SW1">Creating an App Extension</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/app-extensions-increase-your-impact/">APP扩展提高你的应用影响力</a> </td>
<td> <a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/index.html#//apple_ref/doc/uid/TP40014214-CH20-SW1">App Extensions Increase Your Impact</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/handling-common-scenarios/">常见问题的处理方案</a> </td>
<td> <a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/ExtensionScenarios.html#//apple_ref/doc/uid/TP40014214-CH21-SW1">Handling Common Scenarios</a></td>
</tr>
</tbody>
</table>
</li>
<li><p>应用扩展类型（App Extension Types）</p>

<table>
<thead>
<tr>
<th>译文 </th>
<th> 译者 / 校对 </th>
<th> 原文</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="http://www.cocoachina.com/ios/20140904/9527.html">Today</a></td>
<td><a href="http://weibo.com/cocoachina">@CocoaChina</a> / <a href="http://weibo.com/p/1005051710992635">唧唧歪歪</a></td>
<td><a href="https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/NotificationCenter.html#//apple_ref/doc/uid/TP40014214-CH11-SW1">Today</a></td>
</tr>
<tr>
<td><a href="http://www.cocoachina.com/ios/20140923/9728.html">Share</a></td>
<td><a href="http://weibo.com/cocoachina">@CocoaChina</a> / <a href="http://blog.csdn.net/guopengzhang/article">张国鹏</a></td>
<td><a href="http://www.cocoachina.com/ios/20140923/9728.html">Share</a></td>
</tr>
<tr>
<td><a href="http://www.cocoachina.com/ios/20140929/9800.html">Action</a></td>
<td><a href="http://weibo.com/cocoachina">@CocoaChina</a></td>
<td><a href="https://developer.apple.com/library/ios/documentation/General/Conceptual/ExtensibilityPG/Services.html#//apple_ref/doc/uid/TP40014214-CH13-SW1">Action</a></td>
</tr>
<tr>
<td><a href="http://www.cocoachina.com/ios/20141015/9918.html">照片编辑</a></td>
<td><a href="http://weibo.com/cocoachina">@CocoaChina</a></td>
<td><a href="">Photo Editing</a></td>
</tr>
<tr>
<td><a href="http://www.jianshu.com/p/359e064ffe20">Finder同步</a></td>
<td><a href="http://weibo.com/u/3227937731">@星夜暮晨</a></td>
<td><a href="https://developer.apple.com/library/ios/documentation/General/Conceptual/ExtensibilityPG/Finder.html#//apple_ref/doc/uid/TP40014214-CH15-SW1">Finder Sync</a></td>
</tr>
<tr>
<td><a href="http://www.jianshu.com/p/2f45696b812b">文档提供</a></td>
<td><a href="http://weibo.com/u/3227937731">@星夜暮晨</a></td>
<td><a href="https://developer.apple.com/library/ios/documentation/General/Conceptual/ExtensibilityPG/FileProvider.html#//apple_ref/doc/uid/TP40014214-CH18-SW1">Document Provider</a></td>
</tr>
<tr>
<td><a href="http://www.jianshu.com/p/987dfa9f3baf">第三方输入法</a></td>
<td><a href="http://weibo.com/u/3227937731">@星夜暮晨</a></td>
<td><a href="https://developer.apple.com/library/ios/documentation/General/Conceptual/ExtensibilityPG/Keyboard.html#//apple_ref/doc/uid/TP40014214-CH16-SW7">Custom Keyboard</a></td>
</tr>
</tbody>
</table>
</li>
</ul>


<h3>5. <a href="https://developer.apple.com/swift/blog/">Swift Blog - Apple Developer</a></h3>

<p>"值得一提的是，Swift博客是苹果官方网站的第一个blog，这也代表了苹果对开发者和消费者的态度正变得越来越开放。"</p>

<table>
<thead>
<tr>
<th>译文 </th>
<th> 译者 </th>
<th> 原文</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="http://www.devtalking.com/articles/failable-initializers/">可失败构造器</a></td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td><a href="https://developer.apple.com/swift/blog/?id=17">Failable Initializers</a></td>
</tr>
<tr>
<td>－</td>
<td>-</td>
<td><a href="https://developer.apple.com/swift/blog/?id=16">Building Your First Swift App Video</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/patterns-playground/">通过Playground展示一些编码模式</a></td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/swift/blog/?id=13">Patterns Playground</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/optionals-case-study/">Swift中Optional类型的使用案例分析：valuesForKeys</a> </td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/ExtensionScenarios.html#//apple_ref/doc/uid/TP40014214-CH21-SW1">Optionals Case Study: valuesForKeys</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/access-control-and-protected/">Swift中的访问控制与protected</a> </td>
<td> <a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/swift/blog/?id=11">Access Control and protected</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/swift-value-and-reference-types/">Swift中的值类型和参照类型</a> </td>
<td> <a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/swift/blog/?id=10">Value and Reference Types</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/swift-balloon/">WWDC2014大会中的Playground大炮气球示例</a> </td>
<td> <a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/swift/blog/?id=9">Balloons</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/swift-boolean/">在Swift中构建布尔类型</a> </td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td>  <a href="https://developer.apple.com/swift/blog/?id=8">Boolean</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/files-and-initialization/">Swift中的文件和初始化</a></td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/swift/blog/?id=7">Files and Initialization</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/swift-c-pointer/">在Swift中使用C语言的指针</a> </td>
<td> <a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/swift/blog/?id=6">Interacting with C Pointers</a></td>
</tr>
<tr>
<td>*<a href="http://www.devtalking.com/articles/swift-access-control/">Swift新特性 -- 访问控制</a>(文档版)</td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a> </td>
<td> <a href="https://developer.apple.com/swift/blog/?id=5">Access Control</a></td>
</tr>
</tbody>
</table>


<h3>6. 快速入门</h3>

<ul>
<li><a href="http://cdn2.raywenderlich.com/wp-content/uploads/2014/06/RW-Swift-Cheatsheet-0_3.pdf">Swift Cheat Sheet(PDF)</a>: 形式以代码先行，极简、有效地Swift语言快速学习指南。另一个更新版本：<a href="http://swift-cheatsheet.co.uk/">iOS8 Swift Cheat Sheet and Quick Reference Guide</a></li>
<li><a href="http://blog.teamtreehouse.com/an-absolute-beginners-guide-to-swift">An Absolute Beginner’s Guide to Swift</a>: 相对于Swift Cheat Sheet带了不少说明，但整个文档不显啰嗦，可读性强</li>
<li><a href="http://www.raywenderlich.com/74138/swift-language-faq">Swift Language FAQ</a>: Raywenderlich的Swift语言FAQ说清楚了很多问题。这份FAQ确实浅显易读，初学者不可或缺好文章！</li>
<li><a href="http://oleb.net/blog/2014/07/swift-strings/">Strings in Swift</a>：了解使用String的更高级技巧（尤其在Unicode的使用上）。文章中作者附上了示列代码在Playground项目中，似乎Swift开发者们已经慢慢地习惯了结合playground讲授Swift使用小技巧及语言特性。</li>
<li>与其它语言对比表:
<a href="http://t.cn/hDwCeY">C vs. Go vs. Swift</a>,
<a href="http://t.cn/RvSOQaN">C# vs. Swift</a>,
<a href="http://t.cn/RvXDwYI">Scala vs. Swift</a>,
<a href="http://t.cn/RvK5m7u">Go vs. Swift</a></li>
<li><a href="http://www.jianshu.com/p/78173bb311ee">iOS 8应用程序扩展开发技巧</a>：比较全面的概括了iOS扩展开发小技巧。By <a href="http://weibo.com/moonisky">@星夜暮晨</a> 原文<a href="http://www.atomicbird.com/blog/ios-app-extension-tips">iOS 8 App Extension Development Tips</a></li>
<li><a href="http://blog.jobbole.com/71250/">Objective-C开发者对Swift亮点的点评</a>: 这篇译文确实不错，含括了常见的亮点。尽管对于Swift相较于Objective C的亮点描述还不够全面，对初学者很受用。<a href="http://www.raywenderlich.com/73997/swift-language-highlights">原文在此</a></li>
<li><a href="http://www.cocoachina.com/applenews/devnews/2013/0930/7091.html">开启iOS/Mac开发之旅，过来人告诉你16件事 (译文来自@CocoaChina)</a>:"我曾向iOS开发者推荐了<a href="http://www.appdesignvault.com/inspiration-35/">《Twitter上最值得关注的30个人》</a>，收到了不少开发者的反馈，受此鼓舞，我向知名iOS开发者和设计师询问了这样一个问题--回到你开始iOS/Mac app开发的时候，你以现在的角度会给“最初的你”哪些建议。"  译文来自，英文原文<a href="http://www.appdesignvault.com/start-advice/">《13 Things You Must Know When Starting Out in iOS/Mac Development》</a></li>
<li><a href="http://practicalswift.com/2014/06/14/the-swift-standard-library-list-of-built-in-functions/">74个Swift标准库</a> (<a href="http://swiftist.org/topics/126">译文</a>): Swift包含了74个内置函数，但在The Swift Programming Langage一书中只介绍了其中的7个，其它的都没有在文档中体现。"文中作者没有提及他是如何发现这么多未在文档中体现的内置函数的，估计是反编译的结果。我测试了好多个都能用，而且Xcode还会给出语法提示：）" by <a href="http://weibo.com/u/1780854425">@李洁信</a></li>
<li><a href="https://github.com/ochococo/Design-Patterns-In-Swift">ochococo/Design-Patterns-In-Swift</a>：这个项目分享了Swift编程中如何使用常用设计模式。作者提供的Playground示例及常用设计模式的简单介绍。</li>
<li><a href="https://developer.apple.com/library/prerelease/ios/referencelibrary/GettingStarted/RoadMapiOSCh/index.html#//apple_ref/doc/uid/TP40012668">马上着手开发 iOS 应用程序 (Start Developing iOS Apps Today)</a>: 来自苹果官方文档</li>
</ul>


<h3>7. iOS Human Interface Guidelines</h3>

<ul>
<li>苹果官方文档：<a href="https://developer.apple.com/library/ios/documentation/userexperience/conceptual/mobilehig/index.html#//apple_ref/doc/uid/TP40006556-CH66-SW1">在线版(英文)</a>, <a href="https://itunes.apple.com/us/book/ios-human-interface-guidelines/id877942287?mt=11">iBooks版(英文)</a></li>
<li><p>非官方中译版</p>

<table>
<thead>
<tr>
<th>译文 </th>
<th> 译者 </th>
<th> 原文</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="http://isux.tencent.com/ios8-human-interface-guidelines.html">UI设计基础</a> </td>
<td><a href="http://weibo.com/txisux">@腾讯ISUX</a></td>
<td> <a href="https://developer.apple.com/library/ios/documentation/userexperience/conceptual/mobilehig/index.html#//apple_ref/doc/uid/TP40006556-CH66-SW1">Designing for iOS</a></td>
</tr>
<tr>
<td><a href="http://isux.tencent.com/ios8-human-interface-guidelines-design-strategies.html">设计策略</a> </td>
<td><a href="http://weibo.com/txisux">@腾讯ISUX</a></td>
<td> <a href="https://developer.apple.com/library/ios/documentation/userexperience/conceptual/mobilehig/Principles.html#//apple_ref/doc/uid/TP40006556-CH4-SW1">Design Principles</a></td>
</tr>
</tbody>
</table>
</li>
</ul>


<h3>8. 相关文档</h3>

<ul>
<li>WWDC 2014

<ol>
<li> <a href="http://v.youku.com/v_show/id_XNzIwOTc0NTA0.html">WWDC 2014发布会(带中文字幕)</a>: 有关Swift语言演讲部分从103:54开始，首先苹果iOS/OS X及公共平台负责人克雷格·费德里吉(Craig Federighi)针对Xcode及Objective C的简要回顾，克里斯·拉特纳(Chris Lattner)上台做Swift语言演示从107:15开始。</li>
<li> <a href="https://developer.apple.com/videos/wwdc/2014/">WWDC 2014 Videos</a>: 需要苹果开发者帐号才能观看。</li>
<li> <a href="http://pan.baidu.com/s/1mgqOVA4">WWDC 2014 PDFs</a>: 107个PDF压缩包 By <a href="http://weibo.com/qingxingfengzi">@清醒疯子</a></li>
</ol>
</li>
<li><a href="http://nondot.org/sabre/">Chris Lattner</a> (<a href="http://blog.jobbole.com/70139/">译文：Swift 编程语言首席架构师</a>): "Chris Lattner（1978年出生）是 LLVM 项目的主要发起人与作者之一，Clang 编译器的作者。他现在是苹果公司『开发者工具』部门的主管，领导 Xcode、Instruments 和 编译器团队，从 2010 年 7 月开始主导" By 伯乐在线</li>
<li><a href="http://www.cocoachina.com/applenews/devnews/2014/0613/8815.html">关于Swift，开发者最需要了解的7个方面</a> （<a href="https://medium.com/@thomasxchen/top-7-things-to-know-about-swift-apples-new-language-for-ios-8-14e09004cada">英文原文</a>): 简明扼要的阐述了Swift语言的几个重要特点</li>
<li><a href="http://tech.qq.com/a/20140609/000862.htm">程序员眼中的苹果Swift语言：简单 易学 高效</a>:“以下是记者准备的七个问题，涉及Swift的优点、缺点。以及Objective-C的结局。索菲斯的答案中有些会有点骇人、令人震惊，或许还有几丝伤感。“ 相关参考：<a href="http://www.zhihu.com/question/24002984">知乎《如何评价 Swift 语言？》</a></li>
<li><a href="http://onevcat.com/2014/06/walk-in-swift/">行走于 Swift 的世界中</a>: 总结了一下近一周以来的一些觉得这个语言里有意思的地方。By <a href="http://weibo.com/onevcat">@onevcat</a></li>
<li><a href="http://imtx.me/archives/1905.html">和Swift亲密接触的这半个月</a>：虽然学习能力及基础不同，但这样的学习体会及认识，至少能带给初学爱好者以启发！[转发] "未来 Swift 会发展的怎么样我无法预言，我是肯定会怀念这段时间和世界人民一起为 Swift 疯狂的日子的。" By <a href="http://weibo.com/tualatrix">@图拉鼎</a></li>
<li><a href="http://tech2ipo.com/79181?utm_source=sinaweibo&amp;utm_medium=sinaweibo_AD&amp;utm_campaign=weibo">我不懂 Swift 语言</a>: 能听到不同的声音是非常有益的，何况作者有些观点很有建设性。比如："Swift 仍旧在改变，它是 beta 版本，所以它肯定是能够改变的。要知道如果你在它是 beta 版的时候还不提出问题，那么如果你可能会需要很久时间才能让它进行改进。"</li>
<li><a href="http://www.csdn.net/article/2014-07-08/2820568">从Objective-C到Swift</a>: "Swift背后的概念大多与Objective-C类似，但更为简洁、自然，也吸收了很多其他语言的语法。本文将对Swift的语法、特点及改进进行全面介绍。" By <a href="http://www.zhihu.com/people/huang-jing-cheng">黄兢成</a></li>
<li><a href="http://io-meter.com/2014/06/04/swift's-functional-programing/">Swift の 函数式编程</a>: "Swift 相比原先的 Objective-C 最重要的优点之一，就是对函数式编程提供了更好的支持。 Swift 提供了更多的语法糖和一些新特性来增强函数式编程的能力，本文就在这方面进行一些讨论。" By <a href="http://weibo.com/u/2717070362">@diumoo</a></li>
<li><a href="http://onevcat.com/2014/07/ios-ui-unique/">iOS界面开发的大一统</a>: "简单介绍了下 Size Classes 和 UIPresentationController 的内容。" By <a href="http://weibo.com/onevcat">@onevcat</a></li>
<li><a href="http://objccn.io/issue-13-1/">MVVM 介绍</a>（译者： <a href="http://weibo.com/nixzhu">@nixzhu</a>，原文：<a href="http://www.objc.io/issue-13/mvvm.html">Introduction to MVVM</a>）: MVVM相较于MVC未必更轻量化，不过它达成了View Controller的轻量化。界面层逻辑(View Model)的抽象，不仅有利于理清View/Controller逻辑的粘连不清，对于单元测度也更容易了。</li>
<li><a href="http://www.raywenderlich.com/73286/top-5-ios-7-animations">Top 5 iOS 7 Animations</a>: iOS 7 排名前5的动画效果预览。谁能解读一下到这些动画效果对应的程序库、或找到对应或相近开源代码分享吗？（Swift版本更佳，OBJC也可以）

<ol>
<li> <a href="https://github.com/IFTTT/JazzHands">IFTTT/JazzHands</a>: Flickr开始界面动画类似效果，OBJC版本实现程序库。</li>
</ol>
</li>
<li><a href="http://www.jessesquires.com/apples-to-apples-part-two/">An analysis of sorts between Objective-C and Swift</a>："Swift 到底比 Objective-C 快多少？结论是：6倍以上（仅排序测试） 。 <a href="https://mikeash.com/pyblog/friday-qa-2014-07-04-secrets-of-swifts-speed.html">这里</a>有为什么快的原因" By <a href="http://weibo.com/tualatrix">@图拉鼎</a></li>
<li><a href="http://wileam.com/iphone-6-screen-cn/">iPhone 6 屏幕揭秘</a>(译者：<a href="http://weibo.com/wileam">@小雪-Joanna</a>)：关于iPhone6屏幕渲染的归纳。建议新手脑补一下这部分知识。原文：<a href="http://www.paintcodeapp.com/news/iphone-6-screens-demystified">iPhone 6 Screens Demystified</a></li>
<li><a href="https://medium.com/swift-programming/15-swift-ios-open-source-projects-you-cannot-ignore-6bd4ac37d7dd">10 Swift IOS open-source projects you cannot ignore</a>：10大不能错过的#Swift#开源项目。P.S. 本指南都有收录。</li>
</ul>


<h2>常用工具</h2>

<ul>
<li><p>开发工具</p>

<ol>
<li> <a href="https://developer.apple.com/swift/resources/">Xcode 6 beta下载</a>: 苹果应用集成开发环境。支持C/C++, Objective C, Swift等。不用购买开发者计划，直接下载。</li>
<li> <a href="http://macromates.com/">Textmate</a>：Mac OS X上一个可高度自定义的编辑器，尤其在我想做出一个快速改变但又不想等待Xcode加载的时候。该工具目前已经<a href="https://github.com/textmate/textmate">开源</a></li>
<li> <a href="http://mouapp.com/">Mou</a>：OS X上一款Markdown的编辑器。非常适用于编写自述文件、变更日志以及其他方面的内容。作者：<a href="http://chenluois.com/">罗晨</a></li>
<li> <a href="http://www.sublimetext.com/">Sublime Text ($)</a>：Mac OS X上另一款非常受欢迎的轻量级，可高度自定义的编辑器。</li>
<li> <a href="http://www.runswiftlang.com/">RunSwift</a>:正在犹豫是否入手苹果电脑开始一段Swift编程旅程的同学们，或仅仅为了试验一段简单Swift代码又懒得打开Xcode，可以试试这款Web版Swift编译环境RunSwift。</li>
</ol>
</li>
<li><p>代码管理</p>

<ol>
<li> <a href="http://github.com/">GitHub</a>：声望日盛的资源分享之地。</li>
<li> <a href="https://mac.github.com/">GitHub for Mac</a>：一个设计的非常美观的git客户端，不能取代你从命令行获得的所有功能，但使用起来非常简单。</li>
<li> <a href="http://git-scm.com/">Git</a>：分布式版本控制系统和源码管理系统，其优点是：快和简单易用。对于新手来说，可在此查看免费电子书籍。</li>
</ol>
</li>
<li><p>Xcode插件</p>

<ol>
<li> <a href="http://beta.cocoapods.org/">CocoaPods</a>：第三方库的管理利器，允许你简单地把第三方库整合进自己的应用中。对我个人来说，我基本上每个项目都使用CocoaPods。</li>
<li> <a href="https://github.com/kattrali/cocoapods-xcode-plugin">CocoaPods Xcode Plugin</a>：一款Xcode插件，允许你直接从Xcode管理CocoaPod依赖。</li>
<li> <a href="https://github.com/onevcat/VVDocumenter-Xcode">onevcat/VVDocumenter-Xcode</a>：快捷注释Xcode插件。By <a href="http://weibo.com/onevcat">@onevcat</a></li>
</ol>
</li>
<li>管理工具

<ol>
<li> <a href="http://brew.sh/index_zh-cn.html">HomeBrew</a>：OS X上非常出色的包管理工具。</li>
<li> <a href="http://panic.com/transmit/">Transmit ($)</a>：一个Mac OS X 上FTP客户端，有着非常漂亮的用户界面和有用的功能。</li>
</ol>
</li>
<li><p>调试工具</p>

<ol>
<li> <a href="http://fuckingclangwarnings.com/">mattt/fuckingclangwarnings.com</a>：警告与语义对照表。以后再也不用为Xcode各种警告纠结啦！By <a href="http://weibo.com/foogry">@foogry</a></li>
</ol>
</li>
<li><p>参考文章</p>

<ol>
<li> <a href="http://www.cocoachina.com/newbie/basic/2014/0417/8187.html">iOS开发工具</a>: "这是我们多篇iOS开发工具系列篇中的一篇，此前的文章比如：那些不能错过的Xcode插件，iOS开发者有价值的工具集，iOS/OS X开发：各种工具快到碗里来！，App原型设计工具使用心得（上）&amp; App原型设计工具使用心得（下），你用哪种工具进行iOS app自动化功能测试？，iOS 开发者必知的 75 个工具" By @CocoaChina</li>
</ol>
</li>
</ul>


<hr />

<h2>Swift教程</h2>

<ul>
<li>苹果官方

<ol>
<li> <a href="https://developer.apple.com/wwdc/resources/sample-code/">示例代码</a>: "比起GitHub上的开源项目来说，官方的代码我觉得是更有参考价值的，比如Session 406的代码，Lister，就用一个Swift实现的包含OSX和iOS的" By <a href="http://weibo.com/lancy1014">@晨钰Lancy</a></li>
<li> Swift入门(视频翻译 By <a href="http://weibo.com/zhaozhecleric">@赵哲A</a>): <a href="http://v.youku.com/v_show/id_XNzI1MTQ5NzYw.html">A001.01</a>, <a href="http://v.youku.com/v_show/id_XNzI1MTU2OTU2.html">A001.02</a>, <a href="http://v.youku.com/v_show/id_XNzI4MDE5ODYw.html">A001.03</a>, <a href="http://v.youku.com/v_show/id_XNzMxODgxNDM2.html">A001.04</a>： WWDC 2014官方Session 402视频翻译。讲得很细致，口齿清晰，英语发音准确，声音非常好听。</li>
<li> Swift进阶(视频翻译 By <a href="http://weibo.com/zhaozhecleric">@赵哲A</a>): <a href="http://v.youku.com/v_show/id_XNzM4NTAwNzk2.html">A002.01</a>, <a href="http://v.youku.com/v_show/id_XNzQ1NDQzNzYw.html">A002.02</a>, <a href="http://v.youku.com/v_show/id_XNzUyNzA2NDYw.html">A002.03</a>, <a href="http://v.youku.com/v_show/id_XNzU5MjA5Mzgw.html?f=22519841">A002.04</a>, <a href="http://v.youku.com/v_show/id_XNzU5MjE5MjI4.html?f=22519841">A002.05</a> WWDC 2014官方Session 403视频翻译。</li>
<li> <a href="https://github.com/CocoaChinaTranslationTeam/TestingWithXcodeDocsCN">Testing with Xcode</a>: 本文的目的在于让测试成为你软件开发的重要组成部分，并使测试更方便并易于使用。</li>
</ol>
</li>
<li><p>中译教程</p>

<table>
<thead>
<tr>
<th>译文 </th>
<th> 译者 </th>
<th>原文 </th>
<th> 来源</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="http://www.devtalking.com/articles/adaptive-layout-1/">Swift自适应布局（Adaptive Layout）教程（一）</a></td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a></td>
<td><a href="http://www.raywenderlich.com/83276/beginning-adaptive-layout-tutorial">Beginning Adaptive Layout Tutorial</a></td>
<td><a href="http://www.raywenderlich.com">raywenderlich</a></td>
</tr>
<tr>
<td><a href="http://www.cocoachina.com/ios/20141010/9860.html">如何使用iOS 8的虚化效果</a></td>
<td><a href="http://weibo.com/cocoachina">@CocoaChina</a></td>
<td><a href="http://www.raywenderlich.com/84043/ios-8-visual-effects-tutorial">iOS 8 Visual Effects Tutorial</a></td>
<td><a href="http://www.raywenderlich.com">raywenderlich</a></td>
</tr>
<tr>
<td><a href="http://www.jianshu.com/p/e82eee3d9228">Web工程师和设计师必须要知道的iOS 8的十个变化</a></td>
<td><a href="http://weibo.com/foru17">@罗罗磊磊</a></td>
<td><a href="http://www.mobilexweb.com/blog/safari-ios8-iphone6-web-developers-designers">iOS 8 and iPhone 6 for web developers and designers: next evolution for Safari and native webapps</a></td>
<td><a href="http://www.mobilexweb.com/">mobilexweb</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/how-to-create-action-extension/">如何在Swift中创建Action扩展</a></td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a></td>
<td><a href="http://nsnerd.co/action-extension-in-swift/">Action Extension in Swift</a></td>
<td><a href="http://nsnerd.co/">nsnerd.co</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/ios8-day-by-day-day2-sharing-extension/">iOS8 Day-by-Day :: Day2 :: 分享应用扩展</a></td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a></td>
<td><a href="http://www.shinobicontrols.com/blog/posts/2014/07/21/ios8-day-by-day-day-2-sharing-extension">iOS8 Day-by-Day :: Day 2 :: Sharing Extension</a></td>
<td><a href="http://www.shinobicontrols.com/">shinobicontrols</a></td>
</tr>
<tr>
<td><a href="http://objccn.io/issue-16-1/">Swift 的强大之处</a></td>
<td><a href="http://cn.gohoopster.com">李子轩</a></td>
<td><a href="http://www.objc.io/issue-16/power-of-swift.html">The Power of Swift</a></td>
<td><a href="http://objc.io">objc.io</a></td>
</tr>
<tr>
<td><a href="http://objccn.io/issue-16-2/">结构体和值类型</a></td>
<td><a href="http://weibo.com/onetaway">@Onetaway</a></td>
<td><a href="http://www.objc.io/issue-16/swift-classes-vs-structs.html">A Warm Welcome to Structs and Value Types</a></td>
<td><a href="http://objc.io">objc.io</a></td>
</tr>
<tr>
<td><a href="http://objccn.io/issue-16-3/">Swift方法的多面性</a></td>
<td><a href="http://weibo.com/u/1709283185">@唯木念</a></td>
<td><a href="http://www.objc.io/issue-16/swift-functions.html">The Many Faces of Swift Functions</a></td>
<td><a href="http://objc.io">objc.io</a></td>
</tr>
<tr>
<td><a href="http://objccn.io/issue-16-4/">Swift 的函数式 API</a></td>
<td><a href="http://weibo.com/small1030light">@请叫我汪二</a></td>
<td><a href="http://www.objc.io/issue-16/functional-swift-apis.html">Functional APIs with Swift</a></td>
<td><a href="http://objc.io">objc.io</a></td>
</tr>
<tr>
<td><a href="http://objccn.io/issue-16-5/">Playground快速原型制</a></td>
<td><a href="http://www.codingtime.info">Programmer.Du</a></td>
<td><a href="http://www.objc.io/issue-16/rapid-prototyping-in-swift-playgrounds.html">Rapid Prototyping in Swift Playgrounds</a></td>
<td><a href="http://objc.io">objc.io</a></td>
</tr>
<tr>
<td><a href="http://www.devtalking.com/articles/custom-subscripts-in-swift/">在Swift中自定义下标</a></td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a></td>
<td><a href="http://www.codingexplorer.com/custom-subscripts-swift">Custom Subscripts in Swift</a></td>
<td><a href="http://www.codingexplorer.com/">codingexplorer</a></td>
</tr>
<tr>
<td><a href="http://beyondvincent.com/blog/2014/08/28/How-To-Make-a-Custom-Control-in-Swift/">如何用 Swift 语言构建一个自定控件</a></td>
<td><a href="http://weibo.com/beyondvincent">@BeyondVincent</a></td>
<td> <a href="http://www.raywenderlich.com/76433/how-to-make-a-custom-control-swift">How To Make a Custom Control in Swift</a> </td>
<td> <a href="http://www.raywenderlich.com/">raywenderlich</a></td>
</tr>
<tr>
<td>UIKit重力学（<a href="http://www.devtalking.com/articles/swift-uikit-dynamics-1/">一</a>, <a href="http://www.devtalking.com/articles/swift-uikit-dynamics-2/">二</a>） </td>
<td><a href="http://weibo.com/jacefu">@DevTalking</a></td>
<td> <a href="http://www.raywenderlich.com/76147/uikit-dynamics-tutorial-swift">UIKit Dynamics Tutorial in Swift</a> </td>
<td><a href="http://www.raywenderlich.com/">raywenderlich</a></td>
</tr>
<tr>
<td><a href="http://swiftist.org/topics/129">Swift中的延迟加载</a></td>
<td><a href="http://weibo.com/u/5171245144">@Swiftist</a></td>
<td><a href="http://mikebuss.com/2014/06/22/lazy-initialization-swift/">Lazy Initialization with Swift</a></td>
<td><a href="http://mikebuss.com/">mikebuss</a></td>
</tr>
<tr>
<td><a href="http://www.cocoachina.com/applenews/devnews/2014/0703/9022.html">The Swift Programming Language: 实验项目相关解决方案</a></td>
<td><a href="http://weibo.com/cocoachina">@CocoaChina</a></td>
<td><a href="http://www.swiftcast.tv/articles/swift-programming-language-solutions-experiments">The Swift Programming Language: Solutions to Experiments</a></td>
<td><a href="http://www.swiftcast.tv/">swiftcast.tv</a></td>
</tr>
</tbody>
</table>
</li>
<li><p><a href="http://v.youku.com/v_show/id_XNzg4MDM0NDgw.html?f=22866104">S008 - iOS 应用基础</a>： 教程对于最基础的UI编程讲得特别细，时有反复强调Swift基础特性。个人感觉这个适合无iOS UI编程经验的同学，甚至也适合无Swift基础的同学。By <a href="http://weibo.com/zhaozhecleric">@赵哲A(</a></p></li>
<li><a href="http://www.sitepoint.com/getting-app-ready-ios-8/">Getting Your App Ready for iOS 8</a>：让你的应用程序适配iOS 8，这篇文章总结的比较完整。 By <a href="http://weibo.com/517433742">@Janselz</a></li>
<li><a href="https://github.com/0dayZh/VectorPDFSupportTest">VectorPDFSupportTest</a>："Xcode 6 支持 vector PDF 来支持多尺寸的图片，虽然是伪矢量图，但我还是写了点东西来把这东西说清楚。" By <a href="http://weibo.com/chinawangchen">@你全家都快到碗里来</a></li>
<li><a href="https://github.com/nettlep/learn-swift">nettlep/learn-swift</a>: 学习《Swift Programming Language》的同时，配合运行这些playgrounds，对于快速掌握Swift最合适不过了.</li>
<li><a href="https://github.com/hackswift/swift-reference-pg">Swift Reference Playground</a>/<a href="https://github.com/hackswift/swift-operators-pg">Swift Operators Playground</a>: "Swift Reference is a handy playground file that can be used when you are starting to learn swift.It covers the basic syntax definitions and different ways to use" 初学Swift语言的同学一定先玩玩这个，可以让您更快感性的了解Swift语言语法、操作符及语言新特点（代码涵盖地比较完整）。</li>
<li><a href="https://github.com/ShinobiControls/iOS8-day-by-day">ShinobiControls/iOS8-day-by-day</a>：追剧iOS 8开发，文章几乎篇篇带示例项目。iOS 8开发者进阶必备！</li>
<li><a href="http://blog.sina.com.cn/virtualgs">VirtualGS教程</a> <a href="http://weibo.com/limtc">(By @林泰前)</a>: 几十年的老程序员，资深的iOS开发工程师，把自己儿子培养成苹果应用商店最年少的应用开发者，哪里能找到这样优质的编程老师？ 教程包括《How to》系列连载和《图形编程》示例项目</li>
<li><a href="http://www.imooc.com/view/149">Swift Weather APP</a>:“林永坚老师将带领大家使用Swift语言开发一个完整的天气 iOS APP。同时大家能够学习到Interface Builder、CocoaPods、Core Location、AFNetworking的使用，以及如何通过Swift调用Objective-C组件”</li>
<li><a href="http://www.imooc.com/learn/173">使用Swift开发iOS8 App实战</a> ：实战学习是最有效的编程学习方法，推荐<a href="http://weibo.com/yongjianlin">@林永坚</a>老师的实战视频。教程代码：1.<a href="https://github.com/JakeLin/ChineseZodiac">ChineseZodiac</a>, 2. <a href="https://github.com/JakeLin/LoveFinder">LoveFinder</a>, 3. <a href="https://github.com/JakeLin/BeautyGallery">BeautyGallery</a></li>
<li><a href="http://jamesonquave.com/blog/developing-ios-8-apps-using-swift-animations-audio-and-custom-table-view-cells/">Developing iOS 8 Apps Using Swift (I) – Animations, Audio, and Custom Table View Cells</a>: "这个教程大概7篇blog，一步步讲解了一个『itunes music search app』的制作对于async http, api delegate, 异步图片，动画，代码分层，interface builder都做了清晰的介绍。" By <a href="https://github.com/gaohailang">gaohailang</a></li>
<li><a href="http://iosdevtips.co/post/88481653818/twitter-ios-app-bird-zoom-animation">Replicating Twitter’s bird zoom startup animation (in Swift!)</a> (<a href="https://github.com/rounak/TwitterBirdAnimation">源代码</a>): 这是一个有关用Swift开发简单动画效果的编程示例，示例开发灵感来源于近期的Twitter iOS版小鸟启动动画。</li>
<li><a href="http://www.jikexueyuan.com/study/89.html">WWDC2014 详解OSX/iOS8/Swift语言</a>: "极客学院全国首发课程，详解OSX/iOS8新特性/崭新编程语言Swift！极客学院团队通宵录制、上传，只为在这一刻把最新最实战的课程呈现给开发者"</li>
<li><a href="http://swiftist.org/topics/96">从零开始学Swift计时器App开发</a>（<a href="https://github.com/lifedim/SwiftCasts/tree/master/001_swift_counter/SwiftCounter">源代码</a>）: "通过完成此教程，我对Swift语言的理解也更进了一步。Swift是一门全新的语言，作为开发者，我们需要不断加深对这门语言的理解，并灵活使用语言提供的特性来编程。..."  by <a href="http://weibo.com/u/1780854425">@李洁信</a></li>
<li><a href="http://www.starming.com/index.php?v=index&amp;view=46">如何用Swift写UIDynamic</a>：如何用Swift写UIDynamic。代码虽短，功能性完整。可读性也很赞！By <a href="http://weibo.com/allstarming">@戴铭</a></li>
<li><a href="http://idlelife.org/archives/716">Swift如何检查系统版本</a>：介绍使用Swift语言检测操作系统版本的方法。 译者：<a href="http://weibo.com/pockry">@pockry</a> 原文：<a href="http://nshipster.com/swift-system-version-checking/">Swift System Version Checking</a> 作者：<a href="https://github.com/mattt">Mattt Thompson </a></li>
<li><a href="http://robb.is/working-on/a-hamburger-button-transition/">How to build a nice Hamburger Button</a>: 小小的按钮，无论在设计上，还是代码上，都进行了精雕细琢。期待作者能尽早发布更完整的Hamburger Buttons. 源码：<a href="https://github.com/robb/hamburger-button">robb/hamburger-button</a></li>
<li><a href="http://holko.pl/2014/07/15/hamburger-button-animation/">Hamburger Button Animation</a>: 又一个实用的Hamburger Button。另外，看了作者的<a href="http://holko.pl/">博客</a>，感觉他对iOS Animation编程非常有经验，强烈推荐关注。源码：<a href="https://github.com/fastred/HamburgerButton">fastred/HamburgerButton</a></li>
<li><a href="http://www.devtalking.com/articles/create-documentation-in-playground/">在Playground中添加说明文档</a>：教你如何在Playground中添加说明文档。By <a href="http://weibo.com/jacefu">@DevTalking</a></li>
<li><a href="https://blog.avoscloud.com/1407/">使用 Swift 和 AVOSCloud 构建 iOS 应用</a>:"使用 AVOSCloud SDK 和 Swift 构建 iOS 应用 | AVOS Cloud Blog" By <a href="http://weibo.com/lazyseq">@AVOS江宏</a> ｜ 这就是业界的速度，先机才是致胜法宝。</li>
<li><a href="http://www.devtalking.com/articles/adaptive-layout-for-iphone6-1/">为iPhone6设计自适应布局</a>（<a href="http://www.devtalking.com/articles/adaptive-layout-for-iphone6-1/">一</a>、<a href="http://www.devtalking.com/articles/adaptive-layout-for-iphone6-2/">二</a>） ："当你们学习完这篇文章后，你们应该会比较自如的使用 storyboard、constaints、size classes 这三个Apple在Xcode里提供的工具，去探索和构建巧妙的自适应布局。" 译者：<a href="http://weibo.com/jacefu">@DevTalking</a> 原文：<a href="http://mathewsanders.com/designing-adaptive-layouts-for-iphone-6-plus/">ADAPTIVE LAYOUTS FOR iPHONE 6</a></li>
<li><a href="http://idlelife.org/archives/755">iOS App集成Apple Pay教程</a>："Apple Pay还给开发者带来了处理支付的新渠道，用户将期望在应用中使用它，因为它将验证和交易极端简化，仅需手指轻轻一触即可完成。如果应用里面有涉及到交易，开发者很有必要集成Apple Pay。那么如何将Apple Pay功能集成到你的应用里呢？" 可惜Demo是Objective-C版本的。 译者：<a href="http://weibo.com/pockry">@pockry</a> 原文：<a href="http://java.dzone.com/articles/integrating-your-ios-app-apple">Integrating Your iOS App with Apple Pay</a></li>
<li><a href="http://onevcat.com/2014/10/ib-customize-view/">WWDC 2014 Session笔记 - 可视化开发，IB 的新时代</a>："通过一个简单例子介绍了 Xcode 6 的 IB 中自定义 view 的基本使用。" 作者：<a href="http://weibo.com/onevcat">@onevcat</a></li>
</ul>


<h2>开发技巧</h2>

<ul>
<li><a href="https://medium.com/ios-os-x-development/learnings-from-building-a-today-view-extension-in-ios-8-710d5f481594">Problems With Building a Today Extension in iOS 8</a>：构建Today扩展时可能碰到的一些问题。</li>
<li><a href="http://io-meter.com/2014/10/24/develop-for-yosemite-some-tips/">开发Yosemite几个小技巧</a>:  "Apple 终于发布了 Xcode 6.1，带来了 Swift for OSX 等多个更新， 这几天我简单研究了下在 Yosemite 下实现一些新的小需求的方法， 这里使用 Swift 语言描述总结一下。" 作者：<a href="http://weibo.com/u/2717070362">@diumoo</a></li>
<li><a href="http://chun.tips/blog/2014/10/23/xiang-jie-uicoordinatespacehe-uiscreenzai-ios-8shang-de-zuo-biao-wen-ti/">详解UICoordinateSpace和UIScreen在iOS 8上的坐标问题</a>：今天在整理AutoLayout API时，发现了一个关于UIScreen 坐标的坑。作者：<a href="http://weibo.com/pockry">@pockry</a></li>
<li><a href="http://idlelife.org/archives/742">我在开发第一个Swift App过程中学到的四件事</a>："本文翻译自raywenderlich.com，作者Greg Heo，是Razeware（Ray创办的公司）的员工，这是他为讲授iOS 8 App Extensions视频教程而实际使用Swift开发了一款App的经验，来看看他的心得体验。" 译者：<a href="http://weibo.com/pockry">@pockry</a></li>
<li><a href="https://github.com/nixzhu/dev-blog/blob/master/2014-06-12-LTBouncyPlaceholder.md">LTBouncyPlaceholder代码解读</a>: "我希望你已经下载了 LTBouncyPlaceholder 的 Demo ，用 Xcode 6 打开并编译、运行，然后在界面中显示的几个 UITextField 里输入一些文字来体验这个扩展。看到 Placeholder 的动画了吗？" By <a href="http://weibo.com/nixzhu">nixzhu</a></li>
<li><a href="http://blog.csdn.net/twlkyao/article/details/30536397#1536434-tsina-1-70302-66a1f5d8f89e9ad52626f6f40fdeadaa">Swift中下划线的妙用</a>: "在Swift中，下划线有很多妙用，这里将已经看到的妙用进行总结，希望可以帮助更多学习Swift的朋友。..." By <a href="http://weibo.com/105712625">@twlkyao</a></li>
<li><a href="http://blog.txx.im/blog/2014/06/07/wwdc14-session-402/">WWDC14 Session 402 学习笔记</a> By <a href="http://weibo.com/rpplusplus">@糖炒小虾_txx</a></li>
<li><a href="http://blog.sina.com.cn/s/blog_877e9c3c0101sexl.html">Swift与Objective-C混编高级教程之混编框架的创建和调用</a></li>
<li><a href="https://github.com/hpique/SwiftSingleton">SwiftSingleton</a>: 三种方法介绍了Swift中Singleton的写法</li>
</ul>


<hr />

<h2>Swift项目</h2>

<h3>1. 实用类库</h3>

<p> 以下实用类库仅做为快速参考，更多实用类库需求，可以去这里<a href="http://www.swifttoolbox.io/">(Swift toolbox is a community-supported catalog
of iOS and OSX libraries)</a> (By <a href="https://www.facebook.com/xpizzle">Adam Leonard</a> from <a href="[http://swiftcast.tv">swiftcast.tv</a>), 这个网站收藏了GitHub开源社区中优质Swift资源库，并提供了分类及查询服务。</p>

<ul>
<li><p><a href="https://github.com/mattt">Mattt Thompson </a>: 著名开源作者，开发了知名的<a href="https://github.com/afnetworking/afnetworking">AFNetworking</a>网络库。也是知名开发博客<a href="http://shipster.com/">NSHipster</a>网站主。</p>

<table>
<thead>
<tr>
<th>类库 </th>
<th> 相关文章 </th>
<th> 备注</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://github.com/Alamofire/Alamofire">Alamofire/Alamofire</a> </td>
<td> <a href="http://nshipster.com/alamofire/">Alamofire</a></td>
<td> 网络请求和相关的封装</td>
</tr>
<tr>
<td><a href="https://github.com/mattt/Euler">mattt/Euler</a> </td>
<td> <a href="http://nshipster.com/swift-operators/">Swift Operators</a> </td>
<td> 这样写是否很数学、很逻辑？∛27÷3±5, ∑[3,1,2], ~0⊻1</td>
</tr>
<tr>
<td><a href="https://github.com/mattt/Surge">mattt/Surge</a> </td>
<td></td>
<td> 基于苹果Accelerate高性能计算框架库，计算效率提升惊人</td>
</tr>
<tr>
<td><a href="https://github.com/mattt/Literally">mattt/Literally</a></td>
<td><a href="http://nshipster.com/swift-literal-convertible/">Swift Literal Convertibles</a></td>
<td> 常用数据类型的使用及转换工具库</td>
</tr>
</tbody>
</table>
</li>
<li><p>工具类</p>

<ul>
<li><a href="https://github.com/ankurp/Dollar.swift">Dollar</a>: 尤其在Array和Dictionary的支持上（实现类库仅一个Dollar.swift文件）。用过Javascript版的Lo-Dash或underscore就知道其实用程度。它是一套函数化编程的工具库。另一个类似的更完整的版本是<a href="https://github.com/pNre/ExSwift">ExSwift</a>，它的实现基于对象化扩展的。</li>
<li><a href="https://github.com/pNre/ExSwift">ExSwift</a>: 实用类扩展库。另一个Lo-Dash或underscore的Swift版本实现，相对于Dollar.swift，此版本有更完整的API实现。包括了对Array, Int, String, Float, Range, Dictionary, NSArray的扩展及其它实用方法。完全遵循面向对象的扩展原则。</li>
<li><a href="https://github.com/lingoer/SwiftyJSON">lingoer/SwiftyJSON</a>:这是解析JSON字符串封装类。实现功能与Javascript中的JSON.parse相近，使用方便。By <a href="http://weibo.com/u/1671421905">@lingoer</a></li>
<li><a href="https://github.com/SwiftyJSON/Alamofire-SwiftyJSON">SwiftyJSON/Alamofire-SwiftyJSON</a> ：简单地整合Alamofire和SwiftyJSON后，远程JSON使用方便了。</li>
<li><a href="https://github.com/typelift/Basis">typelift/Basis</a>：这个实用类库支持范围很宽范，封装主要以简化及方便调用系统API为主，使程序代码看上去更优雅。遗憾地是，目前作者并没有提供API文档或示例代码，对于初学者使用会额外带来一点点学习成本。</li>
<li><a href="https://github.com/owensd/json-swift">owensd/json-swift</a>: 功能与Swifty几乎一致，使用上要更方便。</li>
<li><a href="https://github.com/gfx/Swift-JsonSerializer">gfx/Swift-JsonSerializer</a>：JSON解析又多了一种选择。</li>
<li><a href="https://github.com/hubertr/Swell">hubertr/Swell</a>： 同时支持Swift和OBJC的Log实用类。喜欢Log4j风格的日志管理类的同学可以收入。</li>
<li><a href="https://github.com/yeahdongcn/RSBarcodes_Swift">RSBarcodes_Swift</a>: "RSBarcodes allows you to read 1D and 2D barcodes using metadata scanning capabilities introduced with iOS 7 and generate the same set of barcode images for displaying and sharing." By <a href="http://weibo.com/r0ckstar">@yeahdongcn</a> Swift语言版二维码识别及生成类库。</li>
<li><a href="https://github.com/SwiftP2P/SwiftSSL">SwiftP2P/SwiftSSL</a>：常用 Digest 和 HMAC 的封装。如此封装后，使用加密算法确实很方便。很不错的一个国产"轮子"！By <a href="http://weibo.com/chinawangchen">@你全家都快到碗里来</a></li>
<li><a href="https://github.com/Hearst-DD/ObjectMapper">Hearst-DD/ObjectMapper</a>：对象与JSON互转实用类库。需要的同学可以收一下。</li>
<li><a href="https://github.com/DaveWoodCom/XCGLogger">DaveWoodCom/XCGLogger</a> ： 这是一款功能比较健全日志输出框架（Log4Swift）。之前推荐过一款类似的 hubertr/Swell，但它的功能明显没有这款强大。</li>
<li><a href="https://github.com/air/JSONHelper">isair/JSONHelper</a> ：又一款JSON转对象类库，算上，lingoer/SwiftyJSON，owensd/json-swift，gfx/Swift-JsonSerializer，已经有四款了。同学们根据喜好及需求，择优使用吧。</li>
</ul>
</li>
<li><p>存储</p>

<ul>
<li><a href="https://github.com/FahimF/SQLiteDB">SQLiteDB in Swift</a>: "This is a basic SQLite wrapper for Swift. It is very simple at the moment and does not provide any advanced functionality. Additionally, it's not pure Swift at the moment due to some difficulties in making all of the necessary sqlite C API calls from Swift."</li>
<li><a href="http://realm.io/">Realm - a mobile database</a>: Realm主打移动数据库。除了更轻量，甚至还可以应用到可穿戴。低耦、面向对象的设计风格也是非常亮丽的。</li>
<li><a href="https://github.com/BjornRuud/Swiftache">BjornRuud/Swiftache</a>: Mustache的Swift语言实现版本。</li>
<li><a href="https://github.com/nerdyc/Squeal">nerdyc/Squeal</a>：一套非常完善的SQLite数据库访问API，无论建库，建表，CRUD等常用数据库操作命令都进行了很好的封装，另外，版本管理、事务管理、并发管理、命令执行及Prepare Statement等都提供相应支持。它是一套不可多得的SQLite管理访问库。</li>
<li><a href="https://github.com/stephencelis">stephencelis/SQLite.swift</a>：简单、轻量，或是使用上最SQL的SQLite封装库。</li>
<li><a href="https://github.com/Haneke/HanekeSwift">Haneke/HanekeSwift</a>：貌似这个轻量地带缓存图片组件还不错。主要功能包括图片二级缓存、异步加载、后台执行、自动缩放等。感兴趣的同学可以试用一下。</li>
<li><a href="https://github.com/SugarRecord/SugarRecord">SugarRecord/SugarRecord</a>：相对于SQL，CoreData可以更方便、高效存储数据，而SugarRecord类库可以让你更方便的使用CoreData，同时作者已经封装好iCloud，使你的应用开发更如虎添翼。</li>
<li> <a href="https://github.com/michaelarmstrong/SuperRecord">michaelarmstrong/SuperRecord</a> ： Swift版CoreData框架扩展类库。相对于同类型CoreData框架库SugarRecord/SugarRecord http://t.cn/RhYLS4n ，SuperRecord要简单、轻量得多。很棒的快速开发类库。</li>
<li><a href="https://github.com/aschuch/AwesomeCache">aschuch/AwesomeCache</a>：Swift语言写的高效能缓存对象存储及管理，定义及使用简单、易于理解。支持为每个Cache对象设定缓存有效期。</li>
<li><a href="https://github.com/daltoniam/Skeets">daltoniam/Skeets</a>：网络图片的获取、缓存及显示类库，支持缓存的清理及时效性管理。</li>
</ul>
</li>
<li>远程访问

<ul>
<li><a href="https://github.com/hallas/agent">Minimalistic Swift HTTP request agent for iOS and OS X</a>: 一个简单、小巧、实用的HTTP请求Swift语言实现类（仅一个Agent.swift类）</li>
<li><a href="https://github.com/lingoer/GRequest">lingoer/GRequest</a>:"@李洁信：个人认为AFNetworking这种较重的第三方网络库将逐渐淡出舞台，而像楼主这种基于NSURLSession并充分利用Swift特性写出来的小而美的库会受到更多人的青睐！" 作者解读<a href="http://swiftist.org/topics/178">《GRequest for HTTP Request》</a>。</li>
<li><a href="https://github.com/daltoniam/SwiftHTTP">daltoniam/SwiftHTTP</a>: Thin wrapper around NSURLSession in swift. Simplifies HTTP requests.感兴趣的可以看看代码，比较与lingoer/GRequest差别。</li>
<li><a href="https://github.com/AshFurrow/Moya">AshFurrow/Moya</a>: 如果你需要<a href="https://github.com/artsy/eidolon/issues/9">如此功能</a>的Swift网络API，可以考虑使用它。它基于Alamofire, swfitz等优秀开源类实现。</li>
<li><a href="https://github.com/aleclarson/emitter-kit">aleclarson/emitter-kit</a>:用EmitterKit代替NSNotificationCenter。这个库貌似短小、精悍、实用的样子。更重要是语法精练。</li>
<li>_<a href="https://github.com/daltoniam/starscream">daltoniam/starscream</a>：Swift版本WebSocket客户端类库，支持iOS/OS X 。 使用方便，跨平台开发不可或缺的"轮子"。</li>
</ul>
</li>
<li>社交网络

<ul>
<li><a href="https://github.com/lingoer/SwiftWeiboKit">lingoer/SwiftWeiboKit</a>: "封装了整个OAuth2.0的授权流程,并提供了几个简便易用的请求方法"</li>
<li><a href="https://github.com/mattdonnelly/Swifter">A Twitter framework for iOS &amp; OS X written in Swift</a>: 一套很完整的Twitter访问框架类库，支持iOS/OS X</li>
</ul>
</li>
<li>框架

<ul>
<li><a href="https://github.com/robb/Cartography">robb/Cartography</a>: Set up your Auto Layout constraints declaratively. 这是有关自动布局约束一个实用的Swift项目，代码看似简单清晰，不过由于设计巧妙。<a href="http://cheunghy.github.io/blog/2014/10/12/intro-to-cartography/">代码解读</a> By <a href="http://weibo.com/kaiyuz">@kaiyuz</a></li>
<li><a href="https://github.com/railsware/Sleipnir">railsware/Sleipnir</a>：一个基于Swift的行为驱动开发框架(BDD-style framework)。API安装，示例及说明相对比较齐全。</li>
<li><a href="https://github.com/Quick/Quick">Quick/Quick</a>：另一款基于Swift的行为驱动开发框架。</li>
<li><a href="https://github.com/inamiy/SwiftTask">inamiy/SwiftTask</a>： 一个很标准的任务及其生命周期管理类库。作者还附上了一个基于Alamofire库完成的网络文件下载的任务管理示例。</li>
<li><a href="https://github.com/inamiy/SwiftState">inamiy/SwiftState</a>：Swift版本State Machine，这是SwiftTask的姐妹篇。开发过Workflow类应用的同学有没有很亲切。</li>
<li><a href="https://github.com/colemancda/NetworkObjects">colemancda/NetworkObjects</a>：基于Swift的轻量版HttpServer框架，可以做为iOS/OS X分布式对象的替代。可惜缺少演示或示例代码。</li>
</ul>
</li>
<li>UI组件

<ul>
<li><a href="https://github.com/jcavar/refresher">jcavar/refresher</a>：一个常用的下拉即刷新列表工具类，提供开放接口定制刷新动态变换效果。</li>
<li><a href="https://github.com/ariok/BWWalkthrough">ariok/BWWalkthrough</a>：让你的页面切换动起来，示例效果杠杠的。作者还提供了比较完整的开发文档及示例解说。</li>
<li><a href="https://github.com/vikmeup/SCLAlertView-Swift">vikmeup/SCLAlertView-Swift</a>: 动画效果弹出框封装库（管理于CocoaPods），使用也足够方便。试着运行了一下，效果还不错。</li>
<li><a href="https://github.com/varshylmobile/MapManager">varshylmobile/MapManager</a>:地图管理封装库（默认支持Google和Apple地图服务）。</li>
<li><a href="https://github.com/varshylmobile/LocationManage">varshylmobile/LocationManage</a>：位置管理封装库（默认支持Google和Apple地图服务）。</li>
<li><a href="https://github.com/ortuman/SwiftForms">ortuman/SwiftForms</a>：这个表单递交库简单实用，支持主要数据类型及定制。快速开发利器。</li>
</ul>
</li>
</ul>


<h3>2. 示例项目</h3>

<ul>
<li><a href="https://github.com/ipader/SwiftGuide/tree/master/VirtualGS">VirtualGS教程示例</a>: 以下示例程序来源于林泰前老师<a href="http://weibo.com/limtc">微博</a>或<a href="http://blog.sina.com.cn/virtualgs">博客</a>发布，为方便大家学习Swift编程，有幸获得林老师的准许在这里发布。</li>
<li><a href="https://github.com/onevcat/Easy-Cal-Swift">Easy-Cal-Swift</a>: "实在忍不了Swift的数字计算时候的好麻烦的强制转换了，重载了一下加减乘除之类的操作符，这样就不用显式地转换类型了...（对于像我这样现在连补全都没有的孩子来说，能省好多时间啊- -）" By <a href="http://weibo.com/onevcat">@onevcat</a></li>
<li><a href="https://github.com/roadfire/SwiftFonts">An app to list the available fonts on iOS</a>: 用Swift语言调用UIKit，列出设备内所有字体名称的小程序。</li>
<li><a href="https://github.com/jxd001/Swift-ZhihuDaily">Swift版的知乎日报</a>: 学习一门新语言，光看是没有用的，想要快速的掌握它，就得投入到真实项目的开发中，仿照@YANGReal 的糗事百科，做了一个Swift版的知乎日报</li>
<li><a href="https://github.com/wantedly/swift-rss-sample">Swift RSS Sample</a>: 用Swift语言开发的RSS阅读器</li>
<li><a href="https://github.com/sxyx2008/Swift-PM25">Swift版PM2.5的例子</a>: 一个很好的Swift与Objective C协同工作GitHub开源项目。用到的开源类库有<a href="https://github.com/topfunky/hpple">TFHpple</a>: 以XPath方式解析HTML，<a href="https://github.com/vikmeup/SCLAlertView-Swift">SCLAlertView</a>: 使用Swift写的AlertView SVProgressHUD 进度条 By <a href="http://weibo.com/qq184675420">@荧星诉语</a></li>
<li><a href="https://github.com/lexrus/LTMorphingLabel">lexrus/LTMorphingLabel</a>: 实现文字飘入飘出的效果。效果非常赞！</li>
<li><a href="https://github.com/android1989/CharacterText">android1989/CharacterText</a>: 相比<a href="https://github.com/lexrus/LTMorphingLabel">lexrus/LTMorphingLabel</a> 的各种酷炫效果，这个版本比较简单实用。</li>
<li><a href="http://t.cn/RveAZ53">practicalswift/Pythonic.swift</a>: 用Swift语言实现Python标准库的一部分。然后，用Swift写一段Python风格的程序，这是Python程序员想要的吗？相信这不过是一个实验，以此说明Swift语言的多变性、动态性的能力。</li>
<li><a href="https://github.com/AshRobinson/GoogleWearAlert">AshRobinson/GoogleWearAlert</a>: Swift语言实现模拟Google Wear风格Alert窗口。</li>
<li><a href="https://github.com/rafaelconde/ios8-ui-kit">rafaelconde/ios8-ui-kit</a>: IOS 8 UI KIT + FOR SKETCH — 最新IOS8免费设计资源</li>
<li><a href="https://github.com/gemtot/iBeacon">gemtot/iBeacon</a>: Swift版iBeacon简单项目（支持最新Beta 6编译）。感兴趣的同学可以学习一下。有关于Passbook应用及Passkit框架编程知识这里有一篇网友较早发布的<a href="http://blog.csdn.net/eqera/article/details/8136880">《iOS 6 - PassKit编程指南》</a></li>
<li><a href="https://github.com/evnaz/ENSwiftSideMenu">evnaz/ENSwiftSideMenu</a>：一个简单的Slide侧拉菜单实现。使用很方便：sideMenu = SideMenu(sourceView: self.view, menuData: ["UIDynamics", "UIGestures", "UIBlurEffect"])</li>
<li><a href="https://github.com/iluuu1994/Pathfinder">iluuu1994/Pathfinder</a>：一个有趣的算法类项目。虽然目前只是个演示项目，不过，作者有计划加入更多算法优化程序，同时，也有计划支持3D地图。</li>
<li><a href="(https://github.com/KhaosT/HomeKit-Demo">KhaosT/HomeKit-Demo</a> ：HomeKit演示项目，可以与HomeKit模拟器协同工作。由此进一步思考：HomeKit配合iBeacon、蓝牙，甚至更具DIY潜力的树莓派(Raspberry Pi)组成未来家居智控中心，这个方向上的开发潜力巨大。感兴趣的同学可以关注一下。</li>
<li><a href="https://github.com/mathewsanders/Animated-Transitions-Swift-Tutorial">mathewsanders/Animated-Transitions-Swift-Tutorial</a>: 结合Xcode开发步聚介绍如何开发动画过渡Prototyping Animatted Transition in Swift(Part I)](http://mathewsanders.com/custom-menu-transitions-in-swift/)</li>
<li><a href="https://github.com/mathewsanders/Custom-Menu-Transition-Swift-Tutorial">mathewsanders/Custom-Menu-Transition-Swift-Tutorial</a>: 结合Xcode开发步聚介绍如何开发动画过渡Transition in Swift(Part II)](http://mathewsanders.com/custom-menu-transitions-in-swift/)</li>
<li><a href="https://github.com/vandadnp/iOS-8-Swift-Programming-Cookbook">vandadnp/iOS-8-Swift-Programming-Cookbook</a>：来自《 O'Reilly's iOS 8 Swift Programming Cookbook》的配套示例。书买不买另说，如此即时、完整、丰富的新书示例项目真不多见。悟性好的同学，开发时参考一下示例是不是就不用买书了？</li>
</ul>


<h3>3. 完整项目</h3>

<ul>
<li><a href="https://github.com/fullstackio/FlappySwift">FlappySwift</a>: 用Swift语言实现的 FlappyBird</li>
<li><a href="https://github.com/JakeLin/SwiftWeather">天气预报iOS项目</a>: 新界面还不错，简单，还带点卡通的味道</li>
<li><a href="https://github.com/tnantoka/edhita">tnantoka/edhita</a>：edhita是一款用Swift重写并完全开源的文本编辑器。AppStore上已经有更新版下载。试用后感觉还不错。它甚至支持Markdown, HTML等文件编辑后的预览显示。</li>
</ul>


<h3>4. 需求文档</h3>

<ul>
<li><a href="http://chris.eidhof.nl/posts/swift-ideas.html">Some ideas for projects in Swift</a>: “正在造轮子的不妨看看~” By <a href="http://chris.eidhof.nl/">Chris Eidhof</a>(creator of objc.io)</li>
</ul>


<hr />

<h2>推荐网站</h2>

<ul>
<li><a href="https://github.com/ksm/SwiftInFlux">ksm/SwiftInFlux</a>:作者(Karol Mazur)将Apple Developer Forums上有关Swift特性、缺陷及变更讨论分类汇总并更新到Github，具有很好的可读性。从中可以一窥Swift缺陷及未来潜在地变化。最关键地是有Chris Lattner及核心团队答疑解惑。</li>
<li><a href="http://www.raywenderlich.com/">raywenderlich.com</a>(<a href="http://www.raywenderlich.com/zh-hans/">中文版</a>): 由Ray Wenderlich创建，专注于开发高质量编程指南（近期优质Swift文章及视频教程不断），著名的iOS/OS X博客及开发教程网站，非常适合新手学习。近期第一时间出了<a href="http://www.raywenderlich.com/74832/three-new-swift-books">三本Swift新书</a>。</li>
<li><a href="http://nshipster.com/">NShipster</a> (<a href="http://nshipster.cn/">中译版</a>): 著名开源作者<a href="https://github.com/mattt">Matt Thompson</a>创建的开发技术博客网站，他开发了<a href="https://github.com/afnetworking/afnetworking">AFNetworking</a>网络库，也是非常多产的开源作者。更多了解参考：<a href="http://www.fallhunter.com/p/10709">《COCOA 潮人 MATTT THOMPSON》</a> By <a href="http://weibo.com/fallhunter">@程序员付恒</a></li>
<li><a href="http://jamesonquave.com/blog/">jamesonquave.com</a>: 移动开发者，优秀个人博客（近期文章同样关注于Swift语言，写得很优质）。同时他将于8/30发布一本新书<a href="http://jamesonquave.com/swiftebook/">《Developing iOS 8 Apps in Swift》</a> (Learn To Make Real World iOS 8 Apps)及视频教程。</li>
<li><a href="http://objc.io">objc.io</a>(<a href="http://objccn.io">中译版 By @onevcat 及其朋友们</a>): "关于 Objective-C 最佳实践和先进技术的期刊。 由 Chris Eidhof, Daniel Eggert 和 Florian Kugler 成立于柏林。我们成立 objc.io 的目的是针对深入的、跟所有 iOS 和 OS X 开发者相关的技术话题创造一个正式的平台。“</li>
<li><a href="https://iosdevweekly.com/">iOS Dev Weekly</a>: 收录一周以来iOS开发资讯链接，并于周五发布。由<a href="http://www.twitter.com/daveverwer">Dave Verwer</a>创办，他是一位iPhone和iPad开发者以及培训师。</li>
<li><a href="http://appcoda.com">Appcoda.com</a>:质量很高的一个iOS开发教程站，其中<a href="http://www.appcoda.com/ios-programming-course/">iOS Programming Course</a>这个专题很适合刚接触iOS开发的新手学习。</li>
<li><a href="https://github.com/tangqiaoboy/iOSBlogCN">中文 iOS/Mac 开发博客列表</a>: By <a href="http://weibo.com/tangqiaoboy">@唐巧_body</a></li>
<li><a href="http://www.devtalking.com/">devtalking.com</a>: 高产的中译博客。翻译了官方博客Swift Blog - Apple Developer,《App Extension Programming Guide》。参与翻译了《Swift Programming Language》等。</li>
</ul>


<hr />

<h2>资源合集</h2>

<p>以下是其它开发者社区或Swift爱好者整理的有关Swift语言学习的资源列表，供参考：</p>

<ul>
<li><a href="http://weekly.manong.io/issues/33?ref=swift">码农周刊《Swift 特刊》</a></li>
<li><a href="http://www.cocoachina.com/bbs/read.php?tid=204512">CocoaChina《Swift新手入门汇集帖》</a></li>
<li><a href="http://code.csdn.net/news/2820075">CSDN_CODE《Swift编程语言资料大合集》</a></li>
<li><a href="http://www.infoq.com/cn/news/2014/06/apple-swift-learning-resources">InfoQ《学习苹果Swift语言的一些在线资源(英文)》</a></li>
<li><a href="https://github.com/Lax/iOS-Swift-Demos/wiki">刘兰涛《Swift学习资源》</a> By <a href="http://weibo.com/u/1653644220">@懒桃儿吃桃儿</a></li>
<li><a href="http://www.learnswift.tips/">learnswift.tips</a>: 国外主流Swift学习资源集合。</li>
<li><a href="https://github.com/vsouza/awesome-ios">Awesome iOS</a>: 一个iOS的各类优秀的开源项目集合。真不错！可惜Swift开源项目资源不足。</li>
<li><a href="http://iosdevelopertips.com/">iOS Developer Tips</a>: 还是有关iOS的开发资源及文章合集。</li>
</ul>


<hr />

<h2>开放平台</h2>

<p><em>开放平台相对于Swift语言更具战略意义，这是开发者不得不面对的挑战。也是苹果新一代创新应用的催化剂。通过Extension达成应用之间的协同及通讯，这是对生态内应用开放的基础。让我更期待的是，Extension在Safari Action上实现及支持，这是实现平台开放及跨平台应用最简单直接的方案。</em></p>

<h3>1. 文章精选</h3>

<ul>
<li><a href="http://imtx.me/archives/1898.html">谈谈 iOS 8 和 OS X 10.10 的 Extension</a>: "我个人认为这是 iOS 和 OS X 发展至今非常具有里程碑意义的一处改进，甚至比 UI 上的改变重要的多。我想简单地谈一下为何 Extensions 这么重要。" By <a href="http://weibo.com/tualatrix">@图拉鼎</a></li>
<li><a href="http://wangzz.github.io/blog/2014/06/23/wwdc2014zhi-app-extensionsxue-xi-bi-ji/">App Extensions学习笔记</a>: "系统中支持extension的区域，extension的类别也是据此区分的，iOS上共有Today,Share,Action,Photo,Editing,Storage Provider,Custom keyboard几种，其中Today中的extension又被称为widget" By <a href="http://weibo.com/foogry">@foogry</a></li>
<li><a href="http://sspai.com/26016">详解 iOS 8 的动作扩展</a>: "动作扩展的出现，意味着用户能在应用程序间的切换上花更少的时间和精力，这是相当大的进步。" 译文作者: <a href="http://weibo.com/210100461">@米斯特苹果</a>, 原文:<a href="http://www.imore.com/action-extensions-ios-8-explained">《Action extensions in iOS 8: Explained》</a></li>
<li><a href="http://digi.tech.qq.com/a/20140715/008974.htm">苹果iBeacon让智能家居走进现实</a>: "iBeacon最初发布的时候是一个协议，苹果希望利用这一协议取代NFC技术。iBeacon技术则可以利用支持该技术的设备创建一个信号区域，相当于实现了地理围栏的功能，当其他支持iBeacon技术的设备如手机进入这一区域时，对应的应用程序就会自动连接这一区域的信号网络，或者对用户进行提示"</li>
<li><a href="http://soft.zol.com.cn/465/4659548_all.html">Android L/iOS8/WP8.1到底谁抄了谁？</a>: "我们发现在三场发布会上都听到了观众这样的声音：“无耻抄袭！抄了谁谁谁的！！”，这种事情似乎说也说不清，所以我们决定把这三个新系统放到一起来看看，然后再下结论。"</li>
<li><a href="http://weibo.com/1418521581/BdXqMkHbq#_rnd1405693766206">Google开源字体Noto Sans CJK简介</a>(By <a href="http://weibo.com/ben7th">@洋气书生</a>): 这篇Noto Sans CJK(CJK: Chinese, Japan, Korean)字体普及文章简单、直接、专业，且易于理解。作者友善地提供了一份<a href="http://pan.baidu.com/s/1mg9M8Gg">本地下载</a>，赞一个！P.S. 毫无疑问，新版Android上会很快支持，iOS/Mac/Windows上也会尽快缺省支持吗？</li>
</ul>


<h3>2. 示例项目</h3>

<ul>
<li><a href="https://github.com/dominic/ViewSource">ViewSource(Swift+Objective-C)</a>: 通过iOS 8 Extension实现让Web工程师喜欢的"显示网页源代码"。</li>
<li><a href="https://github.com/indragiek/Unzip">indragiek/Unzip</a>: 浏览ZIP文件的iOS 8 Action扩展。</li>
</ul>


<h3>3. 安全控制</h3>

<ul>
<li><a href="http://objccn.io/issue-14-4/">Back to Mac - XPC by objc.io</a>: XPC 是 OS X 下的一种 IPC (进程间通信) 技术, 它实现了权限隔离, 使得 App Sandbox 更加完备。</li>
</ul>


<h3>4. 实用资源</h3>

<ul>
<li><a href="https://github.com/google/material-design-icons">google/material-design-icons</a> ：对于喜欢 Material Design风格的同学，这是难得好资源。Google提供了极为完整的各种图标（包含iOS各种精度及SVG）设计资源。</li>
</ul>


<hr />

<h2>媒体文章</h2>

<ul>
<li><a href="http://www.pingwest.com/pingraphic-wwdc-2014/">WWDC 2014给开发者带来了什么？</a>: "苹果向第三方开发者开放了大量的可调用特性和4000个新API——指纹识别、云存储、智能家居平台、相机控制、健康数据平台、3D图形API、对iOS 8可扩展程序的调用，以及新的编程语言Swift。PingWest制作了一种信息图带你一览这些新特性"</li>
<li><a href="http://www.36kr.com/p/212612.html">编程语言进化链的顶端：为什么说Swift正在颠覆整个互联网生态？(36Kr)</a>: "Swift 代表的程序猿先进生产力的发展要求（提高编程效率），代表了计算机先进文化的发展方向（语法简洁，现代），代表了广大人民的根本利益（写起来爽，学起来快）。"</li>
<li><a href="http://tech.sina.com.cn/it/apple/2014-06-03/15219414757.shtml">苹果编程语言Swift解析：将推动应用开发巨变(CNET)</a>: "如果编程语言更加易学易用，那么应用开发的门槛将会降低，导致更多新手开发者参与这一行业。"</li>
<li><a href="http://tech.sina.com.cn/it/apple/2014-06-09/08499425442.shtml">外媒评论：苹果公司Swift语言将改变一切</a>: 美国财经网站Motley Fool针对Swift比较中性的一篇评论文章，因此目标读者是非技术人员，可读性还不错。</li>
<li><a href="http://weibo.com/p/1001603720039017670032">苹果新贵 Swift 之前世今生(池建强)</a>: 这篇文章故事性很强，不过，的确把前世今生、来龙去脉交待了一遍，适合刚开始了解swift语言的程序员。</li>
<li><a href="http://qdaily.com/display/articles/1002">WWDC 2014: 给第三方开发者的情书(Qdaily 李如一)</a>: "iOS 和 Mac 上的御用语言 Objective-C 可以追溯至 NeXT 时代，换言之，它已经有超过二十年的历史。Swift 作为苹果发明的编程语言，也继承了苹果产品的传统"</li>
<li><a href="http://www.csdn.net/article/2014-07-08/2820566-swift-receives-significant-update">苹果发布Xcode 6 Beta 3，Swift迎来重大更新！</a>:"苹果在面向开发者推送iOS 8 Beta 3以及OS X Yosemite的第三个预览版的同时，也发布了全新的Xcode 6 Beta 3，并对Swift语言进行了大幅改进。新版Swift修正了许多开发者提出的请求，尤其是对数组进行了重新设计。" 扩展阅读<a href="http://andelf.github.io/blog/2014/07/08/swift-beta3-changes/">《Swift 在 Beta3 中的变化》</a></li>
<li><a href="http://tech.163.com/14/0715/20/A17J8UFT000915BD.html">《连线：为什么苹果Swift语言将会迅速普及》</a>：为苹果硬件开发了15年软件产品的麦克·艾什（Mike Ash）相信，苹果最终会将Swift开源，而且他也相信该语言会在苹果的控制之外发展壮大——因为该语言的开发者拉特纳有着很深的开源情节。“有他在掌舵，我觉得他会做出正确的选择”。原文：<a href="http://www.wired.com/2014/07/apple-swift/">Why Apple’s Swift Language Will Instantly Remake Computer Programming</a></li>
<li><a href="http://weibo.com/swiftguide">Swift中文翻译组</a>: 近30人9天协作完成翻译近670页的英文文档

<ol>
<li> <a href="http://www.36kr.com/p/212811.html">协同写作的力量——中国开发者9天完成《Swift语言》中文版</a>: "详细介绍了GitHub上开源翻译《Swift语言》这个开完项目，发起者是一个90后的大学生，整个翻译团队在9天内完成了近670页的Swift语言文档翻译工作。" By 36Kr</li>
<li> <a href="http://swiftist.org/topics/44">翻译暂时告一段落 写点感想吧</a> : "现在翻译已经告一段落，感觉这段时间的效率真是高的可怕，也许是因为一种成就感，或许带了那么一点功利心（我想每个人或多或少的都会有一点吧）。" By <a href="http://weibo.com/u/3969796349">@CoverXiT</a></li>
<li> <a href="http://www.xiaozhou.net/the-swift-language-2014-06-12.html">Apple的Swift语言</a>: "哥也无意中在Github上看到这个翻译项目，并有幸参与了翻译，算是亲身体验了一把多人协作的开源项目，感觉很赞也很有成就感……" By <a href="http://weibo.com/timothyye">@TimothyYe</a></li>
<li> <a href="http://swiftist.org/topics/81">雨燕Swift</a>: "...我做翻译这件事的目的其实挺自私的，没想改变世界，没想着跟世界同步，没想干什么轰轰烈烈的大事。... 我是Aminby，和大多数程序员一样默默无闻地用国内外先进的技术或解决方案为工作忙活着的普通人。" By <a href="http://weibo.com/aminby">@老白经aminby</a></li>
</ol>
</li>
<li><a href="http://my.txtshare.in/article/da01660222c4603f3ff9fd86dfe5bff6/?from=timeline&amp;isappinstalled=0">蒂姆·库克的苹果</a>: "当库克走向舞台左侧的暗处时，气氛一时变得神秘起来。这时苹果软件工程负责人克莱格·费德里西(Craig Federighi)快步走上台。他和库克插肩而过，走到聚光灯下，向大家介绍这款新品。它不是一款新的消费产品，而是一套名为“开发工具包”的软件工具，可以帮助开发人员开发出更好的应用。这个世界上的其他人可能会对此打哈欠，但开发者们站起身，兴奋地叫嚷起来。"</li>
</ul>


<h2>其它相关</h2>

<ul>
<li><p><a href="http://wang9262.github.io/blog/2014/06/06/install-mac-os-x-10-dot-10-by-vmare/">VM10装Mac OS X 10.9.3及更新到Mac OS X 10.10</a>: "嗯，我写的。屌丝学生党买不起Mac，只能在黑苹果和虚拟机上先折腾会了。" By <a href="http://weibo.com/VongLo">@Vong_HUST</a></p></li>
<li><p><a href="http://facebook.github.io/origami/">Origami</a>: 快速原型动画开发工具。Origami由Facebook开发Quartz Composer工具库，它使原型开发更容易。参考文章：</p>

<ol>
<li> <a href="http://www.csdn.net/article/2014-06-09/2820131">次时代交互原型神器Origami档案</a>: "随着iOS 7的推出，扁平化和极简主义设计风格在移动互联网领域流行起来，App动效越来越成为了决定App气质的重要因素，原型的动态保真度似乎成为了阻碍设计师发挥想象力的一道门槛。传统的以点按为主的App设计，逐渐演变成为大量手势交互，这使得Axure类工具表现手势交互显得心有余而力不足。基于QC的Origami应运而生。"</li>
<li> <a href="https://github.com/nixzhu/dev-blog/blob/master/2014-06-22-quartz-composer-and-origami-tutorial-button-animation.md">用 Quartz Composer 和 Origami 制作一个简单的按钮动画(译文)</a>: "结识了 QC 和 Origami 之后，我就能用很短的时间制作出这个动画的原型。我爱上了 QC 和 Origami —— 我希望你在使用它们之后，也会爱上它们。同时，我十二分地感谢 Facebook 创造了 Origami，以及 Apple 创造了 Quartz Composer。"  By <a href="http://weibo.com/nixzhu">@nixzhu</a></li>
</ol>
</li>
<li><p><a href="http://www.iwangke.me/2014/06/07/wwdc-2014-download-script/">WWDC 2014 PDF 及session 视频下载脚本</a>:一段下载WWDC2014 全部PDF 和Session 的终端脚本。</p></li>
</ul>