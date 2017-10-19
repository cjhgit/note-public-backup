人性的弱点

在李善友教授看来，他相信世界上存在数量稀少但足可信赖的“第一性原理”，它们像数学公理一样，应该构成我们理解世界的基本起点。

蚊子

图片压缩
https://tinypng.com/


保存聊天记录

http://readium.org/

http://www.cnblogs.com/diligenceday/p/5185716.html

epub Github

epub.js

https://github.com/futurepress/epub.js

node.js epub reader
https://github.com/julien-c/epub

整理文件：

Cordova


https://github.com/kezzbracey/postcss-bem

@component-namespace mint {
    @component actionsheet {
      position: fixed;
      background: #e0e0e0;
      width: 100%;
      text-align: center;
      bottom: 0;
      left: 50%;
      transform: translate3d(-50%, 0, 0);
      backface-visibility: hidden;
      transition: transform .3s ease-out;


vi /etc/nginx/nginx.conf

mkdir /etc/nginx/vhost



/usr/sbin/nginx -s reload

service nginx restart




include /etc/nginx/vhost/*;

# vi /etc/nginx/vhost/jianan-front


server {
    listen 80;
    server_name canalifecare.com;
	location / {
 		proxy_pass http://localhost:9983;
	}
}


/usr/sbin/nginx -c /etc/nginx/nginx.conf

/usr/sbin/nginx-----------文件

重启指令：./nginx  -s  reload  



---------------配置文件目录：/etc/nginx/conf.d/default.conf-----------------



server  {
        listen  80;
        server_name  develop.liangchuantech.com;
        location  /  {
                root  /usr/local/nginx-app/coolkeke-front;
                try_files  $uri  $uri/  /index.html;
        }
}