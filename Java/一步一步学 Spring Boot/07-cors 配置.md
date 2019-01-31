---
id: 1548925777
title: 07-cors 配置
date: 2019-01-31 17:09:37
---

## 配置

编辑之前的配置文件：`src/main/java/com/example/api/config/WebMvcConfigurerImpl.java`

```java
package com.example.api.config;

import com.alibaba.fastjson.serializer.SerializerFeature;
import com.alibaba.fastjson.support.config.FastJsonConfig;
import com.alibaba.fastjson.support.spring.FastJsonHttpMessageConverter;
import org.springframework.context.annotation.Configuration;
import org.springframework.http.converter.HttpMessageConverter;
import org.springframework.web.servlet.config.annotation.CorsRegistry;
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
    /**
     * 配置 FastJson
     *
     * @param converters
     */
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

    /**
     * 配置跨域请求
     *
     * @param registry
     */
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
                .allowedOrigins("*")
                .allowedMethods("*")
                .allowedHeaders(("*"))
                .allowCredentials(true)
                .maxAge(3600L);
    }
}

```

