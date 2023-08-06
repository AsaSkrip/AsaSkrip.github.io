---
date: 2018-02-03 12:26:40
layout: post
title: H5和C3
subtitle: H5以及C3的面试题
description: H5以及C3都是我们学习前端最基础的东西，所以想要入门前端 ，H5和C3是一定要学会的
image: https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559821648/theme8_knvabs.jpg
optimized_image: https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559821648/theme8_knvabs.jpg
category: H5和C3
tags:
  - H5
  - C3
author: 李梓涵
---

<a name="JnlKs"></a>

## 1、盒子塌陷的原因？解决方式

```
原因: 1. 浮动导致的塌陷,浮动会脱落标准流
		 2. 嵌套的两个盒子,子盒子设置margin-top会导致父盒子一下下移
解决方法:第一种情况 1 清除浮动;  2 给父盒子加高度;  3 给父元素添加overflow:hidden
				第一种情况 1 给父元素加上边框; 2 给父元素添加overflow:hidden
```

<a name="kOjxl"></a>

## 2、不定宽高的div水平垂直居中

```
答: 1、父元素添加 position: relative
		div{
			position:absolute;
			top: 50%;
             left: 50%;
             transform: translate(-50%, -50%);
		}
	2、div {
	   display: flex;
       justify-content:center; //子元素水平居中
       align-items:center; //子元素垂直居中
	 }
      
    3、#box {
        width: 100px;
        height: 100px;
        position: relative;
    }

    #content {
        width: 50px;
        height: 50px;
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        margin: auto;
    }
```

<a name="v8n41"></a>

## 3、css写一个三角形

```
答: div {
      width: 0;
      height: 0;
      border: 20px solid transparent;
      border-width: 40px 20px 0 0;
      border-right-color: #f99;
    }
```

<a name="OH4lK"></a>

## 4、css选择器的优先级

```
答: !important>行内样式>id选择器>类/属性/伪类选择器>伪元素/标签选择器>通配符选择器*
```

<a name="LrGuA"></a>

## 5、px、em和rem的区别

```
答: px是固定单位,  
    em是相对单位,相当于当前文字的大小,如果没有就找父元素
    rem也是相对单位,相对于html的fontsize的大小
```


<a name="lVJwx"></a>

## 6、flex常用的容器属性

```
答:
1. flex-direction: 设置容器中的主轴方向
2. flex-wrap: 项目在主轴方向上是否换行显示
3. justify-content: 设置容器中的项目在主轴上的对齐方式
4. align-items: 单行项目在侧轴上的排列方式
5. align-content: 多行项目侧轴上的对齐方式
6. flex-flow: 是flex-direction和flex-wrap的合写, 默认值为row nowrap
```

<a name="l3joM"></a>

## 7、如何设置比12px更小的字体

```
答:
   p {
    	font-size:12px;
			-webkit-transform:scale(0.8);
    	}
```

<a name="NDSx4"></a>

## 8、H5新增了那些特性

```
答: 
1. 语义化标签: header nav section article aside footer
2. 多媒体标签: video audio
3. 表单控件: number search email tel date file time  url
4. 本地离线存储 localStorage 长期存储数据,改变浏览器数据不会丢失
			  sessionStorage 浏览器关闭数据会丢失
5. 自定义属性 data-*
6. 画布 Canvas
7. 拖拽释放 (Drap and Drap) API ondrop
8. 新的技术文本 webworker
9. 地理位置 (Geolocation) API
```

<a name="mQDJe"></a>

## 9、C3新增了那些特性

```
答:
1. 圆角 border-radius
2. 盒子模型 box-sizing
3. 阴影 box-shadow 盒子阴影  text-shadow 文字阴影
4. 过渡 transition
5. 2D转换transform  translate(平移) scale(缩放)  skew(斜切) rotate(旋转) transform-origin 控制转换中心点
6. 3D转换 perspective(透视距)  transform-style(3D控件效果)
7. 渐变 linear-gradient radial-gradient
8. 弹性布局 flex
9. 媒体查询 @media screen and () {...}
10. 边框图片 border-image
11. 自定义动画 @keyframes    animation
12. 颜色 新增RGBA HSLA模式
13. 背景 background-size   background-origin   background-clip
```

