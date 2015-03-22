---
layout: post
title: 日就月将之HTML5入门教程2
---

首先，我们比较一下下面的两段代码：

第一段：

```html
<html>
    <head></head>
    <body>
        <div id="header"></div>
        <div id="nav">
            <ul>
                <li></li>
                <li></li>
                <li></li>
            </ul>
        </div>
        <div id="content"></div>
        <div id="footer"></div>
    </body>
</html>
```

第二段：

```html
<!DOCTYPE html>
<html>
    <head></head>
    <body>
        <header></header>
        <nav>
            <ul>
                <li></li>
                <li></li>
                <li></li>
            </ul>
        </nav>
        <section>
            <article></article>
        </section>
        <footer></footer>
    </body>
</html>
```

是不是发现第二段更加简洁干净、易于理解呢？

可是`<header></header>` ，`<article></article>`等等这些都是什么呀，浏览器又怎么会支持这些写法呢？

## HTML元素列表

![HTML元素列表](/images/post/20110122html5.png)

HTML 5 包含了很多新的元素，比如：`<nav>`, `<header>`, `<footer>` 以及 `<figure>` 等等。下面是HTML 4.01和HTML5相比较的元素标签列表：

（按照字母排序 4: 指示在 HTML 4.01 中定义了该元素 5: 指示在 HTML 5 中定义了该元素 ）

