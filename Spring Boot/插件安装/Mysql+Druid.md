maven 代码库：

https://mvnrepository.com/artifact/mysql/mysql-connector-java

https://mvnrepository.com/artifact/com.alibaba/druid-spring-boot-starter

配置参考：

https://github.com/alibaba/druid/tree/master/druid-spring-boot-starter

```xml
       <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid-spring-boot-starter</artifactId>
            <version>1.1.10</version>
        </dependency>
```



```ini
### MySQL 连接信息
spring.datasource.url=jdbc:mysql://localhost:3306/database
spring.datasource.username=username
spring.datasource.password=password
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
### 数据源类别
spring.datasource.type=com.alibaba.druid.pool.DruidDataSource
### 初始化大小，最小，最大
spring.datasource.druid.initial-size=5
spring.datasource.druid.min-idle=10
spring.datasource.druid.max-active=20
### 配置获取连接等待超时的时间，单位是毫秒
spring.datasource.druid.max-wait=60000
### 打开PSCache，并且指定每个连接上PSCache的大小
spring.datasource.druid.pool-prepared-statements=true
spring.datasource.druid.max-pool-prepared-statement-per-connection-size=20
spring.datasource.druid.validation-query=show status like '%Service_Status%'
spring.datasource.druid.validation-query-timeout=30
spring.datasource.druid.test-on-borrow=false
spring.datasource.druid.test-on-return=false
spring.datasource.druid.test-while-idle=true
### 配置间隔多久才进行一次检测，检测需要关闭的空闲连接，单位是毫秒
spring.datasource.druid.time-between-eviction-runs-millis=2000
### 配置一个连接在池中最小生存的时间，单位是毫秒
spring.datasource.druid.min-evictable-idle-time-millis=300000
spring.datasource.druid.max-evictable-idle-time-millis=900000
### 配置监控统计拦截的filters，去掉后监控界面sql无法统计，'wall'用于防火墙
spring.datasource.druid.filters=stat,wall,config
### 合并多个 DruidDateSource 的监控数据
spring.datasource.druid.use-global-data-source-stat=true
### 通过connectProperties属性来打开mergeSql功能；慢SQL记录
spring.datasource.druid.connection-properties=druid.stat.mergeSql=true;druid.stat.slowSqlMillis=5000
```