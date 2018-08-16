---
title: cookie和session
date: 2018-08-16 19:54:23
tags:
---

## Cookie

1、服务器通过 Set-Cookie 头给客户端一串字符串
4、客户端每次访问相同域名的网页时 ， 必须带上这段字符串
3、客户端要在一段时间内保存这个 Cookie
4、前端不要读写 cookie，用 local sortage
### cookie 可以在后台更改保存时间
setMaxAge
```js
cookie.setMaxAge(0);//不记录cookie
cookie.setMaxAge(-1);//会话级cookie，关闭浏览器失效
cookie.setMaxAge(60*60);//过期时间为1小时
```
过时了的expires
```js
Set-Cookie: name=Nicholas; expires=Sat, 02 May 2018 23:38:25 GMT
//星期六 5月2号 2010年 23:38:25时过期
```

## Session

1、将SessionID （ 随 机 数 ）通过 Cookie 发给客户端
2、客户端访问服务器时，服务器读取SessionID
5、服务器有一块内存（哈希表）保存了所有 session
4、通过 SessionID 我们可以得到对应用户的隐私信息，如 id 、email
5、这块内存（哈希表）就是服务器上的所有 session



## cookie和session的区别
### 1. cookie
- cookie是由服务器发送给浏览器的响应头里的`Set-Cookie:`的值构成的。
- cookie保存在客户端，并且每次都随着请求发送给server。
- 没有session之前，cookie里保存的是用户信息，由于任何人可以读写，不安全
### 2. session
- session是依附于cookie而存在的
- 有了session，服务器将用户的信息保存在服务器中的session表里，然后赋予相应的信息一个sessionID，于是将响应头里的`Set-Cookie`的值改为sessionID
- 浏览器请求时带上cookie，服务器就通过cookie里的sessionID查找session表里对应的信息
- 这样暴露给其他人的就只有sessionID，很安全。