---
title: Cocoapods的安装过程
---
## 新mac电脑上cocoapods的安装过程
<!--more-->
### 升级gem
```bash
sudo gem update --system

```
### 安装rvm
```bash
curl -L get.rvm.io | bash -s stable
source ~/.bashrc
source ~/.bash_profile
```


### 安装homebrew
```base
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

```

### ruby升级
```bash
rvm install x.x.x

```
设置默认版本
```bash
rvm use 2.4.0 --default

```

### 安装cocoapods

#### 查看当前源
```bash
gem sources -l

```

#### 移除默认的ruby源
```bash
gem sources --remove https://rubygems.org/

```
#### 更改为国内源
```bash
gem sources -a https://gems.ruby-china.org/

```
#### 安装
```bash
sudo gem install cocoapods

```

成功之后执行pod setup
测试 pod search AFNetworking
报错：Unable to find a pod with name, author, summary, or description matching `SDWebImage`
解决办法：rm ~/Library/Caches/CocoaPods/search_index.json
再次测试 ok
出现上面错误的原因是因为你在没有完全安装好cocoapods的时候执行的search操作
