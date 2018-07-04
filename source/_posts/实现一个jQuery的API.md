---
title: 实现一个jQuery的API
date: 2018-07-04 12:06:54
tags:
---
## 需求
在不使用jQuery函数库的情况下自制一个与jQuery类似的API
首先，确认以下两个需求：
```js
var $div = $('div')
$div.addClass('red') // 可将所有 div 的 class 添加一个 red
$div.setText('hi') // 可将所有 div 的 textContent 变为 hi
```
## 创建
先创建一个新的window对象jQuery，它是一个函数，并返回带有参数新的对象
```js
window.jQuery=function(node){
    return{
        addClass:function(node){},
        setText:function(node){}
}
```
## 参数
```js
var $div = $('div')
```
要实现这个功能，需要区分传入的参数是一个选择器还是节点，并以伪数组的形式返回。
```js
window.jQuery = function (nodeOrSelector) {
            let nodes = {}
            if (typeof nodeOrSelector === 'string') {
                let temp = document.querySelectorAll(nodeOrSelector)
                for (let i = 0; i < temp.length; i++) {
                    nodes[i] = temp[i]
                }   
                   nodes.length = temp.length

            } else if (nodeOrSelector instanceof Node) {
                nodes = {
                    0: nodeOrSelector,
                    length: 1
                }
            }
        }
```
如果只是单单实现所需要的功能，可以简化成
```js
window.jQuery = function (nodeOrSelector) {
            let nodes = document.querySelectorAll(nodeOrSelector)
        }
```
## 需求实现
```js
$div.addClass('red')// 可将所有 div 的 class 添加一个 red
```
nodes是一个伪数组。如果每个div都要添加class的话，需要一个for循环，然后每一次用DOM的方法里的classList.add功能对div添加class。
```js
addClass: function (className) {
                    for (let i = 0; i < nodes.length; i++) {
                        nodes[i].classList.add(className)
                    }
                }
```
同理可实现
```js
$div.setText('hi') // 可将所有 div 的 textContent 变为 hi

setText: function (text) { 
                    for (let i = 0; i < nodes.length; i++) {
                        nodes[i].textContent=text
                    }
                }
```
把addClass和setText的内容结合到函数内，得到：
```js
        window.jQuery = function (nodeOrSelector) {
            let nodes = {}
            if (typeof nodeOrSelector === 'string') {
                let temp = document.querySelectorAll(nodeOrSelector)
                for (let i = 0; i < temp.length; i++) {
                    nodes[i] = temp[i]
                    nodes.length = temp.length
                }

            } else if (nodeOrSelector instanceof Node) {
                nodes = {
                    0: nodeOrSelector,
                    length: 1
                }

            }
            return {
                addClass: function (className) {
                    for (let i = 0; i < nodes.length; i++) {
                        nodes[i].classList.add(className)
                    }
                },
                setText: function (text) { 
                    for (let i = 0; i < nodes.length; i++) {
                        nodes[i].textContent=text
                    }
                }
            }
        }
        window.$ = jQuery
```











