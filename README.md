# springCloud-conifgCenter
springcloud分布式配置中心

## 项目目录规范，和配置文件命名规范 

- config项目应该是config-server项目配置的search-paths:
```
###服务注册到eureka地址
eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:58670/eureka/
spring:
  application:
    ####注册中心应用名称
    name: config-server
  cloud:
    config:
      server:
        git:
          ###git环境地址
          uri: https://gitee.com/yushengjun/test_config.git
          ####搜索目录
          search-paths:
            - config
      ####读取分支
      label: master
```
- config目录下的配置文件名称应该是和config-client项目配置中心客户端名称一致，举个栗子
```
spring:
  application:
    name: eureka-client
  cloud:
    config:
      profile: dev
      discovery:
        service-id: config-server
        enabled: true

server:
  port: 58672

eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:58670/eureka/
management:
  endpoints:
    web:
      exposure:
        include: "*"
```
 
