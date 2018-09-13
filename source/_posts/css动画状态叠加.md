---
title: css 状态叠加
date: 2018-09-13 14:18:02
tags:
---
### 问题描述
在做网易云过程中遇到的一个问题，`animation-play-state`在微信内置浏览器和iosSafari中不起作用。导致歌曲播放动画无法暂停
### 解决方案
采用 css3 属性叠加
```js
var isPlaying = false;
var container = document.querySelector(".container");
var disk = container.querySelector(".disk");

disk.addEventListener("click", function bindEvent() {
isPlaying ? pause() : play();
});
function pause() {
isPlaying = false;
var dTransform = getComputedStyle(disk).transform;
var cTransform = getComputedStyle(container).transform;
container.style.transform =
cTransform === "none" ? dTransform : dTransform.concat(" ", cTransform);
disk.classList.remove("active");
}
function play() {
isPlaying = true;
disk.classList.add("active");
}
```
[源码链接](https://github.com/wjiangwang/demo/tree/master/css%20%E5%8A%A8%E7%94%BB%E7%8A%B6%E6%80%81%E5%8F%A0%E5%8A%A0)
[预览链接](https://wjiangwang.github.io/demo/css%20%E5%8A%A8%E7%94%BB%E7%8A%B6%E6%80%81%E5%8F%A0%E5%8A%A0/index.html)


