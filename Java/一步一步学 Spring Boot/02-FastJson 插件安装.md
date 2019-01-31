---
id: 1548922842
title: 02-FastJson 插件安装
date: 2019-01-31 16:20:42
---

## 参考资料

项目地址：https://github.com/alibaba/fastjson

maven地址：https://mvnrepository.com/artifact/com.alibaba/fastjson

```xml
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>fastjson</artifactId>
    <version>1.2.56</version>
</dependency>
```

## 配置

```java
package com.example.api.config;

import com.alibaba.fastjson.serializer.SerializerFeature;
import com.alibaba.fastjson.support.config.FastJsonConfig;
import com.alibaba.fastjson.support.spring.FastJsonHttpMessageConverter;
import org.springframework.context.annotation.Configuration;
import org.springframework.http.converter.HttpMessageConverter;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

import java.util.List;
/**
 * WebMvcConfigurerImpl
 *
 * @author Where
 * @date 2019-01-31
 */
@Configuration
public class WebMvcConfigurerImpl implements WebMvcConfigurer {
    @Override
    public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {
        FastJsonHttpMessageConverter converter = new FastJsonHttpMessageConverter();
        FastJsonConfig config = new FastJsonConfig();
        config.setSerializerFeatures(
                SerializerFeature.WriteMapNullValue
        );
        converter.setFastJsonConfig(config);
        converters.add(0, converter);
    }
}

```

