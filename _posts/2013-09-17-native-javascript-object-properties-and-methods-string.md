---
layout: post
title: JavaScript原生对象属性和方法详解——String对象
excerpt: <p>本文介绍String对象的主要属性和方法 ...</p>
---

## **length**

length 属性可返回字符串中的字符数目。

length 是根据字符串的UTF-16编码来获取长度的，空字符串长度为0。length 不可修改。

## **charAt()**

charAt() 方法可返回指定位置的字符。注意，JavaScript 并没有一种有别于字符串类型的字符数据类型，所以返回的字符是长度为 1 的字符串。

`stringObject.charAt(index)`

参数index是必需的。表示字符串中某个位置的数字，即字符在字符串中的下标。字符串中第一个字符的下标是 0。如果参数 index 不在 0 与 string.length 之间，该方法将返回一个空字符串。

注意：charAt() 方法对于一些非 BMP(Basic-Multilingual-Plane) 字符支持会有问题，参考：[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)

## **charCodeAt()**

charCodeAt() 方法可返回指定位置的字符的 Unicode 编码。这个返回值是 0 – 65535 之间的整数。
方法 charCodeAt() 与 charAt() 方法执行的操作相似，只不过前者返回的是位于指定位置的字符的编码，而后者返回的是字符子串。

`stringObject.charCodeAt(index)`

参数index是可选的。表示字符串中某个位置的数字，即字符在字符串中的下标。字符串中第一个字符的下标是 0。如果 index 是负数，或大于等于字符串的长度，则 charCodeAt() 返回 NaN。index为空时默认为0。

Unicode 编码的范围是 0 到 1,114,111。前128个Unicode 编码和ASCII字符编码匹配。charCodeAt() 方法返回的值总是小于65536，因为更高值的字符会成对出现，需要用charCodeAt(i)和charCodeAt(i+1)同时检索。

## **concat()** –不推荐使用

concat() 方法用于连接两个或多个字符串。

`stringObject.concat(stringX, stringX, …, stringX)`

参数stringX是必需的。是将被连接为一个字符串的一个或多个字符串对象。

concat() 方法将把它的所有参数转换成字符串，然后按顺序连接到字符串 stringObject 的尾部，并返回连接后的字符串。请注意，stringObject 本身并没有被更改。

