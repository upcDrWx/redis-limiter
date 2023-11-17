# redis-limiter
基于 Redis + Lua 结合自定义注解实现后端接口限流

## 介绍
redis-limiter 是一个使用 Redis + Lua + AOP 结合自定义注解实现的后端接口限流器，可根据自定义 key、IP、请求处理的方法名 三种限流方式。

redis-limiter 可以任意集成到需要接口限流的项目中。

## 文件说明
**Limit**：自定义注解，主要包括注解的名字、key、给定的时间范围、最多访问次数、限流的类型；

**LimitType**：限流类型；

**RedisLimiterHelper**：Redis 配置类；

**LimitInterceptor**：限流切面实现，拦截有 @Limit 注解的方法，根据限流类型确定 Redis 的 key，并执行限流的 Lua 脚本；

**LimiterController**：测试的 Controller 类，分别测试自定义 key、IP、请求处理的方法名，三种限流方式；

**application.properties**：配置文件，需要配置 Redis 访问地址。

## 运行测试
1. 克隆项目到本地
```
git clone https://github.com/upcDrWx/redis-limiter.git
```
2. 修改配置文件**application.properties**
```
spring.redis.host = 自己Redis地址
```
3. 启动类启动测试

## 说明
项目仅供个人学习使用。
