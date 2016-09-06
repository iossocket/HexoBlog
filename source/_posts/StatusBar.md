---
title: iOS Status Bar Change Color
date: 2016-09-06 09:46:20
tags:
---
**Key point**：永远都是window的root view controller 来决定status bar style

### 三种情况：
1. 最简单的情况下：window的root view controller 是一个普通的view controller，此时若想改变status bar，需要做三步操作：
  * 给当前项目的info.plist文件添加一个key-value: `View controller-based status bar appearance: YES`
  * 给需要改变status bar的view controller的viewDidLoad中一个方法：
```Swift
  setNeedsStatusBarAppearanceUpdate();
```
  * 给需要改变status bar的view controller中加一个方法
```Swift
  override func preferredStatusBarStyle() -> UIStatusBarStyle {
    return .LightContent
  }
```
2. 当前window的root view controller 是一个navigation view controller，那么：
```Swift
  self.navigationController?.navigationBar.barStyle = .Black
```
3. 这种情况比较特殊：有一个抽屉
```Swift
     let vc = UIStoryboard.init(name: "Main", bundle: nil).instantiateViewControllerWithIdentifier("MyHomeWelcomeViewController")
     let nav = UINavigationController(rootViewController: vc)
     let countryVC = UIStoryboard.init(name: "Main", bundle: nil).instantiateViewControllerWithIdentifier("MyHomeCountryViewController")

     let slideMenuController = SlideMenuController(mainViewController: nav, rightMenuViewController: countryVC)
     window = UIWindow(frame: UIScreen.mainScreen().bounds)
     window?.rootViewController = slideMenuController
     window?.makeKeyAndVisible()
```
在这种情况下，若想改变，则需要改变slideMenuController，改变的方法同方法一

**由此可见，永远都是window的root view controller 来决定status bar style.**
