mycar## 原型

每个对象拥有一个**原型对象**，对象以其原型为模板、从原型继承方法和属性。原型对象也可能拥有原型，并从中继承方法和属性，一层一层、以此类推。这种关系常被称为**原型链**这个属性是一个对象，它包含了实例共享的属性和方法

具体就是每个对象都会创建一个`prototype`属性指向原型，所有原型对象自动获得一个名为`constructor`的属性指向其构造函数

```js
function Person() {}

Person.prototype.name = "海森伯格";
Person.prototype.sayMyName = function () {
  console.log(this.name);
};
let person1 = new Person();
person1.sayMyName(); // "海森伯格"

let person2 = new Person();
person2.sayMyName(); // "海森伯格"

Person.prototype.constructor === Person; // true
```

每个构造函数都有一个原型对象，原型有`constructor`属性指回构造函数，而实例有一个内部指针指向原型

## new

1. 新生成了一个对象
2. 链接到原型
3. 绑定 this
4. 返回新对象

```js
function create() {
  // 创建一个空的对象
  let obj = new Object();
  // 获得构造函数
  let Con = [].shift.call(arguments);
  // 链接到原型
  obj.__proto__ = Con.prototype;
  // 绑定 this，执行构造函数
  let result = Con.apply(obj, arguments);
  // 确保 new 出来的是个对象
  return typeof result === "object" ? result : obj;
}
```

## 继承

继承主要通过原型链实现的，将对象的原型指向引用类型的实例从而达到继承的作用

也就是将子类的原型指向父类

```js
function Super() {}

Super.prototype.getNumber = function () {
  return 1;
};

function Sub() {}

//Sub继承Super
Sub.prototype = new Super();

let instance = new Sub();
console.log(instance.getNumber()); // 1
```

## 类

从上面也可以看出实现继承的代码过于复杂，所以 ES6 引进`class`类

```js
class Vehicle {
  constructor() {
    this.name = "vehicle";
  }
}
//继承类
class Bus extends Vehicle {
  constructor() {
    super(); //继承Vehicle的构造函数
  }
}
let mycar = new Bus();
console.log(mycar instanceof Vehicle); // true
console.log(mycar instanceof Bus); // true
```
