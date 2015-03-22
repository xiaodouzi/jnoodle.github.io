---
layout: post
title: JavaScript原生对象属性和方法详解——Date对象
excerpt: <p>本文介绍Date对象的主要属性和方法 ...</p>
---

创建 Date 对象的语法：

```javascript
//Date 对象会自动把当前日期和时间保存为其初始值。
new Date();

//value-毫秒：代表自世界协调时1970年1月1日00:00:00开始的数值。
new Date(value);

//dateString-日期字符串：表示日期的字符串值。此字符串应该是在parse方法中识别的格式。
new Date(dateString);

//year-年：代表年份的整数值。为了避免2000年问题最好指定4位数的年份; 使用1998, 而不要用98
//month-月：代表月份的整数值从0（1月）到11（12月）
//day-日：代表一个月中的第几天的整数值，从1开始
//hour-小时：代表一天中的小时数的整数值 (24小时制)
//minute-分钟
//second-秒
//millisecond-毫秒
new Date(year, month, day [, hour, minute, second, millisecond]);
```

## **Date()**

Date() 方法可返回当天的日期和时间。

```javascript
console.log(Date());  //"Tue Sep 17 2013 12:22:55 GMT+0800 (中国标准时间)"
```

## **parse()**

parse() 方法可解析一个日期时间字符串，并返回 1970/1/1 午夜距离该日期时间的毫秒数。

`Date.parse(datestring)`

参数datestring是必需的，表示日期和时间的字符串。

注意，该方法是 Date 对象的静态方法。一般采用 Date.parse() 的形式来调用，而不是通过 dateobject.parse() 调用该方法。

```javascript
console.log(Date.parse(Date()));        //1379392301000
console.log(Date.parse("Aug 9, 1995")); //807897600000
```

## **UTC()**

UTC() 方法可根据世界时返回 1970 年 1 月 1 日 到指定日期的毫秒数。

`Date.UTC(year, month, day, hours, minutes, seconds, ms)`

参数year是必需的，表示年份的四位数字；month是必需的，表示月份的整数，介于 0 ~ 11；day是可选的，表示日期的整数，介于 1 ~ 31；hours是可选的，表示小时的整数，介于 0 ~ 23；minutes是可选的，表示分钟的整数，介于 0 ~ 59；seconds是可选的，表示秒的整数，介于 0 ~ 59；ms是可选的，表示毫秒的整数，介于 0 ~ 999。

Date.UTC() 是一种静态方法。Date.UTC() 方法的参数指定日期和时间，它们都是 UTC 时间，处于 GMT 时区。指定的 UTC 时间将转换成毫秒的形式，这样构造函数 Date() 和方法 Date.setTime() 就可以使用它了。

ECMAScript中的Date类型是早期Java中的Java.util.Date类基础上构建的。为此，Date类型使用来自UTC(Coordinated Universal Time,国际协调时间)1970年1月1日午夜（零时）开始经过的毫秒数来保存日期。在使用这种数据存储格式的条件下，Date类型保存的日期能够精确到1970年1月1日之前或之后的285616年。

**注意：parse()日期和时间都基于本地时区而非GMT来创建。而UTC()是基于GMT来创建。他们的参数也不相同。**

