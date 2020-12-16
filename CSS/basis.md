# CSS 简介

CSS(Cascading Style Sheets)层叠样式表，主要作用就是美化网页

CSS 语法规则

```css
/*h1标题设置紫颜色*/
h1 {
    color: red;//这是一条声明
}
h1:选择器
color:属性
red:值
```

# CSS 添加方法

- 行内添加

```css
<p style = "color:red;"></p>
/*通过style属性设置HTML标签*/
```

- 嵌入式

```css
/*在header或body标签里使用style标签设置样式*/

<style type = "text/css">
	p { color:red;}
</style>
```

- 引入式

```css
/*在外部创建style.css文件*/
p {
  color: red;
}
```

```html
//在HTML的header标签内引用 <link rel="stylesheet" href="style.css" />
```

**优先级**

**就近原则** ：行内样式>嵌入>引用

# CSS 选择器

CSS 选择器是 CSS 语法规则的第一部分，其主要作用就是告诉浏览器哪个 HTML 元素该使用什么样式。

- 元素类型

  ```css
  /*选择HTML的所有h1元素*/
  h1 {
  }
  ```

- id 选择器

  ```css
  /*选择id为one的HTML元素*/
  #one {
  }
  ```

- class 选择器

  ```css
  /*选择类名为box的所有HTML元素*/
  .box {
  }
  ```

- 标签属性选择器

  ```css
  /*根据一个有特定值的标签属性是否存在来选择
  选择超链接为"https://baidu.com"的a标签*/
  a[href="https://baidu.com"]
  {
  }
  ```

- 伪类选择器

  ```css
  /*选择一个元素的特定状态，:hover表示鼠标放在a标签上的状态
  a:hover { }
  ```

- 伪元素选择器

  ```css
  /*选择一个元素的某个部分，::first-line表示第一行*/
  p::first-line {
  }
  ```

- 后代选择器

  ```css
  /*选择p标签下的span标签*/
  p span {
  }
  ```

- 奇偶选择器

  ```css
  /*选择奇数行*/
  tr:nth-child(odd)

  偶数:even
  奇数:odd
  ```

常用的声明方法

```css
全局声明
*{text-align:center;}
全部居中

集体声明
h1,p{text-align:center;}
h1和p标签都会居中
```

# CSS 样式

## 文本

| 属性            | 名称     | 属性值                                          |
| --------------- | -------- | ----------------------------------------------- |
| color           | 文本颜色 | red、 十六进制#ff0000、 rgb（255，0,0）         |
| letter-spacing  | 字符间距 | 2px                                             |
| line-height     | 行高     | 14px、 1.5em 1.5 倍行高、 120%                  |
| text-align      | 对齐     | center、left、right、 justify 两端对齐          |
| text-decoration | 装饰线   | none 、overline 上方、 underline、 line-through |
| text-indent     | 首行缩进 | 2em                                             |

行高和区域的高度一样的时候会垂直居中

装饰线 `none` 经常用来去掉超链接的下划线

## 字体

| 属性        | 名称         | 属性值                    |
| :---------- | ------------ | ------------------------- |
| font        | 设置字体属性 | bold 18px ‘幼圆’          |
| font-family | 字体系列     | “Microsoft YaHei"微软雅黑 |
| font-size   | 字号         | 14px、 120%               |
| font-style  | 斜体         | italic                    |
| font-weight | 粗体         | bold                      |

font 简化使用方法

font：italic bold 16px/1.5em ‘宋体’

字体：斜体 粗体 字号/行高 字体。

## 背景

| 属性                | 名称     | 属性值                                                                      |
| ------------------- | -------- | --------------------------------------------------------------------------- |
| background-color    | 背景颜色 | red、 #ff0000、 rgb（255，0,0）                                             |
| background-image    | 背景图片 | url（"loggo.jpg"）相对路径                                                  |
| background-repeat   | 填充方式 | repeat 全部填充 ；repeat-x or -y 横向或者纵向； no-repeat 只显示一次 不平铺 |
| background-position | 位置     | right top                                                                   |

## 超链接

| 属性       | 名称             |
| ---------- | ---------------- |
| a：link    | 未被访问的链接   |
| a：visited | 已访问的链接     |
| a：hover   | 鼠标悬停上方     |
| a：active  | 链接被点击的时刻 |

在设置一个超链接的多个样式的时候`hover`必须位于`link`和`visited`之后

`active`必须位于`hover`之后

## 列表

| 属性                | 名称                      |
| :------------------ | ------------------------- |
| list-style          | 所有属性设置于一个声明中  |
| list-style-image    | 列表项标志设置图像        |
| list-style-position | 标志的位置 inside outside |
| list-style-type     | 标志的类型                |

## 表格

| 属性            | 名称                                       | 属性值                         |
| --------------- | ------------------------------------------ | ------------------------------ |
| width height    | 宽高                                       | 18px                           |
| border          | 边框                                       | border 1px solid #eee 实线灰色 |
| border-collapse | 表格的边框是否被折叠成一个单一的边框或隔开 | 默认表格样式 collapse 不折叠   |

# CSS 布局与定位

## 盒子模型

页面中所有元素都可以看成一个盒子

盒子模型由高度 height、宽度 width、内容 content、border 边框、padding 内边距、margin 外边距组成