<table class="light" style="width: 90%;" border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td valign="top" width="30%"><strong>标签</strong></td>
<td valign="top" width="60%"><strong>描述</strong></td>
<td valign="top" width="5%"><strong>4</strong></td>
<td valign="top" width="5%"><strong>5</strong></td>
</tr>
<tr>
<td valign="top">&lt;!–…–&gt;</td>
<td valign="top">定义注释。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;!DOCTYPE&gt;</td>
<td valign="top">定义文档类型。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;a&gt;</td>
<td valign="top">定义超链接。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;abbr&gt;</td>
<td valign="top">定义缩写。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;acronym&gt;</td>
<td valign="top">HTML 5 中不支持。定义首字母缩写。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;address&gt;</td>
<td valign="top">定义地址元素。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;applet&gt;</td>
<td valign="top">HTML 5 中不支持。定义 applet。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;area&gt;</td>
<td valign="top">定义图像映射中的区域。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;article&gt;</span></strong></td>
<td valign="top">定义 article。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;aside&gt;</span></strong></td>
<td valign="top">定义页面内容之外的内容。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;audio&gt;</span></strong></td>
<td valign="top">定义声音内容。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;b&gt;</td>
<td valign="top">定义粗体文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;base&gt;</td>
<td valign="top">定义页面中所有链接的基准 URL。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;basefont&gt;</td>
<td valign="top">HTML 5 中不支持。请使用 CSS 代替。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;bdo&gt;</td>
<td valign="top">定义文本显示的方向。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;big&gt;</td>
<td valign="top">HTML 5 中不支持。定义大号文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;blockquote&gt;</td>
<td valign="top">定义长的引用。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;body&gt;</td>
<td valign="top">定义 body 元素。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;br&gt;</td>
<td valign="top">插入换行符。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;button&gt;</td>
<td valign="top">定义按钮。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;canvas&gt;</span></strong></td>
<td valign="top">定义图形。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;caption&gt;</td>
<td valign="top">定义表格标题。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;center&gt;</td>
<td valign="top">HTML 5 中不支持。定义居中的文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;cite&gt;</td>
<td valign="top">定义引用。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;code&gt;</td>
<td valign="top">定义计算机代码文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;col&gt;</td>
<td valign="top">定义表格列的属性。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;colgroup&gt;</td>
<td valign="top">定义表格列的分组。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;command&gt;</span></strong></td>
<td valign="top">定义命令按钮。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;datalist&gt;</span></strong></td>
<td valign="top">定义下拉列表。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;dd&gt;</td>
<td valign="top">定义定义的描述。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;del&gt;</td>
<td valign="top">定义删除文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;details&gt;</span></strong></td>
<td valign="top">定义元素的细节。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;dfn&gt;</td>
<td valign="top">定义定义项目。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;dir&gt;</td>
<td valign="top">HTML 5 中不支持。定义目录列表。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;div&gt;</td>
<td valign="top">定义文档中的一个部分。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;dl&gt;</td>
<td valign="top">定义定义列表。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;dt&gt;</td>
<td valign="top">定义定义的项目。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;em&gt;</td>
<td valign="top">定义强调文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;embed&gt;</span></strong></td>
<td valign="top">定义外部交互内容或插件。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;fieldset&gt;</td>
<td valign="top">定义 fieldset。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;figcaption&gt;</span></strong></td>
<td valign="top">定义 figure 元素的标题。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;figure&gt;</span></strong></td>
<td valign="top">定义媒介内容的分组，以及它们的标题。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;font&gt;</td>
<td valign="top">HTML 5 中不支持。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;footer&gt;</span></strong></td>
<td valign="top">定义 section 或 page 的页脚。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;form&gt;</td>
<td valign="top">定义表单。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;frame&gt;</td>
<td valign="top">HTML 5 中不支持。定义子窗口（框架）。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;frameset&gt;</td>
<td valign="top">HTML 5 中不支持。定义框架的集。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;h1&gt; to &lt;h6&gt;</td>
<td valign="top">定义标题 1 到标题 6。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;head&gt;</td>
<td valign="top">定义关于文档的信息。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;header&gt;</span></strong></td>
<td valign="top">定义 section 或 page 的页眉。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;hgroup&gt;</span></strong></td>
<td valign="top">定义有关文档中的 section 的信息。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;hr&gt;</td>
<td valign="top">定义水平线。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;html&gt;</td>
<td valign="top">定义 html 文档。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;i&gt;</td>
<td valign="top">定义斜体文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;iframe&gt;</td>
<td valign="top">定义行内的子窗口（框架）。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;img&gt;</td>
<td valign="top">定义图像。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;input&gt;</td>
<td valign="top">定义输入域。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;ins&gt;</td>
<td valign="top">定义插入文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;keygen&gt;</span></strong></td>
<td valign="top">定义生成密钥。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;isindex&gt;</td>
<td valign="top">HTML 5 中不支持。定义单行的输入域。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;kbd&gt;</td>
<td valign="top">定义键盘文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;label&gt;</td>
<td valign="top">定义表单控件的标注。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;legend&gt;</td>
<td valign="top">定义 fieldset 中的标题。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;li&gt;</td>
<td valign="top">定义列表的项目。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;link&gt;</td>
<td valign="top">定义资源引用。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;map&gt;</td>
<td valign="top">定义图像映射。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;mark&gt;</span></strong></td>
<td valign="top">定义有记号的文本。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;menu&gt;</td>
<td valign="top">定义菜单列表。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;meta&gt;</td>
<td valign="top">定义元信息。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;meter&gt;</span></strong></td>
<td valign="top">定义预定义范围内的度量。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;nav&gt;</span></strong></td>
<td valign="top">定义导航链接。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;noframes&gt;</td>
<td valign="top">HTML 5 中不支持。定义 noframe 部分。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;noscript&gt;</td>
<td valign="top">定义 noscript 部分。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;object&gt;</td>
<td valign="top">定义嵌入对象。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;ol&gt;</td>
<td valign="top">定义有序列表。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;optgroup&gt;</td>
<td valign="top">定义选项组。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;option&gt;</td>
<td valign="top">定义下拉列表中的选项。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;output&gt;</span></strong></td>
<td valign="top">定义输出的一些类型。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;p&gt;</td>
<td valign="top">定义段落。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;param&gt;</td>
<td valign="top">为对象定义参数。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;pre&gt;</td>
<td valign="top">定义预格式化文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;progress&gt;</span></strong></td>
<td valign="top">定义任何类型的任务的进度。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;q&gt;</td>
<td valign="top">定义短的引用。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;rp&gt;</span></strong></td>
<td valign="top">定义若浏览器不支持 ruby 元素显示的内容。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;rt&gt;</span></strong></td>
<td valign="top">定义 ruby 注释的解释。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;ruby&gt;</span></strong></td>
<td valign="top">定义 ruby 注释。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;s&gt;</td>
<td valign="top">HTML 5 中不支持。定义加删除线的文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;samp&gt;</td>
<td valign="top">定义样本计算机代码。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;script&gt;</td>
<td valign="top">定义脚本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;section&gt;</span></strong></td>
<td valign="top">定义 section。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;select&gt;</td>
<td valign="top">定义可选列表。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;small&gt;</td>
<td valign="top">定义小号文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;source&gt;</span></strong></td>
<td valign="top">定义媒介源。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;span&gt;</td>
<td valign="top">定义文档中的 section。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;strike&gt;</td>
<td valign="top">HTML 5 中不支持。定义加删除线的文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;strong&gt;</td>
<td valign="top">定义强调文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;style&gt;</td>
<td valign="top">定义样式定义。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;sub&gt;</td>
<td valign="top">定义下标文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;summary&gt;</span></strong></td>
<td valign="top">定义 details 元素的标题。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;sup&gt;</td>
<td valign="top">定义上标文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;table&gt;</td>
<td valign="top">定义表格。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;tbody&gt;</td>
<td valign="top">定义表格的主体。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;td&gt;</td>
<td valign="top">定义表格单元。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;textarea&gt;</td>
<td valign="top">定义 textarea。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;tfoot&gt;</td>
<td valign="top">定义表格的脚注。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;th&gt;</td>
<td valign="top">定义表头。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;thead&gt;</td>
<td valign="top">定义表头。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;time&gt;</span></strong></td>
<td valign="top">定义日期/时间。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;title&gt;</td>
<td valign="top">定义文档的标题。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;tr&gt;</td>
<td valign="top">定义表格行。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;tt&gt;</td>
<td valign="top">HTML 5 中不支持。定义打字机文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;u&gt;</td>
<td valign="top">HTML 5 中不支持。定义下划线文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
<tr>
<td valign="top">&lt;ul&gt;</td>
<td valign="top">定义无序列表。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;var&gt;</td>
<td valign="top">定义变量。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top"><strong><span style="color: #800000;">&lt;video&gt;</span></strong></td>
<td valign="top">定义视频。</td>
<td valign="top" width="12"></td>
<td valign="top" width="33">5</td>
</tr>
<tr>
<td valign="top">&lt;xmp&gt;</td>
<td valign="top">HTML 5 中不支持。定义预格式文本。</td>
<td valign="top" width="12">4</td>
<td valign="top" width="33"></td>
</tr>
</tbody>
</table>

