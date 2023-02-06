[TOC]

# 举个例子
放学了，小朋友们排着队，跟着老师，走向校门口。
老师停，学生停；老师走，学生走。瞎跑是不行的。
到了门口，来了二十个家长，接了二十个小朋友，各回各家，老师也回家了。
校内的路，老师和同学可以看作在一个线程内的，顺序执行，前边的停下来，后边的必须等。
到了门口，家长接了，就等于分出了一个线程，二十个家长，二十个线程，每个线程负责把自己的孩子送回家，线程之间没有次序依赖，同时进行。
如果一个线程出了异常，比如跟家长回家的路上，一个小朋友跌倒了，要去医院。
显然，这不影响其的小朋友回家，也不该归放了学的老师管。
是由受伤小朋友的家长处理，也就是说，异常应由所在的线程处理，别的线程没有义务或上下文，来处理你的异常。
本质上来说，分一个线程，意味着不必等。
就像老师不必等待所有孩子都到家才下班。

不必等，意味着不知道其他线程的进度，也不必处理其他线程的问题。
孩子摔倒时，老师可能已经到家了，就好像题主的代码里，新线程里出异常，原线程可能已经跑完了。

# 线程与异常
每一个Java应用程序都是一个进程，在进程中会启动多个线程来执行各类任务。
因为Java线程的本质，所以当在一个Java的线程中抛出异常的时候，需要在当前线程中catch并处理。
如果当前线程没有catch住这个异常，那么这个异常就会被抛出，并导致这个线程运行终止。
因此对于Java的线程异常处理只能由当前线程来处理，其他线程是无法感知的。（run方法不能向上抛出）

# UncaughtExceptionHandler
实现`Thread.UncaughtExceptionHandler`接口
```java
/**
 * 描述：
 * 自己的MyUncaughtExceptionHanlder
 */
public class MyUncaughtExceptionHandler implements Thread.UncaughtExceptionHandler {

    private String name;

    public MyUncaughtExceptionHandler(String name) {
        this.name = name;
    }

    @Override
    public void uncaughtException(Thread t, Throwable e) {
        Logger logger = Logger.getAnonymousLogger();
        logger.log(Level.WARNING, "线程异常，终止啦" + t.getName());
        System.out.println(name + "捕获了异常" + t.getName() + "异常");
    }
}
```
Thread类源码
```java
public class Thread implements Runnable {
    // null unless explicitly set
    private static volatile UncaughtExceptionHandler defaultUncaughtExceptionHandler;

    public static void setDefaultUncaughtExceptionHandler(UncaughtExceptionHandler eh) {
        SecurityManager sm = System.getSecurityManager();
        if (sm != null) {
            sm.checkPermission(
                new RuntimePermission("setDefaultUncaughtExceptionHandler")
            );
        }
        defaultUncaughtExceptionHandler = eh;
     }

    /**
     * 当一个线程因未捕获的异常而即将终止时虚拟机将使用 Thread.getUncaughtExceptionHandler()
     * 获取已经设置的 UncaughtExceptionHandler 实例，并通过调用其 uncaughtException(...) 方
     * 法而传递相关异常信息。
     * 如果一个线程没有明确设置其 UncaughtExceptionHandler，则将其 ThreadGroup 对象作为其
     * handler，如果 ThreadGroup 对象对异常没有什么特殊的要求，则 ThreadGroup 会将调用转发给
     * 默认的未捕获异常处理器（即 Thread 类中定义的静态未捕获异常处理器对象）。
     *
     * @see #setDefaultUncaughtExceptionHandler
     * @see #setUncaughtExceptionHandler
     * @see ThreadGroup#uncaughtException
     */
    @FunctionalInterface
    public interface UncaughtExceptionHandler {
        /**
         * Method invoked when the given thread terminates due to the
         * given uncaught exception.
         * <p>Any exception thrown by this method will be ignored by the
         * Java Virtual Machine.
         * @param t the thread
         * @param e the exception
         */
        void uncaughtException(Thread t, Throwable e);
    }
}
```
主线程持有`UncaughtExceptionHandler`
```java
/**
 * 描述：
 * 使用刚才自己写的UncaughtExceptionHandler
 */
public class UseOwnUncaughtExceptionHandler implements Runnable {

    public static void main(String[] args) throws InterruptedException {

        //设置异常捕获器
        Thread.setDefaultUncaughtExceptionHandler(new MyUncaughtExceptionHandler("捕获器1"));

        new Thread(new UseOwnUncaughtExceptionHandler(), "MyThread-1").start();
        Thread.sleep(300);
        new Thread(new UseOwnUncaughtExceptionHandler(), "MyThread-2").start();
        Thread.sleep(300);
        new Thread(new UseOwnUncaughtExceptionHandler(), "MyThread-3").start();
        Thread.sleep(300);
        new Thread(new UseOwnUncaughtExceptionHandler(), "MyThread-4").start();

    }

    @Override
    public void run() {
        throw new RuntimeException();
    }
}
```
# 步骤
1. 实现UncaughtExceptionHandler
2. 主线程setDefaultUncaughtExceptionHandler