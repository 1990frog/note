
<!-- TOC -->

- [饿汉式](#%E9%A5%BF%E6%B1%89%E5%BC%8F)
- [懒汉式](#%E6%87%92%E6%B1%89%E5%BC%8F)
- [双重检测](#%E5%8F%8C%E9%87%8D%E6%A3%80%E6%B5%8B)
- [静态内部类](#%E9%9D%99%E6%80%81%E5%86%85%E9%83%A8%E7%B1%BB)
- [枚举](#%E6%9E%9A%E4%B8%BE)
- [定义](#%E5%AE%9A%E4%B9%89)
- [对比定义](#%E5%AF%B9%E6%AF%94%E5%AE%9A%E4%B9%89)
- [饿汉式](#%E9%A5%BF%E6%B1%89%E5%BC%8F)
- [含懒汉式[双重校验锁 推荐用]](#%E5%90%AB%E6%87%92%E6%B1%89%E5%BC%8F%E5%8F%8C%E9%87%8D%E6%A0%A1%E9%AA%8C%E9%94%81-%E6%8E%A8%E8%8D%90%E7%94%A8)
- [内部类[推荐用]](#%E5%86%85%E9%83%A8%E7%B1%BB%E6%8E%A8%E8%8D%90%E7%94%A8)
- [枚举[推荐用]](#%E6%9E%9A%E4%B8%BE%E6%8E%A8%E8%8D%90%E7%94%A8)

<!-- /TOC -->

> 单例模式主要是为了避免因为创建了多个实例造成资源的浪费，且多个实例由于多次调用容易导致结果出现错误，而使用单例模式能够保证整个应用中有且只有一个实例。

为什么要使用单例？单例存在哪些问题？单例与静态类的区别？有何替代的解决方案？


要实现一个单例，我们需要关注的点无外乎下面几个：
构造函数需要是 private 访问权限的，这样才能避免外部通过 new 创建实例；
考虑对象创建时的线程安全问题；
考虑是否支持延迟加载；
考虑 getInstance() 性能是否高（是否加锁）。

# 饿汉式
饿汉式的实现方式比较简单。在类加载的时候，instance 静态实例就已经创建并初始化好了，所以，instance 实例的创建过程是线程安全的。不过，这样的实现方式不支持延迟加载（在真正用到 IdGenerator 的时候，再创建实例）
```java
public class IdGenerator { 
  private AtomicLong id = new AtomicLong(0);
  private static final IdGenerator instance = new IdGenerator();
  private IdGenerator() {}
  public static IdGenerator getInstance() {
    return instance;
  }
  public long getId() { 
    return id.incrementAndGet();
  }
}
```

有人觉得这种实现方式不好，因为不支持延迟加载，如果实例占用资源多（比如占用内存多）或初始化耗时长（比如需要加载各种配置文件），提前初始化实例是一种浪费资源的行为。最好的方法应该在用到的时候再去初始化。不过，我个人并不认同这样的观点。如果初始化耗时长，那我们最好不要等到真正要用它的时候，才去执行这个耗时长的初始化过程，这会影响到系统的性能（比如，在响应客户端接口请求的时候，做这个初始化操作，会导致此请求的响应时间变长，甚至超时）。采用饿汉式实现方式，将耗时的初始化操作，提前到程序启动的时候完成，这样就能避免在程序运行的时候，再去初始化导致的性能问题。如果实例占用资源多，按照 fail-fast 的设计原则（有问题及早暴露），那我们也希望在程序启动时就将这个实例初始化好。如果资源不够，就会在程序启动的时候触发报错（比如 Java 中的 PermGen Space OOM），我们可以立即去修复。这样也能避免在程序运行一段时间后，突然因为初始化这个实例占用资源过多，导致系统崩溃，影响系统的可用性。


# 懒汉式
有饿汉式，对应的，就有懒汉式。懒汉式相对于饿汉式的优势是支持延迟加载。
```java

public class IdGenerator { 
  private AtomicLong id = new AtomicLong(0);
  private static IdGenerator instance;
  private IdGenerator() {}
  public static synchronized IdGenerator getInstance() {
    if (instance == null) {
      instance = new IdGenerator();
    }
    return instance;
  }
  public long getId() { 
    return id.incrementAndGet();
  }
}
```
不过懒汉式的缺点也很明显，我们给 getInstance() 这个方法加了一把大锁（synchronzed），导致这个函数的并发度很低。量化一下的话，并发度是 1，也就相当于串行操作了。而这个函数是在单例使用期间，一直会被调用。如果这个单例类偶尔会被用到，那这种实现方式还可以接受。但是，如果频繁地用到，那频繁加锁、释放锁及并发度低等问题，会导致性能瓶颈，这种实现方式就不可取了。

# 双重检测
饿汉式不支持延迟加载，懒汉式有性能问题，不支持高并发。那我们再来看一种既支持延迟加载、又支持高并发的单例实现方式，也就是双重检测实现方式。在这种实现方式中，只要 instance 被创建之后，即便再调用 getInstance() 函数也不会再进入到加锁逻辑中了。所以，这种实现方式解决了懒汉式并发度低的问题。
```java
public class IdGenerator { 
  private AtomicLong id = new AtomicLong(0);
  private static IdGenerator instance;
  private IdGenerator() {}
  public static IdGenerator getInstance() {
    if (instance == null) {
      synchronized(IdGenerator.class) { // 此处为类级别的锁
        if (instance == null) {
          instance = new IdGenerator();
        }
      }
    }
    return instance;
  }
  public long getId() { 
    return id.incrementAndGet();
  }
}
```

网上有人说，这种实现方式有些问题。因为指令重排序，可能会导致 IdGenerator 对象被 new 出来，并且赋值给 instance 之后，还没来得及初始化（执行构造函数中的代码逻辑），就被另一个线程使用了。要解决这个问题，我们需要给 instance 成员变量加上 volatile 关键字，禁止指令重排序才行。实际上，只有很低版本的 Java 才会有这个问题。我们现在用的高版本的 Java 已经在 JDK 内部实现中解决了这个问题（解决的方法很简单，只要把对象 new 操作和初始化操作设计为原子操作，就自然能禁止重排序）。

# 静态内部类
```java

public class IdGenerator { 
  private AtomicLong id = new AtomicLong(0);
  private IdGenerator() {}

  private static class SingletonHolder{
    private static final IdGenerator instance = new IdGenerator();
  }
  
  public static IdGenerator getInstance() {
    return SingletonHolder.instance;
  }
 
  public long getId() { 
    return id.incrementAndGet();
  }
}
```
SingletonHolder 是一个静态内部类，当外部类 IdGenerator 被加载的时候，并不会创建 Sin0gletonHolder 实例对象。只有当调用 getInstance() 方法时，SingletonHolder 才会被加载，这个时候才会创建 instance。instance 的唯一性、创建过程的线程安全性，都由 JVM 来保证。所以，这种实现方法既保证了线程安全，又能做到延迟加载。

# 枚举
这种实现方式通过 Java 枚举类型本身的特性，保证了实例创建的线程安全性和实例的唯一性。
```java

public enum IdGenerator {
  INSTANCE;
  private AtomicLong id = new AtomicLong(0);
 
  public long getId() { 
    return id.incrementAndGet();
  }
}
```

单例的实现单例有下面几种经典的实现方式。

饿汉式
饿汉式的实现方式，在类加载的期间，就已经将 instance 静态实例初始化好了，所以，instance 实例的创建是线程安全的。不过，这样的实现方式不支持延迟加载实例。

懒汉式
懒汉式相对于饿汉式的优势是支持延迟加载。这种实现方式会导致频繁加锁、释放锁，以及并发度低等问题，频繁的调用会产生性能瓶颈。

双重检测
双重检测实现方式既支持延迟加载、又支持高并发的单例实现方式。只要 instance 被创建之后，再调用 getInstance() 函数都不会进入到加锁逻辑中。所以，这种实现方式解决了懒汉式并发度低的问题。静态内部类利用 Java 的静态内部类来实现单例。这种实现方式，既支持延迟加载，也支持高并发，实现起来也比双重检测简单。

枚举
最简单的实现方式，基于枚举类型的单例实现。这种实现方式通过 Java 枚举类型本身的特性，保证了实例创建的线程安全性和实例的唯一性。课堂讨论




尽管单例是一个很常用的设计模式，在实际的开发中，我们也确实经常用到它，但是，有些人认为单例是一种反模式（anti-pattern），并不推荐使用。所以，今天，我就针对这个说法详细地讲讲这几个问题：单例这种设计模式存在哪些问题？为什么会被称为反模式？如果不用单例，该如何表示全局唯一类？有何替代的解决方案？



大部分情况下，我们在项目中使用单例，都是用它来表示一些全局唯一类，比如配置信息类、连接池类、ID 生成器类。单例模式书写简洁、使用方便，在代码中，我们不需要创建对象，直接通过类似 IdGenerator.getInstance().getId() 这样的方法来调用就可以了。但是，这种使用方法有点类似硬编码（hard code），会带来诸多问题。


















------

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