<a name="2d451857"></a>

## 10、请说下初始化CSS样式的意义

**答**：<br />由于浏览器兼容问题，不同的浏览器中，标签的默认样式可能不尽相同，CSS初始化是指重设浏览器的样式，保证在所有浏览器中，标签的默认样式相同，同时减少CSS代码量，节约网页下载时间。<br />**常见写法**：<br />①：最简单的初始化方法就是： `* {padding: 0; margin: 0;}` 。这样一个通用符在编写代码的时候是快，但这样写的话，他会把所有的标签都初始化一遍，这样就增加了网站运行的负载，会使网站加载过慢。<br />②：最好的做法是针对常用的标签进行初始化即可。<br />参考淘宝、腾讯等网站的css初始化：[https://www.jb51.cc/css/1113842.html](https://www.jb51.cc/css/1113842.html)
<a name="T3EjK"></a>

## 11、谈谈你对HTML语义化的理解？

**答：**<br />根据页面的结构，选择合适的**语义化**标签，便于开发者阅读和写出更优雅的代码，同时让浏览器的爬虫和机器很好的解析。<br />**追问：为什么要语义化**<br />为了在没有CSS的情况下，页面也能呈现出很好的内容结构和代码结构。<br />增加用户体验：例如title、alt用于解释名词或解释图片信息、label标签的活用<br />有利于SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息（爬虫依赖于标签来确定上下文和各个关键字和权重）<br />方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页<br />便于团队开发和维护，语义化更具可读性，是下一步网页的重要动向，遵循W3C标准的团队都遵循这个标准，可以减少差异化<br />**追问：平时你写HTML代码还有那些注意事项？**<br />1）尽可能少的使用无语义的标签div和span<br />2）在语义不明显时，既可以使用div或者p时，尽量用p，因为p在默认情况下有上下间距，对兼容特殊终端有利<br />3）不要使用纯样式标签，如：b、font、u等，改用CSS设置<br />4）需要强调的文本，可以包含在strong或者em标签中（浏览器预设样式，能用css指定就不用他们），strong默认样式是加粗（不要用b），em是斜体（不用i）<br />5）使用表格时，标题要用caption，表头用thead，主体部分用tbody包围，尾部用tfoot包围。表头和单元格要区分开，表头用th，单元格用td<br />6）表单域要用fieldset标签抱起来，并用legend标签说明表单的用途<br />7）每个input标签对应的说明文本都需要使用label标签，并且通过为input设置id属性，在label标签中设置for=someId来让说明文本和相对应的input关联起来<br />**追问：你知道有哪些HTML5新增的语义标签？**<br />article（定义文章）、aside（定义文章的侧边栏）、figure（一组媒体对象以及文字）、figurecaption（定义figure的标题）、footer（定义页脚）、header（定义页眉）、nav（定义导航栏）、section（定义文档中的区段）、time（定义日期和时间）、dialog（定义一个对话框）

<a name="S3DbS"></a>

## 12、请说下如何居中一个div？

答： 方法有很多，我大概记得以下5~6种吧。（回答可以直接说标题即可）<br />**方法一： 利用定位**

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .parent {
      width: 500px;
      height: 500px;
      border: 1px solid #000;
      position: relative;
    }

    .child {
      width: 100px;
      height: 100px;
      border: 1px solid #999;
      position: absolute;
      top: 50%;
      left: 50%;
      margin-top: -50px;
      margin-left: -50px;
    }
  </style>
</head>

<body>
  <div class="parent">
    <div class="child">我是子元素</div>
  </div>
</body>

</html>
```

**方法二：利用 margin:auto;**

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .parent {
      width: 500px;
      height: 500px;
      border: 1px solid #000;
      position: relative;
    }

    .c hild {
      width: 100px;
      height: 100px;
      border: 1px solid #999;
      position: absolute;
      margin: auto;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
    }
  </style>
</head>

<body>
  <div class="parent">
    <div class="child">我是子元素</div>
  </div>
</body>

</html>
```

**方法三： 利用 display:table-cell**

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .parent {
      width: 500px;
      height: 500px;
      border: 1px solid #000;
      display: table-cell;
      vertical-align: middle;
      text-align: center;
    }

    .c hild {
      width: 100px;
      height: 100px;
      border: 1px solid #999;
      display: inline-block;
    }
  </style>
</head>

<body>
  <div class="parent">
    <div class="child">我是子元素</div>
  </div>
</body>

</html>
```

**方法四： 利用 display： flex;设置垂直水平都居中**

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .parent {
      width: 500px;
      height: 500px;
      border: 1px solid #000;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .c hild {
      width: 100px;
      height: 100px;
      border: 1px solid #999;
    }
  </style>
</head>

<body>
  <div class="parent">
    <div class="child">我是子元素</div>
  </div>
</body>

</html>
```

**方法五： 计算父盒子与子盒子的空间距离(这跟方法一是一个道理)**

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .parent {
      width: 500px;
      height: 500px;
      border: 1px solid #000;
    }

    .c hild {
      width: 100px;
      height: 100px;
      border: 1px solid #999;
      margin-top: 200px;
      margin-left: 200px;
    }
  </style>
</head>

<body>
  <div class="parent">
    <div class="child">我是子元素</div>
  </div>
</body>

</html>
```

**方法六： 利用 transform**

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .parent {
      width: 500px;
      height: 500px;
      border: 1px solid #000;
      position: relative;
    }

    .c hild {
      width: 100px;
      height: 100px;
      border: 1px solid #999;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  </style>
</head>

<body>
  <div class="parent">
    <div class="child">我是子元素</div>
  </div>
</body>

</html>
```

<a name="66a8954f"></a>

## 13、请说下px/em/rem这三个单位有什么区别？

**答：**<br />①： px 是绝对单位，而 em 和 rem 是相对单位。<br />②： em相对于**当前元素**内文本的字体大小，找不到就找父亲的文字大小，而 rem是相对的** HTML 根元素**文字大小<br />③： px适合于固定文字大小， em经常用于比如段落首行缩进等， rem在后期移动端开发经常用于做适配。

<a name="f6be016b"></a>

## 14、你说下rem布局的原理和思路吧？

**答：**<br />①：根据屏幕的大小，动态的改变html标签的font-size的大小。<br />②：后代所有子元素的样式基于 html 进行运算，从而实现等比缩放。
<a name="gTUzL"></a>

## 15、通过CSS如何写一个三角形？

**答：**<br />①：主要是通过CSS边框来实现的，边框粗细决定这三角大小。<br />②：给盒子宽高为0，给显示的边框添加颜色，其余边框为透明色即可。
<a name="d8amz"></a>

## 16、如何实现两侧固定中间自适应的布局？

**答：**<br />①：这是一个比较常见的圣杯布局的方式。<br />②：最简单方法，可以通过flex布局来显示， 大盒子里面包含左中右三个小盒子，父盒子利用display：flex。两侧直接写固定宽度，中间盒子给flex:1 即可。
<a name="YeDhR"></a>

## 17、你知道BFC吗？

**答：**<br />①：BFC（Block Formatting Context），即块级格式化上下文，它是页面中的一块渲染区域，并且有一套属于自己的渲染规则，BFC目的是形成一个相对于外界完全独立的空间，让内部的子元素不会影响到外部的元素<br />②：触发BFC的条件

- 根元素，即HTML元素
- 浮动元素：float值为left、right
- overflow值不为 visible，为 auto、scroll、hidden
- display的值为inline-block、inltable-cell、table-caption、table、inline-table、flex、inline-flex、grid、inline-grid
- position的值为absolute或fixed

③：BFC的主要使用场景：

- 防止margin重叠（塌陷）。   比如给父级添加overflow，就触发了BFC， 还有子元素浮动，不会触发外边距塌陷原因也是因为触发了BFC
- 清除内部浮动。   同样，清除浮动方法中有个overflow:hidden 方法

<a name="afafbf4e"></a>
### 









