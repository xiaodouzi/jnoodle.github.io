---
layout: post
title: JavaScript原生对象属性和方法详解——Number对象
excerpt: <p>本文介绍Number对象的主要属性和方法 ...</p>
---

创建 Number 对象的语法：

`var myNum = new Number(value);`

`var myNum = Number(value);`

当 Number() 和运算符 new 一起作为构造函数使用时，它返回一个新创建的 Number 对象。如果不用 new 运算符，把 Number() 作为一个函数来调用，它将把自己的参数转换成一个原始的数值，并且返回这个值（如果转换失败，则返回 NaN）。

## **MAX_VALUE**

MAX_VALUE 属性是 JavaScript 中可表示的最大的数。它的近似值为 1.7976931348623157 x 10308。最大的负数是 -MAX_VALUE。

比MAX_VALUE还要大的数是Infinity。MAX_VALUE是一个静态属性，所以调用方法应该是Number.MAX_VALUE。

```javascript
console.log(Number.MAX_VALUE)  //1.7976931348623157e+308
```

## **MIN_VALUE**

MIN_VALUE 属性是 JavaScript 中可表示的最小的数（**接近 0 ，但不是负数**）。它的近似值为 5 x 10-324。

所有**比MIN_VALUE小的数都会被转换成0**。

MIN_VALUE是一个静态属性，所以调用方法应该是 Number.MIN_VALUE。

## **NaN**

NaN 属性是代表非数字值的特殊值。该属性用于指示某个值不是数字。可以把 Number 对象设置为该值，来指示其不是数字值。

可以使用 isNaN() 全局函数来判断一个值是否是 NaN 值。

Number.NaN 是一个特殊值，说明某些算术运算（如求负数的平方根）的结果不是数字。方法 parseInt() 和 parseFloat() 在不能解析指定的字符串时就返回这个值。对于一些常规情况下返回有效数字的函数，也可以采用这种方法，用 Number.NaN 说明它的错误情况。

JavaScript 以 NaN 的形式输出 Number.NaN。**请注意，NaN 与其他数值进行比较的结果总是不相等的，包括它自身在内。因此，不能与 Number.NaN 比较来检测一个值是不是数字，而只能调用 isNaN() 来比较。**

注意：全局变量NaN 和Number.NaN 是一样的，NaN是一个不可配置，不可修改的属性。

```javascript
console.log(parseInt("abc"));    //NaN
console.log(NaN === NaN);        //false
console.log(Number.NaN === NaN); //false
console.log(isNaN(NaN));         //true
console.log(isNaN(Number.NaN));  //true
```

## **NEGATIVE_INFINITY**

NEGATIVE_INFINITY 属性表示小于 -Number.MAX_VALUE 的值。该值代表负无穷大。

JavaScript 显示 NEGATIVE_INFINITY 时使用的是 -Infinity。这个值的算术行为和无穷大非常相似。例如，任何数乘无穷大结果仍为无穷大，任何数被无穷大除的结果为 0。

**-Infinity 和 Number.NEGATIVE_INFINITY 相等。**

```javascript
var x = (-Number.MAX_VALUE) * 2;
var y = Number.NEGATIVE_INFINITY;
console.log(x);     //-Infinity
console.log(y);     //-Infinity
console.log(x===y); //true
```

## **POSITIVE_INFINITY**

POSITIVE_INFINITY 属性表示大于 Number.MAX_VALUE 的值。该值代表正无穷大。

JavaScript 显示 POSITIVE_INFINITY 时使用的是 Infinity。这个值的算术行为和无穷大非常相似。例如，任何数乘无穷大结果仍为无穷大，任何数被无穷大除的结果为 0。

**Infinity 和 Number.POSITIVE_INFINITY相等。**

**`isFinite()` 方法可以判断参数是否是有限的数字。**

```javascript
var x = Number.NEGATIVE_INFINITY;
var y = Number.POSITIVE_INFINITY;
var z = Infinity;
var a = "abc";
var b = 123;

console.log(isFinite(x));  //false
console.log(isFinite(y));  //false
console.log(isFinite(z));  //false
console.log(isFinite(a));  //false
console.log(isFinite(b));  //true
```

## **toString()**

toString() 方法可把一个 Number 对象转换为一个字符串，并返回结果。

`NumberObject.toString(radix)`

参数radix是可选的。规定表示数字的基数，使 2 ~ 36 之间的整数。**若省略该参数，则使用基数 10，建议总是带着此参数，防止误解。**例如，当 radix 为 2 时，NumberObject 会被转换为二进制值表示的字符串。

