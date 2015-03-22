---
layout: post
title: NPM设置国内代理镜像，提高下载速度
---

基于众所周知的原因，在国内使用npm下载资源的时候非常缓慢，甚至失败。使用一个靠谱的国内代理镜像是较好地解决方案：

<!--more-->

以<http://npm.cbyun.com/> 为例，如下方式都可以使用：

#### 临时使用的方法：

`npm --registry http://npm.cbyun.com install express`

#### 持久使用的方法：

修改或者新建 `~/.npmrc`，加入以下一行

`registry = http://npm.cbyun.com/`

通过config命令：

`npm config set registry http://registry.cnpmjs.org`

`npm info underscore` （如果上面配置正确这个命令会有字符串response）

可以通过定制的 cnpm (gzip 压缩支持) 命令行工具代替默认的 npm：

`npm install -g cnpm --registry=http://npm.cbyun.com`

安装时直接使用：

`cnpm install [name]`

---

#### 下面列出国内一些靠谱的镜像资源：

### <http://r.cnpmjs.org/>

使用最多的NPM镜像，不过因为使用量越来越大，最近越来越慢。

### <http://registry.npm.taobao.org>

淘宝的 NPM 镜像是一个完整的 npmjs.org 镜像。可以用此代替官方版本(只读)，同步频率目前为 15分钟 一次以保证尽量与官方服务同步。

### <http://npm.cbyun.com>

一个NPM 国内高速镜像

