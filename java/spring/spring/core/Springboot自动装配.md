[TOC]


# 前置基础
@bean：指示方法产生一个由Spring容器管理的bean

写个start类，加个@SpringBootApplication注解


# 原理
@Import + @Configuration + Spring spi
+ 自动配置类由各个starter提供，使用@Configuration+@Bean定义配置1类，放到META-INF/spring.factories下
+ 使用Spring spi扫描META-INF/spring.factories下的配置类
+ 使用@Import导入自动配置类

@SpringBootApplication（复合注解）
+ @SpringBootConfiguration：其实就是@Configuration注解
+ @ComponentScan：指定扫描的路径，n个参数
+ @EnableAutoConfiguration 两种方法：
    + @AutoConfigurationPackage，其使用了@Import(AutoConfigurationPackageRegistrar.class)手工注册bean，注册扫描路径到全局变量里面，提供查询
    + @Import(AutoConfigurationImportSelector.class)，它里面有个方法selectImports通过SpringFactoriesLoadFactoryNames加载META-INF/spring.factories中的EnableAutoConfiguration，返回一个字符串数组，其内存储预加载类的全路径，spring读到之后通过反射的方式，将类放到IOC容器，这些类就变成了bean。如果这些bean里面也带有@Configuration+@Bean加载配置，也会完成自动装配









@ComponentScan 属性
    value：指定要扫描的package；
    includeFilters=Filter[]：指定只包含的组件
    excludeFilters=Filter[]：指定需要排除的组件；
    useDefaultFilters=true/false：指定是否需要使用Spring默认的扫描规则：被@Component, @Repository, @Service, @Controller或者已经声明过@Component自定义注解标记的组件；

    在过滤规则Filter中：
    FilterType：指定过滤规则，支持的过滤规则有
        ANNOTATION：按照注解规则，过滤被指定注解标记的类；
        ASSIGNABLE_TYPE：按照给定的类型；
        ASPECTJ：按照ASPECTJ表达式；
        REGEX：按照正则表达式
        CUSTOM：自定义规则；
    value：指定在该规则下过滤的表达式；













----------------------





# 流程
1. @SpringBootApplication注解包含@EnableAutoConfiguration
2. @EnableAutoConfiguration下的@import注解（ImportSelector方式）AutoConfigurationImportSelector


# AutoConfigurationImportSelector
SpringBoot自动配置的核心就在@EnableAutoConfiguration注解上，这个注解通过@Import(AutoConfigurationImportSelector)来完成自动配置

```java
public class AutoConfigurationImportSelector implements DeferredImportSelector, BeanClassLoaderAware,
		ResourceLoaderAware, BeanFactoryAware, EnvironmentAware, Ordered
```

+ DeferredImportSelector：继承了ImportSelector接口，该接口主要是为了导入@Configuration的配置项
+ BeanClassLoaderAware、ResourceLoaderAware、EnvironmentAware：继承了Aware接口，事项了改接口的类可以被Spring感知
+ Ordered：从 Spring 4.0 开始，Spring 中的很多组件都支持基于 Order 注解的排序，但是使用了该注解后，不会影响bean的加载顺序，Bean的加载顺序是由依赖关系和 @DependsOn 注解来决定的。


# Aware感知器
[demo](https://blog.csdn.net/dfBeautifulLive/article/details/123633123)

# Aware
+ Spring框架优点：Bean感知不到容器的存在
+ 使用场景：需要使用Spring容器的功能资源
+ 缺点：Bean和容器强耦合

## 常用的Aware
|              类名              |                作用                 |
| ----------------------------- | ----------------------------------- |
| BeanNameAware                 | 获得容器bean名称                      |
| BeanClassLoaderAware           | 获得类加载器                          |
| BeanFactoryAware              | 获得bean创建工厂                      |
| EnvironmentAware              | 获得环境变量                          |
| EmbeddedValueResolverAware     | 获取spring容器加载的properties文件属性值 |
| ResourceLoaderAware            | 获得资源加载器                        |
| ApplicationEventPublisherAware | 获得应用事件发布器                     |
| MessageSourceAware             | 获得文本信息                          |
| ApplicationContextAware        | 获得当前应用上下文                     |

# Aware调用
+ doCreateBean
+ initializeBean
+ invokeAwareMethods
+ applyBeanPostProcessorsBeforInitialization
+ ApplicationContextAwareProcessor

# 自定义实现Aware
1. 定义一个接口继承Aware接口
2. 定义setX方法
3. 写一个BeanPostProcessor实现
4. 改写postProcessorsBeforeInitialization方法