当调用该方法的对象不是 Number 时抛出 TypeError 异常。

```javascript
var a = 100;

console.log(a.toString());    //100
console.log(a.toString(10));  //100
console.log(a.toString(2));   //1100100
console.log(a.toString(8));   //144
console.log(a.toString(16));  //64
```

## **toLocaleString()**

toLocaleString() 方法可把一个 Number 对象转换为本地格式的字符串。

数字的字符串表示，由实现决定，根据本地规范进行格式化，可能影响到小数点或千分位分隔符采用的标点符号。

当调用该方法的对象不是 Number 时抛出 TypeError 异常。

```javascript
var a = 123456;

console.log(a.toLocaleString());  //123,456
console.log(a.toLocaleString("zh-Hans-CN-u-nu-hanidec"));  //一二三,四五六
```

更多参数可以参考：[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toLocaleString)

## **toFixed()**

toFixed() 方法可把 Number 四舍五入为指定小数位数的数字。

NumberObject.toFixed(num)

**参数num是必需的。**规定小数的位数，是 0 ~ 20 之间的值，包括 0 和 20，有些实现可以支持更大的数值范围。如果省略了该参数，将用 0 代替。

返回 NumberObject 的字符串表示，不采用指数计数法，小数点后有固定的 num 位数字。如果必要，该数字会被舍入，也可以用 0 补足，以便它达到指定的长度。如果 num 大于 le+21，则该方法只调用 NumberObject.toString()，返回采用指数计数法表示的字符串。

当 num 太小或太大时抛出异常 RangeError。0 ~ 20 之间的值不会引发该异常。有些实现支持更大范围或更小范围内的值。当调用该方法的对象不是 Number 时抛出 TypeError 异常。

```javascript
var n = 12345.6789;

console.log(n.toFixed());            //12346
console.log(n.toFixed(2));           //12345.68
console.log(n.toFixed(6));           //12345.678900
console.log((1.23e+20).toFixed(2));  //123000000000000000000.00
console.log((1.23e-10).toFixed(2));  //0.00
```

**注意：由于对浮点数的处理，toFixed() 方法展现出的结果并不是所谓的“四舍五入”或者是“四舍六入五成双”，而是四舍，六入，五的表现十分混乱。**

```javascript
//Chrome中
console.log(( 0.035 ).toFixed( 2 )); //0.04
console.log(( 0.045 ).toFixed( 2 )); //0.04
```

建议自己写方法来替换toFixed()默认行为，可以参考：[SO上的讨论](http://stackoverflow.com/questions/566564/javascript-functions-math-roundnum-vs-num-tofixed0-and-browser-inconsistenci)

```javascript
Number.prototype.toFixed = function(len){
    var temp = Math.pow(10,len);
    var s = Math.ceil(this * temp)
    return s/temp;
}

console.log(( 0.035 ).toFixed( 2 ));  //0.04
console.log(( 0.045 ).toFixed( 2 ));  //0.05
```

## **toExponential()**

toExponential() 方法可把对象的值转换成指数计数法。

`NumberObject.toExponential(num)`

参数num是可选的。规定指数计数法中的小数位数，是 0 ~ 20 之间的值，包括 0 和 20，有些实现可以支持更大的数值范围。如果省略了该参数，将使用尽可能多的数字。

返回 NumberObject 的字符串表示，采用指数计数法，即小数点之前有一位数字，小数点之后有 num 位数字。该数字的小数部分将被舍入，必要时用 0 补足，以便它达到指定的长度。

当 num 太小或太大时抛出异常 RangeError。0 ~ 20 之间的值不会引发该异常。有些实现支持更大范围或更小范围内的值。当调用该方法的对象不是 Number 时抛出 TypeError 异常。

```javascript
var num = 10000.1234;

console.log(num.toExponential());    //1.00001234e+4
console.log(num.toExponential(2));   //1.00e+4
console.log(num.toExponential(10));  //1.0000123400e+4
```

## **toPrecision()**

toPrecision() 方法可将数值格式化为一个十进制数形式的字符串。

`NumberObject.toPrecision(num)`

参数num是可选的。用于控制数字的精度。该参数是 1 ~ 21 之间（且包括 1 和 21）的值。如果省略了该参数，则调用方法 toString()，而不是把数字转换成十进制的值。

```javascript
var num = 10000.1234;

console.log(num.toPrecision());    //10000.1234
console.log(num.toPrecision(2));   //1.0e+4
console.log(num.toPrecision(10));  //10000.12340
```

