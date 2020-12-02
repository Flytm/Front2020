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

## 常用标签

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
- 区域
  `<div></div>`

## 超链接

`<a href="url(网站地址)">链接文本</a>`
链接到其他网站 `http：xxxx.com`,或者本网页内的目标位置

```html
<a href="#ok"> 点击进行锚点跳转到锚点 </a>
<h3 id="ok">锚点目标</h3>
```

不加`href`属性是虚超链接 点击后不会跳转，但是有点击效果
`a`标签默认不换行，需要用段落`p`标签或者`br`标签换行

## 图片

```html
<img src="url" alt="some_text" /> <img src=”../Image/logo.gif" alt="text"
width="300" height="200">
```

`src`属性：图片来源或者完整路径
**绝对路径**：以根目录为标准
**相对路径**：以该文档所在的位置为基准
`..` 表示上级文件夹
**JPG**：有损压缩
**Gif**：简单动画
**Png**：无损压缩
`alt`属性 图片不显示的时候的替换文本，告诉读者失去的信息
`height`（高度） 与 `width`（宽度）属性用于设置图像的高度与宽度

## 列表

**无序列表**`<ul></ul>`

```html
<ul>
  <li>列表项1</li>
  <li>列表项2</li>
</ul>
```

在浏览器中显示效果和下方的相似

- 列表项 1
- 列表项 2

**有序列表**`<ol></ol>`

```html
<ol>
  <li>列表项1</li>
  <li>列表项2</li>
</ol>
```

在浏览器中显示效果和下方的相似 1.列表项 1 2.列表项 2

**自定义列表**
自定义列表`<dl></dl>`，列表项`<dt></dt>`，描述`<dd></dd>`

```html
<dl>
  <dt>列表项1</dt>
  <dd>描述列表项1</dd>
  <dt>列表项2</dt>
  <dd>描述列表项2</dd>
</dl>
```

## 表格

表格由 `<table>` 标签来定义。每个表格的行（由 `<tr>` 标签定义），每行有若干单元格（由 `<td> `标签定义），数据单元格可以包含文本、图片、列表、段落、表单、水平线、表格等等。

```html
<table border="1">
  <tr>
    <th>Header 1</th>
    <th>Header 2</th>
  </tr>
  <tr>
    <td>row 1, cell 1</td>
    <td>row 1, cell 2</td>
  </tr>
  <tr>
    <td>row 2, cell 1</td>
    <td>row 2, cell 2</td>
  </tr>
</table>
```

| Header 1   | Header 2   |
| ---------- | ---------- |
| row1,cell2 | row1,cell2 |
| row2,cell2 | row2,cell2 |

## 表单

表单是允许用户在表单中输入内容,比如：账户、密码等；`<form></form>`标签定义表单元素

```html
<form>
  用户名: <input type="text" name="username" /><br />
  密码: <input type="password" name="password" />
</form>

//下来选项框
<select>
  <option selected=" selected">xx</option>
</select>
```

`<input>`输入标签
`type`属性定义表单的类型
`type="radio"` 单选
`type="checkbox"` 多选
`type="submit"` 提交
`type="reset"` 重置
`type="textarea"`文本框
