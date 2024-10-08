---
cards-deck: Default
createAt: 2022-03-07 18:02
draft: false
publish: true
title: "\u8E29\u5751\u65E5\u8BB0-\u65E0\u6CD5\u542F\u52A8spring\u9879\u76EE"
updateAt: 2022-03-07 18:02:31
---
tags: #java/springboot #踩坑 


```java
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v2.5.9)

2022-03-07 18:00:32.261  INFO 23176 --- [           main] c.a.n.c.c.impl.LocalConfigInfoProcessor  : LOCAL_SNAPSHOT_PATH:C:\Users\admin\nacos\config
2022-03-07 18:00:32.285  INFO 23176 --- [           main] c.a.nacos.client.config.impl.Limiter     : limitTime:5.0
2022-03-07 18:00:32.311  INFO 23176 --- [           main] c.a.nacos.client.config.utils.JvmUtil    : isMultiInstance:false
2022-03-07 18:00:32.314 DEBUG 23176 --- [           main] o.s.boot.env.OriginTrackedYamlLoader     : Loading from YAML: Byte array resource [base-service]
2022-03-07 18:00:32.318 DEBUG 23176 --- [           main] o.s.boot.env.OriginTrackedYamlLoader     : Merging document (no matchers set): {server={port=7090}, spring={application={name=base-service}, cloud={nacos={discovery={server-addr=10.32.132.61:8848, namespace=social-governance, ip=10.32.132.61}}}, servlet={multipart={enabled=true, max-file-size=10MB, max-request-size=100MB}}, datasource={dynamic={datasource={master={driver-class-name=org.postgresql.Driver, url=jdbc:postgresql://10.32.132.61:5432/postgis001?currentSchema=base, username=postgres, password=123456}}}}, redis={host=10.32.132.66, port=6379, password=123456, database=5, timeout=1000}}, pagehelper={reasonable=true, support-methods-arguments=false, offset-as-page-num=false, params=count=countSql, row-bounds-with-count=false}, mybatis-plus={mapper-locations=classpath:mapper/*.xml, log-impl=org.apache.ibatis.logging.stdout.StdOutImpl}, management={endpoints={web={exposure={include=*}}}, endpoint={health={show-details=always}}}, logging={config=classpath:logback.xml}, swagger={enabled=true, title=基础服务, description=基础服务_接口文档, contactName=test, version=2.0}}
2022-03-07 18:00:32.318 DEBUG 23176 --- [           main] o.s.boot.env.OriginTrackedYamlLoader     : Loaded 1 document from YAML resource: Byte array resource [base-service]
2022-03-07 18:00:32.323  WARN 23176 --- [           main] c.a.c.n.c.NacosPropertySourceBuilder     : Ignore the empty nacos configuration and get it based on dataId[base-service.yml] & group[DEFAULT_GROUP]
2022-03-07 18:00:32.326  WARN 23176 --- [           main] c.a.c.n.c.NacosPropertySourceBuilder     : Ignore the empty nacos configuration and get it based on dataId[base-service-dev.yml] & group[DEFAULT_GROUP]
2022-03-07 18:00:32.326  INFO 23176 --- [           main] b.c.PropertySourceBootstrapConfiguration : Located property source: [BootstrapPropertySource {name='bootstrapProperties-base-service-dev.yml,DEFAULT_GROUP'}, BootstrapPropertySource {name='bootstrapProperties-base-service.yml,DEFAULT_GROUP'}, BootstrapPropertySource {name='bootstrapProperties-base-service,DEFAULT_GROUP'}]
三月 07, 2022 6:00:33 下午 org.apache.coyote.AbstractProtocol init
信息: Initializing ProtocolHandler ["http-nio-7090"]
三月 07, 2022 6:00:33 下午 org.apache.catalina.core.StandardService startInternal
信息: Starting service [Tomcat]
三月 07, 2022 6:00:33 下午 org.apache.catalina.core.StandardEngine startInternal
信息: Starting Servlet engine: [Apache Tomcat/9.0.56]
三月 07, 2022 6:00:34 下午 org.apache.catalina.core.ApplicationContext log
信息: Initializing Spring embedded WebApplicationContext
三月 07, 2022 6:00:35 下午 org.apache.catalina.core.StandardService stopInternal
信息: Stopping service [Tomcat]
Disconnected from the target VM, address: '127.0.0.1:65465', transport: 'socket'
```


只有```信息: Stopping service [Tomcat]``` 没有其他报错信息。如何排查。

## 抓取错误
实际上这个就是Java的main方法报错了，导致了tomcat停止了，只需要try catch下main方法的异常就能知道为什么停止了。

```
@SpringBootApplication  
@EnableScheduling  
public class DemoApplication {  
  
    public static void main(String[] args) {  
        try {  
            SpringApplication.run(DemoApplication.class, args);  
        } catch (Exception e) {  
            System.out.println("Application startup failed "+e.getMessage());  
        }  
    }  
  
}
```
![Pasted_image_20220307180644.png](/images/Pasted_image_20220307180644.png)

没有加数据库驱动导致的。