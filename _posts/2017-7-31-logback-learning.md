---
layout: post
title: java日志神器——logback使用心得
categories: Java
description: java日志神器——logback使用心得
keywords: Java,log
---

最近因为要处理一个非常耗时的事情，于是打日志就是非常重要的事情了。传统的log4j无法把日志分成多部分记录，比如login-error.log只负责登录报错，article-info负责记录所有文章相关的日志。
这时候就要用到logback了。

> Logback是由log4j创始人Ceki Gülcü设计的又一个开源日志组件。

## 浅析

Logback的核心对象：Logger、Appender、Layout

Logger:日志的记录器，把它关联到应用的对应的context上后，主要用于存放日志对象，也可以定义日志类型、级别。Logger对象一般多定义为静态常量。

Appender:用于指定日志输出的目的地，目的地可以是控制台、文件、远程套接字服务器、 MySQL、 PostreSQL、Oracle和其他数据库、 JMS和远程UNIX Syslog守护进程等。

Layout:负责把事件转换成字符串，格式化的日志信息的输出。具体的Layout通配符，可以直接查看帮助文档。

## 具体使用方法

先见一个appender，代表打印到哪个日志。再建一个logger代表打印哪个类里的日志。

```
<!-- 一个只打印error级别的appender，file是文件名，rollingPolicy是历史文件名-->
    <appender name="error" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <Append>true</Append>
        <File>${LOG_PATH}/system-error.log</File>
        <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
            <level>ERROR</level>
        </filter>
        <encoder>
            <pattern>${FILE_LOG_PATTERN}</pattern>
        </encoder>
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <fileNamePattern>${LOG_PATH}/system-error.log.%d{yyyy-MM-dd}</fileNamePattern>
            <maxHistory>7</maxHistory>
        </rollingPolicy>
    </appender>
```

然后添加一个logger

```
    <!-- 所有的error级别level都打到上面规则的文件中 -->
    <logger name="org.springframework" level="error">
        <appender-ref ref="error"/>
    </logger>
```

## 参考资料

[Logback浅析](http://www.cnblogs.com/yongze103/archive/2012/05/05/2484753.html)

[从Log4j迁移到LogBack的理由](http://www.oschina.net/translate/reasons-to-prefer-logbak-over-log4j)