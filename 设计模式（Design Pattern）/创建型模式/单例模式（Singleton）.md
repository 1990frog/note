
<!-- TOC -->

- [问题](#%E9%97%AE%E9%A2%98)
    - [保证一个类只有一个实例。 为什么会有人想要控制一个类所拥有的实例数量？](#%E4%BF%9D%E8%AF%81%E4%B8%80%E4%B8%AA%E7%B1%BB%E5%8F%AA%E6%9C%89%E4%B8%80%E4%B8%AA%E5%AE%9E%E4%BE%8B-%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BC%9A%E6%9C%89%E4%BA%BA%E6%83%B3%E8%A6%81%E6%8E%A7%E5%88%B6%E4%B8%80%E4%B8%AA%E7%B1%BB%E6%89%80%E6%8B%A5%E6%9C%89%E7%9A%84%E5%AE%9E%E4%BE%8B%E6%95%B0%E9%87%8F)
    - [为该实例提供一个全局访问节点。 还记得你 （好吧， 其实是我自己） 用过的那些存储重要对象的全局变量吗？](#%E4%B8%BA%E8%AF%A5%E5%AE%9E%E4%BE%8B%E6%8F%90%E4%BE%9B%E4%B8%80%E4%B8%AA%E5%85%A8%E5%B1%80%E8%AE%BF%E9%97%AE%E8%8A%82%E7%82%B9-%E8%BF%98%E8%AE%B0%E5%BE%97%E4%BD%A0-%E5%A5%BD%E5%90%A7-%E5%85%B6%E5%AE%9E%E6%98%AF%E6%88%91%E8%87%AA%E5%B7%B1-%E7%94%A8%E8%BF%87%E7%9A%84%E9%82%A3%E4%BA%9B%E5%AD%98%E5%82%A8%E9%87%8D%E8%A6%81%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%85%A8%E5%B1%80%E5%8F%98%E9%87%8F%E5%90%97)
- [解决方案](#%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88)
- [真实世界类比](#%E7%9C%9F%E5%AE%9E%E4%B8%96%E7%95%8C%E7%B1%BB%E6%AF%94)
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

单例是一种创建型设计模式，让你能够保证一个类只有一个实例，并提供一个访问该实例的全局节点。

# 问题
单例模式同时解决了两个问题，所以违反了单一职责原则:
## 保证一个类只有一个实例。 为什么会有人想要控制一个类所拥有的实例数量？ （特殊职能？）
最常见的原因是控制某些共享资源 （例如数据库或文件） 的访问权限。它的运作方式是这样的： 如果你创建了一个对象， 同时过一会儿后你决定再创建一个新对象， 此时你会获得之前已创建的对象， 而不是一个新对象。
注意， 普通构造函数无法实现上述行为， 因为构造函数的设计决定了它必须总是返回一个新对象（Effective Java 第一章）。

## 为该实例提供一个全局访问节点。 还记得你 （好吧， 其实是我自己） 用过的那些存储重要对象的全局变量吗？ 
它们在使用上十分方便， 但同时也非常不安全， 因为任何代码都有可能覆盖掉那些变量的内容， 从而引发程序崩溃。

和全局变量一样， 单例模式也允许在程序的任何地方访问特定对象。 但是它可以保护该实例不被其他代码覆盖。

还有一点： 你不会希望解决同一个问题的代码分散在程序各处的。 因此更好的方式是将其放在同一个类中， 特别是当其他代码已经依赖这个类时更应该如此。

如今， 单例模式已经变得非常流行， 以至于人们会将只解决上文描述中任意一个问题的东西称为单例。

# 解决方案
所有单例的实现都包含以下两个相同的步骤：

将默认构造函数设为私有， 防止其他对象使用单例类的 new运算符。
新建一个静态构建方法作为构造函数。 该函数会 “偷偷” 调用私有构造函数来创建对象， 并将其保存在一个静态成员变量中。 此后所有对于该函数的调用都将返回这一缓存对象。
如果你的代码能够访问单例类， 那它就能调用单例类的静态方法。 无论何时调用该方法， 它总是会返回相同的对象。


# 真实世界类比
政府是单例模式的一个很好的示例。 一个国家只有一个官方政府。 不管组成政府的每个人的身份是什么，​“某政府” 这一称谓总是鉴别那些掌权者的全局访问节点。



# 适合应用场景

如果程序中的某个类对于所有客户端只有一个可用的实例，
可以使用单例模式。


单例模式禁止通过除特殊构建方法以外的任何方式来创建自
身类的对象。该方法可以创建一个新对象，但如果该对象已
经被创建，则返回已有的对象。

如果你需要更加严格地控制全局变量，可以使用单例模式。


单例模式与全局变量不同，它保证类只存在一个实例。除了
单例类自己以外，无法通过任何方式替换缓存的实例。

请注意， 你可以随时调整限制并设定生成单例实例的数量，
只需修改 获取实例 方法， 即 getInstance 中的代码即可实
现


# 优缺点
优点
你可以保证一个类只有一个实例。

你获得了一个指向该实例的全局访问节点。

仅在首次请求单例对象时对其进行初始化。

缺点
违反了_单一职责原则_。该模式同时解决了两个问题。

单例模式可能掩盖不良设计，比如程序各组件之间相互了解
过多等。


该模式在多线程环境下需要进行特殊处理，避免多个线程多
次创建单例对象。


单例的客户端代码单元测试可能会比较困难，因为许多测试
框架以基于继承的方式创建模拟对象。由于单例类的构造函
数是私有的，而且绝大部分语言无法重写静态方法，所以你
需要想出仔细考虑模拟单例的方法。要么干脆不编写测试代
码，或者不使用单例模式。


# 与其他模式的关系

外观类通常可以转换为单例类，因为在大部分情况下一个外
观对象就足够了。
• 如果你能将对象的所有共享状态简化为一个享元对象，那么
享元就和单例类似了。但这两个模式有两个根本性的不同。
1. 只会有一个单例实体，但是享元类可以有多个实体，各实
体的内在状态也可以不同。
2. 单例对象可以是可变的。享元对象是不可变的。
• 抽象工厂、生成器和原型都可以用单例来实现。






单例模式主要是为了避免因为创建了多个实例造成资源的浪费，且多个实例由于多次调用容易导致结果出现错误，而使用单例模式能够保证整个应用中有且只有一个实例。

为什么要使用单例？单例存在哪些问题？单例与静态类的区别？有何替代的解决方案？

要实现一个单例，我们需要关注的点无外乎下面几个：
构造函数需要是 private 访问权限的，这样才能避免外部通过 new 创建实例；
考虑对象创建时的线程安全问题；
考虑是否支持延迟加载；
考虑 getInstance() 性能是否高（是否加锁）。

# 饿汉式
饿汉式的实现方式比较简单。在类加载的时候，instance 静态实例就已经创建并初始化好了，所以，instance 实例的创建过程是线程安全的。不过，这样的实现方式不支持延迟加载。
```java
public class Singleton {
    //构造器私有化
    private Singleton(){
         
    }
    //在类的内部自己创建实例
    private static Singleton singleton = new Singleton();
 
    //提供get 方法以供外界获取单例
    public static Singleton getInstance(){
        return singleton;
    }
     
}
```

取舍
不支持延迟加载（占用内存多）

如果实例占用资源多，按照 fail-fast 的设计原则（有问题及早暴露），那我们也希望在程序启动时就将这个实例初始化好。如果资源不够，就会在程序启动的时候触发报错（比如 Java 中的 PermGen Space OOM），我们可以立即去修复。这样也能避免在程序运行一段时间后，突然因为初始化这个实例占用资源过多，导致系统崩溃，影响系统的可用性。

初始化耗时长（比如需要加载各种配置文件）

如果初始化耗时长，那我们最好不要等到真正要用它的时候，才去执行这个耗时长的初始化过程，这会影响到系统的性能（比如，在响应客户端接口请求的时候，做这个初始化操作，会导致此请求的响应时间变长，甚至超时）。采用饿汉式实现方式，将耗时的初始化操作，提前到程序启动的时候完成，这样就能避免在程序运行的时候，再去初始化导致的性能问题。


# 懒汉式
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
懒汉式相对于饿汉式的优势是支持延迟加载。不过懒汉式的缺点也很明显，我们给 getInstance() 这个方法加了一把大锁（synchronzed），导致这个函数的并发度很低。量化一下的话，并发度是 1，也就相当于串行操作了。而这个函数是在单例使用期间，一直会被调用。如果这个单例类偶尔会被用到，那这种实现方式还可以接受。但是，如果频繁地用到，那频繁加锁、释放锁及并发度低等问题，会导致性能瓶颈，这种实现方式就不可取了。

# 双重检测
饿汉式不支持延迟加载，懒汉式有性能问题，不支持高并发。那我们再来看一种既支持延迟加载、又支持高并发的单例实现方式，也就是双重检测实现方式。在这种实现方式中，只要 instance 被创建之后，即便再调用 getInstance() 函数也不会再进入到加锁逻辑中了。所以，这种实现方式解决了懒汉式并发度低的问题。
```java
public class IdGenerator { 
  private AtomicLong id = new AtomicLong(0);
  private static IdGenerator instance;
  private IdGenerator() {}
  public static IdGenerator getInstance() {
    if (instance == null) {
      synchronized {
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
SingletonHolder 是一个静态内部类，当外部类 IdGenerator 被加载的时候，并不会创建 SingletonHolder 实例对象。只有当调用 getInstance() 方法时，SingletonHolder 才会被加载，这个时候才会创建 instance。instance 的唯一性、创建过程的线程安全性，都由 JVM 来保证。所以，这种实现方法既保证了线程安全，又能做到延迟加载。

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
最简单的实现方式，基于枚举类型的单例实现。这种实现方式通过 Java 枚举类型本身的特性，保证了实例创建的线程安全性和实例的唯一性。




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