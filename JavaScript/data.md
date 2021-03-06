# 数据类型

基本类型：字符串（String）、数字(Number)、布尔(Boolean)、对空（Null）、未定义（Undefined）、Symbol

引用数据类型：对象(Object)、数组(Array)、函数(Function)

## 字符串

字符串(String)表示一系列的文本字符数据由`Unicode`字符，数字，标点组成；可以存储一系列字符,可以使用单引号或双引号

```js
var name = "这是一个字符串";
var name = "这是一个字符串";
```

> 两者不能混合使用，比如 'xxxxx" 这样是错误的使用方法

你可以使用索引位置来访问字符串中的每个字符

```js
var name = "这是一个字符串";
var character = name[5];
```

!> 索引是从零开始的，5 表示第 6 个

**转义字符**

- `\'` 单引号
- `\"` 双引号
- `\\` 反斜杠
- `\n` 换行
- `\r` 回车
- `\t` 一个制表符
- `\f` 换页
- `\b` 退格
- `\0` 空字符

```js
var name = 'I'm iron man';
//会报错，这整句话应该是一个字符串，但是只有'I'会被识别成字符串，字符串的单引号和双引号都是一对一对出现的
var name = 'I\'m iron man';
// 应该使用转义字符,告诉计算机中间的单引号是文本
```

## 数字

JavaScript 只有一种数字类型(nameber)可以表示 32 整数以及 64 位的浮点数

```js
var x1 = 34.0; //使用小数点来写
var x2 = 34; //不使用小数点来写
var x3 = 123e-5; // 科学记数法 0.00123
```

- 整数：例如 100、-5
- 浮点数：有小数点或小数位，例如 10.00
- 双精度：比浮点数的精度更高，意味着它可以表示的小数更多
- 十进制：我们常用的 7、8、9、10、11 就是十进制
- 二进制：由 0 和 1 组成，计算机底层就是二进制，例如二进制的 11 表示 3
- 八进制：逢八进一，由 0-7 组成
- 十六进制：由 0-9 和 a-f 组成

```js
var x = 34;
var y = "哈哈";
var result = y + y; //链接字符串
var result2 = x + y; // 数字加上字符串 会转换成字符串  "34哈哈"
```

## 布尔

- `true`: 真
- `false`: 假
- 作用：用于表示条件的结果，如果做运算的话`true`可以表示 1，`false`表示 0

## 空

- `null`: 对象为空，将对象设为`null`,可以释放内存

## 未定义

`undefined`:

- 声明变量未赋值
- 访问对象不存在的属性

```js
null === undefined; // false
null == undefined; // true
//null 和 undefined 的值相等，但类型不等
```

null 是一个表示"无"的对象，转为数值时为 0；undefined 是一个表示"无"的原始值，转为数值时为 NaN

## Symbol

符号`Symbol`是原始值，其实例是唯一不可变的

```js
let aSymbol = Symbol("ok");
let bSymbol = Symbol("ok");

console.log(aSymbol == bSymbol); //false
```

## 数据类型转换

js 是弱类型语言，它是由数据来决定变量的数据类型的

```js
var x; //undefined
x = 34; //number
x = "34"; //string
```

**隐式转换**

自动转换，不需要人为参与

`typeof()`函数获取变量的数据类型

```js
var num = 10;
var s = typeof num; //获取num的数据类型

typeof 1; // 'number'
typeof "1"; // 'string'
typeof undefined; // 'undefined'
typeof true; // 'boolean'
typeof Symbol(); // 'symbol'
typeof b; // b 没有声明，但是还会显示 undefined
typeof []; // 'object'
typeof {}; // 'object'
typeof console.log; // 'function'
```

`NaN`(Not a Number)不是一个数字
`isNaN()`函数判断数据是否为非数字，返回结果为布尔类型
返回`true` 说明不是一个数字
返回`false` 说明是一个数字

!> 所有数据类型和字符串 String 做加法运算时，结果都为 String

**显式转换(强制转换)**

`toString()`函数强制将数据类型转换为字符串

```js
var num = 3;
var s = toString(num); // "3"
```

`parseInt()`函数获取指定数据的整数部分，从左到右，碰到第一个非整数字符就停止转换

```js
var num = "3a";
var s = parseInt(num); // 3
var s = parseInt("你好3"); // NaN
```

`parseFloat()`函数将指定数据转换成小数，用法类似`parseInt()`

```js
var num = parseFloat("3.6"); // 3.6
var num2 = parseFloat("3.6a"); // 3.6
var num3 = parseFloat("a3.6a"); // NaN
```

`Number()`函数将一个字符串解析为`number`类型,用法和上述一样，不过需要注意的是只有包含非数字字符就会返回`NaN`
