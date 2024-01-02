[TOC]

# 生产
使用loadBeanDefinitions方法加载Bean，将加载的bean存放在beanDefintitionMap容器内



IOC中bean的生命周期

bean种类：
+ 系统bean：dataSource,template,...
+ 用户自定义bean

bean的阶段：
+ 生产
+ 使用
+ 销毁


# 生产
loadBeanDefinitions 加载 Bean 定义，将其存放在 beanDefinitionMap 容器内。
+ run()
+ refreshContext()
+ refresh()
+ obtainFreshBeanFactory()
+ refreshBeanFactory()
+ loadBeanDefinitions()

然后通过 createBean 方法。创建 Bean 对象。
+ run()
+ refreshContext()
+ refresh()
+ finishBeanFactoryInitialization()
+ preInstantiateSingletons()
+ doGetBean()
+ createBean()

创建Bean大体分为”构造对象、填充属性、初始化实例、注册销毁”四个步骤


# 构造对象
createBeanInstance，先用反射机制从“Bean定义”中的BeanClass拿到这个类的构造方法（单构造方法、多构造方法、@Autowired）。在选择了确定的构造方法之后，就要准备这个构造方法需要的参数了。会在单例池中基于Class类型进行查找，如果这个参数在池中有多个实例，则会通过参数名进行匹配，如果没有找到就会任务构造信息不完整直接报错。在参数准备好之后通过反射进行bean的实例化

# 属性填充
polulateBean基于spring的三级缓存进行填充，也就是依赖注入。

# 初始化实例
initializeBean初始化容器相关信息，通过invokeAwareMethods方法，为实现了各种Aware接口的Bean设置诸如beanName、beanFactory等容器信息。Aware接口代表信息感知接口，一旦实现这类接口，就可以在bean实例中感知并获取到相对应的信息。然后通过invokeInitMethods方法实现Bean的初始化方法。这个方法是通过实现InitializingBean接口而实现的afterPropertiesSet方法。bean填充属性后执行。之后还会继续执行initMethod方法。在执行初始化方法之前和之后还需要对“Bean后置处理器”BeanPostProcessors进行处理。分别在applyBeanPostProcessorsBeforeInitialization、applyBeanPostProcessorsAfterInitialization分别在初始化之前和之后处理各种bean的后置处理器。这些处理器包括负责AOP的AnnotationAwareAspectJAutoProxyCreator，负责构造后@PostConstruct和销毁前@PreDestroy处理的InitDestroyAnnotationBeanPostProcessor等系统级处理器，这些处理器可以通过实现PriorityOrdered接口来指定顺序

# 注册销毁
通过注册销毁registerDisposableBean方法，将实现了销毁接口DisposableBean的Bean进行注册，这样在销毁时就可以执行destroy方法了。最后将这些Bean对象通过挨刀的Singleton方法放入单例池singletonObjects中就可以被获取和使用了。



