# Java web 学习笔记 - 创建简单的 web 项目

## 相关软件

* Intellij Idea 2017.1.3
* JDK 1.8.0
* Tomcat 8.15.5

## 创建项目

第零步，菜单【File】->【New】->【Project】。选择【Java】，勾选【Web Application】，点击【Next】按钮。

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/javaee-demo-1-0.png)

第一步，输入项目名和项目地址，点击【Finish】按钮。

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/javaee-demo-1-0-1.png)

创建的项目结构如下：

![](http://www.chenjianhang.com/wp-content/uploads/2017/08/javaweb-demo-1-2.png)

第二步，双击打开 `index.jsp` 文件，修改成以下内容。

```html
<html>
<head>
    <meta charset="utf-8">
</head>
<body>
Hello World
</body>
</html>
```

第三步，配置 Tomcat。

点击菜单【Run】->【Edit Configurations】，在弹出的界面找到【Defaults】->【Tomcat Server】->【Local】，进行 Tomcat 相关的配置。

第四步，点击【Run】按钮，浏览器会自动打开一个页面。页面上显示“Hello World”。

附：[项目源码下载](https://github.com/cjhgit/javaweb-demos/blob/master/javaweb-demo.zip?raw=true)














## 参考

http://blog.csdn.net/wangyang1354/article/details/50452806