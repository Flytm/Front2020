# 响应式布局

## 布局方式

- 固定宽度布局
- 流式布局 ：百分比设置相对宽度
- 响应式布局：检测设备信息，设备宽度不同，布局不同
- 混合使用

## 响应式布局

**媒体查询 MediaQuery**

Viewport视口：显示网页的区域
视口规定: 
1.布局视口 = 设备视觉视口 `width=device-width` 
2.不可以用缩放的形式来完成响应式布局 `user-scalable = no` 

实现方式:
```html
<meta name="viewport" content="width=device-width, user-scalable =no,initial-scale=1.0">
```

根据不同宽度来设定不同的CSS样式

设备屏幕|尺寸px
-|-
超小屏extra small | <768
小屏small | >=768
中等 medium | >992
大屏 large | >=1200

例子：
```html
<style>
    body{
        background-color:black;
    }
    @media screen and (min-width:768px){
        body{
            background-color:red;
        }
    }
    @media screen and (min-width:992px){
        body{
            background-color:green;
        }
    }
</style>
```
背景颜色默认是黑色的，然后判断设备宽度是否大于768像素点，如果满足大于768像素点就设置为红色，否则就是黑色，如果是红色就再向下判断设备宽度是否大于992像素点，如果满足就设置为绿色，否则是红色

## Bootstrap
