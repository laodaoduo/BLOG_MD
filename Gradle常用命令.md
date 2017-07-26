---
title: Gradle常用命令
date: 2017-07-24 15:48:34
tags: Android
---

./代表当前目录，gradlew代表 gradle wrapper，意思是gradle的一层包装，大家可以理解为在这个项目本地就封装了gradle，即gradle wrapper， 在./gradle/wrapper/gralde-wrapper.properties文件中声明了它指向的目录和版本。只要下载成功即可用grdlew wrapper的命令代替全局的gradle命令。
以下的命令都是在项目目录下操作
<!--more-->

* 查看版本号:

```bash
$ ./gradlew -v
第一次执行这条命令会下载安装
```

* 清除项目目录下的build文件夹

```bash
$ ./gradlew clean
```
* 检查依赖编译打包

```bash
$ ./gradlew build

这个命令把debug、release环境的包都打出来
```
* 打Debug包

```bash
$ ./gradlew assembleDebug

```

* 打Release包

```bash
$ ./gradlew assembleRelease

```
