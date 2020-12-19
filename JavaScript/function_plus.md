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
`arguments`是一个类似数组的对象，它只有数组的`length`属性和索引，主要包含调用函数时传入的**所有参数**。

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

## 函数方法与属性

**prototype**

函数实例中共享的方法与属性都保存在函数的`prototype`属性上，比如`toString()`,`valueOf()`等方法

**call()**

`call()`作用是改变`this`指向

```js
window.color = "red";
let o = {
  color: "blue",
};
let sayColor = () => console.log(this.color);

sayColor(); //red

sayColor.call(this); //red
sayColor.call(window); //red
sayColor.call(o); //blue
```

**apply()**
`apply()`作用和`call()`一样，就是接受参数的方式一样，`apply()`第一个是函数内的`this`值，第二个是参数数组。
而`call()`的第二个参数是一系列参数。

```js
function sum(num1, num2) {
  return num1 + num2;
}

function callSum1(num1, num2) {
  return sum.apply(this, arguments); //arguments代表函数的参数数组
}

function callSum1(num1, num2) {
  return sum.apply(this, [num1, num2]); //传入数组
}

console.log(callSum1(10, 10)); // 20
console.log(callSum2(10, 10)); // 20
```

`apply()`与`call()`的好处是可以将任意对象设置为任意函数的作用域，这样对象可以不用关心方法

**bind()**
`bind()`方法会创建一个新的函数实例，其`this`值会被绑定到传给`bind()`的对象

```js
window.color = "red";
let o = {
  color: "blue",
};
let sayColor = () => console.log(this.color);

sayColor(); //red

let objectSayColor = sayColor.bind(o);
objectSayColor(); //blue
```

## 递归

递归函数就是一个函数通过名称调用自己

```js
function factorial(num) {
  if (num <= 1) {
    return 1;
  } else {
    return factorial(num - 1) * num;
  }
}
```

## 闭包

闭包指的是那些引用另一个函数作用域中变量的函数，通常的在嵌套函数中实现的

```js
function A() {
  let a = 1;
  function B() {
    console.log(a);
  }
  return B;
}
```
