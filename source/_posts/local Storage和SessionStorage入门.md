---
title: local Storage  SessionStorage入门
date: 2018-08-16 20:18:18
tags:
---
## localStorage
1. - 与cookie不同，请求的时候浏览器不会带上localStorage
    - 而且每个域名localStorage最大存储量5Mb左右，cookie只有4k左右
    - 而且localStorage理论上不会过期，除非清理缓存
    - 所以持续化存东西的时候用localStorage
2. session是服务器上的hash，localStorage是浏览器上的hash，localStorage里存的东西保存在本地。
3. 只有相同域名的网页才能互相读取localStorage。
4. **API:**
```js
localStorage.setItem('a',1);
localStorage.getItem('a');    //1
```
5. 用来记录有没有提示过用户等信息，不能用来记录密码之类的

## sessionStorage
1. sessionStorage和session没有关系
2. sessionStorage和localStorage的1、2、3点是一样的，区别是关掉浏览器后sessionStorage就会被清除