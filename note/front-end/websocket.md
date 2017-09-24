# WebSocket

双向通信


轮询（polling）和Comet技术。

tomcat 7
注意：需要拷贝Tomcat7目录下的catalina.jar和tomcat-coyote.jar，在部署时，需要删除程序目录下的catalina.jar，否则会导致servlet加载不成功。

首先，spring4的这个demo已经完全没有xml配置文件了，连web.xml都木有了，这是spring的一个推荐风格。

用nginx做反向代理的需要注意啦，socket请求需要做特殊配置的，切记！

Tomcat的处理方式建议修改为NIO的方式，同时修改连接数到合适的参数，请自行Google！

<dependency>
            <groupId>javax.websocket</groupId>
            <artifactId>javax.websocket-api</artifactId>
            <version>1.1</version>
        </dependency>

websocket协议中有一些子协议，可以从更高的层次实现编程模型，就像我们使用HTTP而不是TCP一样。这些子协议有STOMP,WAMP等。


第一步就是选择一个消息的格式。有许多简单消息协议诸如STOMP，MQTT和WAMP。这些都适合应用于网页客户端，并为基本的消息模式提供支持。我们选择了STOMP，因为它的消息格式是基于HTTP模块化的，同时它也能被广泛的支持。然而，我们的处理模块并没有过分依赖于STOMP，这个处理模块也能被扩展成支持其他简单协议。

Web Socket 可以穿越防火墙
websocket使用标准的80和443端口，这两个端口都是防火墙的友好端口所以不需要防火墙的允许。


1 TOMCAT从7.0.27开始支持WEBSOCKET,本例是在TOMCAT7.0.32下开发的
2 目前谷歌、火狐、360急速、IE9（未测试过）都支持WEBSOCKET


http://www.cnblogs.com/ylbtech/p/3344027.html
群数据库设计

http://www.th7.cn/db/mssql/201405/53897.shtml
至"http://www.miitbeian.gov.cn/"。例