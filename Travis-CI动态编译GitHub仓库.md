---
title: Travis_CI动态编译GitHub仓库
date: 2017-07-06 13:24:00
tags: [Travis, Hexo]

---
我的博客是用hexo部署在GitHub上的有时候换个电脑或是有个小改动的话 就会很不方便 Travis刚好解决了这个问题

<!--more-->

* 什么是Travis_CI

  *Travis CI 是目前新兴的开源持续集成构建项目，它与jenkins，Go的很明显的 特别在于采用yaml格式，同时他是在在线的服务，不像jenkins需要你本地打架服务器，简洁清新独树一帜。目前大多数的github项目都已经移入到Travis CI的构建队列中，据说Travis CI每天运行超过4000次完整构建。*

* GitHub账号登录Travis_CI 在左上角有加好按钮 把需要添加的项目开关打开

* github上添加access token

  登录github，进入到setting => develop setting => personal access tokens
  在description里输入任意token 名字，比如Travis-CI，并勾选上下面所有复选框。这个时候会生成token，请务必记住，因为他只会出现一次，否则需要重新生成(这个就是)。

* 添加access token到travis上

  在travis右上角more options里找到setting，打开后，勾选 [Build only if .travis.yml is present] 并且 在Environment Variables中添加github上的access token。

* 添加编写.travis.yml

  *在项目源码根目录(我的是troy-yang.github.io source分支), 添加.travis.yml文件，下面是我的:*

  ```js
  language: node_js
  node_js: stable
  # S: Build Lifecycle
  install:
  - npm install hexo-cli -g
  - npm install
  before_install:
  - git submodule update --init --remote --recursive
  #before_script:
  # - npm install -g gulp
  script:
  - hexo g
  after_script:
  - cd ./public
  - git init
  - git config user.name "laodaoduo"
  - git config user.email "2295990355@qq.com"
  - git add .
  - git commit -m "Update docs"
  - git push --force --quiet "https://${GitHub_TOKEN}@${GH_REF}" master:master
  # E: Build LifeCycle
  env:
  global:
  - GH_REF: github.com/laodaoduo/laodaoduo.github.io.git
  ```

* 最后可以测试看看了 参考[链接](http://troyyang.com/2017/06/24/Travis_Auto_Build_Deploy_Github_Projects/)
