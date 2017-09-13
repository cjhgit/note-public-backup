# 环境搭建

## 过程

### 下载JDK

进入[官方下载页面](http://www.oracle.com/technetwork/java/javase/downloads/index.html)，点击【Java DOWNLOAD】。

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/QQ截图20170819110108.png)

选中【Accept License Agreement】，下载 64 位 Windows 安装包。

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/QQ截图20170819110509.png)

或百度云盘下载：[jdk-8u144-windows-x64.exe](http://pan.baidu.com/s/1o8HnAMQ)

默认安装。

### 配置环境变量

我的 JDK 安装目录是 `F:\java\jdk`。

变量名：`JAVA_HOME`，变量值：`F:\java\jdk`
变量名：`CLASSPATH`，变量值：`.;%JAVA_HOME%\lib\tools.jar;%JAVA_HOME%\lib\dt.jar;`（注意最前面的.不可省略）
变量名：`PATH`，变量值中添加：`%JAVA_HOME%\bin`

### 检查

打开 Cmd，输入 `java -version`，显示出版本信息，则说明安装配置成功。

```
java -version
java version "1.8.0_144"
Java(TM) SE Runtime Environment (build 1.8.0_144-b01)
Java HotSpot(TM) 64-Bit Server VM (build 25.144-b01, mixed mode)
```
