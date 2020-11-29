# 函数进阶

## 箭头函数

```js
//多个参数需要括号
let sum = (a, b) => {
  return a + b;
};
console.log(sum(3, 5)); // 8

//没有参数也要括号
let random = () => {
  return Math.random();
};
console.log(random);

//如果只有一个参数，可以省略括号
let double = (x) => {
  return x * 2;
};
console.log(double());
```

箭头函数不能使用`super`、`arguments`，也不能作构造函数。此外，箭头函数也没有`prototype`属性

## 参数

JS 的函数的参数再传入的时候是以一个数组的形式传入的，所以 JS 函数不会关心参数的个数和数据类型。所以 JS 函数没有像 JAVA 那样的重载(函数名相同，但参数数量和类型不同，根据输入的不同输出不同的结果)，如果 JS 定义了两个相同的函数，那么后定义的会覆盖前面的函数。
使用`function`定义非箭头函数时，可以在函数内通过`arguments`访问参数，箭头函数的参数不能使用`arguments`关键字访问

```js
function myPrint() {
  console.log(arguments[0] + "," + arguments[1]);
}
//上面的函数等价于
function myPrint(a, b) {
  console.log(a + "," + b);
}
```

## 默认参数

```js
function myPrint(name = 'nb' ){
    console.log(name);
}

let myName = (name = '张三'，value = 3) => '${name}'+ '${value}';
console.log(myName) // 张三3
```

默认参数是按顺序初始化的，先初始化的不能引用后初始化的

```js
let myName = (name = '张三'，value = name) => '${name}'+ '${value}';
console.log(myName) // 张三张三
```

## 函数提升

类似**变量提升**，函数也可以先使用再声明，因为 JS 引擎在代码执行前会读取函数声明，但不推荐这样使用。

```js
console.log(sum(10, 5)); // 15
function sum(num1, num2) {
  return num1 + num2;
}
```

函数名在 JS 中就是变量

```js
console.log(sum(10, 5)); //报错
let sum = function (num1, num2) {
  return num1 + num2;
};
```

函数定义在变量的初始化语句中，而不是函数声明中，所以代码如果没有执行到第二行，JS 是不知道有函数定义的，并不是`let`的原因，换成`var`也是同样的问题。

## 函数内部

**arguments**
`arguments`是一个类似数组的对象，它只有数组的`length`属性和索引，主要包含调用函数时传入的所有参数。

```js
//阶乘函数
function factorial(num) {
  if (num <= 1) {
    return 1;
  } else {
    return num * arguments.callee(num - 1);
  }
}
```

`arguments.callee`指向参数所属的当前执行的函数。在上面的代码中就是指向`factorial`

**this**

在函数中，`this`引用的是把函数当成方法调用的对象

```js
window.color = "red";
let o = {
  color: "blue",
};
function sayColor() {
  console.log(this.color);
}
sayColor(); //red

o.saycolor = sayColor;
o.saycolor(); // blue
```

第一次`this`指向的是全局对象`window`，第二次指向的是`o`

在箭头函数中`tihs`引用的是定义函数的上下文

```js
window.color = "red";
let o = {
  color: "blue",
};
let sayColor = () => console.log(this.color);

sayColor(); //red

o.saycolor = sayColor;
o.saycolor(); // red
```

因为箭头还是是在全局上下文中定义的，所以两次引用的都是`window`对象

**prototype**
