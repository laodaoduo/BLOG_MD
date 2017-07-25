---
title: Hexo与GitHub搭建个人博客
date: 2017-07-05 14:30:54
tags: Hexo
---
#### hexo与GitHub搭建个人博客过程
<!--more-->
* 创建GitHub仓库,名字为:

  `
  GitHub昵称.github.io
  `

  ![github截图](/source/repository.png)

* 添加秘钥

  1.0 终端用以下命令 按提示 生成秘钥 公钥 生成的文件 保存在 ~/.ssh 文件夹下

  `
  $ ssh-keygen -t rsa -C "2295990355@qq.com"
  `

  *参数-t:是加密类型 -C:提供一个新注释*

  2.0 将公钥复制到GitHub上 https://github.com/settings/keys

  ![rsa_pub截图](/source/rsa_pub.png)

  ![github截图](/source/ssh.png)

* 安装node.js [node.js官网](https://nodejs.org/en/)

  里面有通用版与最新版 两个版本 选择一个下载安装即可

  ##### 我这里是在终端用brew安装

  `$ brew install node`

  安装之后可以创建js文件测试
  ```js
  var http = require('http');
  http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
  }).listen(8124, "127.0.0.1");
  console.log('Server running at http://127.0.0.1:8124/');
  --------------------------------------------------------
  测试
  $ node ~/js文件
 ```
* 安装Hexo

  `$ npm install -g hexo-cli`

* 配置

  建立一个博客文件夹，<folder>为文件夹的名称,到自己对应的博客文件夹下依次执行以下命令

  `$ hexo init <folder> `

  `$ cd <folder>`

  `$ npm install `

  写一个博客试试
  ```bash
  $ hexo new "文章标题"
  $ hexo s
  ```
  打开网址http://localhost:4000/
  ![OK啦](/source/hexo.png)

* 上传github
1. ssh配置 就不说了
2. 修改博客_config.yml文件  主要有二处

```js
一、
# Site
title: LWJ
subtitle: 临帝子之长洲， 得天人之旧馆。 层峦耸翠， 上出重霄； 飞阁流丹， 下临无地。 鹤汀凫渚， 穷岛屿之萦回； 桂殿兰宫， 即冈峦之体势。
description:
author: LWJ_wen
language: zh_CN
timezone: Asia/Shanghai
二、
deploy:
  type: git
  repo: https://github.com/laodaoduo/laodaoduo.github.io.git
  branch: master


```

第一次上传的时候会让输入你的GitHub用户名密码
* 遇到的一些坑

报错信息:
(node:1134) [DEP0061] DeprecationWarning: fs.SyncWriteStream is deprecated.
原因我新建了一个文件 里面都是shell脚本 可能是不能识别 报错了

(node:1299) [DEP0061] DeprecationWarning: fs.SyncWriteStream is deprecated. ERROR Deployer not found: git

解决办法: npm install hexo-deployer-git --save
