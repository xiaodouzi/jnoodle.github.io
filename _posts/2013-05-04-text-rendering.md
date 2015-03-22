---
layout: post
title: text-rendering 详解
---

Text-rendering 属性是一个非标准属性，主要用来告诉渲染引擎（rendering engine）渲染文字的时候如何来优化，浏览器根据这个属性来权衡速度、易读性、几何精度等方面。
暂时只有Gecko（Firefox）and WebKit（Safari 或 Chrome）支持这个属性。

<div class="box info"><p>注：
Gecko是套开放原始码的、以C++编写的网页排版引擎。目前为Mozilla家族网页浏览器以及Netscape 6以后版本浏览器所使用。
WebKit 是一个开源的浏览器引擎，与之相对应的引擎有Gecko（Mozilla Firefox 等使用）和Trident（也称MSHTML，IE 使用）。同时WebKit 也是苹果Mac OS X 系统引擎框架版本的名称，主要用于Safari，Dashboard，Mail 和其他一些Mac OS X 程序。

 <br> <br>现在浏览器的内核引擎，基本上是四分天下： <br>
Trident: IE 以Trident 作为内核引擎; <br>
Gecko: Firefox 是基于 Gecko 开发; <br>
WebKit: Safari, Google Chrome,傲游3 基于 Webkit 开发。 <br>
Presto: Opera的内核，但由于市场选择问题，主要应用在手机平台–Opera mini</p></div>

Text-rendering属性有如下取值：

<table border="1" cellspacing="0" cellpadding="0" class="light">
<tbody>
<tr>
<td valign="top">
<p align="center">取值</p>
</td>
<td valign="top">
<p align="center">描述</p>
</td>
</tr>
<tr>
<td valign="top">
<p align="center">auto</p>
</td>
<td valign="top">浏览器为速度、易读性、几何精度等自动优化来绘制文本&nbsp;<p></p>
<p>在实践中，Gecko桌面浏览器（Firefox）如果字体大小为20 px或者更大，会使用optimizeLegibility；否则对于较小的文本使用optimizeSpeed</p></td>
</tr>
<tr>
<td valign="top">
<p align="center">optimizeSpeed</p>
</td>
<td valign="top">绘制文本时速度优先，会禁用字距调整和连字</td>
</tr>
<tr>
<td valign="top">
<p align="center">optimizeLegibility</p>
</td>
<td valign="top">绘制文本时易读性优先，会启用字距调整和连字</td>
</tr>
<tr>
<td valign="top">
<p align="center">geometricPrecision</p>
</td>
<td valign="top">绘制文本时几何精度优先，暂时和optimizeLegibility相同</td>
</tr>
</tbody>
</table>

明显的效果是optimizeLegibility 在文字较小（20px以下）的时候，在一些特殊字体设定下（如Microsoft’s Calibri、Candara等）启用了连字（比如 ff、fi、fl）

下面是一些例子：

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>text-rendering</title>
    <style>
        body {
            text-rendering: auto;
        }
        p {
            margin: 20px 0;
            font-size: 30px;
        }
        p.auto {
            text-rendering: auto;
        }
        p.optimizeSpeed {
            text-rendering: optimizeSpeed;
        }
        p.optimizeLegibility {
            text-rendering: optimizeLegibility;
        }
        p.geometricPrecision {
            text-rendering: geometricPrecision;
        }
    </style>
</head>
<body>
<p class="auto">Welcome to Feeldesign Studio <br>ligatures: ff, fi, fl, ffl</p>
<p class="optimizeSpeed">Welcome to Feeldesign Studio <br>ligatures: ff, fi, fl, ffl</p>
<p class="optimizeLegibility">Welcome to Feeldesign Studio <br>ligatures: ff, fi, fl, ffl</p>
<p class="geometricPrecision">Welcome to Feeldesign Studio <br>ligatures: ff, fi, fl, ffl</p>
</body>
</html>
```

注意下面的图片中顺序是:

1. text-rendering: auto;
2. text-rendering: optimizeSpeed;
3. text-rendering: optimizeLegibility;
4. text-rendering: geometricPrecision;

Chrome：

Chrome text-rendering 默认宋体

![image](/images/post/20130504text-rendering01.png)

Firefox：

Firefox text-rendering 默认宋体

![image](/images/post/20130504text-rendering02.png)

换个字体，小于20px：

```css
p {
    font: 19px 'DejaVu Serif', Constantia;
}
```

Chrome：

Chrome text-rendering 小于20px

![image](/images/post/20130504text-rendering03.png)

Firefox：

Firefox text-rendering 小于20px

![image](/images/post/20130504text-rendering04.png)

换个字体，大于20px：

```css
p {
     font: 30px 'DejaVu Serif', Constantia;
}
```

Chrome：

![image](/images/post/20130504text-rendering051.png)

Firefox：

![image](/images/post/20130504text-rendering06.png)

可以比较明显的看出，不同的text-rendering属性在Chrome下的区别比较明显，在Firefox下基本上没有区别。