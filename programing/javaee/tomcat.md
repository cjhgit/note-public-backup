# Tomcat

启动tomcat8w.exe出现错误 Unable to open the Service 'tomcat8'

Tomcat:Can't load IA 32-bit .dll on a AMD 64-bit platform问题的解决



19-Aug-2017 14:21:38.534 警告 [main] org.apache.catalina.core.AprLifecycleListener.init The APR based Apache Tomcat Native library failed to load. The error reported was [G:\install\tomcat-8.5.15\bin\tcnative-1.dll: Can't load AMD 64-bit .dll on a IA 32-bit platform]
 java.lang.UnsatisfiedLinkError: G:\install\tomcat-8.5.15\bin\tcnative-1.dll: Can't load AMD 64-bit .dll on a IA 32-bit platform



文章配图参考
https://segmentfault.com/a/1190000007090110

1. 【Run】->【Edit Configurations】，在【Default】->【Tomcat Server】->【Local】。
2. 点击【Configuration】按钮，选择 Tomcat 安装目录。
3. 确定





https://github.com/ruanyf/es6tutorial



## Tomcat
下载解压：http://mirror.bit.edu.cn/apache/tomcat/

设置默认项目：
方法一：将项目拷贝到webapps下，并将项目名称改为ROOT； 
方法二：设置虚拟路径。修改tomcat/conf/server.xml的Context配置项&lt;Context path="" debug="0" docBase="你项目的决定路径" reloadable="true"&gt;&lt;/Context&gt;。并且删除webapps下的ROOT目录




<Connector port="8080" protocol="HTTP/1.1"
connectionTimeout="20000"
               redirectPort="8443" URIEncoding="UTF-8"/>


【Tomcat安装】
*创建CATALINA_HOME环境变量指向Tomcat安装路径
*启动：安装路径\bin\startup.bat
*测试：把刚才准备好的test.jsp放在 安装路径\webapps\examples\jsp目录下, 在地址栏中输入http://localhost:8080/examples/jsp/test.jsp，如果浏览器中显示"Hello World！"，则说明你的JSP环境配置成功了！
 

 
【在MyEclipse中配置JDK】
*preferences->java->installed JREs
*add
*选择standard VM
*选择F:\java\jre，点击完成
*返回Preferences，将刚刚配置的JRE选中
 
 
【myEclipse配置tomcat服务器】
*菜单window->preferences->servers->tomcat
*选择当前tomcat版本
*选择enable
*选择tomcat安装目录

*window->preferences->servers->tomcat->tomcat x.x->jdk，选择之前配置的JDK（java，找不到则重新打开preferences）
 
 
eclipse下设置tomcat,修改Java代码不必重启tomcat：
*点击Servers（下面的Tab）
*双击tomcat
*设置server.xml中的reloadable=true(自动重载)
*使用Debug模式,前提是仅限于局部修改。(修改类不用重启--热加载)
 
第一步：
 
Tomcat安装目录下，修改 conf/server.xml 中的 Host 配置，设置其reloadable属性为true，即在Host标签中添加reloadable="true"这一句，重启Tomcat使配置文件生效。
 
第二步：
 
在conf文件夹中的web.xml文件中添加
 
<init-param>
<param-name>development</param-name>
<param-value>true</param-value>
</init-param>


【Tomcat安装】 *创建CATALINA_HOME环境变量指向Tomcat安装路径 *启动：安装路径\bin\startup.bat *测试：把刚才准备好的test.jsp放在 安装路径\webapps\examples\jsp目录下, 在地址栏中输入http://localhost:8080/examples/jsp/test.jsp，如果浏览器中显示”Hello World！”，则说明你的JSP环境配置成功了！ 【配置java环境变量】 *JAVA_HOME：F:\java\jdk *PATH：F:\java\jdk\bin *CLASSPATH：.;%JAVA_HOME%\lib \tools.jar;%JAVA_HOME%\lib\dt.jar;，注意最前面的.不可省略。 *这样配置之后，单击开始菜单—运行—输入cmd—确定，键盘输入java -version（注意java与-之间有一空格）显示出版本信息，则证明配置成功。 【在MyEclipse中配置JDK】 *preferences->java->installed JREs *add *选择standard VM *选择F:\java\jre，点击完成 *返回Preferences，将刚刚配置的JRE选中 【myEclipse配置tomcat服务器】 *菜单window->preferences->servers->tomcat *选择当前tomcat版本 *选择enable *选择tomcat安装目录 *window->preferences->servers->intergrated sandbox，把myeclipse自带的tomcat取消掉 *window->preferences->servers->tomcat->tomcat x.x->jdk，选择之前配置的JDK（java，找不到则重新打开preferences） 【启动tomcat】 *点击run/restart/stop myeclipse services *选择tomcat->run 【myEclipse部署项目】 *点击deploy…按钮 *选择project与tomcat *重新启动tomcat 用tomcat进行web开发时，修改Java代码往往要重启代码，当工程较大启动较慢时，严重影响效率，本文通过eclipse下tomcat开发和发布web程序时，对一些Java代码一般修改（不是增减方法、变量，或变更名称等“较巨大”的操作），可以不必重启机器的设置 eclipse下设置tomcat,修改Java代码不必重启tomcat： *点击Servers（下面的Tab） *双击tomcat *设置server.xml中的reloadable=true(自动重载) *使用Debug模式,前提是仅限于局部修改。(修改类不用重启–热加载) 第一步： Tomcat安装目录下，修改 conf/server.xml 中的 Host 配置，设置其reloadable属性为true，即在Host标签中添加reloadable=”true”这一句，重启Tomcat使配置文件生效。 第二步： 在conf文件夹中的web.xml文件中添加 <init-param> <param-name>development</param-name> <param-value>true</param-value> </init-param> 第三步： 重启tomcat服务器，使修改生效。然后在MyEclipse中的servers窗口里，点击图中红圈的按钮（部署新项目到tomcat）。