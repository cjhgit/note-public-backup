# REST

[TOC]


[RESTful实践：如何设计API的错误消息](http://my.oschina.net/foxty/blog/382344)




## REST的优点
 
*   可以利用缓存来提高响应速度。
*   通讯本身的无状态性可以让不同的服务器的处理一系列请求中的不同请求，提高服务器的扩展性
*   浏览器即可作为客户端，简化软件需求
*   相对于其他叠加在HTTP协议之上的机制，REST的软件依赖性更小
*   不需要额外的资源发现机制
*   在软件技术演进中的长期的兼容性更好
 
 
[RESTful API 设计指南](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)
 
[为啥REST如此重要？](http://www.csdn.net/article/2013-08-01/2816424-Why-REST-is-so-important)
 
[RESTful API 设计最佳实践](http://blog.jobbole.com/41233/)

[RESTful实践：如何设计API的错误消息](http://my.oschina.net/foxty/blog/382344?fromerr=smgnuNyZ)

## 其他

http://localhost:8080/Spring-MVC-REST/rest/user/1.json (返回json格式)

http://localhost:8080/Spring-MVC-REST/rest/user/1.xml (返回xml格式)



 
为了将总数发给客户端，使用订制的HTTP头： X-Total-Count.
 
链接到下一页或上一页可以在HTTP头的link规定，遵循Link规定:
 
Link: <https://blog.mwaysolutions.com/sample/api/v1/cars?offset=15&limit=5>; rel="next",
<https://blog.mwaysolutions.com/sample/api/v1/cars?offset=50&limit=3>; rel="last",
<https://blog.mwaysolutions.com/sample/api/v1/cars?offset=0&limit=5>; rel="first",
<https://blog.mwaysolutions.com/sample/api/v1/cars?offset=5&limit=5>; rel="prev",



-- Web --
推荐随便搞！可以用重量级的AngularJS，也可以用轻量级 Backbone + jQuery 等。

-- Server --
推荐： Spring MVC 或者 Jersey 或者 Play Framework

-- Android --
推荐： RetroFit ( Retrofit ) 或者 Volley ( mcxiaoke/android-volley · GitHub Google官方的被block，就不贴了 ) 

增删改查都是一个地址，具体靠http头部信息判断。

把 github API v3 看一遍就好了

底层的集合实际上是空的情况下，返回长度是0的集合或者是数组，不要返回null。