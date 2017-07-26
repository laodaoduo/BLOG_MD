---
title: Android_生命周期
date: 2017-07-23 21:08:38
tags:
---

一把都是成对出现的 onCreate--onDestroy onStart--onStop onResume--onPause

<!--more-->

### Activity
##### 生命周期

* onCreate
创建activity的方法
* onStart
启动activity
* onResume
执行此方法之后 用户可以看到 h获取焦点
* onPause
失去焦点 可见 不可交互
* onStop
不可见
* onDestroy
销毁当前activity的页面实例
* onRestart
将置于后台的activity重新被置于前台

成对出现
onCreate--onDestroy onStart--onStop onResume--onPause
##### Task
一个app启动的时候会包含多个Activity页面,这些Activity所组成的操作就是一个task任务
#### back Task 任务栈

点击一个app 就会开启一个task任务  这个任务中所有的activity就会被放在一个任务栈(back stack
)中 位于任务栈 栈顶的Activity用户可见
新的Activity进入栈的时候 已存在栈中的Activity会压栈

#### 启动activity

* startActivity

  Intent intent = new Intent(MainActivity.this, SecondActivity.class);

  startActivity(new Intent(intent)) ;

* startActivityForResult (带返回值的跳转)

  Intent intent = new Intent(MainActivity.this, SecondActivity.class);
  // 参数一: intent对象 参数二: 请求码 用来区分页面
  startActivityForResult(intent, 10);

  重写系统方法 onActivityResult

```

@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    super.onActivityResult(requestCode, resultCode, data);

    if (requestCode==10&&resultCode==RESULT_OK){


        TextView tv = (TextView) findViewById(R.id.textView);

        /*将数据取出 并展示出来*/
        tv.setText(data.getStringExtra("key"));

    }
}

```