GMT：[世界时](http://baike.baidu.com/view/37429.htm)，即格林尼治所在地的标准时间。

```javascript
var d = new Date();

console.log(Date.parse(d));  //1379393562000
console.log(Date.UTC(d.getFullYear(), d.getMonth(), d.getDate(), d.getHours(), d.getMinutes(), d.getSeconds(), d.getMilliseconds()));  //1379422362020
```

ECMAScript5添加了Data.now()方法，返回表示调用这个方法时的日期和时间的毫秒数。IE9才开始支持，不过我们可以通过 + 操作符来把Data对象转换成字符串，得到同样的值。

```javascript
var d1 = Date.now();
var d2 = + new Date();

console.log(d1);  //1379393793104
console.log(d2);  //1379393793104
```

**JavaScript中的日期转换非常的诡异，不仅会因为参数不同而有不同的解释结果，而且在各个浏览器中的表现也有所不同，如下：**

```javascript
var d1 = new Date("2012/03/13");
var d2 = new Date("2012-03-13");
var d3 = new Date("2012-3-13");

console.log(d1);  //Tue Mar 13 2012 00:00:00 GMT+0800 (中国标准时间)
console.log(d2);  //Tue Mar 13 2012 08:00:00 GMT+0800 (中国标准时间)
console.log(d3);  //Tue Mar 13 2012 00:00:00 GMT+0800 (中国标准时间)
```

在不同浏览器中的表现参考：<http://dygraphs.com/date-formats.html>

为了避免这些问题，请遵照下面的建议：

* 坚持使用 ”YYYY/MM/DD” 的日期字符串格式
* 避免使用带有连字号的日期字符串格式”YYYY-MM-DD”
* 要指定四位数的年份
* Chrome浏览器的比其他浏览器能接受更多的日期字符串，所以如果在Chrome浏览器没有问题，不代表其他浏览器没有问题

更多信息可以参考：[JavaScript and Dates, What a Mess!](http://blog.dygraphs.com/2012/03/javascript-and-dates-what-mess.html) 和 [SO中的讨论](http://stackoverflow.com/questions/2587345/javascript-date-parse)

## **get系列方法**

* `getDate()` 从 Date 对象返回一个月中的某一天 (1 ~ 31)。
* `getDay()` 从 Date 对象返回一周中的某一天 (0 ~ 6)。
* `getMonth()` 从 Date 对象返回月份 (0 ~ 11)。
* `getFullYear()` 从 Date 对象以四位数字返回年份。注意不要使用getYear()。
* `getHours()` 返回 Date 对象的小时 (0 ~ 23)。
* `getMinutes()` 返回 Date 对象的分钟 (0 ~ 59)。
* `getSeconds()` 返回 Date 对象的秒数 (0 ~ 59)。
* `getMilliseconds()` 返回 Date 对象的毫秒(0 ~ 999)。
* `getTime()` 返回 1970 年 1 月 1 日至今的毫秒数。
* `getTimezoneOffset()` 返回本地时间与格林威治标准时间 (GMT) 的分钟差。
* `getUTCDate()` 根据世界时从 Date 对象返回月中的一天 (1 ~ 31)。
* `getUTCDay()` 根据世界时从 Date 对象返回周中的一天 (0 ~ 6)。
* `getUTCMonth()` 根据世界时从 Date 对象返回月份 (0 ~ 11)。
* `getUTCFullYear()` 根据世界时从 Date 对象返回四位数的年份。
* `getUTCHours()` 根据世界时返回 Date 对象的小时 (0 ~ 23)。
* `getUTCMinutes()` 根据世界时返回 Date 对象的分钟 (0 ~ 59)。
* `getUTCSeconds()` 根据世界时返回 Date 对象的秒钟 (0 ~ 59)。
* `getUTCMilliseconds()` 根据世界时返回 Date 对象的毫秒(0 ~ 999)。

## **set系列方法**

* `setDate()` 设置 Date 对象中月的某一天 (1 ~ 31)。
* `setMonth()` 设置 Date 对象中月份 (0 ~ 11)。
* `setFullYear()` 设置 Date 对象中的年份（四位数字）。注意不要使用setYear()方法。
* `setHours()` 设置 Date 对象中的小时 (0 ~ 23)。
* `setMinutes()` 设置 Date 对象中的分钟 (0 ~ 59)。
* `setSeconds()` 设置 Date 对象中的秒钟 (0 ~ 59)。
* `setMilliseconds()` 设置 Date 对象中的毫秒 (0 ~ 999)。
* `setTime()` 以毫秒设置 Date 对象。
* `setUTCDate()` 根据世界时设置 Date 对象中月份的一天 (1 ~ 31)。
* `setUTCMonth()` 根据世界时设置 Date 对象中的月份 (0 ~ 11)。
* `setUTCFullYear()` 根据世界时设置 Date 对象中的年份（四位数字）。
* `setUTCHours()` 根据世界时设置 Date 对象中的小时 (0 ~ 23)。
* `setUTCMinutes()` 根据世界时设置 Date 对象中的分钟 (0 ~ 59)。
* `setUTCSeconds()` 根据世界时设置 Date 对象中的秒钟 (0 ~ 59)。
* `setUTCMilliseconds()` 根据世界时设置 Date 对象中的毫秒 (0 ~ 999)。

## **toString系列方法**

* `toString()` 把 Date 对象转换为字符串，toString()总是返回一个用美式英语表达的字符串。
* `toTimeString()` 把 Date 对象的时间部分转换为字符串。
* `toDateString()` 把 Date 对象的日期部分转换为字符串。
* `toUTCString()` 根据世界时，把 Date 对象转换为字符串。
* `toLocaleString()` 根据本地时间格式，把 Date 对象转换为字符串。
* `toLocaleTimeString()` 根据本地时间格式，把 Date 对象的时间部分转换为字符串。
* `toLocaleDateString()` 根据本地时间格式，把 Date 对象的日期部分转换为字符串。

```javascript
var d = new Date();

console.log(d);                      //Tue Sep 17 2013 13:37:04 GMT+0800 (中国标准时间)
console.log(d.toString());           //Tue Sep 17 2013 13:37:04 GMT+0800 (中国标准时间)
console.log(d.toTimeString());       //13:37:04 GMT+0800 (中国标准时间)
console.log(d.toDateString() );      //Tue Sep 17 2013
console.log(d.toUTCString());        //Tue, 17 Sep 2013 05:37:04 GMT
console.log(d.toLocaleString());     //2013年9月17日 下午1:37:04
console.log(d.toLocaleTimeString()); //下午1:37:04
console.log(d.toLocaleDateString()); //2013年9月17日
```

注意toLocaleString()系列方法可以接收参数，来确定按照什么习惯来输出，参考：[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString)

```javascript
var d = new Date();

console.log(d.toLocaleString("ko-KR"));  //2013년 9월 17일 오후 1:48:24
```
