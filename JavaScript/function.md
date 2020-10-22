# 函数

函数(function)，也可以称之为方法(method),是一段 **预定义好** ，并可以被 **反复使用** 的代码块，其中包含多条可执行语句

**预定义好**：事先声明好，但不执行

**反复使用**：允许被多个元素或者函数使用

**代码块**：包含多条可执行的代码

## 语法

```js
function 函数名(){
    可执行语句;
}
```
## 函数的调用

执行函数中的内容

```js
function hello(){
    console.log("hello");
}

hello();
```

## 参数与返回值

**带参数的函数**
```js
function 函数名(参数列表){
    //代码块
}
```
参数列表：由一个或多个变量名称组成
声明函数时定义的参数，称为 **形参**

例子：
```js
function printInfo(name,password){
    console.log('用户名:' + name + '密码:' + password );

}

prinInfo('admin','123456');
```
在调用函数时所传递的参数值称为**实参**

**带返回值的函数**
```js
function 函数名(参数列表){
    //代码块
    return 值;
}
```
例子：
```js
function add(num1,num2){
    return num1 + num2;

}

var result = add(1,2);
console.log(result);
```
## 变量的作用域

作用域是变量或函数的可访问范围，其控制着变量或函数的可见性和**生命周期**

**函数作用域** 只在当前函数内可访问

**全局作用域**  任何位置都可以访问

## 局部变量

函数作用域中的变量称为局部变量，只在当前函数内可以访问到
```js
function add(){
    var sum = 1 + 2;   //局部变量
    console.log(sum); // 输出3
}
console.log(sum);  //报错，sum只在函数内可以访问
```
## 全局变量 :id = global_variable

```js
var sum = 0; 、// 全局变量
function add(){
    sum = 1 + 2;
    console.log(sum); //输出3
}
console.log(sum); //正确 输出3
```

```js
// 全局变量
function add(){
    sum = 1 + 2; // 未用var声明的变量，默认为全局变量
}
add(); //必须调用一次
console.log(sum); //正确 输出3
```

## 按值传递

传递参数时，实际上是将 实参 复制一份副本传递给函数。在函数内对变量进行修改，实际上不会影响到外部的实参变量

```js

var n = 100; //全局变量
function fun(n){ //参数变量也是局部变量
    n +=3;
    console.log(n) 
}
fun(n) // 按值传递，方法内输出103
console.log(n) //输出全局变量的值100
```
！> 如果`fun`函数没有参数的，最后输出的就不是100，是103，因为并没有传递值进去，而是直接操作全局变量


