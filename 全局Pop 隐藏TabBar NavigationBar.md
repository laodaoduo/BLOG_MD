---
title: 全局Pop 隐藏TabBar NavigationBar
---

### 全局Pop(侧边缘滑动的拓展)
<!--more-->
#### 思路:给系统的侧边缘滑动runtime添加target action

```Swift
import UIKit

class CustomNavigationController: UINavigationController {

override func viewDidLoad() {
    super.viewDidLoad()

    // 1. 获取系统的Pop手势
    let systemGes = interactivePopGestureRecognizer
    // 2. 获取手势的view用于添加新的手势
    let gesView = systemGes?.view

    // 3. 获取target/action


    // 3.1 利用运行时机制获取所有的属性名称
    var count : UInt32 = 0
    let ivars = class_copyIvarList(UIGestureRecognizer.self, &count)!
    for i in 0..<count {
        let ivar = ivars[Int(i)]
        let name = ivar_getName(ivar)!
        print(String(cString : name))
    }

    let targets = systemGes?.value(forKey: "_targets") as? [NSObject]
    let targetObjc = targets?.first
    // 3.2 取出target
    guard let target = targetObjc?.value(forKey: "target") else { return }
    // 3.3 取出action
    let action = Selector(("handleNavigationTransition:"))
    // 4. 创建自己的Pan手势
    let panGes = UIPanGestureRecognizer()
    gesView?.addGestureRecognizer(panGes)
    panGes.addTarget(target, action: action)

}

}
```
#### 隐藏tabBar
    import UIKit

    class CustomNavigationController: UINavigationController {

     override func viewDidLoad() {
        super.viewDidLoad()

     }

     override func pushViewController(_ viewController: UIViewController, animated: Bool) {
         viewController.hidesBottomBarWhenPushed = true
         super.pushViewController(viewController, animated: animated)
     }
    }
#### 隐藏NavigationBar

    class ViewController: UIViewController,UIGestureRecognizerDelegate {

    override func viewWillAppear(_ animated: Bool) {
    super.viewWillAppear(animated)

    navigationController?.setNavigationBarHidden(true, animated: true)

    navigationController?.interactivePopGestureRecognizer?.delegate = self
    navigationController?.interactivePopGestureRecognizer?.isEnabled = true
    }

    override func viewWillDisappear(_ animated: Bool) {
    super.viewWillDisappear(animated)

    navigationController?.setNavigationBarHidden(false, animated: true)
    }
    override func viewDidLoad() {
    super.viewDidLoad()

    }

    }
