---
layout: post
title: JavaScript模块化开发（三）——AMD规范
---

本文介绍一下AMD规范（注意，这里的AMD和做cpu的AMD可不是一回事）。

<!--more-->

根据[之前文章](http://www.feeldesignstudio.com/2013/09/javascript-module-pattern-basics)的知识，我们知道一个模块系统最起码要有下面这些功能：

* 可以创建封装的模块
* 可以定义对其他模块的依赖
* 可以导出功能，被其他模块使用

[AMD](https://github.com/amdjs/amdjs-api/wiki/AMD)是“Asynchronous Module Definition”的缩写，意思就是“异步模块定义”。从名称上就可以看出，它是通过异步方式加载模块的，模块的加载不影响后续语句的执行，所有依赖加载中的模块的语句，都会放在一个回调函数中，等到该模块加载完成后，这个回调函数才运行。

AMD规范的API非常简单：

`define(id?, dependencies?, factory);`

规范定义了一个define函数，它用来定义一个模块。它包含三个参数，前两个参数都是可选的。

* 第一个参数 id：是一个string字符串，它表示模块的标识（也就是模块的路径，通过id才能知道从什么位置去加载依赖的模块）
* 第二个参数 dependencies：是一个数组，成员是依赖模块的id
* 第三个参数 factory：是一个回调函数，在依赖的模块加载成功后，会执行这个回调函数，它的参数是所有依赖模块的引用，如果回调函数有返回值，会导出出来

一个**完整的模块定义**包含模块名称，模块的依赖和回调函数，比如下面的代码：

```javascript
define("adder", ["math"], function (math) {
    return {
        addTen : function (x) {
            return math.add(x, 10);
        }
    };
});
```

如果这个模块并没有依赖，那么默认的依赖是`["require", "exports", "module"]`，这时模块可以改写为：

```javascript
define("adder", function (require, exports) {
    exports.addTen = function (x) {
        return x + 10;
    };
});
```

如果省略第一个参数，则会定义一个**匿名模块**，见代码：

```javascript
define(["math"], function (math) {
    return {
        addTen : function (x) {
            return math.add(x, 10);
        }
    };
});
```

在实际中，**使用的更多的是匿名模块定义方式**，因为这样更加的灵活，模块的标识和它的源代码不再相关，开发人员可以把这个模块放在任意的位置而不需要修改代码。一般只有在要使用工具打包模块到一个文件中时，才会声明第一个参数，所以应该尽量避免给模块命名。

在写模块的时候，也有可能没有依赖或者稍后才需要加载依赖，也就是说我们可以省略第一个和第二个参数，下面代码展示了这种用法，这也是CommonJS的写法，算是一种兼容：

```javascript
define(function (require, exports, module) {

    ……

    var a = require('a'),
        b = require('b');

    exports.action = function () {
        ……
    };
});
```

注意上述回调函数里的require的使用将被自动进行动态加载。



到现在，下面这些库都实现了AMD规范：

* [RequireJS](http://requirejs.org/)
* [curl](https://github.com/cujojs/curl)
* [lsjs](https://github.com/zazl/lsjs)
* [Dojo](http://dojotoolkit.org/) 1.7+

还有很多js库都支持了AMD规范，自己作为一个模块而存在，比如[jQuery](http://jquery.com/)，[MooTools](http://mootools.net/)等，所以AMD规范基本上已经是非常普及了，成为了事实上的标准。


