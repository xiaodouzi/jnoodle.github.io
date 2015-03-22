---
layout: post
title: JavaScript中的两个等号(==)和三个等号(===)
---

> “Determining whether two variables are equivalent is one of the most important operations in programming.” （确定两个变量是否相等是编程中最重要的操作之一）

> <cite>——[Nicholas Zakas](http://www.nczonline.net/)</cite>

JavaScript中作比较有两个方式：严格模式（strict comparison 使用三个等号 ===）和概要模式（abstract comparison 使用两个等号 ==），对于他们的意义和行为，本文做一个归纳。

<!--more-->

为了避免舍本逐末，学习任何知识应该先从标准的定义开始，下面是这两种比较方式在[ECMA262标准](http://ecma-international.org/ecma-262/5.1/)中的定义：

## **严格模式 ===**

**The Strict Equality Comparison Algorithm（严格相等比较算法）**

The comparison x === y, where x and y are values, produces true or false. Such a comparison is performed as follows:（判断步骤如下，**注意次序**）

<ol>
<li>If&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-8">Type</a>(<i>x</i>) is different from&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-8">Type</a>(<i>y</i>), return&nbsp;<b>false</b>.</li>
<li>If&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-8">Type</a>(<i>x</i>) is Undefined, return&nbsp;<b>true</b>.</li>
<li>If&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-8">Type</a>(<i>x</i>) is Null, return&nbsp;<b>true</b>.</li>
<li>If&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-8">Type</a>(<i>x</i>) is Number, then
<ul style="list-style-type: circle;">
<li>If&nbsp;<i>x</i>&nbsp;is&nbsp;<b>NaN</b>, return&nbsp;<b>false</b>.</li>
<li>If&nbsp;<i>y</i>&nbsp;is&nbsp;<b>NaN</b>, return&nbsp;<b>false</b>.</li>
<li>If&nbsp;<i>x</i>&nbsp;is the same Number value as&nbsp;<i>y</i>, return&nbsp;<b>true</b>.</li>
<li>If&nbsp;<i>x</i>&nbsp;is&nbsp;<b>+0</b>&nbsp;and&nbsp;<i>y</i>&nbsp;is&nbsp;<b>−0</b>, return&nbsp;<b>true</b>.</li>
<li>If&nbsp;<i>x</i>&nbsp;is&nbsp;<b>−0</b>&nbsp;and&nbsp;<i>y</i>&nbsp;is&nbsp;<b>+0</b>, return&nbsp;<b>true</b>.</li>
<li>Return&nbsp;<b>false</b>.</li>
</ul>
</li>
<li>If&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-8">Type</a>(<i>x</i>) is String, then return&nbsp;<b>true</b>&nbsp;if&nbsp;<i>x</i>&nbsp;and&nbsp;<i>y</i>&nbsp;are exactly the same sequence of characters (same length and same characters in corresponding positions); otherwise, return&nbsp;<b>false</b>.</li>
<li>If&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-8">Type</a>(<i>x</i>) is Boolean, return&nbsp;<b>true</b>&nbsp;if&nbsp;<i>x</i>&nbsp;and&nbsp;<i>y</i>&nbsp;are both&nbsp;<b>true</b>&nbsp;or both&nbsp;<b>false</b>; otherwise, return&nbsp;<b>false</b>.</li>
<li>Return&nbsp;<b>true</b>&nbsp;if&nbsp;<i>x</i>&nbsp;and&nbsp;<i>y</i>&nbsp;refer to the same object. Otherwise, return&nbsp;<b>false</b>.</li>
</ol>

## **概要模式 ==**

**The Abstract Relational Comparison Algorithm**

The comparison x < y, where x and y are values, produces true, false, or undefined (which indicates that at least one operand is NaN). In addition to x and y the algorithm takes a Boolean flag named LeftFirst as a parameter. The flag is used to control the order in which operations with potentially visible side-effects are performed upon x and y. It is necessary because ECMAScript specifies left to right evaluation of expressions. The default value of LeftFirst is true and indicates that the x parameter corresponds to an expression that occurs to the left of the y parameter’s corresponding expression. If LeftFirst is false, the reverse is the case and operations must be performed upon y before x. Such a comparison is performed as follows:（判断步骤如下，**注意次序**）

<ol>
<li>If the&nbsp;<i>LeftFirst</i>&nbsp;flag is&nbsp;<b>true</b>, then
<ul style="list-style-type: circle;">
<li>Let&nbsp;<i>px</i>&nbsp;be the result of calling&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-9.1">ToPrimitive</a>(<i>x</i>, hint Number).</li>
<li>Let&nbsp;<i>py</i>&nbsp;be the result of calling&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-9.1">ToPrimitive</a>(<i>y</i>, hint Number).</li>
</ul>
</li>
<li>Else the order of evaluation needs to be reversed to preserve left to right evaluation
<ul style="list-style-type: circle;">
<li>Let&nbsp;<i>py</i>&nbsp;be the result of calling&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-9.1">ToPrimitive</a>(<i>y</i>, hint Number).</li>
<li>Let&nbsp;<i>px</i>&nbsp;be the result of calling&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-9.1">ToPrimitive</a>(<i>x</i>, hint Number).</li>
</ul>
</li>
<li>If it is not the case that both&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-8">Type</a>(<i>px</i>) is String and&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-8">Type</a>(<i>py</i>) is String, then
<ul style="list-style-type: circle;">
<li>Let&nbsp;<i>nx</i>&nbsp;be the result of calling&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-9.3">ToNumber</a>(<i>px</i>). Because&nbsp;<i>px</i>&nbsp;and&nbsp;<i>py</i>&nbsp;are primitive values evaluation order is not important.</li>
<li>Let&nbsp;<i>ny</i>&nbsp;be the result of calling&nbsp;<a href="http://ecma-international.org/ecma-262/5.1/#sec-9.3">ToNumber</a>(<i>py</i>).</li>
<li>If&nbsp;<i>nx</i>&nbsp;is&nbsp;<b>NaN</b>, return&nbsp;<b>undefined</b>.</li>
<li>If&nbsp;<i>ny</i>&nbsp;is&nbsp;<b>NaN</b>, return&nbsp;<b>undefined</b>.</li>
<li>If&nbsp;<i>nx</i>&nbsp;and&nbsp;<i>ny</i>&nbsp;are the same Number value, return&nbsp;<b>false</b>.</li>
<li>If&nbsp;<i>nx</i>&nbsp;is&nbsp;<b>+0</b>&nbsp;and&nbsp;<i>ny</i>&nbsp;is&nbsp;<b>−0</b>, return&nbsp;<b>false</b>.</li>
<li>If&nbsp;<i>nx</i>&nbsp;is&nbsp;<b>−0</b>&nbsp;and&nbsp;<i>ny</i>&nbsp;is&nbsp;<b>+0</b>, return&nbsp;<b>false</b>.</li>
<li>If&nbsp;<i>nx</i>&nbsp;is&nbsp;<b>+∞</b>, return&nbsp;<b>false</b>.</li>
<li>If&nbsp;<i>ny</i>&nbsp;is&nbsp;<b>+∞</b>, return&nbsp;<b>true</b>.</li>
<li>If&nbsp;<i>ny</i>&nbsp;is&nbsp;<b>−∞</b>, return&nbsp;<b>false</b>.</li>
<li>If&nbsp;<i>nx</i>&nbsp;is&nbsp;<b>−∞</b>, return&nbsp;<b>true</b>.</li>
<li>If the mathematical value of&nbsp;<i>nx</i>&nbsp;is less than the mathematical value of&nbsp;<i>ny</i>&nbsp;—note that these mathematical values are both finite and not both zero—return&nbsp;<b>true</b>. Otherwise, return&nbsp;<b>false</b>.</li>
</ul>
</li>
<li>Else, both&nbsp;<i>px</i>&nbsp;and&nbsp;<i>py</i>&nbsp;are Strings
<ul style="list-style-type: circle;">
<li>If&nbsp;<i>py</i>&nbsp;is a prefix of&nbsp;<i>px</i>, return&nbsp;<b>false</b>. (A String value&nbsp;<i>p</i>&nbsp;is a prefix of String value&nbsp;<i>q</i>&nbsp;if&nbsp;<i>q</i>&nbsp;can be the result of concatenating&nbsp;<i>p</i>&nbsp;and some other String&nbsp;<i>r</i>. Note that any String is a prefix of itself, because&nbsp;<i>r</i>&nbsp;may be the empty String.)</li>
<li>If&nbsp;<i>px</i>&nbsp;is a prefix of&nbsp;<i>py</i>, return&nbsp;<b>true</b>.</li>
<li>Let&nbsp;<i>k</i>&nbsp;be the smallest nonnegative integer such that the character at position&nbsp;<i>k</i>&nbsp;within&nbsp;<i>px</i>&nbsp;is different from the character at position&nbsp;<i>k</i>&nbsp;within&nbsp;<i>py</i>. (There must be such a&nbsp;<i>k</i>, for neither String is a prefix of the other.)</li>
<li>Let&nbsp;<i>m</i>&nbsp;be the integer that is the code unit value for the character at position&nbsp;<i>k</i>&nbsp;within&nbsp;<i>px</i>.</li>
<li>Let&nbsp;<i>n</i>&nbsp;be the integer that is the code unit value for the character at position&nbsp;<i>k</i>&nbsp;within&nbsp;<i>py</i>.</li>
<li>If&nbsp;<i>m</i>&nbsp;&lt;&nbsp;<i>n</i>, return&nbsp;<b>true</b>. Otherwise, return&nbsp;<b>false</b>.</li>
</ul>
</li>
</ol>


通过定义，可以归纳出下面的特点：

* **=== 不做类型转换，类型不同的一定不等，返回false；**
* **两个string严格相等表示它们有相同的字符排列、相同的长度和每个位置的字符都相同；**
* **两个number严格相等表示它们有相同的数值，NaN和任何东西都不相等，包括NaN它自己；正负零彼此之间相等；**
* **两个boolean严格相等表示它们同时为true或者同时为false；**
* **两个不同的object在严格和概要比较中都不相等，返回false；**
* **两个object相等唯一的情况是他们引用了相同的object；**
* **== 在两边值类型不同的时候，会做如下的转换再严格比较：**
  * null == undefined 但是 null !== undefined；
  * 如果有一个操作数是一个数字或布尔值，如果可能，另一个操作数转换为数字；否则，如果其中一个操作数为字符串，如果可能，另一个操作数被转换为字符串；
  * 如果两个操作数都是对象，那会比较对象在内存中的引用是否相同。

根据上面的规则，我们知道：如果在比较时两个变量的类型很重要，就要使用严格比较（===）；否则可以使用一般比较（==）。

在JavaScript中，下面的值被当做假（false），除了下面列出的值，都被当做真（true）：

* false
* null
* undefined
* 空字符串 ”
* 数字 0
* NaN

分析如下的代码：

```javascript
5 == '5'   // true  右边的字符串会被转换为数字，然后进行比较

"1" == true  // true true会先转换成数值 1，然后进行比较

//注意 String 对象和 string字符串不同，String对象一般来说很少使用
var a = new String("foo");
var b = new String("foo");

a == b      //false
a === b     //false
a == "foo"  //true
a === "foo" //false
```

注意在使用 == 时，在类型不同时，会进行强制类型转换，这个转换的规则十分复杂（上面的特点中有简单的说明，详见 [ToPrimitive](http://ecma-international.org/ecma-262/5.1/#sec-9.1)），不了解规则时，会发现表现十分的奇怪：

```javascript
'' == '0'   //false
0 == ''     //true
0 == '0'    //true

false == 'false'    //false
false == '0'        //true
false == undefined  //false
false == null       //false
null == undefined   //true

' \t\r\n ' == 0     //true
```

通过上面的例子可以看出，== 在传递性（即 a == b, a == c 推出 b == c）上是不可靠的，以上例子中如果使用 ===，结果都会是 false。所以***建议除非非常清楚自己想要的，一般尽量使用 === 来进行比较。***

下面介绍与判断相等相关的几个知识：

## **!! 运算符**

注意下面的代码：

```javascript
NaN   ===  NaN     //false
!!NaN === !!NaN    //true
```

我们经常会在代码中看到 !! 运算符，它是一个编程技巧，作用主要是把一个变量或表达式转换为boolean，看下面的代码（均返回 true）：

```javascript
!!false === false
!!true === true

!!0 === false
!!parseInt("foo") === false // NaN 为 false
!!1 === true
!!-1 === true

!!"" === false //空字符串为false
!!"foo" === true  //非空字符串都为true
!!"false" === true  //非空字符串都为true

!!window.foo === false //undefined为false
!!null === false //null为false

!!{} === true  //空对象为true
!![] === true  //空数组为true

!!new Boolean(false) === true  //这里是个对象
!!Boolean(false) === false     //这里才是boolean值
```

相类似的快速转换类型写法还有下面的两个：

`Number(foo) === +foo`

`String(foo) === ”+foo`

## **变量和常量的顺序**

大家在阅读js资料时可能会发现有这样的写法推荐，即变量放在双等号的右边，常量放在左边：

```javascript
//尽量使用
if ( '0' == a ) { ......

//不要使用
if ( a == '0' ) { ......
```

这是“Yoda表示法”，名字来源于《星球大战》的 Yoda 大师。他说话的单词顺序相当奇特，比如：“Backwards it is, yes!”。

这样写主要是防止缺少等号的笔误，比如把 if ( a == ’0′ ) 误写成了 if ( a = ’0′ )，如果采用了常量在前的判断写法，如果把 if ( ’0′ == a ) 误写成了 if ( ’0′ = a )，则会抛出错误（ReferenceError: Invalid left-hand side in assignment）。

一般来说，作为代码书写规范来说，推荐**常量在左**进行判断的写法。