<br>

## HTML5新增元素详解：

![HTML5新增元素详解](/images/post/20110122structurehtml5.gif)

### `<article>`

定义外部的内容，外部内容可以是来自一个外部的新闻提供者的一篇新的文章，或者来自 blog 的文本，或者是来自论坛的文本。亦或是来自其他外部源内容。

### `<aside>`

定义外部的内容，括号备注，脚注，引用，注释等类似于侧边栏的东西。

### `<audio>`

定义声音，比如音乐或其他音频流。可以在开始标签和结束标签之间放置文本内容，这样老的浏览器就可以显示出不支持该标签的信息。audio主要是来取代object标签的复杂表现。

```html
<audio src="someaudio.wav">
您的浏览器不支持 audio 标签。
</audio>
```

### `<canvas>`

定义图形，比如图表和其他图像。canvas标签以后的文章会详细说到。

### `<command>`

定义命令按钮，比如单选按钮、复选框或按钮。

### `<datalist>`

定义选项列表。需要使用 input 元素的 list 属性来绑定 datalist，来定义 input 可能的值。

datalist 及其选项不会被显示出来，它仅仅是合法的输入值列表。

```html
<input id="food" list="foods" />
<datalist id="foods">
  <option value="huiguorou">
  <option value="yuxiangrousi">
  <option value="gongbaojiding">
</datalist>
```

### `<details>`

用于描述文档或文档某个部分的细节。

### `<summary>`

包含 details 元素的标题。

```html
<details>
<summary>HTML 5</summary>
This document teaches you everything you have to learn about HTML 5.
</details>
```

### `<embed>`

定义嵌入的内容，比如flash。但是不能在开始标签和结束标签之间写文本，来说明旧式的浏览器不支持该标签。

```html
<embed src="demo.swf" />
```

### `<figure>`

对元素进行组合

### `<figcaption>`

