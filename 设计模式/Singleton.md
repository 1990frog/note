
<!-- TOC -->

- [定义](#%E5%AE%9A%E4%B9%89)
- [对比定义](#%E5%AF%B9%E6%AF%94%E5%AE%9A%E4%B9%89)
- [饿汉式](#%E9%A5%BF%E6%B1%89%E5%BC%8F)
- [含懒汉式[双重校验锁 推荐用]](#%E5%90%AB%E6%87%92%E6%B1%89%E5%BC%8F%E5%8F%8C%E9%87%8D%E6%A0%A1%E9%AA%8C%E9%94%81-%E6%8E%A8%E8%8D%90%E7%94%A8)
- [内部类[推荐用]](#%E5%86%85%E9%83%A8%E7%B1%BB%E6%8E%A8%E8%8D%90%E7%94%A8)
- [枚举[推荐用]](#%E6%9E%9A%E4%B8%BE%E6%8E%A8%E8%8D%90%E7%94%A8)

<!-- /TOC -->

> 单例模式主要是为了避免因为创建了多个实例造成资源的浪费，且多个实例由于多次调用容易导致结果出现错误，而使用单例模式能够保证整个应用中有且只有一个实例。

# 定义
只需要三步就可以保证对象的唯一性
+ 不允许其他程序用new对象
+ 在该类中创建对象
+ 对外提供一个可以让其他程序获取该对象的方法

# 对比定义
+ 私有化该类的构造函数
+ 通过new在本类中创建一个本类对象
+ 定义一个公有的方法，将在该类中所创建的对象返回

# 饿汉式
```java
/**
 * 1.单例模式的饿汉式[可用]
 * (1)私有化该类的构造函数
 * (2)通过new在本类中创建一个本类对象
 * (3)定义一个公有的方法，将在该类中所创建的对象返回
 * <p>
 * 优点：从它的实现中我们可以看到，这种方式的实现比较简单，在类加载的时候就完成了实例化，避免了线程的同步问题。
 * 缺点：由于在类加载的时候就实例化了，所以没有达到Lazy Loading(懒加载)的效果，也就是说可能我没有用到这个实例，但是它
 * 也会加载，会造成内存的浪费(但是这个浪费可以忽略，所以这种方式也是推荐使用的)。
 */

public class SingletonEHan {

    private SingletonEHan() {}

    /**
     * 1.单例模式的饿汉式[可用]
     */
    private static SingletonEHan singletonEHan = new SingletonEHan();

    public static SingletonEHan getInstance() {
        return singletonEHan;
    }

//     SingletonEHan instance= SingletonEHan.getInstance();

    /**
     * 2. 单例模式的饿汉式变换写法[可用]
     * 基本没区别
     */
    private static SingletonEHan singletonEHanTwo = null;

    static {
        singletonEHanTwo = new SingletonEHan();
    }

    public static SingletonEHan getSingletonEHan() {
        if (singletonEHanTwo == null) {
            singletonEHanTwo = new SingletonEHan();
        }
        return singletonEHanTwo;
    }
    //     SingletonEHan instance= SingletonEHan.getSingletonEHan();


}
```

# 含懒汉式[双重校验锁 推荐用]
```java
public class SingletonLanHan {

    private SingletonLanHan() {}

    /**
     * 3.单例模式的懒汉式[线程不安全，不可用]
     */
    private static SingletonLanHan singletonLanHan;

    public static SingletonLanHan getInstance() {
        if (singletonLanHan == null) { // 这里线程是不安全的,可能得到两个不同的实例
            singletonLanHan = new SingletonLanHan();
        }
        return singletonLanHan;
    }

    /**
     * 4. 懒汉式线程安全的:[线程安全，效率低不推荐使用]
     * <p>
     * 缺点：效率太低了，每个线程在想获得类的实例时候，执行getInstance()方法都要进行同步。
     * 而其实这个方法只执行一次实例化代码就够了，
     * 后面的想获得该类实例，直接return就行了。方法进行同步效率太低要改进。
     */
    private static SingletonLanHan singletonLanHanTwo;

    public static synchronized SingletonLanHan getSingletonLanHanTwo() {
        if (singletonLanHanTwo == null) { // 这里线程是不安全的,可能得到两个不同的实例
            singletonLanHanTwo = new SingletonLanHan();
        }
        return singletonLanHanTwo;
    }

    /**
     * 5. 单例模式懒汉式[线程不安全，不可用]
     * <p>
     * 虽然加了锁，但是等到第一个线程执行完instance=new Singleton()跳出这个锁时，
     * 另一个进入if语句的线程同样会实例化另外一个Singleton对象，线程不安全的原理跟3类似。
     */
    private static SingletonLanHan instanceThree = null;

    public static SingletonLanHan getSingletonLanHanThree() {
        if (instanceThree == null) {
            synchronized (SingletonLanHan.class) {// 线程不安全
                instanceThree = new SingletonLanHan();
            }
        }
        return instanceThree;
    }

    /**
     * 6.单例模式懒汉式双重校验锁[推荐用]
     * 懒汉式变种,属于懒汉式的最好写法,保证了:延迟加载和线程安全
     */
    private static SingletonLanHan singletonLanHanFour;

    public static SingletonLanHan getSingletonLanHanFour() {
        if (singletonLanHanFour == null) {
            synchronized (SingletonLanHan.class) {
                if (singletonLanHanFour == null) {
                    singletonLanHanFour = new SingletonLanHan();
                }
            }
        }
        return singletonLanHanFour;
    }
}
```

# 内部类[推荐用]
```java
/**
 * 7. 内部类[推荐用]
 * <p>
 * 这种方式跟饿汉式方式采用的机制类似，但又有不同。
 * 两者都是采用了类装载的机制来保证初始化实例时只有一个线程。
 * 不同的地方:
 * 在饿汉式方式是只要Singleton类被装载就会实例化,
 * 内部类是在需要实例化时，调用getInstance方法，才会装载SingletonHolder类
 * <p>
 * 优点：避免了线程不安全，延迟加载，效率高。
 */

public class SingletonIn {

    private SingletonIn() {
    }

    private static class SingletonInHodler {
        private static SingletonIn singletonIn = new SingletonIn();
    }

    public static SingletonIn getSingletonIn() {
        return SingletonInHodler.singletonIn;
    }
}

```

# 枚举[推荐用]
```java
/**
 * 8. 枚举[极推荐使用]
 *
 * 这里SingletonEnum.instance
 * 这里的instance即为SingletonEnum类型的引用所以得到它就可以调用枚举中的方法了。
 借助JDK1.5中添加的枚举来实现单例模式。不仅能避免多线程同步问题，而且还能防止反序列化重新创建新的对象
 */

public enum SingletonEnum {

    instance;

    private SingletonEnum() {
    }

    public void whateverMethod() {

    }

    // SingletonEnum.instance.method();

}

```