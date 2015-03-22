---
layout: post
title: JavaScript模块化开发（四）——RequireJS
---

[RequireJS](http://requirejs.org/) 是一个JavaScript文件和模块加载器，它主要用于浏览器端，但也可以适用于Rhino / Node 等环境。RequireJS遵循了AMD规范，使用非常广泛。

之前的文章[（一）](http://www.feeldesignstudio.com/2013/09/javascript-module-pattern-basics)、[（二）](http://www.feeldesignstudio.com/2013/09/javascript-module-pattern-commonjs)、[（三）](http://www.feeldesignstudio.com/2013/09/javascript-module-pattern-amd)已经介绍了JavaScript模块化开发的一些基础知识和规范。本文主要说一说RequireJS的使用。

<!--more-->

## **获取和开始使用RequireJS**

点击[这个链接](http://requirejs.org/docs/download.html)即可下载最新版的RequireJS。

下载之后，把它放在项目的脚本文件夹下，比如 js 文件夹下，项目结构看上去应该是：

![项目结构](/images/post/20130927090001.gif)

要充分使用RequireJS，在 index.html 文件中，应该把所有的内联脚本都移除，只留下一句话：

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Sample Project</title>
    <!-- data-main 属性告诉 require.js 在 require.js  加载之后加载 js/main.js -->
    <script data-main="js/main" src="js/require.js"></script>
</head>
<body>
<h1>My Sample Project</h1>
</body>
</html>
```

在 main.js 中，可以通过 require() 加载依赖的脚本，这样不用在 html 中显示声明。main.js 相当于是一个入口点：

```javascript
require(["helper/util"], function (util) {
    // 当 scripts/helper/util.js 加载完毕，会执行这个回调函数
    // 如果 util.js 也声明了依赖的文件（模块），那么这个函数会等到那些依赖的文件（模块）加载完毕后才调用

    //TODO
});
```

## **RequireJS API**

### 加载js文件

通过刚才的介绍，可以看出来 RequireJS 采用了不同于传统 `<script>` 标签的加载方式，传统的 `<script>` 标签方式一般都会有下面的代码：

```html
<body>

<script type="text/javascript" src="js/jquery.js"></script>
<script type="text/javascript" src="js/jquery.plugin.xx.js"></script>
<script type="text/javascript" src="js/a1.js"></script>
<script type="text/javascript" src="js/a2.js"></script>
<script type="text/javascript" src="js/a3.js"></script>
……
</body>
```

这样的代码极复杂又难以维护。RequireJS 采用了模块ID的方式替代了通过URL加载脚本的方式，还记得那句声明么：

`<script data-main="js/main" src="js/require.js"></script>`

RequireJS 查找脚本的路径，主要是通过 baseUrl，在 data-main 中，声明了 baseUrl 的路径，在这句代码里也就是 js 文件夹；如果不声明 data-main，则 baseUrl 默认指向这个 html 页面所在的文件夹。当然，也可以通过配置来声明 baseUrl，下文会详述。

**注意，data-main 中声明的模块会被异步加载，也就意味着如果页面后面通过 `<script>` 加载多个脚本，这些脚本不一定在 data-main 中声明的模块加载之后才加载；或者后面的js代码如果有对 data-main 中声明的模块的依赖，则有可能会出现错误。**

RequireJS 会假定所有依赖项默认都是脚本，所以书写依赖时可以省略 “.js” 后缀，RequireJS 会自动加上这个后缀。RequireJS 会自动把模块ID翻译成一个路径（path），我们也可以在配置中声明多个路径（paths），通过 baseUrl + paths，可以用很少的代码找到相应的 js 文件，比起 `<script>` 标签要优雅简洁很多。

一般来说，通过 baseUrl + paths 就可以找到js文件，不过有时候，可能会有例外，一旦 RequireJS 发现模块 ID 中包含如下的字符，那么它就不按照 baseUrl + paths 的方式来寻找这个模块的js文件了，而是采用 URL 的方式：

* 如果 ID 以 “.js” 结尾
* 如果 ID 以 “/” 开头
* 如果 ID 以 “http:” 或者 “https:” 开头

一般来说，最好使用 baseUrl + paths 的方式来声明模块ID，这样做会有更多的灵活性。同样的，我们在组织js代码文件的时候，尽量避免使用很深的路径，而最好把js文件都放置在 baseUrl 下面，最好不要超过两层的深度，下面就是一个很好的例子：

<ul>
<li>www/
<ul>
<li>index.html</li>
<li>js/
<ul>
<li>app/
<ul>
<li>sub.js</li>
</ul>
</li>
<li>lib/
<ul>
<li>jquery.js</li>
<li>canvas.js</li>
</ul>
</li>
<li>app.js</li>
</ul>
</li>
</ul>
</li>
</ul>

在 index.html 中：

`<script data-main="js/app.js" src="js/require.js"></script>`

在 app.js 中：

```javascript
requirejs.config({
    //默认从 js/lib 中加载模块
    baseUrl : 'js/lib',

    //如果模块ID以app开头，则会在 js/app 目录下寻找
    //不过要注意千万不要加上 ".js"，否则paths的规则就会失效
    paths : {
        app : '../app'
    }
});

requirejs(['jquery', 'canvas', 'app/sub'],
    function ($, canvas, sub) {
        //jQuery, canvas 和 app/sub 模块都加载完毕后，会执行这个函数

        //TODO
    });
```

使用RequireJS时，建议像 jQuery 这样带有版本号的库，用单独的文件来标识版本号，在文件命名中把版本号去掉。

### 定义模块

RequireJS 要求一个js文件只定义一个模块。不过这样的话，每加载一个模块，就会产生一个HTTP请求，RequireJS 提供了一个[优化工具](http://requirejs.org/docs/optimization.html)，在最后生产环境中，可以打包所有模块到一个文件中。

定义模块可以使用 define() 方法，define() 有三个参数，可以参考[前文中的介绍](http://www.feeldesignstudio.com/2013/09/javascript-module-pattern-amd)。

定义一个只有键值对，没有任何依赖的模块：

```javascript
define({
    color : "black",
    size : "M"
});
```

定义一个函数，没有依赖：

```javascript
define(function () {
    //TODO

    return {
        color : "black",
        size : "M"
    }
});
```

定义一个有依赖的函数，第一个参数是依赖的模块ID数组，后面是回调函数，会在所有依赖加载完毕后执行：

```javascript
define(["cart"], function (cart) {
    //TODO
    return {
        color : "blue",
        size : "M",
        addToCart : function () {
            cart.add(this);
        }
    }
});
```

当然不一定只是返回Object，也可以返回一个函数：

```javascript
define(["cart"], function (cart) {
    //TODO
    return function (title) {
        return title ? (window.title = title) : cart.name;
    }
});
```

更多的API可以参考[官方说明](http://requirejs.org/docs/api.html)。


## **RequireJS 工作原理**

RequireJS 采用 head.appendChild() 的方式来加载所有依赖的脚本，这个方式的原理很简单，看看下面的代码就明白了：

```javascript
function loadjscssfile(filename, filetype) {
    if (filetype == "js") { //作为js文件载入
        var fileref = document.createElement('script')
        fileref.setAttribute("type", "text/javascript")
        fileref.setAttribute("src", filename)
    }
    else if (filetype == "css") {  //作为css文件载入
        var fileref = document.createElement("link")
        fileref.setAttribute("rel", "stylesheet")
        fileref.setAttribute("type", "text/css")
        fileref.setAttribute("href", filename)
    }
    if (typeof fileref != "undefined")
        document.getElementsByTagName("head")[0].appendChild(fileref)
}

loadjscssfile("myscript.js", "js")
loadjscssfile("javascript.php", "js")
loadjscssfile("mystyle.css", "css")
```

RequireJS 会顺着依赖链（也就是顺着模块声明的依赖层层进入，直到没有依赖为止）把所有需要加载的模块按顺序一一加载完毕，然后才执行回调函数。

## **加载非规范的模块**

在加载没有实现AMD规范的模块（这种模块比实现了AMD规范的模块更多）时，RequireJS 也提供了简洁的方式，就是通过配置定义这些模块的特征，比如：

```javascript
requirejs.config({

    // 要使用 shim 来配置没有实现 AMD 规范的模块
    // 不过注意 shim 不能用来配置已经实现 AMD 规范的模块
    shim : {
        'backbone' : {
            //定义依赖，会在 backbone.js 载入前载入这些依赖
            deps : ['underscore', 'jquery'],
            //导出 Backbone
            exports : 'Backbone'
        },
        'underscore' : {
            exports : '_'
        }
    }
});

//jQuery
requirejs.config({
    shim : {
        'jquery.colorize' : {
            deps : ['jquery'],
            exports : 'jQuery.fn.colorize'
        },
        'jquery.scroll' : {
            deps : ['jquery'],
            exports : 'jQuery.fn.scroll'
        }
    }
});
```