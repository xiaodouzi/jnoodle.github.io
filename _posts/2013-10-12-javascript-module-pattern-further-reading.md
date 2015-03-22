---
layout: post
title: JavaScript模块化开发（五）——延伸阅读
---

## **Sea.js**

[Sea.js](http://seajs.org/)是一个提供简单、极致的模块化开发体验的JavaScript模块加载框架。Sea.js的主要目的是令JavaScript开发模块化并可以轻松愉悦进行加载，将前端工程师从繁重的JavaScript文件及对象依赖处理中解放出来，可以专注于代码本身的逻辑。

<!--more-->

Sea.js的作者是前淘宝UED，现支付宝前端工程师玉伯。

Sea.js是国内比较流行的JavaScript模块加载框架，Sea.js 遵循 [MIT 协议](http://seajs.org/LICENSE.md)，无论个人还是公司，都可以免费自由使用。

在 Sea.js 中，所有 JavaScript 模块都遵循[CMD模块定义规范](https://github.com/cmdjs/specification/blob/master/draft/module.md)，定义规范。该规范明确了模块的基本书写格式和基本交互规则（这里是规范的[中文介绍](https://github.com/seajs/seajs/issues/242)）。

详细信息，可以参阅[Sea.js文档](http://seajs.org/docs/#docs)。

## **LABjs**

[LABjs](http://labjs.com/)是由Kyle Simpson编写，用来管理JS下载执行的一个开源模块。下图是LABjs的分析图（转自[携程UED](http://ued.ctrip.com/blog/?p=3305)）

![image](/images/post/20131012LabJs.png)

还可以参考[官方网站](http://labjs.com/)或者[这篇文章](http://oldj.net/article/labjs-study/)。

## **Do**

[Do](http://kejun.github.io/Do/)是一个很轻量文件加载和依赖关系管理的库（Do是Douban的前两个字母）。目前do.min.js（4.6k）。可能灵活的组织开发中的JS/CSS模块文件，定制各种加载策略。

一些轻量级的网站可以使用Do，源码可以在[这里找到](https://github.com/kejun/Do)。

## **My.js**

[my.js](https://github.com/hax/my.js)是按照ES6草案的module/loader规范实现的，ES6（ECMAScript 6）模块的目标是创建的格式能让CJS（CommonJS规范）和AMD（Asynchronous Module Definition，异步模块定义）的用户都能满意。

