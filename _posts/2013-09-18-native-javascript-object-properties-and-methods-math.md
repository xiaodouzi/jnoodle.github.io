---
layout: post
title: JavaScript原生对象属性和方法详解——Math对象
excerpt: <p>本文介绍Math对象的主要属性和方法 ...</p>
---

Math对象主要是用来执行一些数学任务，介绍它们的同时，也帮大家回忆一下数学知识。

## **E**

Math.E 属性代表算术常量 e，即[自然对数的底数](http://baike.baidu.com/view/36492.htm#sub7987864)，其值近似于 2.71828。

## **LN2**

LN2 属性就是 loge2，即 2 的自然对数，其值近似于 0.69314718055994528623。

复习一下[对数](http://zh.wikipedia.org/zh-cn/%E5%B0%8D%E6%95%B8)：如果 a<sup>b</sup>=n，那么 log<sub>(a)</sub>(n)=b。其中，a叫做“底数”，n叫做“真数”，b叫做“以a为底的n的对数”。 log<sub>(a)</sub>(n) 函数叫做对数函数。对数函数中n的定义域是n>0，零和负数没有对数；a的定义域是a>0且a≠1。

## **LN10**

LN10 属性就是 loge10，即 10 的自然对数，其值近似于 2.3025850929940459011。

## **LOG2E**

LOG2E 属性就是 log2e，即以 2 为底 e 的对数，其值近似于 1.442695040888963387。

## **PI**

PI 属性就是 π，也就是常说的[圆周率](http://zh.wikipedia.org/zh/%E5%9C%93%E5%91%A8%E7%8E%87)，即圆的周长和它的直径之比。这个值近似为 3.141592653589793。

## **SQRT2**

SQRT2 属性返回 2 的平方根。这个值近似为 1.4142135623730951。

## **SQRT1_2**

SQRT1_2 属性返回 2 的平方根的倒数。这个值近似为 0.7071067811865476。

```javascript
console.log(Math.E);        //2.718281828459045
console.log(Math.LN2);      //0.6931471805599453
console.log(Math.LN10);     //2.302585092994046
console.log(Math.LOG2E);    //1.4426950408889634
console.log(Math.LOG10E);   //0.4342944819032518
console.log(Math.PI);       //3.141592653589793
console.log(Math.SQRT1_2);  //0.7071067811865476
console.log(Math.SQRT2);    //1.4142135623730951
```

## **abs(x)**

abs() 方法可返回数的绝对值。

**参数x是必需的**，必须是一个数值。方法会返回x的绝对值，如果x不是数字或者不能转换成数字，会返回NaN；如果x为null，会返回0。

abs() 是静态方法，调用的方式是Math.abs(x)，Math对象的方法一般都是静态方法，调用方式均为 Math.方法名(参数)，就不一一说明了。

```javascript
Math.abs('-1');     // 1
Math.abs(-2);       // 2
Math.abs(null);     // 0
Math.abs("string"); // NaN
Math.abs();         // NaN
```

## **ceil(x)**

ceil() 方法可对一个数进行上舍入，方法执行的是向上取整计算。

**参数x是必需的，必须是一个数值。方法会返回大于等于 x，并且与它最接近的整数。**

```javascript
Math.ceil(.95);   // 1
Math.ceil(4);     // 4
Math.ceil(7.004); // 8
```

## **floor(x)**

floor() 方法可对一个数进行下舍入，方法执行的是向下取整计算。

参数x是必需的，可以是任意数值或表达式。方法会返回小于等于 x，并且与它**最接近的整数**。

```javascript
Math.floor(.95);   // 0
Math.floor(4);     // 4
Math.floor(7.004); // 7
```

## **round(x)**

round() 方法可把一个数字舍入为最接近的**整数**。

参数x是**必需的**，必须是一个数值。方法返回与 x 最接近的整数。

对于 0.5，该方法将进行上舍入。例如，3.5 将舍入为 4，而 -3.5 将舍入为 -3。

```javascript
Math.round(20.49);  //20
Math.round(20.5);   //21
Math.round(-20.5);  //-20
Math.round(-20.51); //-21
```

在JavaScript中没有现成的四舍五入解决方法，通过对round()的改造，可以进行四舍五入。下面给出一个**推荐的方法**来进行四舍五入：

```javascript
function roundNumber(number, digits) {
    if (arguments.length == 1)
        return Math.round(number);

    var multiple = Math.pow(10, digits);
    var rndedNum = Math.round(number * multiple) / multiple;
    return rndedNum;
}
```

## **exp(x)**

exp() 方法可返回 e 的 x 次幂的值。

参数x是必需的，可以是任意数值或表达式，被用作指数。方法会返回 e 的 x 次幂。e 代表自然对数的底数，其值近似为 2.71828。

```javascript
Math.exp(1);  //2.718281828459045
Math.exp(2);  //7.3890560989306495
```

## **log(x)**

log() 方法可返回一个数的自然对数。

**参数x是必需的**，可以是任意数值或表达式。方法会返回 x 的自然对数。

如果参数的值是0，则会返回 -Infinity；如果参数是负数，则会返回NaN。

```javascript
Math.log(10);   //2.302585092994046
Math.log(0);    //-Infinity
Math.log(-1);   //NaN
Math.log("a");  //NaN
```

## **max(x…)**

max() 方法可返回两个或多个指定的数中带有较大的值的那个数。

**参数x可以为0 或多个值。**

方法返回参数中最大的值。如果没有参数，则返回 -Infinity；如果有某个参数为 NaN，或是不能转换成数字的非数字值，则返回 NaN。

```javascript
Math.max(7.25,7.30,7.301);  //7.301
Math.max();                 //-Infinity
Math.max(1,"a");            //NaN
```

## **min(x…)**

min() 方法可返回指定的数字中带有最低值的数字。

**参数x可以为0 或多个值。**

方法返回参数中最小的值。如果没有参数，则返回 Infinity；如果有某个参数为 NaN，或是不能转换成数字的非数字值，则返回 NaN。

```javascript
Math.min(7.25,7.30,7.301);  //7.25
Math.min();                 //Infinity
Math.min(1,"a");            //NaN
```

## **pow(x,y)**

pow() 方法可返回 x 的 y 次幂的值。

参数x和y都是必需的，必须是数字。

方法返回 x 的 y 次幂。如果结果是虚数或负数，则该方法将返回 NaN。如果由于指数过大而引起浮点溢出，则该方法将返回 Infinity。

```javascript
Math.pow(2,2);    //4
Math.pow(2,2,3);  //4
Math.pow(2,"a");  //NaN
Math.pow(2);      //NaN
Math.pow();       //NaN
Math.pow(1000000,1000000); //Infinity
```

## **sqrt(x)**

sqrt() 方法可返回一个数的平方根。

**参数x是必需的**，必须是大于等于 0 的数。

方法会返回参数 x 的平方根。如果 x 小于 0，则返回 NaN。

```javascript
Math.pow(2,2);  //4
Math.sqrt(4);   //2
```

## **random()**

random() 方法可返回介于 0 ~ 1 之间（不包括1）的一个随机数。

注意 random() 方法的种子是根据当前时间来的，和Java类似。

如果想要获取一个范围内的随机数，可以采用下面的方法：

```javascript
//获取min和max之间的随机数
function getRandomArbitrary(min, max) {
  return Math.random() * (max - min) + min;
}

//获取min和max之间的随机整数
function getRandomInt(min, max) {
  return Math.floor(Math.random() * (max - min + 1) + min);
}
```

一个更完整的方法：

```javascript
Math.randomRange = function(min, max) {
    if (min && max) {
        return (min + Math.floor(Math.random() * (max - min + 1)));
    } else if (min) {
        return (Math.floor(Math.random() * min + 1))
    } else {
        return (Math.floor(Math.random() * 101));
    }
}
```

给出一个随机创建GUID的方法，更多方法可以参考：[SO上的问题](http://stackoverflow.com/questions/105034/how-to-create-a-guid-uuid-in-javascript)。

```javascript
generateGUID =
    (typeof(window.crypto) != 'undefined' && typeof(window.crypto.getRandomValues) != 'undefined')
        ? function () {
            var buf = new Uint16Array(8);
            window.crypto.getRandomValues(buf);
            var S4 = function (num) {
                var ret = num.toString(16);
                while (ret.length < 4) {
                    ret = "0" + ret;
                }
                return ret;
            };
            return (S4(buf[0]) + S4(buf[1]) + "-" + S4(buf[2]) + "-" + S4(buf[3]) + "-" + S4(buf[4]) + "-" + S4(buf[5]) + S4(buf[6]) + S4(buf[7]));
        }
        : function () {
            return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function (c) {
                var r = Math.random() * 16 | 0, v = c == 'x' ? r : (r & 0x3 | 0x8);
                return v.toString(16);
            });
        };
```

## **三角函数和反三角函数**

回忆一下中学数学。[三角函数](http://zh.wikipedia.org/zh-cn/%E4%B8%89%E8%A7%92%E5%87%BD%E6%95%B0)的基本定义：

### 1、直角三角形中的三角函数：

下面是一个直角三角形，这个三角形中，角 θ 的对边、邻边和斜边分别是a、b 和 h，如下图所示：

![image](/images/post/20130918-Trigonometry_triangle_sim.png)

* **θ的正弦是对边与斜边的比值：sinθ = a / h**
* **θ的余弦是邻边与斜边的比值：cosθ = b / h**
* **θ的正切是对边与邻边的比值：tanθ = a / b**
* θ的余切是邻边与对边的比值：cotθ = b / a
* θ的正割是斜边与邻边的比值：secθ = h / b
* θ的余割是斜边与对边的比值：cscθ = h / a

**注意，你可能熟悉tg和ctg这两个写法，不过现在已经不再使用了，而是使用tan和cot代替。**

由于 cot、sec、csc很容易由sin、cos、tan推算出来(cotθ = cosθ / sinθ，secθ = 1 / cosθ，cscθ = 1 / sinθ )，所以现在基本不使用了。

三角函数与角度大小的关系是：正弦值与正切值和角度成正比 ，余弦值与余切值和角度成反比。

### 2、任意角的三角函数计算方式：

![三角函数](/images/post/201309182AGA64TKO06B6CAX.gif)

如上图，在平面直角坐标系中设 O-x 为任意角α的始边，在角α终边上任取一点P（x，y），令OP=r。

**sinα = y / r   cosα = x / r    tanα = y / x**

注意符号的**正负**：

* 第一象限内任何一个角的三角函数值都是“+”；
* 第二象限内只有正弦、余割是“+”，其余全部是“-”；
* 第三象限内只有正切、余切函数是“+”，其余函数是“-”；
* 第四象限内只有余弦、正割是“+”，其余全部是“-”。

### 3、弧度制与角度制的转换：

一个角度制数值所对应的弧度制数值等于单位圆中圆心角角度与该角度制数值相同时该圆心角所对应的弧长。用rad表示弧度制数值，用deg表示角度制数值，二者转换关系为：

![image](/images/post/20130918873fb3a9723036d13ac4ad87ebb17bcc.png)

常用的弧度转换公式：![image](/images/post/20130918641c3518e7acf7d0e38560f5f70ec96e.png)

### 4、常用的三角函数公式：

![image](/images/post/201309188044379582d6972f8bfc5e045dd65bac.png)

![image](/images/post/20130918b3bf9b6ebe195125b128c23e4371b6cf.png)

![image](/images/post/20130918751e9a35fc7c76c6a735573b2bef5d22.png)

![image](/images/post/2013091851ae1ae6b131eedcf53585e6fe0b72ed.png)

还有一些倍角公式、半角公式、和差化积、积化和差等等的公式，这里就不详述了，只要大家有一个印象就可以了，更多公式可以参考：[维基教科书](http://zh.wikibooks.org/wiki/%E4%B8%89%E8%A7%92%E5%87%BD%E6%95%B8)。

### 5、反三角函数：

[反三角函数](http://zh.wikipedia.org/zh-tw/%E5%8F%8D%E4%B8%89%E8%A7%92%E5%87%BD%E6%95%B0)是反正弦Arcsin x，反余弦Arccos x，反正切Arctan x，反余切Arccot x 这些函数的统称，各自表示其正弦、余弦、正切、余切为x的角。

![image](/images/post/20130918QQ20130918165035.jpg)

## **cos(x)**

cos() 方法可返回一个数字的余弦值。

参数x是必需的，是一个以弧度表示的角。（将角度乘以 0.017453293 （2PI/360）即可转换为弧度，下同）。

方法返回 x 的余弦值。返回的是 -1.0 到 1.0 之间的数。

## **sin(x)**

sin() 方法可返回一个数字的正弦。

参数x是必需的，是一个以弧度表示的角。

方法返回 x 的正弦值。返回值在 -1.0 到 1.0 之间。

## **tan(x)**

tan() 方法可返回一个表示某个角的正切的数字。

参数x是必需的，是一个以弧度表示的角。

方法返回 x 的正切值。

## **acos(x)**

acos() 方法可返回一个数的反余弦。

参数x是必需的，必须是 -1.0 ~ 1.0 之间的数。

方法返回 x 的反余弦值。返回的值是 0 到 PI 之间的弧度值。

**注意：如果参数 x 超过了 -1.0 ~ 1.0 的范围，那么浏览器将返回 NaN。如果参数 x 取值 -1，那么将返回 PI。**

## **asin(x)**

asin() 方法可返回一个数的反正弦值。

参数x是必需的，必须是 -1.0 ~ 1.0 之间的数。

方法返回 x 的反正弦值。返回的值是 -PI/2 到 PI/2 之间的弧度值。

注意：如果参数 x 超过了 -1.0 ~ 1.0 的范围，那么浏览器将返回 NaN。如果参数 x 取值 -1，那么将返回 PI。

## **atan(x)**

atan() 方法可返回数字的反正切值。

参数x是必需的，必须是一个数值。

方法返回 x 的反正切值。返回的值是 -PI/2 到 PI/2 之间的弧度值。

## **atan2(y,x)**

atan2() 方法可返回从 x 轴到点 (x,y) 之间的角度。

注意参数的坐标顺序，Y 坐标在 X 坐标之前传递。y是指定点的 Y 坐标，x是指定点的 X 坐标。

方法返回 -PI 到 PI 之间的值，是从 X 轴正向逆时针旋转到点 (x,y) 时经过的角度。



