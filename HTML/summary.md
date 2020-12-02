# HTML 入门总结

## HTML 是什么

HTML 的全称是超文本标记语言(Hyper Text Markup Language)，是一种标记语言，主要通过一系列标签来描述网页

HTML 的文档后缀为 html 或者 htm，其内容结构如下所示

```html
<!DOCTYPE html> //告诉浏览器这是那种HTML版本
<html>
  <head>
    <meta charset="UTF-8" />
    // 编码格式
    <title>页面标题</title>
    // 页面
  </head>
  <body>
    <h1>我的第一个标题</h1>
    //标题标签

    <p>我的第一个段落。</p>
    //段落标签
  </body>
</html>
```

新建一个记事本，复制上方代码，另存为`index.html`文件，用浏览器打开，如下图所示

![img](https://www.runoob.com/wp-content/uploads/2013/06/html-first.png)

这就是一个 HTML 文件的基本结构

- \<!DOCTYPE html> 声明为 HTML5 文档
- \<html> 元素是 HTML 页面的根元素
- \<head> 元素包含了文档的元数据
- \<title> 元素描述了文档的标题
- \<body> 元素包含了可见的页面内容

# HTML 标签

HTML 标签是有尖括号包围的关键词，如`<html>`
一般情况下都是成对出现的，比如`<p></p>`

# 常用标签

- 标题
  `<h1>标题</h1>`
  `<h2>标题</h2>`
  `<h3>标题</h3>`
  `<h4>标题</h4>`
  `<h5>标题</h5>`
  `<h6>标题</h6>`
- 段内换行
  `<br>` 单独出现直接换行
- 段内分组
  `<span></span>`组合行内元素，通过 css 样式来格式化
- 段落
  `<p></p>` 忽略连续空格，也不会显示空行，不会换行
- 预留格式
  `<pre></pre>`标签中的空格和换行符全部保留
- 水平线
  `<hr>` 单独出现 -注释
  `<!-- 注释内容-->`

## 链接

- 超链接
  `<a href="url(网站地址)">链接文本</a>`
  链接到其他网站 `http：xxxx.com`,或者本网页内的目标位置

```html
<a href="#two"> 点击进行锚点跳转到锚点 </a>
<h3 id="two">锚点目标</h3>
```

不加`href`属性是虚超链接 点击后不会跳转，但是有点击效果
默认不换行，`a`标签需要用段落`p`标签或者`br`标签换行
