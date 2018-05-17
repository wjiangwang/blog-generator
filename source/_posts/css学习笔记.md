---
title: css学习笔记
date: 2018-05-17 12:28:55
tags: css
---
### 引入css四种方式：
- 内联       
- style标签          
- css link  `<link rel="stylesheet" href="./a.css">`     
- @import url()
### 几种元素

- float: 指定一个元素应沿其容器的左侧或右侧放置， `clearfix` 添加在所有浮动元素爸爸身上

- Hover: 当鼠标悬浮时

- display: block  元素生成一个块元素盒。  inline-block该元素生成一个块状盒，该块状盒随着周围内容流动，如同它是一个单独的行内盒子（表现更像是一个被替换的元素）

- margin:给定元素设置所有四个（上下左右）方向的外边距属性。这是四个外边距属性设置的简写。可以为负，

- padding:属性设置一个元素的内边距，padding 区域指一个元素的内容和其边界之间的空间，该属性不能为负值。

- border：一个用于设置各种单独的边界属性的简写属性。border调试大法 `border: 1px solid red;`

- inherit：继承关键字，使得元素获取其父元素的计算值(computed value )。
### 文档流（normal flow）
- 文档流：文档内元素流动的方向，在文档流中, 元素按照其在 HTML 中的先后位置至上而下布局, 在这个过程中, 行内元素水平排列, 直到当行被占满然后换行; 块级元素则会被渲染为完整的一个新行.
- 脱离文档流：1.浮动机制2.绝对定位

- div 高度由其内部文档流元素的高度总和决定
### 内联元素和块级元素的主要区别
#### 内联元素
1.独占一行,默认情况下，其宽度自动填满其父元素宽度
2.可以设置width，height属性	
3.可以设置margin和padding属性	
4.对应于     display:block
#### 块级元素
1.相邻的行内元素会排列在同一行里，直到一行排不下，才会换行，其宽度随元素的内容而变化
2.行内元素设置width，height属性无效
3.行内元素起边距作用的只有margin-left、margin-right、padding-left、padding-right，其它属性不会起边距效果。
4. 对应于    display:inline；
### 背景图
- Background-position: center center; 背景图 ：水平 垂直 居中；

- background-size: cover;  背景图自适应
- 给背景图加上面具 ：background-color: rgba(0,0, 0, 0.65);

- rgba(red, green, blue, Alpha透明度。取值0~1之间。)
### 居中
对于一个div，如果他有一个宽度  `Margin-left：auto；  Margin-right：auto;`
### 画一个三角形
1.span里不放DIV
2.示例代码
    {
        border: 10px solid transparent;
        width:0px;
        border-left-color: #e6686a;
        border-top-width: 0px;
    }
#### 绝对定位
- 子元素上  `position: absolute;`
- 父元素上    `position: relative;`
- 子元素相对于父元素定位

- position： fixed；脱离文档流,相对于屏幕固定



