# 数组

数组在任何编程语言中都是比较重要的类型，但 ES 的数组和其他语言的区别在于它的数组可以储存不同的类型数据
ES6 中`Array`构造函数新增了两个方法`from()`和`of()`

- `from()`将类似数组结构的转化为数组实例
  第一个参数是类数组对象，第二个参数是可选的映射函数，第三个可选参数是指定映射函数中的`this`值
- `of`将一组参数转换为数组实例

```js
console.log(Array.from("matt")); // ["m","a","t","t"]

let arr = Array.from([1, 2, 3], (x) => x * 10);
// arr[0] == 10;
// arr[1] == 20;
// arr[2] == 30;
console.log(Array.from(1, 2, 3)); //[1, 2, 3]
```

## 迭代

检索数组内容的方法三种

- `keys()` 返回数组索引的迭代器
- `values()`返回数组元素的迭代器
- `entries()` 返回索引/值的迭代器

```js
const a = ["a", "b", "c"];

const aKeys = Array.from(a.keys());
const aValues = Array.from(a.values());
const aEntries = Array.from(a.entries());

console.log(aKeys); //[0,1,2]
console.log(aValues); //["a","b","c"]
console.log(aEntries); //[[0,"a"],[1,"b"],[2,"c"]]

for (const [id, element] of a.entries()) {
  console.log(id);
  console.log(element);
}
// 0
//"a"
// 1
// "b"
// 2
// "c"
```

常用方法
toString()
var last = fruits.pop();
