maven 地址：
https://mvnrepository.com/artifact/org.mybatis.spring.boot/mybatis-spring-boot-starter
https://mvnrepository.com/artifact/tk.mybatis/mapper-spring-boot-starter

项目地址：
https://github.com/abel533/Mapper

一个可参考的项目
https://github.com/435242634/Spring-Boot-Demo

```xml
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>1.3.2</version>
</dependency>
<dependency>
    <groupId>tk.mybatis</groupId>
    <artifactId>mapper-spring-boot-starter</artifactId>
    <version>2.0.4</version>
</dependency>
```

mybatis 配置

```ini
# 在resources/application.properties下配置
mybatis.type-aliases-package=com.demo.api.mapper
mybatis.mapper-locations=classpath:mapper/*.xml
```

tk.mybatis 配置

```java
package com.demo.api.mapper;

import com.demo.model.Admin;
import org.springframework.stereotype.Repository;
import tk.mybatis.mapper.common.Mapper;

@Repository
public interface AdminMapper extends Mapper<Admin> {
    Integer count();
}
```