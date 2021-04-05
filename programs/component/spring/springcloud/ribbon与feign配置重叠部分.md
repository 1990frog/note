[TOC]

# 仅设置ribbon超时时间
```yml
ribbon:
  ReadTimeout: 1
  ConnectTimeout: 1

feign:
  client:
    config:
      # 全局配置
      default:
        loggerLevel: full
#        connectTimeout: 1000
#        readTimeout: 1000
```
运行结果：
```
2020-03-08 10:18:59.078 ERROR 12020 --- [nio-8011-exec-1] o.a.c.c.C.[.[.[/].[dispatcherServlet]    : 
Servlet.service() for servlet [dispatcherServlet] in context with path [] 
threw exception [Request processing failed; nested exception is feign.RetryableException: Read timed out executing GET http://productor/productor] with root cause

java.net.SocketTimeoutException: Read timed out
	at java.net.SocketInputStream.socketRead0(Native Method) ~[na:1.8.0_242]
	at java.net.SocketInputStream.socketRead(SocketInputStream.java:116) ~[na:1.8.0_242]
	at java.net.SocketInputStream.read(SocketInputStream.java:171) ~[na:1.8.0_242]
	at java.net.SocketInputStream.read(SocketInputStream.java:141) ~[na:1.8.0_242]
	at java.io.BufferedInputStream.fill(BufferedInputStream.java:246) ~[na:1.8.0_242]
	......
```

# 仅设置feign超时时间
```yml
ribbon:
#  ReadTimeout: 1
#  ConnectTimeout: 1

feign:
  client:
    config:
      # 全局配置
      default:
        loggerLevel: full
        connectTimeout: 1000
        readTimeout: 1000
```
运行结果：
```
2020-03-08 10:21:36.560 ERROR 12510 --- [nio-8011-exec-1] o.a.c.c.C.[.[.[/].[dispatcherServlet]    : 
Servlet.service() for servlet [dispatcherServlet] in context with path [] 
threw exception [Request processing failed; nested exception is feign.RetryableException: Read timed out executing GET http://productor/productor] with root cause

java.net.SocketTimeoutException: Read timed out
	at java.net.SocketInputStream.socketRead0(Native Method) ~[na:1.8.0_242]
```

# 同时设置Ribbon与feign超时时间
## ribbon合理，feign不合理
```yml
ribbon:
  ReadTimeout: 1000
  ConnectTimeout: 1000

feign:
  client:
    config:
      # 全局配置
      default:
        loggerLevel: full
        connectTimeout: 1
        readTimeout: 1
```
运行结果：
```
2020-03-08 10:24:33.493 ERROR 12849 --- [nio-8011-exec-2] o.a.c.c.C.[.[.[/].[dispatcherServlet]    : 
Servlet.service() for servlet [dispatcherServlet] in context with path [] 
threw exception [Request processing failed; nested exception is feign.RetryableException: Read timed out executing GET http://productor/productor] with root cause

java.net.SocketTimeoutException: Read timed out
```
## ribbon不合理，feign合理
```yml
ribbon:
  ReadTimeout: 1
  ConnectTimeout: 1

feign:
  client:
    config:
      # 全局配置
      default:
        loggerLevel: full
        connectTimeout: 1000
        readTimeout: 1000
```
运行结果：
```
正常
```
## 结论
feign的超时时间配置优先级高于ribbon
## Feign优于Ribbon的原因
```java
public class LoadBalancerFeignClient implements Client {

    IClientConfig getClientConfig(Request.Options options, String clientName) {
        IClientConfig requestConfig;
        //这点是关键，只要Feign的options配置不是默认的，就会使用我们的配置，
        //反之会使用DefaultClientConfigImpl的实例，这个类实例化请看上面，
        //主要是enableDynamicProperties被设置为true后会先去读ribbon的配置
        if (options == DEFAULT_OPTIONS) {
            requestConfig = this.clientFactory.getClientConfig(clientName);
        } else {
            requestConfig = new FeignOptionsClientConfig(options);
        }
        return requestConfig;
    }
}
```
## 为什么connectTimeout和readTimeout必须同时配置
```java
class FeignClientFactoryBean implements FactoryBean<Object>, InitializingBean,
        ApplicationContextAware {

    protected void configureUsingProperties(FeignClientProperties.FeignClientConfiguration config, Feign.Builder builder) {
        if (config == null) {
            return;
        }
        if (config.getLoggerLevel() != null) {
            builder.logLevel(config.getLoggerLevel());
        }
        //此处，必须俩值都不为null才会替换新options
        if (config.getConnectTimeout() != null && config.getReadTimeout() != null) {
            builder.options(new Request.Options(config.getConnectTimeout(), config.getReadTimeout()));
        }
    }
}
```
## 最终配置生效
```java
public class RetryableFeignLoadBalancer extends FeignLoadBalancer implements ServiceInstanceChooser {
    @Override
    public RibbonResponse execute(final RibbonRequest request, IClientConfig configOverride)
            throws IOException {
        final Request.Options options;
        if (configOverride != null) {
            RibbonProperties ribbon = RibbonProperties.from(configOverride);
            options = new Request.Options(
                   //超时时间设置的关键，内部包含一个clientConfig，就是上面根据options判断得来的
                   //DefaultClientConfigImpl或者FeignOptionsClientConfig
                   //一个优先从ribbon拿超时时间，一个只从Feign拿超时时间，主要是受enableDynamicProperties的影响
                   // 具体代码见DefaultClientConfigImpl#getProperty
                   ribbon.connectTimeout(this.connectTimeout),
                   ribbon.readTimeout(this.readTimeout));
        }
}
```