---
title: Swift小知识
date: 2017-07-21 17:15:48
tags: Swift
---

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