![CSS box-model](https://flytm-figure.oss-cn-beijing.aliyuncs.com/img/box-model.gif)

- **Margin(外边距)** - 清除边框外的区域，外边距是透明的。

- **Border(边框)** - 围绕在内边距和内容外的边框。

- **Padding(内边距)** - 清除内容周围的区域，内边距是透明的。

- **Content(内容)** - 盒子的内容，显示文本和图像。

  **box-sizing**

  `box-sizing`默认属性是`content-box `，指定盒子模型为 W3C 标准，也就是内边距与边框会被算入宽高中

  `border-box`指定盒模型为 IE 模型，设置`border`、`padding`不会影响元素的`width`与`height`的尺寸

## 边框

`border-width`: 单位`px`、 粗`thin`、中`medium`、细`thick`

`border-style` ：`solid`实线、`dotted`点组成、`double`双实线、 `dashed` 横线

简写形式

```css
border:5px solid red; 宽度、样式、颜色
```

## 外边距

margin 在垂直方向上会合并， 选用父元素与子元素中外边距最大的那个，左右不合并

水平居中

```css
margin: 0 auto;
```

图片边框之间浏览器默认有空隙

```css
font-size：0;可以除掉空隙
```

对浏览器默认的设置清零

```css
* {
  margin: 0;
  padding: 0;
}
```

取值为 0 的时候可以省略单位

## 内边距

`padding`填充元素与边框之间的空间

简写属性

```css
/*有四个属性值的时候依次表示上右下左 顺时针方向 */
padding: 25px 50px 75px 100px;

/*有三个属性值的时候依次表示上、左右、下 */
padding: 25px 50px 75px;

/*有两个属性值的时候依次表示上下、左右 */
padding: 25px 50px;

/*有一个属性值的时候依次表示所有方向 */
padding: 25px;
```

`margin`、`border`也是如此使用的

## 显示

`display`属性设置一个元素应如何显示，

- `display:block` -- 显示为块级元素
- `display:inline `-- 显示为内联元素
- `display:inline-block` -- 显示为内联块元素
- `display:none`--隐藏元素

**块级元素**的特性是独占一行，其后面的元素必须另起一行显示，并且可以控制其宽高，内外边距，比如`div`、`h1~h6`等标签

**内联元素**的特性是和相邻元素在同一行，宽高内外边距不可以改变，比如`span`、`a`等标签

**内联块元素**表现为在同一行，又可以修改其宽高与内外边距

`display`隐藏的元素不会占用任何空间，该元素会从页面布局中消失

`visibility:hidden`也可以隐藏元素，该隐藏元素还是占用布局空间

当文本内容溢出盒子模型的时候可以设置`overflow`属性

`hidden` 超出部分不显示

`scroll` 滚动条

`auto` 如果有超出部分就限速滚动条

## 定位

`position` 属性指定了元素的定位类型

- `static` 没有定位, 正常显示

- `fixed` 固定定位，相对于浏览器窗口不会随着浏览器窗口的滚动条移动，总在视线里，类似广告

- `realtive` 相对定位，相对于父元素，原位置保留存在

- `absolute` 绝对定位，相对于`static`定位以外绝对定位或相对定位的第一个父元素，如果没有则其将相对 body 进行定位，原位置会丢失
- `sticky`粘性定位，在目标区域内是相对定位，当页面滚动超出目标区域，它会固定在目标位置

注:父元素一般是相对定位，子元素是绝对定位

元素通过设置`z-index`属性来决定元素的堆叠顺序，值越大的显示在最前面

## 浮动

`float`会使元素水平移动，其周围的元素也会重新排列

- `float:left`左浮动
- `float:right`右浮动
- `float:none`不浮动

清楚左右浮动

```css
clear: both;
```

# CSS3

CSS 最新的标准

## 圆角边框

border-top-left-radius 左上角的弧度

border-top-right-radius 右上角的弧度

border-bottom-left-radius 左下角的弧度

border-bottom-right-radius 右下角的弧度

简写方式

```css
border-radius: 15px 50px 30px 5px;
```

## 阴影

- box-shadow 边框阴影
- text-shadow 文本阴影

```css
div {
    box-shadow: 10px 10px 5px #ff0000;依次表示水平偏移距离 垂直偏移 模糊距离 颜色
}
h1 {
	text-shadow:2px 2px 8px blue;同上
}
```

文本换行

```css
word-wrap:break-word; 允许文本换行
word-break: break-all;
```

## 旋转

**2D 旋转**

```css
transform: rotate(30deg);顺时针旋转30度
transform: translate(50px,100px);向右移动50px 向下100px
transform: scale(1.2); 放大20%
transform: scale(2,3); 宽度放大
```

**3D 旋转**

```css
transform: rotateX(120deg); 围绕x轴旋转120度
transform: rotateY(120deg); Y轴
```

**透视**

```css
perspective: 100px;
```

相对于站在 100px 距离之外看物体的效果

## 过渡

过渡是将某个或多个属性在指定的时间内过渡到另一个值

简写方式

```css
transition: 属性名 持续时间 过渡方法
transition: all 1s linear
```

- linear 匀速变化
- ease 开始慢，中间快，结尾慢
- ease-in 开始慢结尾快
- ease-out 开始快结尾慢
- ease-in-out 开始慢结尾慢

## 动画

动画是使元素从一种样式逐渐变化为另一种样式的效果。

0% 是动画的开始，100% 是动画的完成，也可以用关键词 "from" 和 "to"

`@keyframes`定义动画 关键帧

`animation`简写动画属性

```css
@keyframes mycolor{
	0% {background-color:red;}
	30%{background-color:blue;}

}

animation:关键帧的名称 指定动画时间 过度方法 播放次数;
div:hover{ animation：mycolor 2s linear infinite;}

animation-play-state: running paused 播放暂停
```
