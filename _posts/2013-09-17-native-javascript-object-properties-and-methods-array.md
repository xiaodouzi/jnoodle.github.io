---
layout: post
title: JavaScript原生对象属性和方法详解——Array对象
excerpt: <p>本文介绍Array对象的主要属性和方法 ...</p>
---

## **length**

设置或返回 数组中元素的数目。

注意：设置 length 属性可改变数组的大小。如果设置的值比其当前值小，数组将被截断，其尾部的元素将丢失。如果设置的值比它的当前值大，数组将增大，新的元素被添加到数组的尾部，它们的值为 undefined。所以length不一定代表数组的元素个数。

```javascript
var arr = new Array(3)
arr[0] = "John"
arr[1] = "Andy"
arr[2] = "Wendy"

console.log(arr);  //["John", "Andy", "Wendy"]
console.log(arr.length);  //3

arr.length = 2;

console.log(arr);  //["John", "Andy"]
console.log(arr.length);  //2

arr.length = 5;

console.log(arr);  //["John", "Andy", undefined, undefined, undefined]
console.log(arr.length);  //5
```

## **concat()**

concat() 方法用于连接两个或多个数组。该方法不会改变现有的数组，而仅仅会返回被连接数组的一个副本。

`arrayObject.concat(arrayX, arrayX, …… arrayX)`

注意：参数是必需的。可以是具体的值，也可以是数组对象，可以是任意多个。返回一个新的数组（该数组是通过把所有 arrayX 参数添加到 arrayObject 中生成的，如果arrayX是元素，则添加arrayX，如果arrayX是数组，则添加arrayX中的元素）。

```javascript
var a = [1,2,3];
var b = a.concat(4,5);
var c = a.concat(4,5,[6,7],8,"123");

console.log(a);  //[1, 2, 3]
console.log(b);  //[1, 2, 3, 4, 5]
console.log(c);  //[1, 2, 3, 4, 5, 6, 7, 8, "123"]
```

## **join()**

join() 方法用于把数组中的所有元素放入一个字符串。元素是通过指定的分隔符进行分隔的。

`arrayObject.join(separator)`

参数代表分隔符，是可选的，默认为半角逗号。注意返回值是字符串，不是数组。

```javascript
var arr = new Array(3)
arr[0] = "George"
arr[1] = "John"
arr[2] = "Thomas"

console.log(arr);  //["George", "John", "Thomas"]
console.log(arr.join());  //"George,John,Thomas"
console.log(arr.join(" & "));  //"George & John & Thomas"
```

