# 对象

Javascript 虽然是一门面向对象的语音，但是它缺少传统的面向对象的基本结构，比如类和接口。
所以常用**引用类型**来称呼 JavaScript 中的“类”，它只是和类有点相似，有自己的属性和方法，但和类不是一个概念。
**对象**是引用类型的实例，通过`new`操作符创建，后跟一个**构造函数**

```js
let now = new Date(2019, 1, 1); // 2019.1.1
```

## Date

创建日期

```js
new Date();
new Date(value); //value是unix时间戳
new Date(dateString);// 时间格式的字符串
new Date(year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]]);

//格式化
new Date().format("yyyy-MM-dd hh:mm:ss");
```

常用方法
`getMonth()`获取月份
`setMouth()`设置月份
`getHours()`获取日期中的小时(0~23)
更多方法可以参考[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date)

## String

创建方法

```js
let str = new String("hello");
let str = "hello";
```

常用方法

```js
let str = " Hello world ";
str = str.trim(); // 消除前后的空格"Hello world"
str.indexOf("o"); // 返回第一次出现o的位置 没有就返回-1
str.includes("hello"); // 判断是否包含"hello" 是的话返回true，否则false
str.slice(3); // "lo World"
str.substring(3, 7); // "lo W" 3-7之间的子字符串 不包含索引位置7上的字符
str.substr(3, 7); // "lo Worl" 索引位置3之后的7个字符
str.concat("!"); // 拼接 "Hello Horld!"
str.toUpperCase(); // 转换为大写
str.toLowerCase(); // 转换为小写
str.split(" "); // 按空格将str划分为["Hello","World"]
```

## Boolean

```js
let myBoolean = new Boolean(false);
typeof myBoolean; // object 对象
typeof false; // boolean
```

## Number

```js
let num = new Number(10);
num.toString(2); //"12" 加2
num.toFixed(2); //"10.00"
num.parseFloat(); //转化为浮点数
num.parseInt(); //转化为整数
num.isInteger(); //判断传递的参数是否为整数
```

## RegEXp

`ECMAScript`通过`RegExP`类型支持正则表达式，正则表达式就是由一个或者多个字符来匹配某个句法规则的字符串搜索模式，比如在判断是否是邮箱格式的时候我们就可以用正则表达式去匹配。

RegExp 的语法:`/pattern正则表达式主体/flags修饰符(可选)`
`flags`主要用来控制匹配模式

- g：全局模式 查找全部匹配
- i：不区分大小写
- m：多行模式

```js
let pattern = /at/i; //查找所有的at
let pattern2 = /[bc]at/i; //查找所有的bat或者cat
let pattern3 = /.at/gi; //查找所有以at结尾的三个字的组合，忽略大小写

var patt = /e/;
patt.exec("The best things in life are free!"); //返回 e
//exec() 函数返回一个数组，其中存放匹配的结果。如果未找到匹配，则返回值为 null
```

## Math

```js
Math.PI; //圆周率
Math.E; //自然对数的基数e

常用方法;
Math.min();
Math.max();
Math.random(); //0-1之间随机数
Math.floor(); //向下取整 floor(2.9) = 2
Math.round(); //四舍五入 round(2.9) = 3
Math.ceil(); //向上取整 ceil(2.9) = 3
Math.sqrt(); // 开根号
Math.abs(); //绝对值
Math.cbrt(); //立方根
Math.cos(); //余弦
Math.pow(x, n); //x的n次幂
```