定义 figure 元素的标题，一般置于 “figure” 元素的第一个或最后一个子元素的位置。

```html
<figure>
  <figcaption>HTML5</figcaption>
  <p>HTML5草案的前身名为Web Applications 1.0。於2004年被WHATWG提出，於2007年被W3C接纳，并成立了新的HTML工作团队。在2008年1月22日，第一份正式草案已公布,预计将在2010年9月正式向公众推荐。</p>
</figure>
```

### `<footer>`

用来描述一节或一个完整Web页面的底部。

### `<header>`

用来描述一节或一个完整Web页面的头部介绍性信息。

### `<hgroup>`

用于对网页或区段（section）的标题进行组合。下面代码中的h1和h2通过`<hgroup>`组合起来，作为主标题和副标题，语义更加明确。

```html
<hgroup>
<h1>...</h1>
<h2>...</h2>
</hgroup>
```

### `<keygen>`

定义生成密钥。

### `<mark>`

定义带有记号的文本。

```html
<p>I love <mark>html5</mark></p>
```

### `<meter>`

定义度量衡。仅用于已知最大和最小值的度量。

```html
<p>
您的分数是：
<meter value="80" min="0" max="100" low="65" high="96" optimum="100">B+</meter>.
</p>
<output>
```

定义不同类型的输出，比如脚本的输出。

### `<nav>`

放置页面的导航元素。

### `<progress>`

定义运行中的进度（进程）。可以使用 `<progress>` 标签来显示 JavaScript 中耗费时间的函数的进度。

### `<rp>`

在 ruby 注释中使用，以定义不支持 ruby 元素的浏览器所显示的内容。

### `<rt>`

定义字符（中文注音或字符）的解释或发音。

### `<ruby>`

定义 ruby 注释（中文注音或字符）。

上面这三个标签可能不太好理解，通过下面的例子就会比较清楚了：

```html
<ruby>日本<rp>(</rp><rt>にほん</rt><rp>)</rp></ruby>
```
![ruby](/images/post/20110122rb.png)

### `<source>`

为媒介元素（比如 `<video>` 和 `<audio>`）定义媒介资源。

### `<section>`

定义文档中的节

### `<time>`

定义日期或时间，或者两者。

```html
<p>我们在每天早上 <time>9:00</time> 开始营业。</p>
```

### `<video>`

定义视频，比如电影片段或其他视频流。

```html
<video src="movie.ogg" controls="controls">
您的浏览器不支持 video 标签。
</video>
```
<br>

## HTML5的兼容性

### HTML5与旧浏览器的兼容

IE6等浏览器要想支持上述新增的标签元素，可以使用如下的Javascript代码：

```html
<script>
  document.createElement('header');
  document.createElement('nav');
  document.createElement('section');
  document.createElement('article');
  document.createElement('aside');
  document.createElement('footer');
</script>
```

### W3C测试

出乎意料的是，主流浏览器HTML5[兼容性测试](http://test.w3.org/html/tests/reporting/report.htm)，IE9竟然排第一，不过针对主流IE浏览器（6、7、8）来说，测试结果却并不理想：

![html5 test](/images/post/20110122ie9html5.jpg)

![html5 test](/images/post/20110122test.png)

### HTML5 Web应用

Safari 对 HTML5 Web 应用的支持最好，除了地理定位功能，其它都支持。

![html5 test](/images/post/20110122test1.gif)

### HTML5网页内嵌对象

内置的画布，视频，音频等对象。全部支持的有 Chrome，Safari，Firefox 3.6，Opera 10.5。IE家族则全军覆没。

![html5 test](/images/post/20110122test2.gif)

### HTML5 音频编码

Opera 10.5 支持的最全面，IE 家族又是颗粒无收。

![html5 test](/images/post/20110122test3.gif)

### HTML5 视频编码

H.264 任重道远。

![html5 test](/images/post/20110122test4.gif)

### HTML5 各种表单对象

Mac 平台下的 Chrome 成绩最佳。这些表单对象让人想起了桌面程序。

![html5 test](/images/post/20110122test5.gif)

### HTML5 表单对象属性与行为

![html5 test](/images/post/20110122test6.gif)

<br>

## 小结

本文主要介绍了HTML5新增的元素以及HTML5的兼容性。