*注意，强烈建议使用 ” + ” 运算符来进行字符串的连接，来替代这个方法，效率也更高，参考：[concat vs + vs join](http://jsperf.com/concat-vs-plus-vs-join)*

## **indexOf()**

indexOf() 方法可返回某个指定的字符串值在字符串中首次出现的位置。

`stringObject.indexOf(searchvalue, fromindex)`

参数searchvalue是必需的，规定需检索的字符串值。参数fromindex是可选的整数参数。规定在字符串中开始检索的位置。它的合法取值是 0 到 stringObject.length – 1。如省略该参数，则将从字符串的首字符开始检索。

该方法将从头到尾地检索字符串 stringObject，看它是否含有子串 searchvalue。开始检索的位置在字符串的 fromindex 处或字符串的开头（没有指定 fromindex 时）。如果找到一个 searchvalue，则返回 searchvalue 的第一次出现的位置。stringObject 中的字符位置是从 0 开始的。

**注意：indexOf() 方法对大小写敏感！如果要检索的字符串值没有出现，则该方法返回 -1。**

## **lastIndexOf()**

lastIndexOf() 方法可返回一个指定的字符串值最后出现的位置，在一个字符串中的指定位置从后向前搜索。

lastIndexOf() 和 indexOf() 参数和使用方法一致，只不过是从后向前搜索。

```javascript
var str="Hello world world!"

console.log(str.indexOf("wo"));        //6
console.log(str.indexOf("wo",2));      //6
console.log(str.indexOf("wo",10));     //12
console.log(str.lastIndexOf("wo"));    //12
console.log(str.lastIndexOf("wo",2));  //-1
console.log(str.lastIndexOf("wo",10)); //6
```

## **localeCompare()**

用本地特定的顺序来比较两个字符串。

`stringObject.localeCompare(target)`

参数target是必需的，要以本地特定的顺序与 stringObject 进行比较的字符串。

返回比较结果的数字。如果 stringObject 小于 target，则 localeCompare() 返回小于 0 的数。如果 stringObject 大于 target，则该方法返回大于 0 的数。如果两个字符串相等，或根据本地排序规则没有区别，该方法返回 0。

把 < 和 > 运算符应用到字符串时，它们只用字符的 Unicode 编码比较字符串，而不考虑当地的排序规则。以这种方法生成的顺序不一定是正确的。例如，在西班牙语中，其中字符 “ch” 通常作为出现在字母 “c” 和 “d” 之间的字符来排序。localeCompare() 方法提供的比较字符串的方法，考虑了默认的本地排序规则。

localeCompare()在某些高级浏览器中的参数还支持locales 和 options，参考下面的代码和 [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare)：

```javascript
//不同文化的排序规则不同
console.log('ä'.localeCompare('z', 'de'));  //-1
console.log('ä'.localeCompare('z', 'sv'));  //1
```

## **match()**

match() 方法可在字符串内检索指定的值，或找到一个或多个正则表达式的匹配。

该方法类似 indexOf() 和 lastIndexOf()，但是它返回指定的值，而不是字符串的位置。

`stringObject.match(regexp)`

参数regexp可以是字符串，也可以是正则表达式 RegExp 对象。

返回存放匹配结果的数组。该数组的内容依赖于 regexp 是否具有全局标志 g。

如果 regexp 没有标志 g，那么 match() 方法就只能在 stringObject 中执行一次匹配。如果没有找到任何匹配的文本， match() 将返回 null。否则，它将返回一个数组，其中存放了与它找到的匹配文本有关的信息。该数组的第 0 个元素存放的是匹配文本，而其余的元素存放的是与正则表达式的子表达式匹配的文本。除了这些常规的数组元素之外，返回的数组**还含有两个对象属性**。index 属性声明的是匹配文本的起始字符在 stringObject 中的位置，input 属性声明的是对 stringObject 的引用。

如果 regexp 具有标志 g，则 match() 方法将执行全局检索，找到 stringObject 中的所有匹配子字符串。若没有找到任何匹配的子串，则返回 null。如果找到了一个或多个匹配子串，则返回一个数组。不过全局匹配返回的数组的内容与前者大不相同，它的数组元素中存放的是 stringObject 中所有的匹配子串，而且也**没有 index 属性或 input 属性**。

没有标志g，调用 stringObject.match(regexp) 和调用 regexp.exec(stringObject) 的结果相同。在全局检索模式下，match() 即不提供与子表达式匹配的文本的信息，也不声明每个匹配子串的位置。如果需要这些全局检索的信息，可以使用 RegExp.exec()。

**注意：如果需要知道一个字符串是否匹配一个正则表达式，使用 regexp.test(string)；如果只想一次匹配，使用 regexp.exec(string) 代替 string.match(regexp)。**

```javascript
var str="Hello world!"
var str2="1 plus 2 equal 3"

console.log(str.match("world"));  //["world", index: 6, input: "Hello world!"]
console.log(str2.match(/\d+/g));  //["1", "2", "3"]
```

## **replace()**

replace() 方法用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。

`stringObject.replace(regexp/substr, replacement)`

参数regexp/substr是必需的。规定子字符串或要替换的模式的 RegExp 对象。如果该值是一个字符串，则将它作为要检索的直接量文本模式，而不是首先被转换为 RegExp 对象。**参数replacement是必需的。是一个字符串值。规定了替换文本或生成替换文本的函数。**

方法会返回一个新的字符串，是用 replacement 替换了 regexp 的第一次匹配或所有匹配之后得到的。

字符串 stringObject 的 replace() 方法执行的是查找并替换的操作。它将在 stringObject 中查找与 regexp 相匹配的子字符串，然后用 replacement 来替换这些子串。如果 regexp 具有全局标志 g，那么 replace() 方法将替换所有匹配的子串。否则，它只替换第一个匹配子串。

replacement 可以是字符串，也可以是函数。如果它是字符串，那么每个匹配都将由字符串替换。但是 replacement 中的 $ 字符具有特定的含义。如下所示，它说明从模式匹配得到的字符串将用于替换：

* $$ – $
* $` - 位于匹配子串左侧的文本。
* $’ - 位于匹配子串右侧的文本。
* $& - 与 regexp 相匹配的子串。
* $number - 与 regexp 中的第 number个子表达式相匹配的文本。

replacement 可以是函数，在这种情况下，每个匹配都调用该函数，它返回的字符串将作为替换文本使用。该函数的第一个参数是匹配模式的字符串。接下来的参数是与模式中的子表达式匹配的字符串，可以有 0 个或多个这样的参数。接下来的参数是一个整数，声明了匹配在 stringObject 中出现的位置。最后一个参数是 stringObject 本身。

```javascript
//替换一次
var str = "Hello Microsoft!";
console.log(str.replace(/Microsoft/, "Google"));  //Hello Google!
console.log(str);  //Hello Microsoft!

//替换多次
var str2 = "Hello Microsoft! and Microsoft! and Microsoft! or Microsoft!";
console.log(str2.replace(/Microsoft/g, "Google"));  //Hello Google! and Google! and Google! or Google!

//字符转换
var str3 = "Doe, John";
console.log(str3.replace(/(\w+)\s*, \s*(\w+)/, "$2 $1"));  //John Doe

var str4 = '"a", "b"';
console.log(str4.replace(/"([^"]*)"/g, "'$1'"));  //'a', 'b'

//使用函数
var str5 = 'aaa bbb ccc';
console.log(str5.replace(/\b\w+\b/g, function(word){
  return word.substring(0,1).toUpperCase()+word.substring(1);}
));   //Aaa Bbb Ccc
```

## **search()**

search() 方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串。

`stringObject.search(regexp)`

参数regexp可以是需要在 stringObject 中检索的子串，也可以是需要检索的 RegExp 对象。

返回stringObject 中第一个与 regexp 相匹配的子串的起始位置。如果没有找到任何匹配的子串，则返回 -1。

注意：search() 方法不执行全局匹配，它将忽略标志 g。它同时忽略 regexp 的 lastIndex 属性，并且总是从字符串的开始进行检索，这意味着它总是返回 stringObject 的**第一个匹配的位置。**

```javascript
var str = "Hello Microsoft!";
console.log(str.search(/Microsoft/));   //6
```

如果只是想知道是否有匹配的字符串，使用search()和使用test()方法差不多。如果想得到更多的信息，可以使用match()和exec()方法，但是效率会低。

## **slice()**

slice() 方法可提取字符串的某个部分，并以新的字符串返回被提取的部分。

`stringObject.slice(start, end)`

参数start是要抽取的片断的起始下标。如果是负数，则该参数规定的是从字符串的尾部开始算起的位置。也就是说，-1 指字符串的最后一个字符，-2 指倒数第二个字符，以此类推。

参数end是紧接着要抽取的片段的结尾的下标。若未指定此参数，则要提取的子串包括 start 到原字符串结尾的字符串。如果该参数是负数，那么它规定的是从字符串的尾部开始算起的位置。

方法会返回一个新的字符串。包括字符串 stringObject 从 start 开始（包括 start）到 end 结束（不包括 end）为止的所有字符。

注意：String 对象的方法 slice()、substring() 和 substr() 都可返回字符串的指定部分。***强烈建议在所有场合都使用 slice() 方法***。

```javascript
var str = "Hello Microsoft!";
console.log(str.slice(6));      //Microsoft!
console.log(str.slice(6, 12));  //Micros
```

## **substring()**

不推荐使用，建议使用slice()替代。

## **substr()**

不推荐使用，建议使用slice()替代。

## **toLocaleLowerCase()**

不推荐使用，只在土耳其语等少数语种中有用，建议使用toLowerCase()替代。

## **toLocaleUpperCase()**

不推荐使用，只在土耳其语等少数语种中有用，建议使用toUpperCase()替代。

## **toLowerCase()**

toLowerCase() 方法用于把字符串转换为小写。

## **toUpperCase()**

toUpperCase() 方法用于把字符串转换为大写。

---

String对象还有很多用于HTML 标签的方法：`anchor()、big()、blink()、bold()、fixed()、fontcolor()、fontsize()、italics()、link()、small()、strike()、sub()、sup()`。他们主要是对String对象进行HTML格式化处理，现在已经很少有人会应用到了，**不推荐使用**。参见：[演示代码](http://www.w3school.com.cn/tiy/t.asp?f=jseg_str_style)