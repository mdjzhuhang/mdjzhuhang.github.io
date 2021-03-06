---
layout: post
title:  HTTP 基础知识
excerpt: http1.0 短时，每一个请求使用一个新的 TCP 连接，一个生命周期就关闭。http1.1 长时，服务端／客户端都可以关闭。http2.0 双工。简单来说https是http的安全版,是使用 TLS/SSL 加密的 HTTP 协议。
category: frontend
---
#### HTTP 简介

HTTP协议，Hyper Text Transfer Protocol 超文本传输协议

用于从万维网（WWW:World Wide Web ）服务器传输超文本到本地浏览器的传送协议。

基于TCP/IP通信协议来传递数据（HTML 文件, 图片文件, 查询结果等）。

是属于应用层的面向对象的协议，由于其简捷、快速的方式，适用于分布式超媒体信息系统

HTTP协议工作于客户端-服务端架构为上。浏览器作为HTTP客户端通过URL向HTTP服务端即WEB服务器发送所有请求。Web服务器根据接收到的请求后，向客户端发送响应信息。

在浏览器地址栏键入URL，按下回车之后会经历以下流程：

<blockquote>
1、浏览器向 DNS 服务器请求解析该 URL 中的域名所对应的 IP 地址

2、解析出 IP 地址后，根据该 IP 地址和默认端口 80，和服务器建立TCP连接

3、浏览器发出读取文件(URL 中域名后面部分对应的文件)的HTTP 请求，该请求报文作为 TCP 三次握手的第三个报文的数据发送给服务器

4、服务器对浏览器请求作出响应，并把对应的 html 文本发送给浏览器

5、释放 TCP连接

6、浏览器将该 html 文本并显示内容　
</blockquote>

#### http1.0，1.1，2.0

http 1.0 短时，每一个请求使用一个新的 TCP 连接，一个生命周期就关闭

http 1.1 长时，服务端／客户端都可以关闭

http 2.0 双工

HTTP 1.0 首部加上 keep-alive，且请求间隔符合服务端keep-alive的设置时间间隔时，多个ajax用一个连接，否则默认一个请求一个连接。

HTTP 1.1 之后 keep-alive（持久连接）被默认启用，除非在响应中指定connection：close，否则 webserver 会假定所有连接都是持久的。

#### URI，URL，URN
URI，uniform resource identifier，统一资源标识符，用来唯一的标识一个资源

URL，uniform resource locator，统一资源定位器，它是一种具体的URI，即URL可以用来标识一个资源，而且还指明了如何locate这个资源

URN，uniform resource name，统一资源命名，URI的子类，是通过名字来标识资源，比如mailto:java-net@java.sun.com。


#### Request 消息结构

1、请求行

&nbsp;&nbsp; 例如：`GET http://www.cnblogs.com/ HTTP/1.1`
- Method 请求方法，如："POST"，"GET"
- Path-to-resoure 请求的资源
- Http/version-number HTTP协议/版本号

2、http header

3、body

#### Response消息结构
1、request line

&nbsp;&nbsp; HTTP协议版本号&nbsp;&nbsp; 状态码&nbsp;&nbsp; 状态消息

2、request header

3、body

header和body之间都有个空行

#### 常见状态码
```
200 OK                        //客户端请求成功
400 Bad Request               //客户端请求有语法错误，不能被服务器所理解
401 Unauthorized              //请求未经授权，这个状态代码必须和WWW-Authenticate报头域一起使用 
403 Forbidden                 //服务器收到请求，但是拒绝提供服务
404 Not Found                 //请求资源不存在，eg：输入了错误的URL
500 Internal Server Error     //服务器发生不可预期的错误
503 Server Unavailable        //服务器当前不能处理客户端的请求，一段时间后可能恢复正常
```

#### HTTPS

HTTPS (Secure Hypertext Transfer Protocol) 安全超文本传输协议

它是一个安全通信通道，它基于HTTP开发，用于在客户计算机和服务器之间交换信息。它使用安全套接字层(SSL)进行信息交换，简单来说它是HTTP的安全版,是使用 TLS/SSL 加密的 HTTP 协议。

HTTP 协议采用明文传输信息，存在信息窃听、信息篡改和信息劫持的风险，而协议 TLS/SSL 具有身份验证、信息加密和完整性校验的功能，可以避免此类问题。

TLS/SSL 全称安全传输层协议 Transport Layer Security, 是介于 TCP 和 HTTP 之间的一层安全协议，不影响原有的 TCP 协议和 HTTP 协议，所以使用 HTTPS 基本上不需要对 HTTP 页面进行太多的改造。


[关于HTTP协议，一篇就够了](https://www.cnblogs.com/ranyonsue/p/5984001.html)

[HTTP、HTTP2.0、SPDY、HTTPS](http://blog.csdn.net/d15874091830/article/details/52700412)

[http 2.0 协议详解](http://blog.csdn.net/zqjflash/article/details/50179235)

[全站 HTTPS 来了](http://www.cnblogs.com/zhuyang/p/5081888.html)

[扒一扒HTTPS网站的内幕](https://blog.wilddog.com/?p=210)