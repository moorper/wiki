---
id: 1548924089
title: 06-Mybatis 插件安装
date: 2019-01-31 16:41:29
---

## 配置参考

* Maven 仓库：https://mvnrepository.com/artifact/org.mybatis.spring.boot/mybatis-spring-boot-starter
* jdbyType 参考：http://www.mybatis.org/mybatis-3/apidocs/reference/org/apache/ibatis/type/JdbcType.html

## `pom.xml`

```xml
<!-- https://mvnrepository.com/artifact/org.mybatis.spring.boot/mybatis-spring-boot-starter -->
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>2.0.0</version>
</dependency>
```

## 配置

`resources/application.properties`

```ini
# mybatis
mybatis.type-aliases-package=com.example.api.mapper
mybatis.mapper-locations=classpath:mapper/*.xml
```

## 使用

新建文件：`src/main/java/com/example/api/mapper/UserMapper.java`

```java
package com.example.api.mapper;

import com.example.api.model.domain.UserDO;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;
import org.springframework.stereotype.Component;

import java.util.List;

/**
 * UserMapper
 *
 * @author Where
 * @date 2019-01-31
 */
@Component
@Mapper
public interface UserMapper {
    /**
     * 获取用户列表
     *
     * @return
     */
    List<UserDO> list();

    /**
     * 统计当前用户数量
     *
     * @return
     */
    @Select("SELECT COUNT(*) FROM USER")
    Integer count();
}
```

新建文件：`src/main/resources/mapper/UserMapper.xml`

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >
<mapper namespace="com.example.api.mapper.UserMapper">
    <resultMap id="UserDO" type="com.example.api.model.domain.UserDO">
        <id column="id" property="id" jdbcType="INTEGER"/>
        <result column="username" property="username" jdbcType="VARCHAR"/>
        <result column="password" property="password" jdbcType="VARCHAR"/>
        <result column="created_at" property="createdAt" jdbcType="TIMESTAMP"/>
        <result column="updated_at" property="updatedAt" jdbcType="TIMESTAMP"/>
        <result column="deleted_at" property="deletedAt" jdbcType="TIMESTAMP"/>
    </resultMap>
    <select id="list" resultMap="UserDO" resultType="list">
        SELECT * FROM USER
    </select>
</mapper>
```

然后，可以在`controller`，`service`等代码中使用

```java
package com.example.api.controller;

import com.example.api.mapper.UserMapper;
import com.example.api.model.domain.UserDO;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;
/**
 * UserController
 * 
 * @author Where
 * @date 2019-01-31
 */
@RestController
@RequestMapping(value = "/user", produces = "application/json; charset=utf-8")
public class UserController {
    @Autowired
    UserMapper userMapper;

    @RequestMapping(value = "/list", method = RequestMethod.GET)
    public List<UserDO> list() {
        return userMapper.list();
    }
}
```

