[TOC]

# 概览
+ 保证可见性
+ 防止重排序（有序性，重排序可能会导致无序）
+ 具有传递性（happens-before）
# 特性
1. volatile修饰符适用于以下场景：某个属性被多个线程共享，其中有一个线程修改了此属性，其他线程可以立即得到修改后的值，比如boolean flag；或者作为触发器，实现轻量级同步。
2. volatile属性的读写都是无锁的，它不能替代synchronized，因为它没有提供原子性和互斥性。因为无锁，不需要花费时间在获取锁和释放锁上，所以说它是低成本的。
3. volatile只能作用于属性，我们用volatile修饰属性，这样compilers就不会对这个属性做命令重排序。
4. volatile提供了可见性，任何一个线程对其的修改将立马对其他线程可见。volatile属性不会被线程缓存，始终从主存中读取。
5. volatile提供了happens-before保证，对volatile变量v的写入happens-before所有其他线程后续对v的读操作。
6. **volatile可以使得long和double的赋值是原子的**。jvm虚拟机栈中它们对应两个slot
# 使用场景
1. boolean flag，如果一个共享变量至始至终只被各个线程赋值，而没有其他的操作，那么就可以用volatile来代替synchronized或者代替原子变量，因为赋值自身是有原子性的，而volatile又保证了可见性，所以就足以保证线程安全。（大部分类型赋值本身就是原子操作，volatile又提供了可见性）
2. 作为刷新之前变量的触发器
3. 避免重排序，volatile之前的所有操作赋值都会被看到
# 可见性、禁止重排序
可见性：读一个volatile变量之前，需要先使相应的本地缓存失效，这样就必须到主内存读取最新值，写一个volatile属性会立即刷入到主内存。
禁止指令重排序优化：解决单例双重锁乱序问题
# 能保证可见性的其他方式
除了volatile可以让变量保证可见性外，synchronized、Lock、并发集合、Thread.join()和Thread.start()等都可以保证可见性
具体看happens-before原则的规定
# 局限性（阻塞就卡住了）
<font color="red">volatile最大的问题就是无法应用于阻塞方法</font>。假设在循环中调用了拥塞方法，任务可能因拥塞而永远不会去检查取消标志位，甚至会造成永远不能停止。
```java
public class PrimeGenerator implements Runnable {
    private static ExecutorService exec = Executors.newCachedThreadPool();

    private final List<BigInteger> primes
            = new ArrayList<BigInteger>();
    //取消标志位
    private volatile boolean cancelled;

    public void run() {
        BigInteger p = BigInteger.ONE;
        //每次在生成下一个素数时坚持是否取消
        //如果取消，则退出
        while (!cancelled) {
            p = p.nextProbablePrime();
            synchronized (this) {
                primes.add(p);
            }
        }
    }

    public void cancel() {
        cancelled = true;
    }

    public synchronized List<BigInteger> get() {
        return new ArrayList<BigInteger>(primes);
    }

    static List<BigInteger> aSecondOfPrimes() throws InterruptedException {
        PrimeGenerator generator = new PrimeGenerator();
        exec.execute(generator);
        try {
            SECONDS.sleep(1);
        } finally {
            generator.cancel();
        }
        return generator.get();
    }
}
```