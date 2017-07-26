---
title: Android_布局
date: 2017-07-24 22:19:15
tags: Android
---

LinearLayout RectiveLayout TablbeLayout

<!--more-->

* LinearLayout

  layout_margin 外边距(控件距离其他空间或是屏幕边缘的距离)

  padding 内边距 (控件内部内容距离控件边缘的距离)

  gravity 表示控件内部内容的对齐方式

  layout_gravity 该控件在父类布局中的对齐方式

  如果线性布局的对齐方式为水平layout_gravity 在水平方向上不起作用

  如果线性布局的对齐方式为垂直layout_gravity 在垂直方向上不起作用

  layout_weight  权重(百分比) 线性布局的特有属性
  如果控件划分的match_parent 成反比
  如果控件划分的wrap_content 成正比

  无权重控件优先级高 然后按剩余页面的控件大小按照权重划分
