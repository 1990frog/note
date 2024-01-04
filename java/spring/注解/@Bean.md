[TOC]

在开发中，基于 XML 文件配置 Bean 对象的做法非常繁琐且不好维护，因此绝大部分情况下都是使用“完全注解开发”。
@Bean仅能作用于方法，用于替代 XML

# Spring中的Bean
Spring中的一个Bean，需要实例化得到一个对象，而实例化就需要用到构造方法。
+ 构造方法实例化，默认的：让Spring调用bean的构造方法，生成bean实例对象给我们
+ 工厂静态方法实例化：让Spring调用一个工厂类的静态方法，得到一个bean实例对象
+ 工厂非静态方法实例化（实例化方法）：让Spring调用一个工厂对象的非静态方法，得到一个bean实例对象

```xml
<!-- 构造方法实例化 -->
<bean id="userDao" class="com.itheima.dao.impl.UserDaoImpl"></bean>

<!-- 工厂静态方法实例化 -->
public class StaticFactory{
    public static UserDao createUserDao(){
        return new UserDaoImpl();
    }
}
<bean id="userDao" class="com.itheima.factory.StaticFactory" 
      factory-method="createUserDao"></bean>

<!-- 工厂非静态方法实例化 -->
public class InstanceFactory{
    public UserDao createUserDao(){
        return new UserDaoImpl();
    }
}
<!-- 先配置工厂 -->
<bean id="instanceFactory" class="com.itheima.factory.InstanceFactory"></bean>
<!-- 再配置UserDao -->
<bean id="userDao" factory-bean="instanceFactory" factory-method="createUserDao"></bean>
```



# 注解
```java
@Target({ElementType.METHOD, ElementType.ANNOTATION_TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Documented
public @interface Bean {
    @AliasFor("name")
    String[] value() default {};

    @AliasFor("value")
    String[] name() default {};

    /** @deprecated */
    @Deprecated
    Autowire autowire() default Autowire.NO;

    boolean autowireCandidate() default true;

    String initMethod() default "";

    String destroyMethod() default "(inferred)";
}
```

# 用法
```java
@Bean
public User getUser() {
    return new User();
}
```

# @Autowired
基于类型自动装配

# @Qualifier
基于名称进行装配

用法：
+ 加载参数前
+ 加在方法上
```java
@Configuration
public class Config {
    @Bean
    public User getUser(@Value("wyt") String name) {
        User user = new User();
        user.setName(name);
        return user;
    }
    @Bean
    public User createUser(@Value("wyt") String name) {
        User user = new User();
        user.setName(name);
        return user;
    }
    @Bean
    public Book createBook(@Qualifier("createUser") User user) {
        Book book = new Book();
        book.setUser(user);
        return book;
    }
}
```

# @Primary
代表当出现多个同类型 bean 时，优先使用哪一个。