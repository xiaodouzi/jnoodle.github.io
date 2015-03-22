---
layout: post
title: JavaScript模块化开发（二）——CommonJS规范
---

从本文开始介绍常见的模块化规范。

模块化规范，主要是为了统一模块化的编写方式，比如不同团队的Java代码，总能用import的方式来加载，C#的话也有using，JavaScript本身没有内置的模块系统（ES6中引入了模块系统，不过等到普及可能是n年后的事情了），JavaScript的模块化规范，一般都是致力于提高 JavaScript 程序的可移植性和可交换性，朝着统一模块化交互方式的方向而努力。

<!--more-->

[CommonJS](http://wiki.commonjs.org/wiki/Modules/1.1) 的目标是定义一套普通应用程序使用的API，从而填补原生JavaScript标准库过少的缺点。终极目标是实现一个像python，java中含有的标准库。现在非常火爆的node.js实际上就是CommonJS 的一个实现。

CommonJS 标准大致如下：

CommonJS有一个全局性的方法 `require()`，主要用于加载模块，加载后，就可以调用模块的方法；

```javascript
var math = require('math');

math.add(2,3);
```

math 模块的add方法是怎么定义的呢，CommonJS还有一个全局变量 `exports`，它用来导入模块的方法，通过它导入的方法，便是这个模块的API，可供调用：

```javascript
//math.js

exports.add = function() {
    var sum = 0, i = 0, args = arguments, l = args.length;
    while (i < l) {
        sum += args[i++];
    }
    return sum;
};
```

在模块里，还有一个变量`module`，它有一个只读的`id属性`，还有一个`uri属性`。

其他还有一些[命名规范和识别规范](http://wiki.commonjs.org/wiki/Modules/1.1)。

通过 CommonJS 的规范和代码可以看出，require 是同步的，模块系统需要同步读取模块文件内容，并编译执行以得到模块接口。在服务端，比如node.js，这一般来说没有问题，文件请求都是本地获取，对性能没有什么影响。但是放在浏览器端，问题就出来了，等到所有模块同步加载完毕，时间不知道要过去多久了。

CommonJS 最早叫做 ServerJS，Modules 1.0规范在node.js上实践的很好，由于知道自身在浏览器中的不足，CommonJS社区把名字改为CommonJS，意为想统一服务器端和浏览器端，但是要实现浏览器端，就要有新的版本的标准，在新的版本制定过程中，社区出现了分歧，在这个分歧中，分出了AMD规范。

由于风格和机制的差异，最终，AMD从CommonJS社区中独立了出来，成为了现在最受欢迎的规范。接下来的文章里，会介绍这个规范。

