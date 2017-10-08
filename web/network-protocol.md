# 网络协议

网络协议（Internet Protocol Suite，IPS）


## 分层


OSI（Open System Interconnect）七层模型：

* 物理层（Physical layer）
* 数据链路层（Data link layer）
* 网络层（Network layer）
* 运输层（Transport layer）：TCP、UDP
* 会话层（Session layer）
* 表示层（Presentation layer）
* 应用层（Application layer）：HTTP、FTP

也有分层五层的。

* 应用层（Application Layer）
* 传输层（Transport Layer）
* 网络层（Internet Layer）
* 数据链路层（）
* 物理层

常见的网络协议

* FTP（File Transfer Protocol，文件传输协议）
* HTTP（HyperText Transfer Protocol，超文本传输协议）
* 

## IP 协议（Internet Protocol，IP）



## TCP 协议

TCP 协议（Transmission Control Protocol，传输控制协议）

三次握手




四次挥手

## UDP 协议

UDP 协议（User Datagram Protocol，用户数据报协议）

## TCP 和 UDP 的区别

* 连接性：TCP 是面向连接的；而 UDP 是无连接的。
* 可靠性：TCP 是可靠的；UDP 是不可靠的。






TCP面向连接；UDP是无连接的。（TCP需要三次握手，而UDP不需要握手）





抓包工具：

* Wireshark
* Fiddler2（手机抓包？）



下载地址：https://www.wireshark.org/download.html

[百度云盘（Wireshark-win64-2.4.1.exe）](https://pan.baidu.com/s/1eRQc1FW)



## DNS

全球一共只有13台根服务器（名字分别为“A”至“M”），1 个为主根服务器（A），在美国，其余 12 个均为辅根服务器。

A 记录

MX 记录

nslookup -qt=类型 目标域名

雪人计划



CDN（Content Delivery Network，内容分发网络）

## GFW

GFW（Great Firewall，中国防火长城）

GFW 的主要技术：国家入口网关的 IP 封锁、主干路由器的关键字过滤阻断、域名劫持和 HTTPS 证书过滤等。

根域名服务器（root name server，简称根服务器）

VPN（Virtual Private Network，虚拟专用网络）
VPS（Virtual Private Server，虚拟专用服务器）

> 为了增加反应速度，网页访问的申请都是由一个数据包所完成的，而一个数据包的长度为256B字节，这就决定了一个数据包只能有13个块，这就从根本上限制了根域名服务器的数量，也就是说根域名服务器只能有13个。

## Spam

Spam（垃圾邮件） 攻击：

* 很难区分垃圾邮件和正常邮件。

反垃圾(Anti-Spam)