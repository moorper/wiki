## 安装
需要屏蔽 Spring Boot 自带的 Log 工具
pom.xml
```xml
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <exclusions>
                <exclusion>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-starter-logging</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
<!-- https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-log4j2 -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-log4j2</artifactId>
        </dependency>
```
## 配置
新建 `resources/log4j2.xml` 文件，在 `application.properties` 中配置：
```ini
logging.config=classpath:log4j2.xml
```
这里有一个官方的配置参考：[https://logging.apache.org/log4j/2.x/manual/configuration.html#XML](https://logging.apache.org/log4j/2.x/manual/configuration.html#XML)