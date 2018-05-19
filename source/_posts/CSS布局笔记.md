---
title: CSS布局笔记
date: 2018-05-19 11:48:01
tags: css 布局 
---
### 左右布局
 使用float，在子元素上使用`float：left;`在父元素上加`class = clearfix`用于清除浮动
 ```css
    .clearfix::after{
        content: '';
        display: block;
        clear: both;
    }
 ```
### 左中右布局
 使用float或者使用绝对定位的方法。
 ```css
    #container{  
        position:relative;  
        margin:20px;  
        height:400px; 
    #left_side{  
        position:absolute;  
        top:0px;  
        left:0px;  
        border:solid 1px #red;  
        width:170px;  
        height:100%;  
    }  
    #content{ 
        position:absolute; 
        margin:0px 190px 0px 190px;  
        border:solid 1px #red;  
        height:100%;  
    }  
    #right_side{  
        position:absolute;  
        top:0px;  
        right:0px;  
        border:solid 1px #red;  
        width:170px;  
        height:10
    }
 ```
### 水平居中
 1.给元素定一个显示式的宽度，然后加上margin的左右值为auto。
 ```css
    .center{
        width: 800px;
        margin-left: auto;
        margin-right: auto;
    }
 ```
 2.使用`display:inline-block;`仅仅inline-block属性是无法让元素水平居中，他的关键之处要在元素的父容器中设置text-align的属性为“center”，这样才能达到效果：
### 垂直居中
 1.不知道自己高度和父容器高度的情况下,使用绝对定位
 ```css
    .parentElement{
        position:relative;
    }

    .childElement{
        position: absolute;
        top: 50%;
            transform:  translateY(-50%);
    }
 ```
 2.若父容器下只有一个元素，且父元素设置了高度，则只需要使用相对定位即可
 ```css
    .parentElement{
        height:xxx;
    }

    .childElement {
        position: relative;
        top: 50%;
            transform:  translateY(-50%);
    }
 ```
 3.flexbox    emmmmmm  还不太会，以后填坑

### 背景图
 背景图水平垂直居中
 ```css
 Background-position: center center;
 ``` 
 背景图自适应
 ```css
    background-size: cover;
 ```
 给背景图加上面具 
 ```css
    background-color: rgba(0,0, 0, 0.65);
 ```
 rgba(red, green, blue, Alpha透明度。取值0~1之间。)

### 选择器
 - tr:nth-child(2n+1) 
    表示HTML表格中的奇数行。

 - tr:nth-child(odd)
    表示HTML表格中的奇数行。

 - tr:nth-child(2n)
    表示HTML表格中的偶数行。

 - tr:nth-child(even)
    表示HTML表格中的偶数行。

 - pan:nth-child(0n+1)
    表示子元素中第一个且为span的元素，与 :first-child 选择器作用相同。

 - span:nth-child(1)
    表示父元素中子元素为第一的并且名字为span的标签被选中

 - span:nth-child(-n+3)
    匹配前三个子元素中的span元素。

### CSS优先级
 - 行内样式 > id样式 > class样式 > 标签名样式

### CSS三角形
 - 先编写一个空元素
 ```html
    <div class="triangle"></div>
 ```
 - 然后，将它四个边框中的三个边框设为透明，剩下一个设为可见，就可以生成三角形效果：
 ```css
    .triangle { 
        border-color: transparent transparent green transparent; 
        border-style: solid; 
        border-width: 0px 300px 300px 300px; 
        height: 0px; 
        width: 0px; 
        }
 ```
### 参考
 * [CSS使用技巧-阮一峰](http://www.ruanyifeng.com/blog/2010/03/css_cookbook.html)
