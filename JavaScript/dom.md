# DOM

DOM 是 W3C 的标准，是中立于平台和语言的接口，它允许程序和脚本动态地访问和更新文档的内容、结构和样式，对网页进行增删改查的操作。

## DOM 查找

- 按`id`属性查找
  `var element = document.getElementById("id");`

- 按标签查找
  `var element = parent.getElementByTagName("tag");`
  查找指定`parent`节点下的所有标签 tag 的子代节点，返回动态集合

- 按`name`属性查找
  `var element = document.getElementByName("name");`

- 按`class`属性查找
  `var element = parent.getElementByClassName("class");`
  查找父元素下指定`class`属性的元素

- 通过`css`选择器查找 1.只查找一个元素
  `var element = parent.querySelector("selector");`
  `selector`支持一切 css 中的选择器，只返回第一个 2.查找多个
  `var element = parent.querySelectorAll("selector");`

## DOM 修改

**读取属性值**

- 先获得属性节点对象，再获得节点对象的值
- 直接获取属性值

```js
var attrNode = elem.attributes[属性名];
attrNode.value; //属性值
var value = elem.getAttribute("属性");
```

**修改属性值**

`elem.setAttrbute("属性名",value);`

**判断是否包含指定属性**

`elem.hasAttrbute("属性名");`

**移除指定属性**

`elem.removeAttrbute("属性名");`

## DOM 添加

**创建空元素**

`var element = document.createElement("元素名");`

**设置关键属性**

```js
a.innerHTML = "go to mooc";
a.herf = "http://tmooc.cn";

//<a herf = "http://tmooc.cn">go to mooc </a>
```

设置样式

```js
a.style.cssText = "width:100px; height:200px";
```

**将元素添加到 DOM 树**

- 可以将一个父元素最后追加一个子节点
  `parentNode.appendChild(childNode)`

- 可以将一个父元素中指定节点之前添加一个子节点
  `parentNode.insertBefore(newChild，existingChild)`
