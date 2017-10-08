

## IDEA 创建 Spring boot 项目

* Open IDEA，choose "New-->Project"
* Choose "Spring Initializr"，next
* next
* Choose "Web"，next。
* 填写项目名称，选择项目位置，finish。
* 新建 `HelloController` 类（见后面）。
* 浏览器打开 `http://localhost:8080/hello`，显示 hello world。


```java
package com.example.demo.controller;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
    @RequestMapping("hello")
    public String index() {
        return "hello world";
    }
}
```

## 热部署

1、加maven依赖

```xml
<dependency>
	<!--Spring 官方提供的热部署插件 -->
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-devtools</artifactId>
	<optional>true</optional>
</dependency>
```
        
2、开启热部署

```xml
<plugin>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-maven-plugin</artifactId>
	<configuration>
		<fork>true</fork>
	</configuration>
</plugin>
···
            