
androidpn-server-bin-tomcat：
2、修改resources/jdbc.properties配置文件
    主要修改数据库名，账户名和密码
3、查看WebRoot/WEB-INF/dispatcher-servlet.xml配置文件 ？？
4、访问地址为；http://localhost:8080/ 端口号为tomcat所使用的端口号

新功能：
androidpn-server
新添加了两个接口：
package org.androidpn.server.console.api;
UserApiController.java 用于获取用户列表，并返回json数据；
NotificationApiController.java 用户消息推送


WebRoot/WEB-INF/dispatcher-servlet.xml文件更新
添加了
/user_api.do=userapiController  
/notification_api.do=notificationapiController

为防止别人恶意用网页群发消息推送，以下可隐藏      
/index.do=filenameController
/user.do=userController
/session.do=sessionController
/notification.do=notificationController 

androidpn服务器收到消息后如何知道要发给哪个用户？
在XmppManager.java类文件里，有这样一行代码：

finalString newUsername = newRandomUUID();

我们只需要把newRandomUUID() 改成用户的名称，如zhangsan，这样，我们的服务器在发消息给androidpn服务器时，就可以指定说要发给zhangsan,这样就行了。

不过我也发现了一点，这个用户名在第一次与服务器端连接时，服务器端就记下来了，后面你再改是不管用的。 