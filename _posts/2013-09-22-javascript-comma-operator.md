---
layout: post
title: JavaScript逗号运算符及使用
---

有一道js面试题，题目是这样的：下列代码的执行结果是什么，为什么？

```javascript
var i, j, k;
for (i=0, j=0; i<10, j<6; i++, j++) {
  k = i+j;
}
document.write(k);
```
<!--more-->

答案是显示10，这道题主要考察JavaScript的逗号运算符。

下面是[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comma_Operator)对逗号运算符的定义：

**逗号运算符计算两个操作数（从左至右）并返回第二个操作数的值。**

根据这个定义，可以扩展一下：

**逗号运算符从左到右计算两个或多个操作数并返回最后一个操作数的值。**

可以感觉一下下面的代码：

```javascript
alert((0, 9));
alert((9, 0));

if (0,9) alert("ok");
if (9,0) alert("ok");
```

逗号运算符在实际代码中有什么样的作用呢？

### 1、交换变量，无需第三个变量

```javascript
var a = "a", b = "b";

//方法一
a = [b][b = a, 0];

//方法二
a = [b, b = a][0];
```

### 2、简化代码

```javascript
if(x){
  foo();
  return bar();
}
else{
  return 1;
}
```

可以简写成：

```javascript
return x ? (foo(), bar()) : 1;
```