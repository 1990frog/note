<!-- TOC -->

- [具体的日志功能实现](#%E5%85%B7%E4%BD%93%E7%9A%84%E6%97%A5%E5%BF%97%E5%8A%9F%E8%83%BD%E5%AE%9E%E7%8E%B0)
- [日志实现的抽象层（门面与实现的区别）](#%E6%97%A5%E5%BF%97%E5%AE%9E%E7%8E%B0%E7%9A%84%E6%8A%BD%E8%B1%A1%E5%B1%82%E9%97%A8%E9%9D%A2%E4%B8%8E%E5%AE%9E%E7%8E%B0%E7%9A%84%E5%8C%BA%E5%88%AB)
- [日志发展历程](#%E6%97%A5%E5%BF%97%E5%8F%91%E5%B1%95%E5%8E%86%E7%A8%8B)
- [demo](#demo)
- [日志实现寻址](#%E6%97%A5%E5%BF%97%E5%AE%9E%E7%8E%B0%E5%AF%BB%E5%9D%80)
- [springboot配置日志](#springboot%E9%85%8D%E7%BD%AE%E6%97%A5%E5%BF%97)
- [日志使用](#%E6%97%A5%E5%BF%97%E4%BD%BF%E7%94%A8)
- [日志级别](#%E6%97%A5%E5%BF%97%E7%BA%A7%E5%88%AB)
- [日志配置](#%E6%97%A5%E5%BF%97%E9%85%8D%E7%BD%AE)
- [configuration子节点](#configuration%E5%AD%90%E8%8A%82%E7%82%B9)
- [常用pattern介绍](#%E5%B8%B8%E7%94%A8pattern%E4%BB%8B%E7%BB%8D)
- [root&logger](#rootlogger)
- [日志实战](#%E6%97%A5%E5%BF%97%E5%AE%9E%E6%88%98)
- [SiftingAppender](#siftingappender)

<!-- /TOC -->

# 具体的日志功能实现
+ JUL
+ Log4j
+ Logback
+ Log4j2

# 日志实现的抽象层（门面与实现的区别）
+ JCL
+ SLF4J（最优）

# 日志发展历程
+ JDK1.3及以前，通过System.(out|err).println打印，存在巨大的缺陷
+ log4j作者推出slf4j，功能完善兼容性好，成为业界主流
+ log4j作者在推出log4j后进行新的改进思考推出logback
+ log4j2是apache对log4j的重大升级，修复已知缺陷，极大提升性能
+ 最佳组合：slf4j+logback（springboot使用）

# demo
```
private Logger logger = LoggerFactory.getLogger(xxx.class);
等价于
@Slf4j
```
# 日志实现寻址
+ LoggerFactory.getLogger
+ findPossibleStaticLoggerBinderPathSet
+ 获取StaticLoggerBinder所在jar包途径
+ 若存在多个日志实现框架打印提示及选择
+ 使用StaticLoggerBinder获得日志工厂再嘚实现

# springboot配置日志
spring-boot-starter-logging
+ logback-classic
+ log4j-to-slf4j
+ jul-to-slf4j

# 日志使用
Logger logger = LoggerFactory.getLogger(xx.clas)
logger.level()
官方推荐使用占位符的方式：
logger.debgug("xyzP {} is {}",i,j)

# 日志级别
+ ERROR
+ WARN
+ INFO
+ DEBUG
+ TRACE

# 日志配置
```
<configuration scan="true" scanPeriod="60 seconds" debug="false"/>
```
+ scan：当设置为true时，配置文件若发生改变，将会重新加载
+ scanPeriod：扫描时间间隔，若没给出时间单位默认为毫秒
+ debug：若设置为true，将打印出logback内部日志信息

# configuration子节点
+ contextName：上下文名称
+ property：属性配置
+ appender：格式化日志输出
+ root：全局日志输出设置
+ logger：具体包或子类输出设置

# 常用pattern介绍
+ logger{length}:输出日志的logger名，可有一个整形参数，功能是缩短logger名
+ contextName|cn：上下文名称
+ date{pattern}：输出日志的打印时间，模式语法与java.text.SimpleDateFormat兼容
+ p/le/level：日志级别
+ M/method：输出日志的方法名
+ r/relative：从程序启动到创建日志记录的时间
+ m/msg/message：程序提供的信息
+ n：换行符

# root&logger
+ root全局
+ logger是指定

# 日志实战
结合切面

aopstarter
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-aop</artifactId>
</dependency>
```

@AfterThrowing(pointcut = "@within()")
@AfterThrowing(pointcut = "within()")



首先，官方推荐使用的xml名字的格式为：logback-spring.xml而不是logback.xml，至于为什么，因为带spring后缀的可以使用<springProfile>这个标签。

在resource下创建logback-spring.xml文件

# SiftingAppender
Logback将写日志事件的任务委托给appender组件完成，SiftingAppender顾名思义就是筛选日志事件
对于Logback委托给它的日志事件，SiftingAppender会对日志事件做一些区分，然后不同的事件SiftingAppender会委托不同的appender去完成真正的写操作。
