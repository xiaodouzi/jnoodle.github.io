---
layout: post
title: JavaScript模块化开发（一）——基础知识
---

随着前段JavaScript代码越来越重，如何组织JavaScript代码变得非常重要，好的组织方式，可以让别人和自己很好的理解代码，也便于维护和测试。模块化是一种非常好的代码组织方式，本文试着对JavaScript模块化开发的一些基础知识做一些阐释。

<!--more-->

## **对象字面量（Object Literals）**

对象字面量表示，其实就是用一对大括号括起来的键值对，也就是JavaScript声明对象的方式。

```javascript
var myObject = {
    variableKey : variableValue,
    functionKey : function() {
       ...
    }
}
```

比较一下下面代码声明方式，使用对象字面量表示，可以减少全局变量的污染，一般来说，**强烈建议在任何时候都不要使用下面的声明方式：**

```javascript
var variableName = ...;

function name1(){
    ...
}
function name2(){
    ...
}
```

## **立即执行函数（IIFE Immediately-Invoked Function Expressions）**

立即执行函数是现在非常流行的写法，大部分JS库都使用了这种技巧，主要是**防止全局变量的污染。**

当我们在声明类似于 `var name1 = function (){ … }` 这样的函数时，在后面加一对括号 ()，就可以让它立即执行，但是如果是 `function name1() { … }` 这样的函数，则会有问题：

```javascript
function name1(){
    alert("123");
}();
```

上面代码在执行时会抛出错误，Unexpected token（意外的标记），因为后面的()会被解析为[分组操作符](http://dmitrysoshnikov.com/ecmascript/chapter-5-functions/#question-about-surrounding-parentheses)。

解决上面的问题，只需要加上括号将function代码全部括住即可，下面就是立即执行函数的声明方式：

```javascript
(function () { /* code */ } ());

(function () { /* code */ })();
```

注意，上面两种方式都是可以的，主要看个人习惯。立即执行函数可以**不对外暴露私有变量**，比如：

```javascript
var myObject = {
    name : "FeeldesignStudio",
    getName : function(){
        return this.name;
    }
};

myObject.name;       //FeeldesignStudio
myObject.getName();  //FeeldesignStudio

var myObject = (function(){
    var name = "FeeldesignStudio";
    return {
        getName : function(){
            return name;
        }
    }
})();

myObject.name;       //出错！
myObject.getName();  //FeeldesignStudio
```

## **导入全局变量**

把全局变量作为参数传递给一个立即执行函数，这样就完成了全局变量的导入，立即执行函数中可以使用此全局变量的方法，并可以修改（简化）全局变量的名称：

```javascript
var myModule = (function ( jQ ) {

    function method1(){
        jQ(".container").html("test");
    }

    return{
        publicMethod: function(){
            method1();
        }
    };

})( jQuery );

myModule.publicMethod();
```

## **模块导出**

当然，有导入也可以有导出，有时我们不仅要导入全局变量，也要把模块导出到全局空间供其他模块使用。通过在立即执行函数中返回一个Object，就可以实现模块导出功能：

```javascript
var myModule = (function () {

  var module = {}, privateVariable = "Feeldesign";

  function privateMethod() {
    // ...
  }

  module.publicProperty = "FeeldesignStudio";
  module.publicMethod = function () {
    console.log( privateVariable );
  };

  return module;

})();
```

## **扩展模块**

在开发中，我们经常会对一些模块进行扩展，扩展当然可以直接修改模块的源代码，但是这不是一个好的方法，比如我们要给 myModule 模块增加几个方法，通过前面的“立即执行函数”、“导入全局变量”、“模块导出”的知识，我们可以推导出下面的扩展方式：

```javascript
var myModule = (function ( my ) {

    my.xxMethod = function () {
        ...
    };

    return my;

})( myModule );
```

问题来了：上面的代码可以很好地对 myModule 进行扩展，不过前提是 myModule 必须已经定义，如果扩展的 xxMethod 方法和 myModule 本身没有任何的依赖，那么要求 myModule 必须已经定义就毫无必要了，怎么解决这个问题呢，非常简单，只需要或一个空对象：

```javascript
//松散扩展
var myModule = (function ( my ) {

    my.xxMethod = function () {
        ...
    };

    return my;

})( myModule || {} );
```

上述代码还存在一个问题，那就是如果a.js中声明了 `var myModule = …`，b.js中也声明了 `var myModule = …`，这样在引入a.js和b.js时，后者会将前者覆盖，这并不是我们期望的，所以对上述代码，可以再加改进：

```javascript
(function ( my ) {

    my.xxMethod = function () {
        ...
    }

})( window.myModule = window.myModule || {} );
```

上面把JavaScript模块化开发的基础知识作了介绍，接下来，会进一步介绍常见的规范和针对这些规范的一些js库实现，通过这些js库，我们可以很好的将模块化开发赋予实施。



参考链接：

<http://addyosmani.com/resources/essentialjsdesignpatterns/book/#modularjavascript>

<http://benalman.com/news/2010/11/immediately-invoked-function-expression/>

<http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html>

<http://blog.davidpadbury.com/2011/08/21/javascript-modules/>