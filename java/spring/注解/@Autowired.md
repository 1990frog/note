[TOC]

@Autowired基于类型注入，添加@Qualifier基于名称注入。如果@Autowired注入的对象有多个，可以使用@Qualifier选择

# 作用范围
+ 构造器
+ 方法
+ 参数
+ 成员变量
+ 注解

# 成员变量
这种方式可能是平时用得最多的
```java
@Service
public class UserService {

    @Autowired
    private IUser user;
}
```

# 构造器
在构造器上使用Autowired注解，注意，在构造器上加Autowired注解，实际上还是使用了Autowired装配方式，并非构造器装配。
```java
@Service
public class UserService {

    private IUser user;

    @Autowired
    public UserService(IUser user) {
        this.user = user;
        System.out.println("user:" + user);
    }
}
```

# 方法
在普通方法上加Autowired注解：
```java
@Service
public class UserService {

    @Autowired
    public void test(IUser user) {
       user.say();
    }
}
```
spring会在项目启动的过程中，自动调用一次加了@Autowired注解的方法，我们可以在该方法做一些初始化的工作。

也可以在setter方法上Autowired注解：
```java
@Service
public class UserService {

    private IUser user;

    @Autowired
    public void setUser(IUser user) {
        this.user = user;
    }
}
```

# 参数
可以在构造器的入参上加Autowired注解：
```java
@Service
public class UserService {

    private IUser user;

    public UserService(@Autowired IUser user) {
        this.user = user;
        System.out.println("user:" + user);
    }
}
```
也可以在非静态方法的入参上加Autowired注解：
```java
@Service
public class UserService {

    public void test(@Autowired IUser user) {
       user.say();
    }
}
```

# 注解
?

