---
title: Mac下的Apache服务
date: 2017-07-06 09:24:02
tags: Apache
---
Mac自带apache服务 在`/usr/sbin/apachectl`文件夹下
<!--more-->
```bash
开启
$ sudo /usr/sbin/apachectl start
关闭
$ sudo /usr/sbin/apachectl stop
重启
$ sudo /usr/sbin/apachectl restart
```
默认打开地址
```bash
/Library/WebServer/Documents/
```
可将测试文件放在上面的文件夹下 如果不方便的话可到配置文件更改Document地址
```bash
$ vim /etc/apache2/httpd.conf
```
找到
*DocumentRoot "/Library/WebServer/Documents"*
更改即可
