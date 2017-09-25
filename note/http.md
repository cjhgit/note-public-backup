# HTTP

HTTP（Hyper Text Transfer Protocol，超文本传输协议）


RFC 2616 定义了 HTTP 1.1。

[HTTP 1.1 标准文档](http://www.ietf.org/rfc/rfc2616.txt)

HTTP/2 的 RFC 编号为 7540，[RFC 7540](http://www.ietf.org/rfc/rfc7540.txt)


```text
Query String Parameters
openId=asas&personName=%E5%A7%93%E5%90%8D&sex=%E5%85%88%E7%94%9F&phoneNum=1256&detailAddress=XX%E5%B8%82XX%E5%8C%BAXX%E8%B7%AFXX%E5%B9%BF%E5%9C%BAXX%E5%AE%A4&houseNumberInformation=%E9%97%A8%E7%89%8C%E4%BF%A1%E6%81%AF&isContain=true
```

HTTPS（Hyper Text Transfer Protocol over Secure Socket Layer），安全版的 HTTP。


## 请求

HTTP 请求由三个部分组成：请求行、消息报头、请求正文

### 请求行

格式：

```text
Method Request-URI HTTP-Version CRLF
```

示例：

```text
POST /index.html HTTP/ (CRLF)
```

GET 请求
GET 请求的请求数据以 name=value&name2=value2 的形式附到 URL 的后面，而 POST 请求的请求数据是放在请求体中，内容也是 name=value&name2=value2 的形式。

POST 请求的 `Content-Type` 是 `application/x-www-form-urlencoded`


### 消息报头

#### 请求报头

request headers

User-Agent：用户代理（含有用户操作系统和浏览器信息的文本）
Content-Type：
Cookie：Cookie。

## 相应

HTTP 相应由三个部分组成：状态行、消息报头、响应正文

### 状态行

## 消息报头

#### 响应报头




Content-Type:application/json;charset=UTF-8

Request Payload
{"name":"测试","phone":"1563333","email":"as@qq.com","gender":1,"status":1,"time":"2017-09-07  00:00:00"}


## 其他

【控制面板】->【程序】->【启用或关闭 Windows 功能】，勾选【Telnet 客户端】，点击【确定】。

打开 cmd，执行 `telnet`

set localecho // 启用本地回显

open www.baidu.com 80

# TODO

* HTTP 2.0





Access-Control-Allow-Origin
