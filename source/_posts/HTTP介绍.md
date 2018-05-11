---
title: HTTP介绍
date: 2018-05-11 13:05:16
tags: HTTP
---
### HTTP请求
- 请求示例1
curl -s -v -H "Frank: xxx" -- &quot;https://www.baidu.com&quot;
- 请求的内容为
GET / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
Frank: xxx
- 请求示例2
curl -X POST -d "1234567890" -s -v -H "Frank: xxx" -- &quot;https://www.baidu.com&quot;
- 请求的内容为
POST / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
Frank: xxx
Content-Length: 10
Content-Type: application/x-www-form-urlencoded

1234567890
- 请求的格式
1 动词 路径 协议/版本
2 Key1: value1
2 Key2: value2
2 Key3: value3
2 Content-Type: application/x-www-form-urlencoded
2 Host: www.baidu.com
2 User-Agent: curl/7.54.0
3 
4 要上传的数据
#### 用Chrome开发者工具查看 HTTP 请求内容
- 请求最多包含四部分，最少包含三部分。（也就是说第四部分可以为空）
- 第三部分永远都是一个回车（\n）
- 动词有 GET POST PUT PATCH DELETE HEAD OPTIONS 等
- 这里的路径包括「查询参数」，但不包括「锚点」
- 如果你没有写路径，那么路径默认为 /
- 第 2 部分中的 Content-Type 标注了第 4 部分的格式
- 打开 Network
- 地址栏输入网址
- 在 Network 点击，查看 request，点击「view source」
- 点击「view source」
- 可以看到请求的前三部分了
- 如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到
### HTTP响应
- 响应示例1
curl -s -v -H "Frank: xxx" -- &quot;https://www.baidu.com&quot;
- 响应内容
HTTP/1.1 200 OK
Accept-Ranges: bytes
Cache-Control: private, no-cache, no-store, proxy-revalidate, no-transform
Connection: Keep-Alive
Content-Length: 2443
Content-Type: text/html
Date: Tue, 10 Oct 2017 09:14:05 GMT
Etag: "5886041d-98b"
Last-Modified: Mon, 23 Jan 2017 13:24:45 GMT
Pragma: no-cache
Server: bfe/1.0.8.18
Set-Cookie: BDORZ=27315; max-age=86400; domain=.baidu.com; path=/

<!DOCTYPE html>
&lt;!--STATUS OK-->&lt;html> &lt;head> 后面太长，省略了……
- 响应示例1
curl -X POST -s -v -H "Frank: xxx" -- &quot;https://www.baidu.com&quot;
- 响应内容
HTTP/1.1 302 Found
Connection: Keep-Alive
Content-Length: 17931
Content-Type: text/html
Date: Tue, 10 Oct 2017 09:19:47 GMT
Etag: "54d9749e-460b"
Server: bfe/1.0.8.18

&lt;html&gt;
&lt;head>
&lt;meta http-equiv="content-type" content="text/html;charset=utf-8"> 后面太长，省略了……
- GET 请求和 POST 请求对应的响应可以一样，也可以不一样
- 响应的第四部分可以很长很长很长
- 响应的格式
1 协议/版本号 状态码 状态解释
2 Key1: value1
2 Key2: value2
2 Content-Length: 17931
2 Content-Type: text/html
3
4 要下载的内容
- 用 Chrome 查看响应
打开 Network
输入网址
选中第一个响应
查看 Response Headers，点击「view source」
你会看到响应的前两部分
查看 Response 或者 Preview，你会看到响应的第 4 部分
###如何使用 curl 命令
curl(transfer a URL),curl命令是一个利用URL规则在命令行下工作的文件传输工具。它支持文件的上传和下载，所以是综合传输工具，但按传统，习惯称curl为下载工具。作为一款强力工具，curl支持包括HTTP、HTTPS、ftp等众多协议，还支持POST、cookies、认证、从指定偏移处下载部分文件、用户代理字符串、限速、文件大小、进度条等特征。做网页处理流程和数据检索自动化，curl可以祝一臂之力。
- 语法
curl(选项)(参数)
- 常见参数
-A/--user-agent <\string>              设置用户代理发送给服务器
-b/--cookie <\name=string/file>        cookie字符串或文件读取位置
-c/--cookie-jar <\file>                操作结束后把cookie写入到这个文件中
-C/--continue-at <\offset>             断点续转
-D/--dump-header <\file>               把header信息写入到该文件中
-e/--referer                           来源网址
-f/--fail                              连接失败时不显示http错误
-o/--output                            把输出写到该文件中
-O/--remote-name                       把输出写到该文件中，保留远程文件的文件名
-r/--range <\range>                    检索来自HTTP/1.1或FTP服务器字节范围
-s/--silent                            静音模式。不输出任何东西
-T/--upload-file <\file>               上传文件
-u/--user <\user[:password]>           设置服务器的用户和密码
-w/--write-out [format]                什么输出完成后
-x/--proxy <\host[:port]>              在给定的端口上使用HTTP代理
-#/--progress-bar                      进度条显示当前的传送状态
