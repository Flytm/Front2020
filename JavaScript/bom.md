# BOM

BOM是专门操作浏览器窗口的API

## 浏览器对象模型

- window 代表整个窗口
- history 封装当前窗口打开后，成功访问过的历史url记录
- navigator 封装浏览器配置信息
- document 封装当前正在加载的网页内容
- location 封装了当前窗口正在打开的url地址
- screen 封装了屏幕的信息
- event 定义了网页的事件机制

## 定时器

让程序按指定时间间隔自动执行任务，网页动态效果，计时功能

**周期性定时器**

```js
setInterval(exp,time):周期性触发代码exp
exp： 执行语句
time： 事件间隔

var timer = setInterval(function(){
    console.log("Hello");
},1000);

clearInterval(timer) // 停止定时器
```
**一次性定时器**

```js
setTimeout(exp,time):周期性触发代码exp
exp： 执行语句
time： 事件间隔

var timer = setTimeout(function(){
    console.log("Hello");
},1000);

```