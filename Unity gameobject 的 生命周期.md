---
title: Unity gameobject 的 生命周期
tags: iOS
---
### Unity3d 基础学习
<!--more-->

#### 脚本生命周期
* Awake

  脚本被载入是调用

* OnEnable

  对象变为可用或激活状态时调用

* Start

  只调用一次

* FixedUpdate

  固定的时间间隔被调用 不受设备的帧率等的影响

* Update

  更新

* LateUpdate

  Update之后更新

* OnGUI

  渲染和处理GUI事件

* OnDisable

  当前对象不可用或处于非激活状态 脚本或对象被销毁的时候调用

* OnDestroy

  当物体 或是 脚本 被销毁

### 常用的方法

* gameObt.GetComponent< compomentName > ();

  获取到对应的compoment

* GetComponent<Rigidbody> ().AddForce (vec3);

  给刚体添加力

<!--more-->
