---
title: JS里的数据类型
date: 2018-06-04 12:53:47
tags: 数据类型
---
#### JS总共有7种数据类型（number,string,boolean,null,undefined,object,symbol）
![数据类型.png](https://i.loli.net/2018/06/04/5b14c929d15fd.png)
### typeof 确定类型 
``` js    
    typeof 123 // "number"
    typeof '123' // "string"
    typeof false // "boolean"
    typeof undefined //undefiend
```
然而函数返回的是function，null返回的是object
``` js
    function f() {}
    typeof f// "function"
    typeof null //object
```

### number（数值）
#### 进制
- 十进制：没有前导0的数值。
- 八进制：有前缀0o或0O的数值，或者有前导0、且只用到0-7的八个阿拉伯数字的数值。
- 十六进制：有前缀0x或0X的数值。
- 二进制：有前缀0b或0B的数值。
#### 特殊值
NaN是 JavaScript 的特殊值，表示“非数字”（Not a Number）
Infinity表示“无穷”，Infinity有正负之分，Infinity表示正的无穷，-Infinity表示负的无穷。
#### 转整数、小数
**parseInt() 转整数**
- parseInt的返回值只有两种可能，要么是一个十进制整数，要么是NaN。
- parseInt方法还可以接受第二个参数（2到36之间），表示被解析的值的进制
- Parseint(1000,2)  以2进制表示1000
- parseInt会将科学计数法的表示方法视为字符串
**parseFloat() 转小数**
parseFloat方法用于将一个字符串转为浮点数。
如果字符串包含不能转为浮点数的字符，则不再进行往后转换，返回已经转好的部分。
``` js
    parseFloat('314e-2') // 3.14
    parseFloat('0.0314E+2') // 3.14
```

### string（字符串）
**字符串默认只能写在一行内，分成多行将会报错。**
- 单引号字符串的内部，可以使用双引号。双引号字符串的内部，可以使用单引号。" ' ' "
- 在单引号字符串的内部，使用单引号，就必须在内部的单引号前面加上反斜杠，用来转义。\
**\.length属性**
length属性返回字符串的长度，该属性也是无法改变的。
``` js
    var s = 'hello';
    s.length // 5
```
**表示多行字符串**
1.模板字符串（`）表示多行字符串，所有的空格和缩进都会被保留在输出之中。
2.用+号链接。


### boolean（布尔值）
**下列运算符会返回布尔值：**

两元逻辑运算符： && (And)，|| (Or)
前置逻辑运算符： ! (Not)
相等运算符：===，!==，==，!=
比较运算符：>，>=，<，<=

**如果 JavaScript 预期某个位置应该是布尔值，会将该位置上现有的值自动转为布尔值。转换规则是除了下面六个值被转为false，其他值都视为true。**
``` js
    undefined
    null
    false
    0
    NaN
    ""或''（空字符串）
```
空数组（[]）和空对象（{}）对应的布尔值，都是true。


### null 与 undefined
都表示没有值
- （规范）如果一个变量没有被赋值，那么这个变量的值就是 undefiend
- （习俗）如果你想表示一个还没赋值的对象，就用 null。如果你想表示一个还没赋值的字符串/数字/布尔/symbol，就用 undefined（但是实际上你直接 var xxx 一下就行了，不用写 var xxx = undefined）



### object（对象）
简单说，对象就是一组“键值对”（key-value）的集合，是一种无序的复合数据集合。
**对象的所有键名都是字符串，无论加不加引号。**
#### 属性
- 对象的每一个键名又称为“属性”（property）属性的值为函数，通常把这个属性称为“方法”，它可以像函数那样调用。

- 读取对象的属性
``` js
    var obj = {
        p: 'Hello World'
    };

    obj.p // "Hello World"
    obj['p'] // "Hello World"
```
• `Obj.p` 或  `Obj['p']`   记得引号，否则会当成变量处理
• **数字属性** 不能用点运算，会被当成小数点，要用方括号 可以不加引号，会自动转成字符串。`Obj[3]`

- 查看所有属性: 
``` js 
    Object.keys[obj]
```

- 删除属性 ： 
``` js 
    delete obj.p //ture`
```
- in运算符
用于检查对象是否包含某个属性（注意：**检查的是键名，不是键值**）
``` js
    var obj={name: wang,age:24}
    'name' in obj  // true
```
- for...in循环用来遍历一个对象的全部属性。
``` js
    var obj = {a: 1, b: 2, c: 3};

    for (var i in obj) {
    console.log(obj[i]);
    }
```

