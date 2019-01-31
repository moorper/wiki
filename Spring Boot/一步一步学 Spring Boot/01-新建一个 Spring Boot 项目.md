---
id: 1548840928
title: 01-新建一个 Spring Boot 项目
date: 2019-01-30 17:35:28
---

#  01-新建一个 Spring Boot 项目



## 参考资料

* [Spring Boot 官网](https://spring.io/projects/spring-boot)

* 本项目所有代码示例：[Demo](https://github.com/moorper/example/tree/master/Spring%20Boot)

* 代码风格指导：[《码出高效：Java 开发手册》](https://github.com/alibaba/p3c/blob/master/%E9%98%BF%E9%87%8C%E5%B7%B4%E5%B7%B4Java%E5%BC%80%E5%8F%91%E6%89%8B%E5%86%8C%EF%BC%88%E8%AF%A6%E5%B0%BD%E7%89%88%EF%BC%89.pdf) by [alibaba/p3c](https://github.com/alibaba/p3c)

## 新建一个空的 Maven 项目

可以使用 [Eclipse][eclipse] / [Intellij IDEA][jetbrains]

## 编辑 `pom.xml` 文件

```xml
<properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>
    </properties>
    <!-- https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-parent -->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.2.RELEASE</version>
    </parent>
    <dependencies>
        <!-- https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-web -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <version>2.1.2.RELEASE</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-test -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <version>2.1.2.RELEASE</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
    <repositories>
        <repository>
            <id>spring-releases</id>
            <url>https://repo.spring.io/libs-release</url>
        </repository>
    </repositories>
```

## 新建一个 `Package`

在`src/main/java`下新建`com.example.api` Package

## 添加启动类 `Application.java`

```java
package com.example.api;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

/**
 * Application
 * 
 * @author Where
 * @date 2019-01-31
 */
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class,args);
    }
}
```

## 创建 `IndexController.java` 控制器文件

IndexController.java

```java
package com.example.api.controller;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;

/**
 * IndexController
 *
 * @author Where
 * @date 2019-01-31
 */
@RestController
@RequestMapping(produces = "application/json; charset=utf-8")
public class IndexController {
    @RequestMapping(value = "/ping", method = RequestMethod.GET)
    public String ping() {
        return "pong";
    }
}
```



运行 `Application.java` 项目创建成功



[eclipse]: https://www.eclipse.org
[jetbrains]: https://www.jetbrains.com/idea/download/

