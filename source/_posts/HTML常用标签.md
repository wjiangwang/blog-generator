---
title: HTML常用标签
date: 2018-05-14 16:10:36
tags:
---
## iframe
- HTML内联框架元素 `<iframe>` 表示嵌套的浏览上下文，有效地将另一个HTML页面嵌入到当前页面中`<iframe src="https://www.baidu.com" name=xxx frameborder="0"></iframe>`，`frameborder="0"`表示没有边框。常见的属性有`name`嵌入的浏览上下文（框架）的名称。该名称可以用作`<a>`标签，`<form>`标签的target属性值，或`<input>` 标签和 `<button>`标签的formtaget属性值。
- `src=""`可以写相对路径src="./index2.html"
- 与`<a>`一起用 
    `<iframe src="#" name=xxx></iframe><a herf="https://www.baidu.com" tarage=xxx>baidu<a>`
## a
`<a> `元素  (或锚元素) 可以创建一个到其他网页、文件、同一页面内的位置、电子邮件地址或任何其他URL的超链接。
- 跳转页面,发起的是GET请求
`target`属性
- `<a href="http://qq.com" target="_blank">QQ</a>`在新页面打开链接
- `<a href="http://qq.com" target="_self">QQ</a>`在当前页面打开
- `<a href="http://qq.com" target="_parent">QQ</a>`在父级页面打开
- `<a href="http://qq.com" target="_top">QQ</a>`在顶层页面打开
 `download` 属性
- 此属性指示浏览器下载URL而不是导航到URL，因此将提示用户将其保存为本地文件。
`href`属性
- 这是一个必需属性为锚定义一个超文本链接来源。这表示链接目标的URL或URL片段。URL片段是由一个hash符号（＃），它指定一个内部目标在当前文档中的位置（ID）开头的名字。URL不限于网页（HTTP）的文件。URL可能使用浏览器所支持的任何协议。例如，文件，FTP，大多数用户代理mailto工作。可以使用 href="#top" 或者 href="#" 链接返回到页面顶部。这种行为在HTML5上被指定。
- javascript伪协议`<a href="javascript:;" target="_blank">QQ</a>`点击QQ`<a>`标签无反应

## form
`<form>` 元素 表示了文档中的一个区域，这个区域包含有交互控制元件，用来向web服务器提交信息。
- 跳转页面,发起的是POST请求
- `method="POST"``method="GET"`浏览器使用这种 HTTP 方式来提交 form
- 需要有`<input>`按钮用于提交表单 
    <form action="index2.html" method="POST">
        <input type="text" name="username">
        <input type="password" name="password">
        <input type="submit" value="提交">
    </form>
`method="GET"`会将username&password放入查询参数。
- 也有`target`属性
## input
`<input>` 元素用于为基于Web的表单创建交互式控件，以便接受来自用户的数据。
- `button`：无缺省行为按钮。
- `checkbox`： 复选框。必须使用 value 属性定义此控件被提交时的值。使用 checked 属性指示控件是否被选择。也可以使用 indeterminate 指示复选框在一种不确定状态（大多数平台上，显示为一条穿过复选框的水平线）。
```html
             <label><input type="checkbox" name="lovefruits" value="orange">橘子</label>
             <label><input type="checkbox" name="lovefruits" value="Banana">香蕉</label>
             <label><input type="checkbox" name="lovefruits" value="apple">苹果</label>
             <label><input type="checkbox" name="lovefruits" value="watermelon">西瓜</label>
```

- `radio`：单选按钮。必须使用 value 属性定义此控件被提交时的值。使用checked 必须指示控件是否缺省被选择。在同一个”单选按钮组“中，所有单选按钮的 name 属性使用同一个值； 一个单选按钮组中是，同一时间只有一个单选按钮可以被选择。
```html
    <label><input type="radio" name="lovefruits" value="orange">橘子</label>
    <label><input type="radio" name="lovefruits" value="Banana">香蕉</label>
    <label><input type="radio" name="lovefruits" value="apple">苹果</label>`
    <label><input type="radio" name="lovefruits" value="watermelon">西瓜</label>
```

- `password`：一个值被遮盖的单行文本字段。使用 maxlength 指定可以输入的值的最大长度 。
- `submit`：用于提交表单的按钮。
- `text`：单行字段；换行会将自动从输入的值中移除。
## button
`<button>` 元素表示一个可点击的按钮，可以用在表单或文档其它需要使用简单标准按钮的地方。
type的类型有：
- `submit`:  此按钮提交表单数据给服务器。未指定时，此值为默认值，或者如果此属性动态变为空值或无效值。
- `reset`:  此按钮重置所有组件为初始值。
- `button`: 此按钮没有默认行为。它可以有与元素事件相关的客户端脚本，当事件出现时可触发。
- `menu`: 此按钮打开一个由指定`<menu>`元素进行定义的弹出菜单。
value
- button的初始值。它定义的值与表单数据的提交按钮相关联。当表单中的数据被提交时，这个值便以参数的形式被递送至服务器。
## select
`<select> `元素是一种表单控件，可创建选项菜单。菜单内的选项为`<option>` , 可以由 `<optgroup>` 元素分组。选项可以被用户预先选择。
```html
    <select name="分组" id="">
        <option value="1">第一组</option>
        <option value="2" disabled>第二组</option>
        <option value="3" selected>第三组</option>
    </select>
```
- multiple这个布尔值的属性标记select是否可以多选. 默认是单选.
- disabled这个布尔值的属性表明一个用户是否可以操控该表单对象. 如果这个属性没有被明确定义, 则从它的父元素继承, 例如 fieldset; 如果没有父元素设置 disabled 属性, 那么默认该表单对象 enabled.



## table
`<table>` 元素表示表格数据 — 即通过二维数据表表示的信息。
```
    <table>
    <tr>
        <td>John</td>
        <td>Doe</td>
    </tr>
    <tr>
        <td>Jane</td>
        <td>Doe</td>
    </tr>
    </table>
```



