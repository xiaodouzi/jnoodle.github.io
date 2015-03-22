---
layout: post
title: Web开发神器，最智能的Javascript IDE——WebStorm
---

我的开发很大一部分是和Javascript打交道，很久以来，我一直在Spket、Aptana、Visual Studio、IntelliJ IDEA、notepad++、vim等选择中徘徊，因为发现他们都很好，但都缺少我想要的……直到我开始使用WebStorm。

<!--more-->

## 什么是我对Javascript IDE选择的标准？

1、快速智能的代码提示（全项目的）和补全

2、支持重构

3、支持代码格式化细节的自定义

4、良好的编辑体验（如快速定位最近的编辑、快速查看代码结构及定义等）

5、轻量、快速

6、便于调试

## WebStorm是什么？

WebStorm是JetBrains的一个专门为Web开发人员设计的IDE，JetBrains大家应该不陌生，Resharper、IntelliJ IDEA等都是出自这个公司。

JetBrains给WebStorm下的定义是：The smartest Javascript IDE。敢这么说，肯定是有两把刷子。但是要注意，这个IDE不是免费的，不过大家都知道应该怎么做的~~

## WebStorm有什么功能？

下面我把WebStorm的功能大致罗列一下（这里只说Javascript编辑的功能，其他的html和css之类的大家自己发掘，记得WebStorm可是支持Zencoding的哟，帅~）：

**1、智能的代码补全：**

支持不同浏览器的提示，还包括所有用户自定义的函数（项目中）

![image](/images/post/20111115JS_DOM_Completion.gif)

代码补全包含了所有流行的库，比如：JQuery, YUI, Dojo, Prototype, Mootools and Bindows。

**2、代码格式化：**

代码不仅可以格式化，而且所有规则都可以自己来定义：

![image](/images/post/20111115JS_code_formatting.gif)

**3、代码编写中的html提示：**

大家经常在js代码中编写html代码，一般来说十分痛苦，不过有了智能提示，就爽多了。

![image](/images/post/20111115html_in_js_2.png)

而且html里面还能有js提示

![image](/images/post/20111115html_in_js_4.png)

**4、代码导航和用法查询：**

只需要按着Ctrl键点击函数或者变量等，就能直接跳转到定义：

可以全项目查找函数或者变量，还可以查找使用并高亮：

**5、代码重构（这个操作有些像Resharper，熟悉Resharper的用户应该上手很快）：**

支持的有重命名、提取变量/函数、内联变量/函数、移动/复制、安全删除等等，比如：

![image](/images/post/20111115js_inline_var_before.png)

内联变量重构之后变为：

![image](/images/post/20111115js_inline_var_after.png)

**6、代码检查和快速修复：**

![image](/images/post/20111115JS_inspection.png)

可以快速找到代码中的错误或者需要优化的地方，并给出修改意见，快速修复。

![image](/images/post/20111115JS_inspection_quick-fix.png)

**7、代码调试：**

![image](/images/post/20111115jsd_toolwindow.png)

**8、代码结构浏览：**

可以快速浏览和定位

![image](/images/post/20111115Structure_view.gif)

**9、代码折叠：**

![image](/images/post/20111115Code_folding_JavaScript.gif)

**10、包裹或者去掉外围代码：**

![image](/images/post/20111115uwrap_js_1.png)

去掉之后就成了：

![image](/images/post/20111115uwrap_js_after.png)

怎么样，这些功能足够多了吧，其中的调试和重构包含了很多，这个还需要你来自己挖掘。

## 怎样获得WebStorm？

WebStorm现在的最新版本是2.1.5，官方下载地址是：[用力点我下载](http://download.jetbrains.com/webide/WebStorm-2.1.5.exe)，这是30天的试用版，不过你知道怎么做的（试试[点我](http://www.baidu.com/s?bs=webstorm+%D7%A2%B2%E1%BB%FA&tn=monline_dg&f=8&rsv_bp=2&wd=webstorm+2.1.5)）

估计马上，应该是年底之前，3.0就要出来了。

## 还有哪些其他功能？

WebStorm还有很多的功能等待挖掘，比如支持所有主流的版本控制，比如svn、git、cvs等；支持FTP的项目，并能自动同步；支持HTML5、Zencoding等等。

我向大家推荐WebStorm做为Javascript编辑器，在使用他的这些日子里，我又重新感受到了编写js的乐趣。

## 更新下载地址（2015-03-22）

[点我下载最新版WebStorm](https://www.jetbrains.com/webstorm/download/)