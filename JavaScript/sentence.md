# 流程控制

## if-else

用法：

```js
if (条件) {
  如果条件是真的话就执行括号里面的代码
} else {
  否则执行else括号里面的代码
}
```

例子：

```js
if (age >= 18) {
    var user = '成年人';
} else {
    var user = '未成年人';
}
```
`if`也可以单独使用
```js
var user = '未成年人';
if (age >= 18) {
    user = '成年人';
} 
```

**else if**

```js
var score = 85;
if (score > 90) {
    result = '优秀';
}else if (score > 80){
    result = '良好';
}else if (score > 70){
    result = '中等';
}else if (score > 60){
    result = '及格';
}else {
    result = '不及格';
}
```
上面的`else if`只要有一个条件为真，后面的`else if`和`else`都不再判断

注意：`if`语句中的条件必须是`boolean`类型的值/表达式/变量，如果不是，JS会自行转化以下情况`if(0/0.0/''/""/null/undefined/NaN)`，都会被认为是`false`

## switch-case
switch 语句用于基于不同的条件来执行不同的动作
```js
switch(条件)
{
    case 情况1:
        执行代码块 1
        break; //停止执行下面的代码
    case 情况2:
        执行代码块 2
        break;
    default: //默认情况
        与 case 1 和 case 2 不同时执行的代码
}
```
例子：
```js
var d = 5; 
switch (d) 
{ 
  case 0:x="今天是星期日"; 
  break; 
  case 1:x="今天是星期一"; 
  break; 
  case 2:x="今天是星期二"; 
  break; 
  case 3:x="今天是星期三"; 
  break; 
  case 4:x="今天是星期四"; 
  break; 
  case 5:x="今天是星期五"; 
  break; 
  case 6:x="今天是星期六"; 
  break; 
}
// 今天是星期五
```

## for循环

用法
```js
for (表达式1; 表达式2; 表达式3)
{
    循环体
}
```

例子：

```js
var x = 0;
for (var i=0; i<5; i++)
{
    x=x + i;
}
// 最后x = 0+1+2+3+4 =10
```

上述for循环执行过程：

先声明了变量`i = 0`；

然后执行表达式2`i < 5`，i为零小于5，所以表达式2为真

执行大括号内的代码`x = 0 + 0;`

然后执行`i++` `i`自加后等于 1 

执行表达式2，1还是小于5，继续执行循环体`x = 0 + 1`

如此往复循环5次，此时的`i`已经等于5了，5不小于5，表达式2为假退出循环

中间的循环体`x = x + 1`执行了5次，此时`x = 10`



## while循环

`while`循环在条件为真时执行循环体
```js
while(条件){
    循环体
}
```
例子：
```js
var x = 0, i = 0;
while (i<5)
{
    x=x + i;
    i++;
}
// 最后x = 10
```
过程和上面的`for`循环差不多当`i`小于5成立时就执行下面的代码

## do while循环

用法：
```js
do{
    循环体;
}
while(条件);
```
和`while`的区别是，先执行一遍循环体再判断条件

```js
var x = 0, i = 0;
do{
    x=x + i;
    i++;
}while (i<5)
// 最后x = 10
```

## break

作用在循环中可以终止整个循环

```js
var i = 0;
while(i < 10){
    console.log(i);
    if(i == 2){
        break;
    }
    i++;
}
//输出结果为 0 1 2 当i=2时，退出循环
```
## continue

作用是终止本次循环，注意`break`是整个循环