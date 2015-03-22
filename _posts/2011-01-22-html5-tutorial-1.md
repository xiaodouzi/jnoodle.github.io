---
layout: post
title: 日就月将之HTML5入门教程1
---

>Be conservative in what you send; be liberal in what you accept.   ——Postel principle

>发送时要保守；接收时要开放。  ——伯斯塔尔法则

## HTML版本发展历史
---

### HTML 2.0

HTML 2.0 是 1996 年由 Internet 工程工作小组的 HTML 工作组开发的。

HTML 2.0 是过时的 HTML 版本，不用为他浪费时间。要注意HTML没有1.0版，吹牛我使用HTML怎么怎么早的时候不要忘记。

### HTML 3.2

HTML 3.2 作为 W3C 标准发布于 1997 年 1 月 14 日。HTML 3.2 向 HTML 2.0 标准添加了被广泛运用的特性，诸如字体、表格、applets、围绕图像的文本流，上标和下标。

这些被添加到 1997 年 HTML 3.2 标准的元素之一 – <font> 标签  - 为 HTML 内容和呈现的分离这个重要的任务带来了不必要的麻烦。

### HTML 4.0

作为一项 W3C 推荐，HTML 4.0 被发布于 1997 年 12 月 18 日。而仅仅进行了一些编辑修正的第二个版本发布于 1998 年 4 月 24 日。

HTML 4.0 最重要的特性是引入了样式表（CSS）。

### HTML 4.01

作为一项 W3C 推荐，HTML 4.01 发布于 1999 年 12 月 24 日。

HTML 4.01 是对 HTML 4.0 的一次较小的更新，对后者进行了修正和漏洞修复。

W3C 不会继续发展 HTML。未来 W3C 的工作会集中在 XHTML 上。

### XHTML 1.0 (最新版本的HTML)

XHTML 1.0 使用 XML 对 HTML 4.01 进行了重新地表示。

作为一项 W3C 推荐，XHTML 1.0 发布于 2000 年 1 月 20 日。

### HTML 5

W3C 于 2008 年 1 月 22 日发布 HTML 5 工作草案。

通过制定如何处理所有 HTML 元素以及如何从错误中恢复的精确规则，HTML 5 改进了互操作性，并减少了开发成本。

HTML 5 中的新特性包括了嵌入音频、视频和图形的功能，客户端数据存储，以及交互式文档。

HTML 5 还包含了新的元素，比如：`<nav>`, `<header>`, `<footer>` 以及 `<figure>` 等等。

HTML 5 工作组包括：AOL, Apple, Google, IBM, Microsoft, Mozilla, Nokia, Opera, 以及数百个其他的供应商。

## HTML5设计理念
---

### 避免不必要的复杂性

比较一下各个版本的doctype：

{% highlight html %}
//HTML 4.01：
<!DOCTYPE html PUBLIC "-//W3C/DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">

//XHTML 1.0：
<!DOCTYPE html PUBLIC "-//W3C/DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

//HTML5：
<!DOCTYPE html>
{% endhighlight %}

比较一下指定文档的字符编码的写法：

```html
//HTML 4.01：
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>

//XHTML 1.0:
<?xml version="1.0" encoding="UTF-8" ?>

//HTML5:
<meta charset="utf-8"/>
```

HTML5其他简洁写法：

```html
<link href="#" rel="stylesheet"/>

<script></script>
```

### 支持已有的内容

HTML5支持已存在的各种不严谨的写法！

```html
<p class="red">Hello world</p>

<p>Hello world</p>

<p class="red">Hello world

<p CLASS="red">Hello world</p>
```

### 解决现实的问题

比如可以将块级元素写入链接中：

```html
<a href="#">
<h2>Headline text</h2>
<p>Paragraph text.</p>
</a>
```

### 求真务实

增加了很多实用的标签，如头部（header）、脚部（footer）、分区（section）、文章（article）等，接下来的文章将会陆续讲到。

### 平稳退化

在使用新标签时，向下兼容，如：

```html
input type="number"
input type="search"
input type="range"
input type="email"
input type="date"
input type="url"
```

不支持HTML5的浏览器都将解析为input type=”text”

### 最终用户优先

一旦遇到冲突，最终用户优先，其次是作者，其次是实现者，其次标准制定者，最后才是理论上的完满。

Hixie（即Ian Hickson， Acid2、Acid3的作者及维护者，HTML5、CSS 2.1规范的制定者）经常说，在有人建议了某个特性，而HTML5工作组为此争论不下时，如果有浏览器厂商说“我们不会支持这个特性，不会在我们的浏览器中实现这个特性”，那么这个特性就不会写进规范。因为即使是把特性写进规范，如果没有厂商实现，规范不过是一纸空文，对不对？实现者可以拒绝实现规范。

## 小结

本文主要介绍了HTML的发展历史和HTML5的设计理念。

PS：WHATWG最近宣布了一条重大消息——HTML5变为HTML。