现在的新主流浏览器，都对 + 运算符做了很好的优化，所以建议使用 + 运算符代替join()方法， 参考 [array join vs string connect](http://jsperf.com/array-join-vs-string-connect/37)

## **pop()**

pop() 方法用于删除并返回数组的最后一个元素。

pop() 方法将改变数组（删除数组的最后一个元素，把数组长度减 1），并且返回它删除的元素的值。如果数组已经为空，则 **pop() 不改变数组，并返回 undefined 值**。

```javascript
var arr = new Array(3)
arr[0] = "George"
arr[1] = "John"
arr[2] = "Thomas"

console.log(arr);        //["George", "John", "Thomas"]
console.log(arr.pop());  //"Thomas"
console.log(arr);        //["George", "John"]
console.log(arr.pop());  //"John"
console.log(arr);        //["George"]
console.log(arr.pop());  //"George"
console.log(arr);        //[]
console.log(arr.pop());  //undefined
console.log(arr);        //[]
```

## **push()**

push() 方法可向数组的末尾添加一个或多个元素，并返回新的长度，也就是添加元素后的数组长度。

`arrayObject.push(newelement1, newelement2, …., newelementX)`

push()方法最少要有一个参数。push() 方法可把它的参数顺序添加到 arrayObject 的尾部。它**直接修改 arrayObject**，而不是创建一个新的数组。push() 方法和 pop() 方法使用数组提供的先进后出栈的功能。

注意：push()方法中的参数不管是什么类型（数组、对象等），一个参数将会被作为一个整体元素插入 arrayObject 的尾部，不做拆分，详见示例。

```javascript
var a = ["a","b"];

var b = {
  name: "Tom"
};

var c = [1,2,3];

console.log(a);
console.log(a.push(b));
console.log(a);
console.log(a.push(c));
console.log(a);

/********* Output *********/

["a", "b"]
3
["a", "b", [object Object] {
  name: "Tom"
}]
4
["a", "b", [object Object] {
  name: "Tom"
}, [1, 2, 3]]
```

## **reverse()**

reverse() 方法用于颠倒数组中元素的顺序。

注意：该方法会改变原来的数组，而不会创建新的数组。

reverse()是sort()的逆序版，reverse()的详细排序行为请参见下文 sort() 方法的解释。

reverse()并非效率最高的数组倒序排列方法，如果你对效率要求更高，可以参考 [JS: Array.reverse() vs. for and while loops](http://jsperf.com/js-array-reverse-vs-while-loop/12)

```javascript
var a = ["a","b","c"];
var b = ["你","我","他"];
var c = [1,2,3];
var d = ["a","b","c",1,2,3,"你","我","他"];

console.log(a.reverse());  //["c", "b", "a"]
console.log(b.reverse());  //["他", "我", "你"]
console.log(c.reverse());  //[3, 2, 1]
console.log(d.reverse());  //["他", "我", "你", 3, 2, 1, "c", "b", "a"]
```

## **shift()**

shift() 方法用于把数组的第一个元素从其中删除，并返回**第一个元素的值**。

如果数组是空的，那么 shift() 方法将不进行任何操作，返回 undefined 值。请注意，该方法不创建新数组，而是**直接修改原有的数组**。

shift() 方法通常比 pop() 方法要慢很多。

```javascript
var arr = new Array(3)
arr[0] = "George"
arr[1] = "John"
arr[2] = "Thomas"

console.log(arr);          //["George", "John", "Thomas"]
console.log(arr.shift());  //"George"
console.log(arr);          //["John", "Thomas"]
console.log(arr.shift());  //"John"
console.log(arr);          //["Thomas"]
console.log(arr.shift());  //"Thomas"
console.log(arr);          //[]
console.log(arr.shift());  //undefined
```

## **slice()**

slice() 方法可从已有的数组中返回选定的元素。

`arrayObject.slice(start, end)`

参数start是必需的，规定从何处开始选取，如果是负数，那么它规定从数组尾部开始算起的位置。也就是说，-1 指最后一个元素，-2 指倒数第二个元素，以此类推。

参数end是可选的，规定从何处结束选取，该参数是数组片断结束处的数组下标。**如果没有指定该参数，那么切分的数组包含从 start 到数组结束的所有元素**。如果这个参数是负数，那么它规定的是从数组尾部开始算起的元素。

注意，该方法并不会修改数组，方法会返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。

**请注意slice()和splice()的区别：**[slice](http://www.iciba.com/slice)意思是切片，即把数组切出来一段；[splice](http://www.iciba.com/splice)意思是绞接，就像我们平时接两根绳子一样，需要把原来的绳子切下来一段，然后再和新绳子接在一起。如果想删除数组中的一段元素，并向数组添加新元素，应该使用方法 Array.splice()。

在使用slice()时，如果参数start超过了数组的起点，则会从数组头部开始；如果参数end超过了数组的结尾，则会从数组的尾部结束；如果start和end中的范围不在数组中，或者end小于start，则会返回空数组；如果start和end不为数字，则会进行转换，转换失败的话，start默认为0，end默认为0。详见示例：

```javascript
var arr = new Array(6);
arr[0] = "George";
arr[1] = "John";
arr[2] = "Thomas";
arr[3] = "James";
arr[4] = "Adrew";
arr[5] = "Martin";

console.log(arr); //["George", "John", "Thomas", "James", "Adrew", "Martin"]
console.log(arr.slice(2,4));      //["Thomas", "James"]
console.log(arr.slice(-3,4));     //["James"]
console.log(arr.slice(-10,4));    //["George", "John", "Thomas", "James"]
console.log(arr.slice(-10,-4));   //["George", "John"]
console.log(arr.slice(4,3));      //[]
console.log(arr.slice(-20,-10));  //[]
console.log(arr.slice("2","4"));  //["Thomas", "James"]
console.log(arr.slice("a","4"));  //["George", "John", "Thomas", "James"]
console.log(arr.slice("a","b"));  //[]
console.log(arr.slice("2a","4a"));//[]
console.log(arr.slice("",""));    //[]
```

## **sort()**

sort() 方法用于对数组的元素进行排序（从小到大）。

`arrayObject.sort(sortby)`

请注意，数组在原数组上进行排序，不生成副本。参数sortby是可选的，是自定义的函数，规定排序方法。

如果调用该方法时没有使用参数，将按字母顺序对数组中的元素进行排序，说得更精确点，是按照字符编码的顺序进行排序。要实现这一点，首先**应把数组的元素都转换成字符串**（如有必要），以便进行比较。

如果想按照其他标准进行排序，就**需要提供比较函数**，该函数要比较两个值，然后返回一个用于说明这两个值的相对顺序的数字。比较函数应该具有两个参数 a 和 b，其返回值如下：

* 若 a 小于 b，在排序后的数组中 a 应该出现在 b 之前，则返回一个小于 0 的值。
* 若 a 等于 b，则返回 0。
* 若 a 大于 b，则返回一个大于 0 的值。

```javascript
var arr = new Array(6);
arr[0] = "10";
arr[1] = "5";
arr[2] = "40";
arr[3] = "25";
arr[4] = "1000";
arr[5] = "1";

function sortNumber(a,b)
{
  return a - b;
}

console.log(arr);  //["10", "5", "40", "25", "1000", "1"]
console.log(arr.sort());  //["1", "10", "1000", "25", "40", "5"]
console.log(arr.sort(sortNumber));  //["1", "5", "10", "25", "40", "1000"]
```

## **splice()**

splice() 方法用于插入、删除或替换数组的元素。

`arrayObject.splice(index, howmany, element1, ….., elementX)`

参数index是必需的。规定从何处添加/删除元素，该参数是开始（包含）插入和（或）删除的数组元素的下标，必须是数字。

参数howmany是必需的。规定应该删除多少元素。必须是数字，但可以是 “0″。如果未规定此参数，则删除从 index 开始到原数组结尾的所有元素。

参数element1…elementX是可选的。规定要添加到数组的新元素，从 index 所指的下标处开始插入。

splice() 方法可删除从 index 处开始的零个或多个元素，并且用参数列表中声明的一个或多个值来替换那些被删除的元素。如果从 arrayObject 中删除了元素，则**返回的是含有被删除的元素的数组。splice()会直接对原数组进行修改。**

注意如果参数index不为数字，则会自动转换，详见示例：

```javascript
var arr = new Array(6);
arr[0] = "George";
arr[1] = "John";
arr[2] = "Thomas";
arr[3] = "James";
arr[4] = "Adrew";
arr[5] = "Martin";

console.log(arr);  //["George", "John", "Thomas", "James", "Adrew", "Martin"]
console.log(arr.splice(2,1));  //["Thomas"]
console.log(arr);  //["George", "John", "James", "Adrew", "Martin"]
console.log(arr.splice(2,2,"William"));  //["James", "Adrew"]
console.log(arr);  //["George", "John", "William", "Martin"]
console.log(arr.splice(2,1,"Tom","Jerry"));  //["William"]
console.log(arr);  //["George", "John", "Tom", "Jerry", "Martin"]
console.log(arr.splice(2));  //["Tom", "Jerry", "Martin"]
console.log(arr);  //["George", "John"]
console.log(arr.splice("2"));  //[]
console.log(arr);  //["George", "John"]
console.log(arr.splice("a"));  //["George", "John"]
console.log(arr);  //[]
```

注意如果index为负数，则会从数组尾部算起；howmany为负数，则不删除。详见示例：

```javascript
var arr = new Array(6);
arr[0] = "George";
arr[1] = "John";
arr[2] = "Thomas";
arr[3] = "James";
arr[4] = "Adrew";
arr[5] = "Martin";

console.log(arr);  //["George", "John", "Thomas", "James", "Adrew", "Martin"]
console.log(arr.splice(-2,1));  //["Adrew"]
console.log(arr);  //["George", "John", "Thomas", "James", "Martin"]
console.log(arr.splice(-2,-1));  //[]
console.log(arr);  //["George", "John", "Thomas", "James", "Martin"]
```

对于大型数组，splice()的效率会比较低，参考 [Splicing a single value](http://jsperf.com/splicing-a-single-value/26)


## **toString()**

toString() 方法可把数组转换为字符串，并返回结果。

Array.toString() 相当于 Array.join() ，返回值与没有参数的 join() 方法返回的字符串相同。

## **unshift()**

unshift() 方法可向数组的开头添加一个或更多元素，并返回新的长度。

`arrayObject.unshift(newelement1, newelement2, …., newelementX)`

参数newelement1……X至少要有一个。unshift() 方法将把它的参数插入 arrayObject 的头部，并将已经存在的元素顺次地移到较高的下标处，以便留出空间。该方法的第一个参数将成为数组的新元素 0，如果还有第二个参数，它将成为新的元素 1，以此类推。

注意，unshift() 方法不创建新的数组，而是**直接修改原有的数组**。在**IE6与IE7中，unshift()会返回 underfined！**

```javascript
var arr = new Array(3);
arr[0] = "George";
arr[1] = "John";
arr[2] = "Thomas";

console.log(arr);  //["George", "John", "Thomas"]
console.log(arr.unshift("William"));  //4
console.log(arr.unshift("Tom","Jerry"));  //6
console.log(arr);  //["Tom", "Jerry", "William", "George", "John", "Thomas"]
```

**改变原数组的方法：`pop()、push()、reverse()、shift()、sort()、splice()、unshift()`**

**不改变原数组的方法：`concat()、join()、slice()、toString()`**

注意：JavaScript里面，没有好的机制来区别Array和Object，一般可以通过下面的方法来识别数组：

```javascript
var isArray = function(value){
  return Object.prototype.toString.apply(value) === '[object Array]';
}
```

Object.prototype.toString对任何变量会永远返回这样一个字符串“[object, class]”，而这个class就是JavaScript内嵌对象的构造函数的名字。至于用户自定义的变量，则class等于object。因此通过Object.prototype.toString.apply(obj)可以准确的获取变量数据类型。通过Object.prototype.toString可以获得的数据类型包括：Date,Object,String,Number,Boolean,Regexp,Function,undefined,null,Math等。

一些JavaScript新版本的方法，在这里就不一一介绍了，可以参考 [MDN](https://developer.mozilla.org/zh-CN/docs/JavaScript/Reference/Global_Objects/Array)。

本文章中的控制台输出使用的 [jsbin](http://jsbin.com/)，调试环境不同，输出结果的显示形式可能有所不同。