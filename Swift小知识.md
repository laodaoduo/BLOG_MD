---
title: Swift小知识
date: 2017-07-21 17:15:48
tags: Swift
---
#### Swift的小知识点集锦
* 设置attributes 属性

```swift

//文档
open func setTitleTextAttributes(_ attributes: [String : Any]?, for state: UIControlState)
//例子
rootNav.tabBarItem.setTitleTextAttributes([NSAttributedStringKey.foregroundColor.rawValue: UIColor.red], for: .selected)

```

* 设置image的 RenderingMode

```sift

let selectImg = UIImage(named: selectImgName)?.withRenderingMode(.alwaysOriginal)

```

* @available #available

*Swift 2.0 中，引入了可用性的概念。对于函数，类，协议等，可以使用@available声明这些类型的生命周期依赖于特定的平台和操作系统版本。而#available用在判断语句中（if, guard, while等），在不同的平台上做不同的逻辑。*

@available放在函数（方法），类或者协议前面。表明这些类型适用的平台和操作系统

```
@available(iOS 9, *)
func myMethod() {
    // do something
}

```

 #available 用在条件语句代码块中，判断不同的平台下，做不同的逻辑处理，比如：

```
if #available(iOS 8, *) {
        // iOS 8 及其以上系统运行
}


guard #available(iOS 8, *) else {
    return //iOS 8 以下系统就直接返回
}
```
* Selector
Swift 中的 Selector 类型其实就是 Objective-C 中的 SEL 类型。在 Swift 中，Selector 的本质是结构体。

```
btn.addTarget(<#T##target: Any?##Any?#>, action: <#T##Selector#>, for: <#T##UIControlEvents#>)

```

类似 Objective-C 中的 NSSelectorFromString，Swift 中的 Selector 也可以使用字符串来构造(会有警告)

```
btn.addTarget(self, action: Selector("btnClick"), for: .touchUpInside)

```
这样写的好处 可以条用类的私有变量 类似OC的运行时机制
handleNavigationTransition:
还有一种方法是

```
btn.addTarget(self, action: #selector(ProfileViewController.itemClick), for: .touchUpInside)

```

如果当期作用域下 只有这一个方法 ProfileViewController可以省略 直接写方法名 方法前加@objc
我们也知道OC中的属性其实是自动生成了getter和setter方法。swift 3中支持获取属性的getter和setter方法 通过#selector:
#selector(setter: <#T##@objc property#>)
#selector(getter: <#T##@objc property#>)
```
class Person: NSObject {
    dynamic var firstName: String
    dynamic let lastName: String
    dynamic var fullName: String {
        return "\(firstName) \(lastName)"
    }

    init(firstName: String, lastName: String) {
        self.firstName = firstName
        self.lastName = lastName
    }
}

let firstNameGetter = #selector(getter: Person.firstName)
let firstNameSetter = #selector(setter: Person.firstName)

```
* layout的属性
```
//每行之间竖直之间的最小间距 （可以大于）
layout.minimumLineSpacing = 1
//同行的cell与cell之间水平之间的最小间距
layout.minimumInteritemSpacing = 1

```
参考: [链接](http://www.jianshu.com/p/f3f2c663115d)
