---
title: JS里的数据类型转换
date: 2018-06-06 13:30:31
tags:
---
### 类型转换
**任意类型转字符串**
- String()
``` js
    String(1) // "1"
    String(true)//"ture"
    String(null)//"null"
    String(undefined)//"undefined"
    String({})//"[object Object]"
```

- .toString()
``` js
    (1).toString() // "1"
    (true).toString()//"ture"
    (null).toString()//"报错"
    (undefined).toString()//"报错"
    ({}).toString()//"[object Object]"
```

- +''
```js
    1+''//"1"
    true+''//"true"
    null+''//"null"
    undefined+''//"undefined"
    var n={}
    n+''//"[object Object]"
```

**任意类型变布尔（boolean）**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;如果 JavaScript 预期某个位置应该是布尔值，会将该位置上现有的值自动转为布尔值。转换规则是除了下面六个值被转为false，其他值都视为true。

1. undefined  &nbsp;&nbsp;&nbsp;&nbsp;  2. null  &nbsp;&nbsp;&nbsp;&nbsp;  3. false  &nbsp;&nbsp;&nbsp;&nbsp;  4. 0  &nbsp;&nbsp;&nbsp;&nbsp;  5. NaN  &nbsp;&nbsp;&nbsp;&nbsp;6. ""或''（空字符串）

- Boolean()
```js
    Boolean(1)//true
    Boolean(0)//false
```
- !!()
```js
    !!(1)//true
    !!(null)//false
```
**任意类型变数字（number)**
- Number()
```js
 Number('1')//1
```
- parseInt(string, radix)
```js
 parseInt(10, 10)//10
 parseInt(110, 2)//6
```
- parseFloat()
```JS
parseFloat("3.14");
parseFloat("314e-2");
parseFloat("0.0314E+2");
parseFloat("3.14more non-digit characters");
//均返回 3.14
```
- -0
```js
'1.23'-0//1.23
```
- +(取正)
```js
+'3.14'//3.14
+'-3.14'//-3.14
```
### 内存图
![内存.png](https://i.loli.net/2018/06/06/5b17a98ee23d6.png)
### 深拷贝浅拷贝
```js
var a = 1
var b = a
b = 2 //这个时候改变 b
a = 1//a 完全不受 b 的影响
```
那么我们就说这是一个深拷贝
对于简单类型的数据来说，赋值就是深拷贝。
**对于复杂类型的数据（对象）来说，才要区分浅拷贝和深拷贝。**

- 这是一个浅拷贝的例子
```js
var a = {name: 'w'}
var b = a
b.name = 'b'
a.name === 'b' // true
//因为我们对 b 操作后，a 也变了
```
- 深拷贝
**什么是深拷贝了，就是对 Heap 内存进行完全的拷贝。**
```js
var a = {name: 'frank'}
var b = deepClone(a) // deepClone 还不知道怎么实现
b.name = 'b'
a.name === 'a' // true
```