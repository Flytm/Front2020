# 基础

## Javascript三大组成部分
- js的核心(**ECMAScript**)定义了JavaScript的基本语法和数据类型
- 文档对象模型(**DOM**,Document Object Model) 让JS可以与网页进行对话，例如修改html的节点
- 浏览器对象模型(**BOM**,Browser Object Model) 让JS可以与浏览器进行交互，例如改变浏览窗口的大小

## JavaScript的用法
JavaScript代码在HTML中是必须位于`<script>`和`</script>`标签之间的，其使用方法和CSS在HTML中的运用类似，主要分以下三种情况，
- 行内引用
- 内嵌引用
- 外部引用
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <!-- //内嵌引用alert函数 -->
    <script>
        alert("嵌入js代码，页面加载就会执行");
    </script>
    <!-- //外部引用 -->
    <script src="pop.js"> 
        // 注意！此script标签内不能再写js代码，不会被执行
    </script>
</head>
<body>
    <!-- //行内引用alert函数 -->
    <button  onclick="alert('行内js代码,button')">单击试试</button>
</body>
</html>
```
`pop.js`文件代码如下：
```js
"alert('外部js');"
```
> alert是弹窗函数，可以让浏览器弹出一个警告窗口
JavaScript中代码行的结尾要加英文状态下的分号" ; "


## 变量

内存：在程序运行过程中，所用到的数据，在计算机中`bit`是信息的最小单位
- 8 bit = 1 byte
- 1024 byte = 1 KB
- 1024 KB = 1 MB
- 1024 MB = 1 GB
- 1024 GB = 1 TB

变量就是内存中的一段储存空间，变量名表示储存空间的别名，可以自定义;变量值就是保存在内存空间的数据

### 变量的声明

使用`var`关键字声明变量
```js
    var x;             //声明变量x
    x = 3;             // 给x赋值
    var y = 5;         //声明变量y，并直接赋值
    var a, b, c;       //声明多个变量
    var a = 1, b = 2;

```
如果不使用var声明，变量会成为[全局变量]() 
声明变量不赋值的话默认值是`undefined`

var声明的变量会成为包含它的函数的[局部变量]()

js的变量声明，无论发生在何处，都在执行任何代码之前进行处理。例如下方代码
```js
    value = 2
    var value;

    // 可以隐式地将以上代码理解为：

    var value;
    value = 2;
```
这样的变量在声明之前使用的情况称为 **变量提升** ，需要注意的是变量的声明提升了，但是给变量赋的值是不会随之提升，比如下方的例子
```js
    console.log(bar); // 输出为undefined而不是10
    var bar = 10;
    console.log(bar); // 输出10

    // 可以隐式地将以上代码理解为：

    var bar;
    console.log(bar); // undefined
    bar = 10;
    console.log(bar); // 10

```
`bar`会发生变量提升，但给它赋的值不会提升，所以第一次输出`bar`的时候是`undefined`。所以建议在使用变量之前声明函数，再看一个例子
```js
    var x = 0;

    function f(){
    var x = y = 1;  
    }
    f();  //执行函数f

    console.log(x, y); //输出为 0, 1

    // 可以隐式地将以上代码理解为：

    var x = 0;

    function f(){
    var x;       //函数内部的x声明是局部变量
    x = y = 1; // y 没有用var声明，所以y是全局变量
    }
    f();  //执行函数f

    console.log(x, y); //输出为 0, 1
    // x 是全局变量
    
    
```
首先`x`为0是因为我们打印的是全局变量`x`，而不是函数内部的；而`y`没有经过`var`声明，所以也是全局变量；如果没有给`y`赋值的话， `console.log(x, y);` 就会抛出`ReferenceError`错误，因为`y`没有经过声明也没有定义的。
在*ECMAScript6*(js标准)中引入了`let`和`const`关键字也可以声明变量

`let`和`var`作用差不多，第一个区别是`let`声明的范围是块作用域，`var`声明的范围是函数作用域
块作用域是函数作用域的子集，所以适用`var`的作用域限制也适用`let`
```js
if (true){
    var name = 'John';
    console.log(name); // John
}
console.log(name);   //John

if (true){
    let age = '25';
    console.log(age); // 25
}
console.log(age);   // ReferenceErroe:age 没有定义
```

`age`变量的作用域仅限于`if`块内，所以不能再`if`块外使用 同理在`for`循环中let``声明的变量也不能在for循环块外引用
```js
for(var i = 0; i < 5; i++){
    //xxxxx
}
console.log(i)  //5

for(let i = 0; i < 5; i++){
    //xxxxx
}
console.log(i)  //ReferenceError: i 没有定义
```
`let`声明迭代变量时，JS会在后台给每个迭代循环声明一个新的迭代变量
第二个区别是`let`也不允许同一个块内出现重复声明，但是不影响嵌套使用
```js
var name;
var name; // 没有报错，可以这样使用

let age;
let age; //SyntaxError: age已经声明过了

var age;
let age; //SyntaxError: age已经声明过了

//嵌套使用let声明
let age = 30;
console.log(age); // 30
if (true){
    let age = '25';
    console.log(age); // 25
}
```
第三个区别是`let`声明的变量不会在作用域中被提升
```js
//age会被提升
console.log(age); // undefined
var age = 30;


console.log(name); // ReferenceError:name没有定义
let name = 'John';

```
第四个区别是使用`let`声明的变量不会成为window对象的属性，而var声明的则会
```js
var age = 30;
console.log(window.age); //30


let name = 'John';
console.log(window.name); // undefined

```
###
`const`的行为基本和`let`相同，主要区别在于`const`声明变量时必须初始化，且不能修改`const`声明的变量，所以不能用来声明循环中的迭代变量
```js
const age = 35;
age = 36; //typeError 给常量赋值
```
`const`的限制只适用于它指向的变量的引用，比如`const`指向的是一个对象，那么修改对象的属性并不会违反`const`的限制
```js
const person = {};
person.age = 36; //没问题
```

### 变量名命名规范


1.可以由字母、数字、下划线以及$组成 
2.不能使用JS的关键字和保留关键字命名;比如`for`就不能当作变量名使用 
3.不能以数字或者下划线`_`开头 
4.大小写敏感：`age`和`Age`代表着不同的变量 
5.见名知意，命名时应该用有意义的单词而不是abcd没有意义的单词 
6.驼峰命名法：首单词小写，之后每个单词首字母大写，比如`var setName;`;只有一个单词全小写 

**常见的关键字**

break | case | catch | class | const
:-:|:-:|:-:|:-:|:-:
continue | debugger | default | delete | do
else |export |extends |finally |for |function
if |import | in |instanceof |new |return
super |switch |this |throw |try
typeof |var |void |while |with
yield |

## 注释

JavacScript中单行注释以`//`开头
多行注释以 `/*` 开始，以 `*/` 结尾。
```js
    // 单行注释
    /* 
    多行注释
    多行注释
    */
```
>在客户端里面一般注释的快捷键都是`Ctrl`+`/`
