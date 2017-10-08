# Nginx

> Nginx是俄罗斯人编写的十分轻量级的HTTP服务器,Nginx，它的发音为“engine X”， 是一个高性能的HTTP和反向代理服务器，同时也是一个IMAP/POP3/SMTP 代理服务器．Nginx是由俄罗斯人 Igor Sysoev为俄罗斯访问量第二的 Rambler.ru站点开发.
  
> Nginx以事件驱动的方式编写，所以有非常好的性能，同时也是一个非常高效的反向代理、负载平衡。其拥有匹配 Lighttpd的性能，同时还没有Lighttpd的内存泄漏问题，而且Lighttpd的mod_proxy也有一些问题并且很久没有更新。但是Nginx并不支持cgi方式运行，原因是可以减少因此带来的一些程序上的漏洞。所以必须使用FastCGI方式来执行PHP程序。

## 安装（Windows）

进入下载页面：http://nginx.org/en/download.html。

点击（如【nginx/Windows-1.13.5】）下载最新的安装包，解压即可。

运行 `nginx.exe` （即 `nginx -c conf\nginx.conf`）启动 Nginx。

浏览器打开 `http://localhost`，网页显示“Welcome to nginx!”。

解压目录下执行 `nginx -s stop` 可关闭 Nginx。

## 其他

配置文件：`conf\nginx.conf`。

查看版本：

```
$ nginx -V
nginx version: nginx/1.13.5
...
```

## 安装（Linux）


