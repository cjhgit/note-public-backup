写这篇教程，目的是

2. 熟悉 gradle














使用IntelliJ IDEA，gradle开发Java web应用步骤

















2 编写第一个构建脚本
新建一个文件build.gradle，然后添加以下代码：

```
task hello {  
    doLast {  
        println 'Hello, Gradle!'  
    }  
}  
```


这是本系列文章里的第一个构建脚本，它定义了一个叫hello的task，task的内容是在最后打印出“Hello, Gradle!”。
我们输入命令gradle hello来执行它：



```plain
msdx@msdx-ubuntu:~/tmp$ gradle hello  
:hello  
Hello, Gradle!  
  
BUILD SUCCESSFUL  
```

```
gradle hello

> Task :hello
Hello, Gradle!


BUILD SUCCESSFUL in 0s
1 actionable task: 1 executed
```


















# Web

build.gradle








修改环境变量重启cmd






适配渠道包






修改桌面文件夹路径











导入：

File – New – Module from Existing Sources… 选择你的eclipse项目，next

选择项目路径，next，next

选择 JDK，finish











