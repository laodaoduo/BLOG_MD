---
title: Android_Intent
date: 2017-07-23 21:10:35
tags: Android
---

#### Intent 的几大属性

<!--more-->

* ComponentName (组件名称)
* Action

字符串类型
```
intent.setAction("com.example.lwj.activitytest");
```

* Category
分类 进一步筛选要选择的内容 一般放在<intent-filter>标签中 常用的有:
LAUNCHER 、DEFAULT、 HOME

* Extra 附加信息(键值对)

传值
putExtra()

```获取附加信息

if (getIntent() != null){
    Intent intent = getIntent();
    String info = intent.getStringExtra("info");
}

```

* Data
