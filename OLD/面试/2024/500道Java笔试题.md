

# 1、关于finally,下面哪个描述正确? （B）
A.在catch块之前但在try块之后执行finally块
B.finally块会被执行无论是否抛出异常
C.只有在执行catch块之后才执行finally块
D.都不是



# 2、覆盖（重写）与重载的关系是（A）
A.覆盖（重写）只有出现在父类与子类之间，而重载可以出现在同一个类中
B.覆盖（重写）方法可以有不同的方法名，而重载方法必须是相同的方法名
C.final修饰的方法可以被覆盖（重写），但不能被重载
D.覆盖（重写）与重载是同一回事


# 3、下列语句序列执行后，输出结果是（B）
```prettyprint
public class ex {
    public static void main(String[] args) {
        int a = 13;
        a = a / 5；
        System.out.println(a);
    }
}
```
A.1
B.2
C.3
D.4

# 4、Java Applet在被浏览器加载的时候首先被执行且在applet整个生命周期中被运行一次的方法是（A）
A.init（）
B.stop（）
C.opreationcrawl()
D.reader()

# 5、对抽象类的描述正确的是(D)
A.抽象类的方法都是抽象方法
B.一个类可以继承多个抽象类
C.抽象类不能有构造方法
D.抽象类不能被实例化

# 6、类 ABC 定义如下,将以下哪个方法插入行 3 是不合法的。（B）
```prettyprint
1 ． public  class  ABC{
2 ． public  int  max( int  a, int  b) {   }
3 ．
4 ． }
```
将以下哪个方法插入行 3 是不合法的。（ ）。
A.public  float  max(float  a, float  b, float  c){  }
B.public  int  max (int  c,  int  d){  }
C.public  float  max(float  a,  float  b){  }
D.private  int  max(int a, int b, int c){  }

# 7、在异常处理中，如释放资源，关闭数据库、关闭文件应由（C）语句来完成。
A.try子句
B.catch子句
C.finally子句
D.throw子句

# 8、以下代码段执行后的输出结果为（D）
```prettyprint
public class Test {
    public static void main(String args[]) {
        int x = -5;
        int y = -12;
        System.out.println(y % x);
    }
}
```
A.-1
B.2
C.1
D.-2
模运算余数的符号跟被除数符号相同，本题中：-12=(-5)*2+(-2)，余数为-2，答案选D

# 9、下列说法正确的是（B）
A.在类方法中可用this来调用本类的类方法
B.在类方法中调用本类的类方法时可直接调用
C.在类方法中只能调用本类中的类方法
D.在类方法中绝对不能调用实例方法
在类方法中不能有this关键字，直接调用类方法即可，A错误，B正确，在类方法中可以通过创建实例对象调用类的实例方法，C\D错误

# 10、在Java中，HashMap中是用哪些方法来解决哈希冲突的？（C）
A.开放地址法
B.二次哈希法
C.链地址法
D.建立一个公共溢出区

# 11、下面有关List接口、Set接口和Map接口的描述，错误的是？（A）
A.他们都继承自Collection接口
B.List是有序的Collection，使用此接口能够精确的控制每个元素插入的位置
C.Set是一种不包含重复的元素的Collection
D.Map提供key到value的映射。一个Map中不能包含相同的key，每个key只能映射一个value

Map接口和Collection接口是同一等级的

# 12、设int x=1,float y=2,则表达式x/y的值是：（D）
A.0
B.1
C.2
D.以上都不是

# 13、命令javac-d参数的用途是？（A）
A.指定编译后类层次的根目录
B.指定编译时需要依赖类的路径
C.指定编译时的编码
D.没有这一个参数

# 14、关于Float，下列说法错误的是(C)
A.Float是一个类
B.Float在java.lang包中
C.Float a=1.0是正确的赋值方法
D.Float a= new Float(1.0)是正确的赋值方法


# 15、下面为true的是？（G）
```prettyprint
1 Integer i = 42;
2 Long l = 42l;
3 Double d = 42.0;
```

A.(i == l)
B.(i == d)
C.(l == d)
D.i.equals(d)
E.d.equals(l)
F.i.equals(l)
G.l.equals(42L)

包装类的“==”运算在不遇到算术运算的情况下不会自动拆箱
包装类的equals()方法不处理数据转型



# 16、关于下面代码片段叙述正确的是（C）

```prettyprint
1 byte b1=1,b2=2,b3,b6; 
2 final byte b4=4,b5=6; 
3 b6=b4+b5; 
4 b3=(b1+b2); 
5 System.out.println(b3+b6);
```
A.输出结果：13
B.语句：b6=b4+b5编译出错
C.语句：b3=b1+b2编译出错
D.运行期抛出异常

被final修饰的变量是常量，这里的b6=b4+b5可以看成是b6=10；在编译时就已经变为b6=10了
而b1和b2是byte类型，java中进行计算时候将他们提升为int类型，再进行计算，b1+b2计算后已经是int类型，赋值给b3，b3是byte类型，类型不匹配，编译不会通过，需要进行强制转换。
Java中的byte，short，char进行计算时都会提升为int类型。



# 17、以下程序的输出结果为（D）

```prettyprint
class Base{
    public Base(String s){
        System.out.print("B");
    }
}
public class Derived extends Base{
    public Derived (String s) {
        System.out.print("D");
    }
    public static void main(String[] args){
        new Derived("C");
    }
}
```
A.BD
B.DB
C.C
D.编译错误

子类构造方法在调用时必须先调用父类的，由于父类没有无参构造，必须在子类中显式调用，修改子类构造方法如下即可：

```prettyprint
public Derived(String s){
    super("s");
    System.out.print("D");
}
```

# 18、下面属于java引用类型的有？（A、D）
A.String
B.byte
C.char
D.Array

java语言是强类型语言，支持的类型分为两类：基本类型和引用类型。
基本类型包括boolean类型和数值类型，数值类型有整数类型和浮点类型。整数类型包括：byte、short、int、long和char；浮点类型包括：float和double
引用类型包括类、接口和数组类型以及特殊的null类型。



# 19、以下哪些继承自 Collection 接口（A，B）
A.List
B.Set
C.Map
D.Array

集合常考点： 
Collection接口：
1.List接口：内容允许重复 {1.ArrayList 2.LinkedList，也实现了Queue接口 3.Vector}
2.Set接口：内容不允许重复 
3.Queue接口：队列接口 
4.sortedSet接口：单值排序接口

Map接口：
1.HashMap接口：无序存放，key不重复 
2.HashTable接口：无序存放，key不重复 
3.TreeMap接口：按key排序，key不重复 
4.IdentityHashMap接口：key可重复 5.WeakHashMap接口：弱引用Map集合


# 20、java中关于继承的描述正确的是（A、C、D）
A.一个子类只能继承一个父类
B.子类可以继承父类的构造方法
C.继承具有传递性
D.父类一般具有通用性，子类更具体


# 21、下面有关java classloader说法正确的是（A、C、D）
A.ClassLoader就是用来动态加载class文件到内存当中用的
B.JVM在判定两个class是否相同时，只用判断类名相同即可，和类加载器无关
C.ClassLoader使用的是双亲委托模型来搜索类的
D.Java默认提供的三个ClassLoader是Boostrap ClassLoader，Extension ClassLoader，App ClassLoader
E.以上都不正确

# 22、下面描述属于java虚拟机功能的是？（A、B、C）
A.通过 ClassLoader 寻找和装载 class 文件
B.解释字节码成为指令并执行，提供 class 文件的运行环境
C.进行运行期间垃圾回收
D.提供与硬件交互的平台

# 23、给出下面的代码段，在代码说明// assignment x=a, y=b处写入如下哪几个代码是正确的？（C、D）

```prettyprint
public class Base {
    int w,
    x,
    y,
    z;
    public Base(int a, int b) {
        x = a;
        y = b;
    }
    public Base(int a, int b, int c, int d) {
        // assignment x=a, y=b
        w = d;
        z = c;
    }
}
```
A.Base(a,b);
B.x=a, y=b;
C.x=a; y=b;
D.this(a,b);

# 24、以下关于final关键字说法错误的是（A、C）
A.final是java中的修饰符，可以修饰类、接口、抽象类、方法和属性
B.final修饰的类不能被继承
C.final修饰的方法不能被重载
D.final修饰的变量不允许被再次赋值

# 25、如下哪些是 java 中有效的关键字（A、D）
A.native
B.NULL
C.false
D.this

# 26、关于ThreadLocal类 以下说法正确的是（D、E）
A.ThreadLocal继承自Thread
B.ThreadLocal实现了Runnable接口
C.ThreadLocal重要作用在于多线程间的数据共享
D.ThreadLocal是采用哈希表的方式来为每个线程都提供一个变量的副本
E.ThreadLocal保证各个线程间数据安全，每个线程的数据不会被另外线程访问和破坏


# 27、java中 String str = "hello world"下列语句错误的是（A、B、C）
A.str+='      a'
B.int strlen = str.length
C.str=100
D.str=str+100


# 28、Java是一门支持反射的语言,基于反射为Java提供了丰富的动态性支持，下面关于Java反射的描述，哪些是错误的：(A、D、F)
A.Java反射主要涉及的类如Class, Method, Filed,等，他们都在java.lang.reflet包下
B.通过反射可以动态的实现一个接口，形成一个新的类，并可以用这个类创建对象，调用对象方法
C.通过反射，可以突破Java语言提供的对象成员、类成员的保护机制，访问一般方式不能访问的成员
D.Java反射机制提供了字节码修改的技术，可以动态的修剪一个类
E.Java的反射机制会给内存带来额外的开销。例如对永生堆的要求比不通过反射要求的更多
F.Java反射机制一般会带来效率问题，效率问题主要发生在查找类的方法和字段对象，因此通过缓存需要反射类的字段和方法就能达到与之间调用类的方法和访问类的字段一样的效率
屏蔽本


# 29、若有定义：byte[]x={11,22,33,﹣66}；其中0≤k≤3，则对x数组元素错误的引用是（C）
A.x[5-3]
B.x[k]
C.x[k+5]
D.x[0]


# 30、以下不属于构造方法特征的是（D）
A.构造方法名与类名相同
B.构造方法不返回任何值，也没有返回类型
C.构造方法在创建对象时调用，其他地方不能显式地直接调用
D.每一个类只能有一个构造方法

D选项描述错误，一个类可以有多个构造方法，形成重载关系。


# 31、java7后关键字 switch 支不支持字符串作为条件：（A）
A.支持
B.不支持


正确答案: A  
在Java7之前，switch只能支持 byte、short、char、int或者其对应的封装类以及Enum类型。在Java7中，呼吁很久的String支持也终于被加上了。
在switch语句中，表达式的值不能是null，否则会在运行时抛出NullPointerException。在case子句中也不能使用null，否则会出现编译错误。
同时，case字句的值是不能重复的。对于字符串类型的也一样，但是字符串中可以包含Unicode转义字符。重复值的检查是在Java编译器对Java源代码进行相关的词法转换之后才进行的。也就是说，有些case字句的值虽然在源代码中看起来是不同的，但是经词法转换之后是一样的，就会在成编译错误。比如：“男”和“\u7537”就是一个意思。
然后看一个源代码及反编译后的代码：
```prettyprint
public class StringForSwitch {
    public void test_string_switch() {
        String result="";  
        switch ("doctor") {
            case "doctor":
                result = "doctor";
                break;
            default:
                break;
        }
    }
}
```

反编译后的，还原成大致的Java的代码如下：
```prettyprint
public class StringForSwitch {
    public StringForSwitch() {
    }
    public void test_string_switch() {
        String result = "";
        String var2 = "doctor";
        switch("doctor".hashCode()) {
            case -1326477025:
                if(var2.equals("doctor")) {
                    result = "doctor";
                }
            default:
                break;
        }
    }
}
```
可以看出，字符串类型在switch语句中利用hashcode的值与字符串内容的比较来实现的；但是在case字句中对应的语句块中仍然需要使用String的equals方法来进一步比较字符串的内容，这是因为哈希函数在映射的时候可能存在冲突。


# 32、下列对接口的说法，正确的是(B)
A.接口与抽象类是相同的概念
B.若要实现一个接口为普通类则必须实现接口的所有抽象方法
C.接口之间不能有继承关系
D.一个类只能实现一个接口

# 33、下面哪个选项是main方法的返回类型？（B）
A.int
B.void
C.Boolean
D.static

java中类的主方法定义如下
```prettyprint
class Demo{
    public static void main(String args[]){
        //代码段
    }
}
```

# 34、编译 Java 源程序文件产生的字节码文件的扩展名为（B）
A.java
B.class
C.html
D.exe


# 35、以下代码执行后输出结果为（B）

```prettyprint
public class ExceptionTest{
    public void method(){
        try{
            System.out.println("进入到try块");
        }
        catch (Exception e){
            System.out.println("异常发生了！");
        }
        finally{
            System.out.println("进入到finally块");
        }
        System.out.println("后续代码");
    }
    
    public static void main(String[] args){
        ExceptionTest test = new ExceptionTest();
        test.method();
    }
}
```
A.进入到try块  异常发生了！  进入到finally块  后续代码
B.进入到try块  进入到finally块  后续代码
C.进入到try块  后续代码
D.异常发生了！  后续代码


# 36、以下程序的运行结果是（B）

```prettyprint
public class Increment{
    public static void main(String args[]){
        int a;
        a = 6;
        System.out.print(a);
        System.out.print(a++);
        System.out.print(a);
    }
}
```
A.666
B.667
C.677
D.676

a++可以理解为当访问a之后再对a进行加一操作


# 37、关于抽象类叙述正确的是？（B）
A.抽象类不能实现接口
B.抽象类必须有“abstract class”修饰
C.抽象类必须包含抽象方法
D.抽象类也有类的特性，可以被实例化

# 38、以下说法错误的是（C）
A.数组是一个对象
B.数组不是一种原生类
C.数组的大小可以任意改变
D.在Java中，数组存储在堆中连续内存空间里

在java中,数组是一个对象, 不是一种原生类,对象所以存放在堆中,又因为数组特性,是连续的,只有C不对


# 39、以下关于Object类的说法正确的是（A）
A.Java中所有的类都直接或间接继承自Object，无论是否明确的指明，无论其是否是抽象类。
B.Java中的接口(interface)也继承了Object类
C.利用“==”比较两个对象时，Java调用继承自Object的equals方法，判断是否相等。
D.如果类的定义中没有重新定义toString()方法，则该类创建的对象无法使用toStrig()方法。

# 40、下面代码运行结果是？（A）

```prettyprint
public class Test{
    static boolean foo(char c){
        System.out.print(c);
        return true;
    }
    public static void main( String[] argv ){
        int i = 0;
        for ( foo('A'); foo('B') && (i < 2); foo('C')){
            i++ ;
            foo('D');
        }
    }
}
```

A.ABDCBDCB
B.ABCDABCD
C.Compilation fails.
D.An exception is thrown at runtime.

```prettyprint
for(条件1;条件2;条件3) {
    //语句
}
```

执行顺序是条件1->条件2->语句->条件3->条件2->语句->条件3->条件2........
如果条件2为true，则一直执行。如果条件2位false，则for循环结束

# 41、以下程序运行的结果为 (A)
```prettyprint
public class Example extends Thread {
    @Override
    public void run() {
        try {
            Thread.sleep(1000);
        } catch(InterruptedException e) {
            e.printStackTrace();
        }
        System.out.print("run");
    }

    public static void main(String[] args) {
        Example example = new Example();
        example.run();
        System.out.print("main");
    }
}
```

A.run main
B.main run
C.main
D.不能确定

此题的争议点只可能是runmain或mainrun

因为Example的run方法里面休眠了100ms，在当今电脑计算性能过剩的时代，如果是多线程启动，main方法肯定会打印出了main。
为啥是runmain而不是mainrun呢？
因为启动线程是调用start方法。
把线程的run方法当普通方法，就直接用实例.run()执行就好了。
没有看到start。所以是普通方法调用。
所以选A。


# 42、下列哪个说法是正确的（D）
A.ConcurrentHashMap使用synchronized关键字保证线程安全
B.HashMap实现了Collction接口
C.Array.asList方法返回java.util.ArrayList对象
D.SimpleDateFormat是线程不安全的


# 43、下面哪种情况会导致持久区jvm堆内存溢出？（C）
A.循环上万次的字符串处理
B.在一段代码内申请上百M甚至上G的内存
C.使用CGLib技术直接操作字节码运行，生成大量的动态类
D.不断创建对象

Java中堆内存分为两部分，分别是permantspace和heap space。permantspace（持久区）主要存放的是Java类定义信息，与垃圾收集器要收集的Java对象关系不大。持久代溢出通常由于持久代设置过小，动态加载了大量Java类，因此C选项正确。
heap space分为年轻代和年老代， 年老代常见的内存溢出原因有循环上万次的字符串处理、在一段代码内申请上百M甚至上G的内存和创建成千上万的对象，也就是题目中的ABD选项。

# 44、如下代码，执行test()函数后，屏幕打印结果为（D）
```prettyprint
public class Test2{
    public void add(Byte b){
        b = b++;
    }
    public void test(){
        Byte a = 127;
        Byte b = 127;
        add(++a);
        System.out.print(a + " ");
        add(b);
        System.out.print(b + "");
    }
}
```
A.127 127
B.128 127
C.129 128
D.以上都不对

public void add(Byte b){ b=b++; } 这里涉及java的自动装包/自动拆包(AutoBoxing/UnBoxing) Byte的首字母为大写，是类，看似是引用传递，但是在add函数内实现++操作，会自动拆包成byte值传递类型，所以add函数还是不能实现自增功能。也就是说add函数只是个摆设，没有任何作用。 Byte类型值大小为-128~127之间。 add(++a);这里++a会越界，a的值变为-128 add(b); 前面说了，add不起任何作用，b还是127


# 45、对于文件的描述正确的是（D）
A.文本文件是以“.txt”为后缀名的文件，其他后缀名的文件是二进制文件。
B.File类是Java中对文件进行读写操作的基本类。
C.无论文本文件还是二进制文件，读到文件末尾都会抛出EOFException异常。
D.Java中对于文本文件和二进制文件，都可以当作二进制文件进行操作。


# 46、下列代码执行结果为（A）
```prettyprint
public static void main(String args[])throws InterruptedException{
    Thread t=new Thread(new Runnable() {
        public void run() {
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            System.out.print("2");
        }
    });
    t.start();

    t.join();
    System.out.print("1");
}
```
A.21
B.12
C.可能为12，也可能为21
D.以上答案都不对

thread.Join把指定的线程加入到当前线程，可以将两个交替执行的线程合并为顺序执行的线程。比如在线程B中调用了线程A的Join()方法，直到线程A执行完毕后，才会继续执行线程B。
t.join();      //使调用线程 t 在此之前执行完毕。
t.join(1000);  //等待 t 线程，等待时间是1000毫秒



# 47、下面代码输出是？（C）
```prettyprint
enum AccountType{
    SAVING, FIXED, CURRENT;
    private AccountType(){
        System.out.println("It is a account type");
    }
}

class EnumOne{
    public static void main(String[]args){
        System.out.println(AccountType.FIXED);
    }
}
```
A.编译正确，输出”It is a account type”once followed by”FIXED”
B.编译正确，输出”It is a account type”twice followed by”FIXED”
C.编译正确，输出”It is a account type”thrice followed by”FIXED”
D.编译正确，输出”It is a account type”four times followed by”FIXED”
E.编译错误


枚举类有三个实例，故调用三次构造方法，打印三次It is a account type


# 48、阅读如下代码。 请问，对语句行 test.hello(). 描述正确的有（A）

```prettyprint
package NowCoder;

class Test {
    public static void hello() {
        System.out.println("hello");
    }
}

public class MyApplication {
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        Test test=null;
        test.hello();
    }
}
```

A.能编译通过，并正确运行
B.因为使用了未初始化的变量，所以不能编译通过
C.以错误的方式访问了静态方法
D.能编译通过，但因变量为null，不能正常运行

因为Test类的hello方法是静态的，所以是属于类的，当实例化该类的时候，静态会被优先加载而且只加载一次，所以不受实例化new Test();影响，只要是使用到了Test类，都会加载静态hello方法！
另外，在其他类的静态方法中也是可以调用公开的静态方法，此题hello方法是使用public修饰的所以在MyApplication中调用hello也是可以的。
总结：即使Test test=null;这里也会加载静态方法，所以test数据中包含Test类的初始化数据。（静态的，构造的，成员属性）因此test.hello是会调用到hello方法的。


# 49、存根（Stub）与以下哪种技术有关（B）
A.交换
B.动态链接
C.动态加载
D.磁盘调度


# 50、（A）运算符和（B）运算符分别把一个值的位向左和向右移动
A.<<
B.>>
C.&&
D.||


# 51、对于jdk1.8,以下为 java 语法保留不能作为类名和方法名使用的是（A、B、C、D）
A.default
B.int
C.implements
D.throws

# 52、下列选项中属于面向对象程序设计语言特征的是（A、B、D）
A.继承性
B.多态性
C.相似性
D.封装性


# 53、下面哪些类实现或继承了 Collection 接口？（B、C）
A.HashMap
B.ArrayList
C.Vector
D.Iterator


# 54、对Collection和Collections描述正确的是（B、D）
A.Collection是java.util下的类，它包含有各种有关集合操作的静态方法
B.Collection是java.util下的接口，它是各种集合结构的父接口
C.Collections是java.util下的接口，它是各种集合结构的父接口
D.Collections是java.util下的类，它包含有各种有关集合操作的静态方法

java.util.Collection 是一个集合接口。它提供了对集合对象进行基本操作的通用接口方法。Collection接口在Java 类库中有很多具体的实现。Collection接口的意义是为各种具体的集合提供了最大化的统一操作方式。
java.util.Collections 是一个包装类。它包含有各种有关集合操作的静态多态方法。此类不能实例化，就像一个工具类，服务于Java的Collection框架。


# 55、下面有关java类加载器，说法正确的是？（A、B、C、D）
A.引导类加载器（bootstrap class loader）：它用来加载 Java 的核心库，是用原生代码来实现的
B.扩展类加载器（extensions class loader）：它用来加载 Java 的扩展库。
C.系统类加载器（system class loader）：它根据 Java 应用的类路径（CLASSPATH）来加载 Java 类
D.tomcat为每个App创建一个Loader，里面保存着此WebApp的ClassLoader。需要加载WebApp下的类时，就取出ClassLoader来使用


jvm classLoader architecture :
a、Bootstrap ClassLoader/启动类加载器
主要负责jdk_home/lib目录下的核心 api 或 -Xbootclasspath 选项指定的jar包装入工作.
B、Extension ClassLoader/扩展类加载器
主要负责jdk_home/lib/ext目录下的jar包或 -Djava.ext.dirs 指定目录下的jar包装入工作
C、System ClassLoader/系统类加载器
主要负责java -classpath/-Djava.class.path所指的目录下的类与jar包装入工作.
B、 User Custom ClassLoader/用户自定义类加载器(java.lang.ClassLoader的子类)
在程序运行期间, 通过java.lang.ClassLoader的子类动态加载class文件, 体现java动态实时类装入特性.


# 56、在你面前有一个n阶的楼梯，你一步只能上1阶或2阶。请问，当N=11时，你可以采用多少种不同的方式爬完这个楼梯（B）,当N=9时呢呢（C）？
A.11
B.144
C.55
D.89


# 57、关于Java中的数组，下面的一些描述，哪些描述是准确的：（A、C、F）
A.数组是一个对象，不同类型的数组具有不同的类
B.数组长度是可以动态调整的
C.数组是一个连续的存储结构
D.一个固定长度的数组可类似这样定义: int array[100]
E.两个数组用equals方法比较时，会逐个遍历其中的元素，对每个元素进行比较
F.可以二维数组，且可以有多维数组，都是在Java中合法的


当数组的初始化完成后数组在内存中所占用的空间将会被固定，即使我们清空这个数组中的元素，它所占用的空间依然会被保留。这造成了Java数组长度的不可变，选项B错误。

Java语言中，数组是一种引用类型的变量，使用它定义变量时，这个引用变量还没有指向任何有效的内存空间，因此定义数组时不能指定数组的长度。而由于这个引用变量并没有指向任何有效的内存空间，所以没有空间来存储任何元素，只有当对数组初始化后，才可以使用这个数组。D选项正确的定义方式为int[] array =new int[100]。

本题易错点是E选项，数组是一种引用数据类型，继承自Object类的，所以其中也包含了未被重写的equals()方法，所有的引用变量都能调用equals()方法来判断他是否与其他引用变量相等，使用这个方法来判断两个引用对象是否相等的判断标准与使用==运算符没有区别，只有在两个引用变量指向同一个对象才会返回true。如果想达到E选项描述的效果，需要使用Arrays.equals()方法。


# 58、只有实现了(A)接口的类，其对象才能序列化。
A.Serializable
B.Cloneable
C.Comparable
D.Writeable

Serializable要实现序列化对象必须要实现的接口


# 59、下列叙述错误的是（C）
A.java程序的输入输出功能是通过流来实现的
B.java中的流按照处理单位可分成两种：字节流和字符流
C.InputStream是一个基本的输出流类。
D.通过调用相应的close()方法关闭输入输出流


# 60、下列选项中，用于在定义子类时声明父类名的关键字是：(C)
A.interface
B.package
C.extends 
D.class


# 61、java有8种基本类型，请问byte、int、long、char、float、double、boolean各占多少个字节？（B）
A.1 2 8 2 4 8 1
B.1 4 8 2 4 8 1
C.1 4 4 2 4 4 2
D.1 4 4 2 4 8 2


# 62、现有一变量声明为 boolean aa; 下面赋值语句中正确的是（A）
A.aa=false;
B.aa=False;
C.aa="true";
D.aa=0;


# 63、执行如下代码后输出结果为（C）
```prettyprint
public class Test {
    public static void main(String[] args) {
        System.out.println("return value of getValue(): " + getValue());
    }
    public static int getValue() {
        int i = 1;
        try {
            i = 4;
        } finally{
            i++;
            return i;
        }
    }
}
```
A.return value of getValue(): 1
B.return value of getValue(): 4
C.return value of getValue(): 5
D.其他几项都不对

当Java程序执行try块、catch块时遇到了return或throw语句，这两个语句都会导致该方法立即结束，但是系统执行这两个语句并不会结束该方法，而是去寻找该异常处理流程中是否包含finally块，如果没有finally块，程序立即执行return或throw语句，方法终止；如果有finally块，系统立即开始执行finally块。只有当finally块执行完成后，系统才会再次跳回来执行try块、catch块里的return或throw语句；如果finally块里也使用了return或throw等语句，finally块会终止方法，系统将不会跳回去执行try块、catch块里的任何代码。综上所述，答案选择C。

# 64、以下（C）不是合法的标识符？
A.STRING
B.x3x
C.void
D.deSf

void属于java中的关键字
[1]Java标识符只能由数字、字母、下划线“_”或“$”符号以及Unicode字符集组成
[2]Java标识符必须以字母、下划线“_”或“$”符号以及Unicode字符集开头
[3]Java标识符不可以是Java关键字、保留字（const、goto）和字面量（true、false、null）
[4]Java标识符区分大小写，是大小写敏感的


# 65、以下定义一维数组的语句中，正确的是：（D）
A.int a [10];
B.int a []=new [10];
C.int a []=new int [5]{1,2,3,4,5};
D.int a []={1,2,3,4,5};


# 66、以下关于 abstract 关键字的说法，正确的是（D）
A.abstract 可以与final 并列修饰同一个类。
B.abstract 类中不可以有private的成员。
C.abstract 类中必须全部是abstract方法。
D.abstract 方法必须在abstract类或接口中。


# 67、下列外部类定义中，不正确的是（C）
A.class x { .... }
B.class x extends y { .... }
C.static class x implements y1,y2 { .... }
D.public class x extends Applet { .... }


# 68、判断对错。List，Set，Map都继承自继承Collection接口。（B）
A.对
B.错

List，Set等集合对象都继承自Collection接口
Map是一个顶层结果，不继承自Collection接口


# 69、假设num已经被创建为一个ArrayList对象，并且最初包含以下整数值：[0，0，4，2，5，0，3，0]。 执行下面的方法numQuest()，数组num会变成？（D）

```prettyprint
private List<Integer> nums;

public void numQuest() {
    int k = 0;
    Integer zero = new Integer(0);
    while (k < nums.size()) {
        if (nums.get(k).equals(zero))
            nums.remove(k);
        k++;
    }
}
```
A.[3, 5, 2, 4, 0, 0, 0, 0]
B.[0, 0, 0, 0, 4, 2, 5, 3]
C.[0, 0, 4, 2, 5, 0, 3, 0]
D.[0, 4, 2, 5, 3]


# 70、以下叙述正确的是（D）
A.实例方法可直接调用超类的实例方法
B.实例方法可直接调用超类的类方法
C.实例方法可直接调用子类的实例方法
D.实例方法可直接调用本类的实例方法


A错误，类的实例方法是与该类的实例对象相关联的，不能直接调用，只能通过创建超类的一个实例对象，再进行调用
B错误，当父类的类方法定义为private时，对子类是不可见的，所以子类无法调用
C错误，子类具体的实例方法对父类是不可见的，所以无法直接调用， 只能通过创建子类的一个实例对象，再进行调用
D正确，实例方法可以调用自己类中的实例方法



# 71、以下代码段执行后的输出结果为（D）

```prettyprint
public class Test {
    public static void main(String args[]) {
        int x = -5;
        int y = -12;
        System.out.println(y % x);
    }
}
```
A.-1
B.2
C.1
D.-2


# 72、当你编译和运行下面的代码时，会出现下面选项中的哪种情况？（B）
```prettyprint
public class Pvf{
    static boolean Paddy;
    public static void main(String args[]){
        System.out.println(Paddy);
    }
}
```
A.编译时错误
B.编译通过并输出结果false
C.编译通过并输出结果true
D.编译通过并输出结果null

类中声明的变量有默认初始值；方法中声明的变量没有默认初始值，必须在定义时初始化，否则在访问该变量时会出错。
boolean类型默认值是false



# 73、关于下列程序段的输出结果，说法正确的是：（D）
```prettyprint
public class MyClass{
    static int i;
    public static void main(String argv[]){
        System.out.println(i);
    }
}
```

A.有错误，变量i没有初始化。
B.null
C.1
D.0


# 74、检查程序，是否存在问题，如果存在指出问题所在，如果不存在，说明输出结果。（C）
```prettyprint
public class HelloB extends HelloA {
    public HelloB(){}{
        System.out.println("I’m B class");
    }
    static{
        System.out.println("static B");
    }
    public static void main(String[] args){
        new HelloB();
    }
}

class HelloA{
    public HelloA(){}
    {
        System.out.println("I’m A class");
    }
    static
    {
        System.out.println("static A");
    }
}
```

A.static A
I’m A class
static B
I’m B class

B.I’m A class
I’m B class
static A
static B

C.static A
static B
I’m A class
I’m B class

D.I’m A class
static A
I’m B class
static B


其中涉及：静态初始化代码块、构造代码块、构造方法
当涉及到继承时，按照如下顺序执行：
1、执行父类的静态代码块

```prettyprint
static {
    System.out.println("static A");
}
```

输出:static A

2、执行子类的静态代码块

```prettyprint
static {
    System.out.println("static B");
}
```

输出:static B
3、执行父类的构造代码块

```prettyprint
{
    System.out.println("I’m A class");
}
```

输出:I'm A class
4、执行父类的构造函数

```prettyprint
public HelloA() {
}
```

输出：无
5、执行子类的构造代码块

```prettyprint
{
    System.out.println("I’m B class");
}
```

输出:I'm B class
6、执行子类的构造函数

```prettyprint
public HelloB() {
}
```

输出：无

那么，最后的输出为：
static A
static B
I'm A class
I'm B class
正确答案：C


# 75、以下代码的运行结果是什么(A)
```prettyprint
class Supper{     
    public int get()    {          
        System.out.println("Supper");         
        return 5;     
    }    
}     

public class Sub{ 
    public int get(){         
        System.out.println("Sub");        
        return new Integer("5");          
    }      
    public static void main(String args[]) {          
        new Supper().get();        
        new Sub().get();          
    }   
}
```

A.Supper Sub
B.Supper 5 Sub
C.Supper 5 5 Sub
D.Supper Sub 5 5


# 76、设有下面两个赋值语句，下述说法正确的是（D）

a = Integer.parseInt("1024");
b = Integer.valueOf("1024").intValue();

A.a是整数类型变量，b是整数类对象。
B.a是整数类对象，b是整数类型变量。
C.a和b都是整数类对象并且它们的值相等。
D.a和b都是整数类型变量并且它们的值相等。


# 77、非抽象类实现接口后，必须实现接口中的所有抽象方法，除了abstract外，方法头必须完全一致。（B）
A.正确
B.错误


# 78、Java1.8之后，Java接口的修饰符可以为（D）
A.private
B.protected
C.final
D.abstract


# 79、以下哪项陈述是正确的？（E）
A.垃圾回收线程的优先级很高，以保证不再使用的内存将被及时回收
B.垃圾收集允许程序开发者明确指定释放哪一个对象
C.垃圾回收机制保证了JAVA程序不会出现内存溢出
D.进入”Dead”状态的线程将被垃圾回收器回收
E.以上都不对

A: 垃圾回收在jvm中优先级相当相当低。
B：垃圾收集器（GC）程序开发者只能推荐JVM进行回收，但何时回收，回收哪些，程序员不能控制。
C：垃圾回收机制只是回收不再使用的JVM内存，如果程序有严重BUG，照样内存溢出。
D：进入DEAD的线程，它还可以恢复，GC不会回收

# 80、下面叙述那个是正确的？（B）
A. java中的集合类（如Vector）可以用来存储任何类型的对象，且大小可以自动调整。但需要事先知道所存储对象的类型，
才能正常使用。
B.在java中，我们可以用违例（Exception）来抛出一些并非错误的消息，但这样比直接从函数返回一个结果要更大的系统开销。
C.java接口包含函数声明和变量声明。
D.java中，子类不可以访问父类的私有成员和受保护的成员。

# 81、java关于异常处理机制的叙述哪些正确（B、C）
A.catch部分捕捉到异常情况时，才会执行finally部分
B.当try区段的程序发生异常时，才会执行catch区段的程序
C.在try区段不论程序是否发生异常及捕获到异常，都会执行finally部分
D.以上都是

Java处理异常的语句由try、catch、finally三部分组成。try块用于包裹业务代码，catch块用于捕获并处理某个类型的异常，finally块则用于回收资源。finally块能够成功回收资源的原因就是无论是否发生异常，finally块一定会执行（一般情况下）。选项A错误，D错误


# 82、以下关于final关键字说法错误的是（A、C）
A.final是java中的修饰符，可以修饰类、接口、抽象类、方法和属性
B.final修饰的类不能被继承
C.final修饰的方法不能被重载
D.final修饰的变量不允许被再次赋值


# 83、下列描述正确的是（A、C）
A.类不可以多继承而接口可以多实现
B.抽象类自身可以定义成员而接口不可以
C.抽象类和接口都不能被实例化
D.一个类可以有多个直接基类和多个基接口


# 84、在Java中下面Class的声明哪些是错误的？（A、B、C）
```prettyprint
A.public abstract final class Test {
    abstract void method();
}

B.public abstract class Test {
    abstract final void method();
}

C.public abstract class Test {
    abstract void method() {
	}
}

D.public class Test {
    final void method() {
	
	}
}
```


# 85、以下各类中哪几个是线程安全的？(B、C、D)
A.ArrayList
B.Vector
C.Hashtable
D.Stack


# 86、关于容器下面说法正确的是？ (D)
A.列表(List)和集合(Set)存放的元素都是可重复的。
B.列表(List)和集合(Set)存放的元素都是不可重复的。
C.映射(Map)<key,value>中key是可以重复的。
D.映射(Map)<key,value>中value是可以重复的。


# 87、“先进先出”的容器是：(B)
A.堆栈(Stack)
B.队列（Queue）
C.字符串(String)
D.迭代器(Iterator)


# 88、HashSet子类依靠什么方法区分重复元素。（C）
A.toString(),equals()
B.clone(),equals()
C.hashCode(),equals()
D.getClass(),clone()

HashSet内部使用Map保存数据，即将HashSet的数据作为Map的key值保存，这也是HashSet中元素不能重复的原因。而Map中保存key值前，会去判断当前Map中是否含有该key对象，内部是先通过key的hashCode，确定有相同的hashCode之后，再通过equals方法判断是否相同。


# 89、类中的数据域使用private修饰为私有变量，所以任何方法均不能访问它。（B）
A.正确
B.错误  


# 90、Java 语言中创建一个对象使用的关键字是（C）
A.class
B.interface
C.new
D.create


# 91、下面哪个选项是main方法的返回类型？（B）
A.int
B.void
C.Boolean
D.static

java中类的主方法定义如下

```prettyprint
class Demo{
    public static void main(String args[]){
    //代码段
    }
}
```

# 92、一个类中，有两个方法名、形参类型、顺序和个数都完全一样，返回值不一样的方法,这种现象叫覆盖。（B）
A.正确
B.错误

# 93、以下类定义中的错误是什么？（C）
```prettyprint
abstract class xy{
    abstract sum (int x, int y) { }
}
```
A.没有错误
B.类标题未正确定义
C.方法没有正确定义
D.没有定义构造函数


# 93、定义类中成员变量时不可能用到的修饰是（B）
A.final
B.void
C.protected
D.static

# 94、类Test1定义如下:（C）
```prettyprint
public class Test1{//1
    public float aMethod(float a,float b){}//2 
    //3
}//4
```
将以下哪种方法插入行3是不合法的。
A.public int aMethod(int a,int b){}
B.private float aMethod(int a,int b,int c){}
C.public float aMethod(float a,float b){}
D.public float aMethod(float a,float b,float c){}

关于方法的重载： 方法重载是指在一个类中定义多个同名的方法，但要求每个方法具有不同的参数的类型或参数的个数。调用重载方法时，Java编译器能通过检查调用的方法的参数类型和个数选择一个恰当的方法。方法重载通常用于创建完成一组任务相似但参数的类型或参数的个数不同的方法。

方法重载具体规范
一.方法名一定要相同。
二.方法的参数表必须不同，包括参数的类型或个数，以此区分不同的方法体。
三.方法的返回类型、修饰符可以相同，也可不同。



# 95、一个文件中的数据要在控制台上显示，首先需要（C）。
A.System.out.print (buffer[i]);
B.FileOutputStream fout = new FileOutputStream(this.filename);
C.FileInputStream fin = new FileInputStream(this.filename);。
D.System.in.read(buffer)。

# 96、若有下列定义，下列哪个表达式返回false？（B）
```prettyprint
String s = "hello";
String t = "hello";
char c[] = {'h', 'e', 'l', 'l', 'o'} ;
```

A.s.equals(t);
B.t.equals(c);
C.s==t;
D.t.equals(new String("hello"));  

Java又不是C++，什么时候字符数组等于字符串了(对这句话我不负责任)？
而常量池中的字符串，只有变量名不同是可以用双等号判断是否相等的，内存都是常量池中的字符串。
但是new出来的字符串，只能用equals，用双等号是不相等的，因为是两个内存对象。

```prettyprint
public class HelloWorld {
    public static void main(String []args) {
        String s = "hello";
        String t = "hello";
        char c[] = {'h','e','l','l','o'} ;
        System.out.println(s.equals(t));
        //c++中定义的东西，不要在java中混为一谈。(对这句话我不负责任)
        System.out.println(t.equals(c));
        System.out.println(s==t);
        System.out.println(t.equals(new String("hello")));
        //这个不相等，因为语句中new的字符串不在常量池，是在堆
        System.out.println(t==new String("hello"));
        //这样可以判断字符数组与字符串是否包含同样的字符序列
        System.out.println(t.equals(new String(c)));
    }
}
```

# 97、内部类（也叫成员内部类）可以有4种访问权限。（A）
A.正确
B.错误

# 98、如果一个接口Cow有个public方法drink()，有个类Calf实现接口Cow，则在类Calf中正确的是？(C)
A.void drink() { …}
B.protected void drink() { …}
C.public void drink() { …}
D.以上语句都可以用在类Calf中


# 99、关于 Socket 通信编程，以下描述错误的是：（D）
A.服务器端通过new ServerSocket()创建TCP连接对象
B.服务器端通过TCP连接对象调用accept()方法创建通信的Socket对象
C.客户端通过new Socket()方法创建通信的Socket对象
D.客户端通过new ServerSocket()创建TCP连接对象


# 100、下面哪个修饰符修饰的变量是所有同一个类生成的对象共享的（C）
A.public
B.private
C.static
D.final


# 101、关于Java中参数传递的说法，哪个是错误的？（D）
A.在方法中，修改一个基础类型的参数不会影响原始参数值
B.在方法中，改变一个对象参数的引用不会影响到原始引用
C.在方法中，修改一个对象的属性会影响原始对象参数
D.在方法中，修改集合和Maps的元素不会影响原始集合参数


# 102、关于访问权限说法正确的是（B）
A.外部类前面可以修饰public,protected和private
B.成员内部类前面可以修饰public,protected和private
C.局部内部类前面可以修饰public,protected和private
D.以上说法都不正确


# 103、关于ASCII码和ANSI码，以下说法不正确的是（D）
A.标准ASCII只使用7个bit
B.在简体中文的Windows系统中，ANSI就是GB2312
C.ASCII码是ANSI码的子集
D.ASCII码都是可打印字符

# 104、下面代码输出结果是？（B）
```prettyprint
class C {
    C() {
        System.out.print("C");
    }
}
class A {
    C c = new C();
    A() {
        this("A");
        System.out.print("A");
    }
    A(String s) {
        System.out.print(s);
    }
}

class Test extends A {
    Test() {
        super("B");
        System.out.print("B");
    }
    public static void main(String[] args) {
        new Test();
    }
}
```

A.BB
B.CBB
C.BAB
D.None of the above
        
初始化过程是这样的： 
1.首先，初始化父类中的静态成员变量和静态代码块，按照在程序中出现的顺序初始化； 
2.然后，初始化子类中的静态成员变量和静态代码块，按照在程序中出现的顺序初始化； 
3.其次，初始化父类的普通成员变量和代码块，在执行父类的构造方法；
4.最后，初始化子类的普通成员变量和代码块，在执行子类的构造方法； 
（1）初始化父类的普通成员变量和代码块，执行 C c = new C(); 输出C 
（2）super("B"); 表示调用父类的构造方法，不调用父类的无参构造函数，输出B 
（3） System.out.print("B"); 
 所以输出CBB


# 105、以下程序段执行后将会有个字节被写入到文件afile.txt中。（C）
```prettyprint
try {
    FileOutputStream fos = new FileOutputStream("afile.txt");
    DataOutputStream dos = new DataOutputStream(fos);
    dos.writeInt(3);
    dos.writeChar(1);
    dos.close();
    fos.close();
} catch (IOException e) {}
```

A.3
B.5
C.6
D.不确定，与软硬件环境相关


# 106、已知 boolean result = false，则下面哪个选项是合法的：（B、D）
A.result=1
B.result=true;
C.if(result!=0) {//so something…}
D.if(result) {//do something…}


# 107、下面哪些类实现或继承了 Collection 接口？（B、C）
A.HashMap
B.ArrayList
C.Vector
D.Iterator


# 108、ArrayLists和LinkedList的区别，下述说法正确的有？（A、B、C、D）
A.ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。
B.对于随机访问get和set，ArrayList绝对优于LinkedList，因为LinkedList要迭代器。
C.对于新增和删除操作add和remove，LinkedList比较占优势，因为ArrayList要移动数据。
D.ArrayList的空间浪费主要体现在在list列表的结尾预留一定的容量空间，而LinkedList的空间花费则体现在它的每一个元素都需要消耗相当的空间。


# 109、以下说法中正确的有？（A、D）
A.StringBuilder是 线程不安全的
B.Java类可以同时用 abstract和final声明
C.HashMap中，使用 get(key)==null可以 判断这个Hasmap是否包含这个key
D.volatile关键字不保证对变量操作的原子性


# 110、String s=null;下面哪个代码片段可能会抛出NullPointerException？（A、C）
A.if((s!=null)&(s.length()>0))
B.if((s!=null)&&(s.length()>0))
C.if((s==null)|(s.length()==0))
D.if((s==null)||(s.length()==0))


s为null，因此只要调用了s.length()都会抛出空指针异常。因此这个题目就是考察if语句的后半部分会不会执行。
A，单个与操作的符号& 用在整数上是按位与，用在布尔型变量上跟&&功能类似，但是区别是无论前面是否为真，后面必定执行，因此抛出异常
B，与操作，前半部分判断为假，后面不再执行
C，这里跟 & 和&& 的区别类似，后面必定执行，因此抛出异常
D，或语句，前面为真，整个结果必定为真，后面不执行


# 111、关于Java中的数组，下面的一些描述，哪些描述是准确的：（A、C、F）
A.数组是一个对象，不同类型的数组具有不同的类
B.数组长度是可以动态调整的
C.数组是一个连续的存储结构
D.一个固定长度的数组可类似这样定义: int array[100]
E.两个数组用equals方法比较时，会逐个遍历其中的元素，对每个元素进行比较
F.可以二维数组，且可以有多维数组，都是在Java中合法的

当数组的初始化完成后数组在内存中所占用的空间将会被固定，即使我们清空这个数组中的元素，它所占用的空间依然会被保留。这造成了Java数组长度的不可变，选项B错误。

Java语言中，数组是一种引用类型的变量，使用它定义变量时，这个引用变量还没有指向任何有效的内存空间，因此定义数组时不能指定数组的长度。而由于这个引用变量并没有指向任何有效的内存空间，所以没有空间来存储任何元素，只有当对数组初始化后，才可以使用这个数组。D选项正确的定义方式为int[] array =new int[100]。

本题易错点是E选项，数组是一种引用数据类型，继承自Object类的，所以其中也包含了未被重写的equals()方法，所有的引用变量都能调用equals()方法来判断他是否与其他引用变量相等，使用这个方法来判断两个引用对象是否相等的判断标准与使用==运算符没有区别，只有在两个引用变量指向同一个对象才会返回true。如果想达到E选项描述的效果，需要使用Arrays.equals()方法。


# 112、Hashtable 和 HashMap 的区别是（B）
A.Hashtable 是一个哈希表，该类继承了 AbstractMap，实现了 Map 接口
B.HashMap 是内部基于哈希表实现，该类继承AbstractMap，实现Map接口
C.Hashtable 线程安全的，而 HashMap 是线程不安全的
D.Properties 类 继承了 Hashtable 类，而 Hashtable 类则继承Dictionary 类
E.HashMap允许将 null 作为一个 entry 的 key 或者 value，而 Hashtable 不允许。

C D E     Hashtable：
（1）Hashtable 是一个散列表，它存储的内容是键值对(key-value)映射。
（2）Hashtable 的函数都是同步的，这意味着它是线程安全的。它的key、value都不可以为null。
（3）HashTable直接使用对象的hashCode。
HashMap：
（1）由数组+链表组成的，基于哈希表的Map实现，数组是HashMap的主体，链表则是主要为了解决哈希冲突而存在的。
（2）不是线程安全的，HashMap可以接受为null的键(key)和值(value)。
（3）HashMap重新计算hash值      
Hashtable,HashMap,Properties继承关系如下：

```prettyprint
public class Hashtable<K,V> extends Dictionary<K,V>
    implements Map<K,V>, Cloneable, java.io.Serializable

public class HashMap<K,V>extends AbstractMap<K,V> implements Map<K,V>, Cloneable, Serializable
java.lang.Objecct
  java.util.Dictionary<K,V>
    java.util.Hashtable<Object,Object>
      java.util.Properties 
```


# 113、下列哪些方法是针对循环优化进行的（A，B，D）
A.强度削弱
B.删除归纳变量
C.删除多余运算
D.代码外提


# 114、下列正确的有（A、C、D）
A.call by value不会改变实际参数的数值
B.call by reference能改变实际参数的参考地址
C.call by reference不能改变实际参数的参考地址
D.call by reference能改变实际参数的内容

参考答案：选ACD。该题考察的是值传递和引用传递参数的调用。 值传递是将变量的一个副本传递到方法中，方法中如何操作该变量副本，都不会改变原变量的值。 引用传递是将变量的内存地址传递给方法，方法操作变量时会找到保存在该地址的变量，对其进行操作。会对原变量造成影响。


# 115、下列关于继承的哪项叙述是正确的？（D）
A.在java中类允许多继承
B.在java中一个类只能实现一个接口
C.在java中一个类不能同时继承一个类和实现一个接口
D.java的单一继承使代码更可靠

java为单继承，但可以实现多个接口


# 116、在Java中，一个类可同时定义许多同名的方法，这些方法的形式参数个数、类型或顺序各不相同，传回的值也可以不相同。这种面向对象程序的特性称为（C）
A.隐藏
B.覆盖
C.重载
D.Java不支持此特性


# 117、为Test类的一个无形式参数无返回值的方法method书写方法头，使得使用类名Test作为前缀就可以调用它，该方法头的形式为(A)
A.static  void  method（）
B.public void  method
C.protected  void  method（）
D.abstract  void method（）


# 118、设A为已知定义的类名，下列创建A类的对象a的语句正确的是(D)
A.float  A  a
B.public  a=A（）
C.A a=new  int ()
D.A  a=new  A()


# 119、以下语句输出的结果是（B）
```prettyprint
int value;
value=2;
System.out.print(value);
System.out.print(value++);
System.out.print(value);
```
A.233
B.223
C.221
D.222


# 120、以下类定义中的错误是什么？（C）
```prettyprint
abstract class xy{
    abstract sum (int x, int y) { }
}
```

A.没有错误
B.类标题未正确定义
C.方法没有正确定义
D.没有定义构造函数


# 121、有以下代码，请问输出的结果是:（A）
```prettyprint
class A{
    public A(String str){
    }
}
public class Test{
    public static void main(String[] args) {
        A classa=new A("he");
        A classb=new A("he");
        System.out.println(classa==classb);
    }
}
```

A.false
B.true
C.报错
D.以上选项都不正确


# 122、为了将包ch4导入到当前程序，可以使用的语句是（A）
A.import ch4.*;
B.package ch4.*;
C.ch4 import;
D.ch4 package;


# 123、abstract和final可以同时作为一个类的修饰符。（B）
A.正确
B.错误


# 124、下面论述正确的是（D）
A.如果两个对象的hashcode相同，那么它们作为同一个HashMap的key时，必然返回同样的值
B.如果a,b的hashcode相同，那么a.equals(b)必须返回true
C.对于一个类，其所有对象的hashcode必须不同
D.如果a.equals(b)返回true，那么a,b两个对象的hashcode必须相同

hashCode方法本质就是一个哈希函数，这是Object类的作者说明的。Object类的作者在注释的最后一段的括号中写道：将对象的地址值映射为integer类型的哈希值。但hashCode()并不完全可靠的，有时候不同的对象他们生成的hashcode也会一样，因此hashCode()只能说是大部分时候可靠。
因此我们也需要重写equals()方法，但因为重写的equals()比较全面比较复杂，会造成程序效率低下，而利用hashCode()进行对比，则只要生成一个hash值进行比较就可以了，效率很高。因此，正常的操作流程是先用hashCode()去对比两个对象，如果hashCode()不一样，则表示这两个对象肯定不相等，直接返回false,如果hashCode()相同，再对比他们的equals()。
综上所述：
equals()相等的两个对象hashCode()一定相等。
hashCode()相等的两个对象equal()不一定相等。
因此选项D正确。


# 125、类A1和类A2在同一包中，类A2有个protected的方法testA2，类A1不是类A2的子类（或子类的子类），类A1可以访问类A2的方法testA2。（A）
A.正确
B.错误


# 126、如果一个接口Cow有个public方法drink()，有个类Calf实现接口Cow，则在类Calf中正确的是？(C)
A.void drink() { …}
B.protected void drink() { …}
C.public void drink() { …}
D.以上语句都可以用在类Calf中


# 127、instanceof运算符能够用来判断一个对象是否为:（C）
A.一个类的实例
B.一个实现指定接口的类的实例
C.全部正确
D.一个子类的实例


# 128、关于以下代码的说明，正确的是（C）
```prettyprint
class StaticStuff{
    static int x=10;
    static {
        x+=5;
    }
    public static void main（String args[ ]）{
        System.out.println(“x=” + x);
    }
    static { x/=3;}
}
```
A.3行与9行不能通过编译，因为缺少方法名和返回类型
B.9行不能通过编译，因为只能有一个静态初始化器
C.编译通过，执行结果为：x=5
D.编译通过，执行结果为：x=3


# 129、Java 中，以下不是修饰符 final 作用的是(C)
A.修饰常量
B.修饰不可被继承的类
C.修饰不可变类
D.修饰不可覆盖的方法


# 130、以下是java concurrent包下的4个类，选出差别最大的一个（C）
A.Semaphone
B.ReentrantLock
C.Future
D.CountDownLatch


# 131、ArrayList和Vector主要区别是什么？（A）
A.Vector与ArrayList一样，也是通过数组实现的，不同的是Vector支持线程的同步
B.Vector与ArrayList一样，也是通过数组实现的，不同的是ArrayList支持线程的同步
C.Vector是通过链表结构存储数据，ArrayList是通过数组存储数据
D.上述说法都不正确

Vector支持线程的同步，也就是内部加锁的
但是效率低，因此在新版jdk中加入线程不安全的Arraylist


# 132、下列哪种异常是检查型异常，需要在编写程序时声明？（C）
A.NullPointerException
B.ClassCastException
C.FileNotFoundException
D.IndexOutOfBoundsException

java中的异常通常分为编译时异常和运行异常。编译时异常需要我们手动的进行捕捉处理，也就是我们用try....catch块进行捕捉处理。对于运行时异常只有在编译器在编译运行时才会出现，这些不需要我们手动进行处理。对于A、 B、 D来说都是运行时异常，因此答案为C


# 133、下面代码运行结果是？（A）

```prettyprint
public class Test{
    static boolean foo(char c){
        System.out.print(c);
        return true;
    }

    public static void main( String[] argv ){
        int i = 0;
        for ( foo('A'); foo('B') && (i < 2); foo('C')){
            i++ ;
            foo('D');
        }
    }
}
```

A.ABDCBDCB
B.ABCDABCD
C.Compilation fails.
D.An exception is thrown at runtime.

```prettyprint
for(条件1;条件2;条件3) {
    //语句
}
```

执行顺序是条件1->条件2->语句->条件3->条件2->语句->条件3->条件2........
如果条件2为true，则一直执行。如果条件2位false，则for循环结束


# 134、关于下面的程序，说法正确的是（D）
```prettyprint
1. class StaticStuff
2. {
3. static int x = 10;
4.
5. static { x += 5; }
6.
7. public static void main(String args[])
8. {
9. System.out.println(“x = ” + StaticStuff .x);
10. }
11. static
12. {x /= 3; }
13.}
```

A.第5行和12行不能编译，因为该方法没有方法名和返回值。
B.第12 行不能编译，因为只能有一个static初始化块。
C.代码编译并执行，输出结果x = 10.
D.代码编译并执行，输出结果 x = 5.
E.代码编译并执行，输出结果 x = 15. 

考察的是代码执行的顺序。
第5、12行属于static修饰的静态代码块。所以A、B说法错误。
静态代码块以及静态变量自上而下的顺序依次随着类加载而执行，所以依据题目的变量初始化：
x初始为10
x+5赋值x，结果为15
x/3赋值给x，结果为5

# 135、以下哪个类包含方法flush()？（B）
A.InputStream
B.OutputStream
C.A和B选项都包含
D.A和B选项都不包含


# 136、URL u =new URL("http://www.123.com");。如果www.123.com不存在，则返回（A）
A.http://www.123.com
B.””
C.null
D.抛出异常

正确答案: A  


# 137、一般有两种用于创建线程的方法,一是(B),二是(D)。
A.从Java.lang.Thread类派生一个新的线程类，重写它的runnable()方法
B.从Java.lang.Thread类派生一个新的线程类，重写它的run()方法
C.实现Thread接口，重写Thread接口中的run()方法
D.实现Runnable接口，重写Runnable接口中的run()方法

创建线程对象两种方式：
1.继承Thread类，重载run方法；
2.实现Runnable接口，实现run方法 


# 138、对于jdk1.8,以下为 java 语法保留不能作为类名和方法名使用的是（A、B、C、D）
B.int
C.implements
D.throws


# 139、Java多线程有几种实现方法？（A、B）
A.继承Thread类
B.实现Runnable接口
C.实现Thread接口
D.以上都不正确

两种。
1、继承Thread类，Override它的run方法；
2、实现Runnable接口，实现run方法；
由于Java只有单继承，所以，第一种方法只能继承一个Thread；第二种则可以实现多继承。


# 140、Java1.8版本之前的前提，Java特性中,abstract class和interface有什么区别（A、B、D）
A.抽象类可以有构造方法，接口中不能有构造方法
B.抽象类中可以有普通成员变量，接口中没有普通成员变量
C.抽象类中不可以包含静态方法，接口中可以包含静态方法
D.一个类可以实现多个接口，但只能继承一个抽象类。


# 141、在JAVA中，下列哪些是Object类的方法（B、C、D）
A.synchronized()
B.wait()
C.notify()
D.notifyAll()
E.sleep()

A synchronized Java语言的关键字，当它用来修饰一个方法或者一个代码块的时候，能够保证在同一时刻最多只有一个线程执行该段代码。
B C D 都是Object类中的方法    
notify():  是唤醒一个正在等待该对象的线程。  
notifyAll(): 唤醒所有正在等待该对象的线程。
E sleep 是Thread类中的方法
wait 和 sleep的区别：
wait指线程处于进入等待状态，形象地说明为“等待使用CPU”，此时线程不占用任何资源，不增加时间限制。
sleep指线程被调用时，占着CPU不工作，形象地说明为“占着CPU睡觉”，此时，系统的CPU部分资源被占用，其他线程无法进入，会增加时间限制。


# 142、以下那些代码段能正确执行(C、D)

A.

```prettyprint
public static void main(String args[]) {
    byte a = 3;
    byte b = 2;
    b = a + b;
    System.out.println(b);
}
```

B.

```prettyprint
public static void main(String args[]) {
    byte a = 127;
    byte b = 126;
    b = a + b;
    System.out.println(b);
}
```

C.

```prettyprint
public static void main(String args[]) {
    byte a = 3;
    byte b = 2;
    a+=b;
    System.out.println(b);
}
```

D.

```prettyprint
public static void main(String args[]) {
    byte a = 127;
    byte b = 127;
    a+=b;
    System.out.println(b);
}
```

# 143、下面HttpServletResponse方法调用，那些给客户端回应了一个定制的HTTP回应头：(A、B)
A.response.setHeader("X-MyHeader", "34");
B.response.addHeader("X-MyHeader", "34");
C.response.setHeader(new HttpHeader("X-MyHeader", "34"));
D.response.addHeader(new HttpHeader("X-MyHeader", "34"));
E.response.addHeader(new ServletHeader("X-MyHeader", "34"));
F.response.setHeader(new ServletHeader("X-MyHeader", "34"));


# 144、java中 String str = "hello world"下列语句错误的是？（A、B、C）
A.str+='a'
B.int strlen = str.length
C.str=100
D.str=str+100


# 145、Java Application 中的主类需包含main方法，以下哪项是main方法的正确形参？（B）
A.String  args
B.String[] args
C.Char  arg
D.StringBuffer[] args


# 146、关于Java语言的内存回收机制，下列选项中最正确的一项是（C）
A.Java程序要求用户必须手工创建一个线程来释放内存
B.Java程序允许用户使用指针来释放内存
C.内存回收线程负责释放无用内存
D.内存回收线程不能释放内存对象


A，java的内存回收是自动的，Gc在后台运行，不需要用户手动操作
B，java中不允许使用指针
D，内存回收线程可以释放无用的对象内存


# 147、下面语句正确的是（D）
A.x+1=5
B.i++=1
C.a++b=1
D.x+=1


# 148、下面关于 new 关键字的表述错误的是（D）
A.new关键字在生成一个对象时会为对象开辟内存空间
B.new关键字在生成一个对象时会调用类的构造方法
C.new关键字在生成一个对象时会将生成的对象的地址返回
D.Java中只能通过new关键字来生成一个对象


# 149、如果类的方法没有返回值，该方法的返回值类型应当是abstract。（B）
A.正确
B.错误

如果类的方法没有返回值，该方法的返回值类型应当是void。
被abstract修饰的类是抽象类，抽象类不能被实例化，但是可以被继承，也可以继承。


# 150、定义一个 接口 必须使用的关键字是（C）
A.public
B.class
C.interface
D.static


# 151、以下（C）不是合法的标识符？
A.STRING
B.x3x
C.void
D.deSf 

void属于java中的关键字
[1]Java标识符只能由数字、字母、下划线“_”或“$”符号以及Unicode字符集组成
[2]Java标识符必须以字母、下划线“_”或“$”符号以及Unicode字符集开头
[3]Java标识符不可以是Java关键字、保留字（const、goto）和字面量（true、false、null）
[4]Java标识符区分大小写，是大小写敏感的


# 152、一个类可以有多个不同名的构造函数 （不考虑内部类的情况）。（B）
A.正确
B.错误


# 153、以下代码的循环次数是（D）
```prettyprint
public class Test {
    public static void main(String args[]) {
        int i = 7;
        do {
            System.out.println(--i);
            --i;
        } while (i != 0);
        System.out.println(i);
    }
}
```
A.0
B.1
C.7
D.无限次


# 154、下列哪个类的声明是正确的？（D）
A.abstract final class HI{}
B.abstract private move(){}
C.protected private number;
D.public abstract class Car
           

A只能有final和abstract的一个，因为final是最终类，不能继承，必须可以创建实例，而abstract是抽象类，只能继承，不有实例。冲突了，所以不对。
B是抽象方法，不能有方法体。所以末尾不是{}而是；才对
C中 访问修饰符只能有一个，而且对象没有类型。
D正确，这是抽象类。



# 155、如果int x=20, y=5，则语句System.out.println(x+y +""+(x+y)+y);  的输出结果是（D）
A.2530
B.55
C.2052055
D.25255


# 156、指出下列程序运行的结果：（B）

```prettyprint
public class Example{
    String str=new String("tarena");
    char[]ch={'a','b','c'};
    public static void main(String args[]){
        Example ex=new Example();
        ex.change(ex.str,ex.ch);
        System.out.print(ex.str+" and ");
        System.out.print(ex.ch);
    }
    public void change(String str,char ch[]){
        //引用类型变量，传递的是地址，属于引用传递。
        str="test ok";
        ch[0]='g';
    }
}
```
A.tarena and abc
B.tarena and gbc
C.test ok and abc
D.test ok and gbc


# 157、java中将ISO8859-1字符串转成GB2312编码，语句为（A）
A.new String("字符串".getBytes("ISO8859-1"),"GB2312")
B.new String(String.getBytes("GB2312"）, ISO8859-1)
C.new String(String.getBytes("ISO8859-1"))
D.new String(String.getBytes("GB2312"))


# 158、假设 A 类有如下定义，设 a 是 A 类同一个包下的一个实例，下列语句调用哪个是正确的？（C）
```prettyprint
class A{
    int  i;
    static  String  s;
    void  method1() {   }
    static  void  method2()  {   }
}
```
A.System.out.println(a.i)；
B.a.method1();
C.A.method1();
D.A.method2()


# 159、下列代码的执行结果是（B）
```prettyprint
public class Test {
    public static int a = 1;
    public static void main(String[] args) {
        int a = 10;
        a++; Test.a++;
        Test t=new Test();
        System.out.println("a=" + a + " t.a=" + t.a);
    }
}
```
A.a=10 t.a=3
B.a=11 t.a=2
C.a=12 t.a=1
D.a=11 t.a=1


# 160、语句：char foo='中'，是否正确？（假设源文件以GB2312编码存储，并且以javac – encoding GB2312命令编译）（A）
A.正确
B.错误


# 161、JDK1.8版本之前，抽象类和接口的区别，以下说法错误的是（D）
A.接口是公开的，里面不能有私有的方法或变量，是用于让别人使用的，而抽象类是可以有私有方法或私有变量的。
B.abstract class 在 Java 语言中表示的是一种继承关系，一个类只能使用一次继承关系。但是，一个类却可以实现多个interface，实现多重继承。接口还有标识（里面没有任何方法，如Remote接口）和数据共享（里面的变量全是常量）的作用。
C.在abstract class中可以有自己的数据成员，也可以有非abstarct的成员方法，而在interface中，只能够有静态的不能被修改的数据成员（也就是必须是 static final的，不过在 interface中一般不定义数据成员），所有的成员方法默认都是 public abstract 类型的。
D.abstract class和interface所反映出的设计理念不同。其实abstract class表示的是"has-a"关系，interface表示的是"is-a"关系。


# 162、设有下面两个赋值语句，下述说法正确的是（D）
a = Integer.parseInt("1024");
b = Integer.valueOf("1024").intValue();

A.a是整数类型变量，b是整数类对象。
B.a是整数类对象，b是整数类型变量。
C.a和b都是整数类对象并且它们的值相等。
D.a和b都是整数类型变量并且它们的值相等。


# 163、下面代码输出是（A）
```prettyprint
double d1=-0.5;
System.out.println("Ceil d1="+Math.ceil(d1));
System.out.println("floor d1="+Math.floor(d1));
```
A.Ceil d1=-0.0
floor d1=-1.0

B.Ceil d1=0.0
floor d1=-1.0

C.Ceil d1=-0.0
floor d1=-0.0

D.Ceil d1=0.0
floor d1=0.0

E.Ceil d1=0
floor d1=-1

ceil：大于等于 x，并且与它最接近的整数。
floor：小于等于 x，且与 x 最接近的整数。


# 164、有关线程的哪些叙述是对的（B、C、D）
A.一旦一个线程被创建，它就立即开始运行。
B.使用start()方法可以使一个线程成为可运行的，但是它不一定立即开始运行。
C.当一个线程因为抢先机制而停止运行，它可能被放在可运行队列的前面。
D.一个线程可能因为不同的原因停止并进入就绪状态。


# 165、java中Hashtable, Vector, TreeSet, LinkedList哪些线程是安全的？（A、B）
A.Hashtable
B.Vector
C.TreeSet
D.LinkedList

HashTable是线程安全的
Vector是线程安全的ArrayList
TreeSet和LinkedList都不是线程安全的


# 166、以下选项中，switch语句判断条件可以接受的数据类型有哪些？（A、B、C、D）
A.int
B.byte
C.char
D.short


# 167、以下关于final关键字说法错误的是（A、C）
A.final是java中的修饰符，可以修饰类、接口、抽象类、方法和属性
B.final修饰的类肯定不能被继承
C.final修饰的方法不能被重载
D.final修饰的变量不允许被再次赋值

被final关键字修饰的类不能被继承，但抽象类存在的意义在于被其它类继承然后实现其内部方法的，这样final和抽象类之间就产生了矛盾。因此，final并不能修饰抽象类，选项A错误，选项B正确。
C选项，重载的实现是编译器根据函数的不同的参数表，对同名函数的名称做修饰，那么对于编译器而言，这些同名函数就成了不同的函数。但重写则是子类方法对父类的方法的延申，即子类不仅继承了父类的方法，还向父类的方法中添加了属于自己的内容，改变了父类方法原本的内容，而final代表了一种不可变，这明显与重写形成了冲突。因此被final修饰的类可以被重载但不能被重写，选项C错误。
当final用来修饰变量时，代表该变量不可被改变，一旦获得了初始值，该final变量就不能被重新赋值，选项D正确。故答案为AC。


# 168、ArrayLists和LinkedList的区别，下述说法正确的有？（A、B、C、D）
A.ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。
B.对于随机访问get和set，ArrayList绝对优于LinkedList，因为LinkedList要迭代器。
C.对于新增和删除操作add和remove，LinkedList比较占优势，因为ArrayList要移动数据。
D.ArrayList的空间浪费主要体现在在list列表的结尾预留一定的容量空间，而LinkedList的空间花费则体现在它的每一个元素都需要消耗相当的空间。


# 169、下列可作为java语言标识符的是（A、B、C）
A.a1
B.$1
C._1
D.11


# 170、在Java中下面Class的声明哪些是错误的？（A、B、C）

A.

```prettyprint
public abstract final class Test {
    abstract void method();
}
```

B

```prettyprint
public abstract class Test {
    abstract final void method();
}
```

C.

```prettyprint
public abstract class Test {
    abstract void method() {
    }
}
```

D.

```prettyprint
public class Test {
    final void method() {
    }
}
```


# 171、下列哪些方法是针对循环优化进行的（A、B、D）
A.强度削弱
B.删除归纳变量
C.删除多余运算
D.代码外提


# 172、执行如下程序代码（A、C）
```prettyprint
char chr = 127;
int sum = 200;
chr += 1;
sum += chr;
```
后，sum的值是（）
备注：同时考虑c/c++和Java的情况的话

A.72
B.99
C.328
D.327


# 173、区分类中重载方法的依据是(C)。
A.不同的形参名称
B.不同的返回值类型
C.不同的形参列表
D.不同的访问权限


# 174、以下不属于构造方法特征的是（D）
A.构造方法名与类名相同
B.构造方法不返回任何值，也没有返回类型
C.构造方法在创建对象时调用，其他地方不能显式地直接调用
D.每一个类只能有一个构造方法

选项描述错误，一个类可以有多个构造方法，形成重载关系。


# 175、类声明中，声明抽象类的关键字是 (B)
A.public
B.abstract
C.final
D.class

public 共有类，可以在包外使用，此时，源文件名必须和类名相同。
abstract 抽象类，抽象类位于继承树的抽象层，抽象类不能被实例化。
final  不能被继承，没有子类，final类中的方法默认是final的。
class 只能在包内使用的类


# 176、代码String str=”123456a”；int i=Integer.parseInt(str);会报异常的是（B）
A.java.lang.NullPoninterException
B.java.lang.NumberFormatException
C.java.lang.RuntimeException
D.java.lang.ArrayindexOutOfBoundsException


# 177、final方法等同于private方法（B）
A.正确
B.错误


# 178、下列关于修饰符混用的说法，错误的是(D)
A.abstract 不能与final并列修饰同一个类
B.abstract 类中不建议有private的成员
C.abstract 方法必须在abstract类或接口中
D.static 方法中能直接处理非static的属性


# 179、有以下程序片段，下列哪个选项不能插入到第一行（A）。
```prettyprint
1.
2.public  class  A{
3.//do sth
4.}
```
A.public class  MainClass{ }
B.package  mine;
C.class ANotherClass{   }
D.import  java.util.*;


# 180、下面哪个不是Java基本类型（B）
A.short
B.Boolean
C.byte
D.float

java规定类名首字母必须大写，这里可以直观的看出来Boolean是一个引用类型，不是基本数据类型。
java中的基本数据类型都对应一个引用类型，如Float是float的引用类型，Integer是int的引用类型


# 181、分析以下代码，说法正确的是（D）
```prettyprint
public static void main(String[] args) {
    System.out.println(val());
}
public static int val() {
    int num = 5;
    try {
        num = num / 0;
    } catch (Exception e) {
        num = 10;
    } finally {
        num = 15;
    }
    return num;
}
```

A.运行时报错
B.程序正常运行，输出值为5
C.程序正常运行，输出值为10
D.程序正常运行，输出值为15


# 182、类 ABC 定义如下（B）

```prettyprint
1 ． public  class  ABC{
2 ． public  int  max( int  a, int  b) {   }
3 ．
4 ． }
```

将以下哪个方法插入行 3 是不合法的。（ ）
A.public  float  max(float  a, float  b, float  c){  }
B.public  int  max (int  c,  int  d){  }
C.public  float  max(float  a,  float  b){  }
D.private  int  max(int a, int b, int c){  }


# 183、下列叙述错误的是（D）
A.在接口中定义的方法除了default和static关键字修饰的方法拥有方法体，其他方法都应是没有方法体的抽象方法（JDK1.8以后）
B.一个java类只能有一个父类,但可以实现多个接口
C.在类声明中,用implements关键字声明该类实现的接口
D.定义接口时使用implements关键字。


# 184、下列哪种异常是检查型异常，需要在编写程序时声明（C）
A.NullPointerException
B.ClassCastException
C.FileNotFoundException
D.IndexOutOfBoundsException

java中的异常通常分为编译时异常和运行异常。编译时异常需要我们手动的进行捕捉处理，也就是我们用try....catch块进行捕捉处理。对于运行时异常只有在编译器在编译运行时才会出现，这些不需要我们手动进行处理。对于A、 B、 D来说都是运行时异常，因此答案为C


# 185、下列循环语句序列执行完成后，i的值是（C）
```prettyprint
int i;
for(i=2;i<=10;i++){
    System.out.println(i);
}
```

A.2
B.10
C.11
D.不确定 


# 186、以下程序的运行结果是？（A）
```prettyprint
public class TestThread{
    public static void main(String args[]){
        Runnable runner = new Runnable(){
            @Override
            public void run(){
                System.out.print("foo");
            }
        };
        Thread t = new Thread(runner);
        t.run();
        System.out.print("bar");
    }
}
```
A.foobar
B.barfoo
C.foobar或者barfoo都有可能
D.Bar
E.Foo
F.程序无法正常运行


# 187、有如下代码：请写出程序的输出结果。（B）
```prettyprint
public class Test{
    public static void main(String[] args){
        int x = 0;
        int y = 0;
        int k = 0;
        for (int z = 0; z < 5; z++) {
            if ((++x > 2) && (++y > 2) && (k++ > 2)) {
                x++;
                ++y;
                k++;
            }
        }
        System.out.println(x + ”” +y + ”” +k);
    }
}
```
A.432
B.531
C.421
D.523

每次循环z,x,y,k对应数值为：
0,1,0,0
1,2,0,0
2,3,1,0
3,4,2,0
4,5,3,1
执行完这次以后，z++为5，不再进入for循环。


# 188、以下程序运行的结果为 (A)
```prettyprint
public class Example extends Thread {   
    @Override
    public void run() {
        try {
            Thread.sleep(1000);
        } catch(InterruptedException e) {
            e.printStackTrace();
        }
        System.out.print("run");
    }

    public static void main(String[] args) {

        Example example = new Example();
        example.run();
        System.out.print("main");
    }
    
}
```
A.run main
B.main run
C.main 
D.run
E.不能确定

此题的争议点只可能是runmain或mainrun
因为Example的run方法里面休眠了100ms，在当今电脑计算性能过剩的时代，如果是多线程启动，main方法肯定会打印出了main。
为啥是runmain而不是mainrun呢？
因为启动线程是调用start方法。
把线程的run方法当普通方法，就直接用实例.run()执行就好了。
没有看到start。所以是普通方法调用。
所以选A。


# 189、JVM内存不包含如下哪个部分（D）
A.Stacks
B.PC寄存器
C.Heap
D.Heap Frame


# 190、若有下列定义，下列哪个表达式返回false？（B）
```prettyprint
String s = "hello";
String t = "hello";
char c[] = {'h', 'e', 'l', 'l', 'o'} ;
```
A.s.equals(t);
B.t.equals(c);
C.s==t;
D.t.equals(new String("hello"));


# 191、下面有关jdbc statement的说法错误的是？（C）
A.JDBC提供了Statement、PreparedStatement 和 CallableStatement三种方式来执行查询语句，其中 Statement 用于通用查询， PreparedStatement 用于执行参数化查询，而 CallableStatement则是用于存储过程
B.对于PreparedStatement来说，数据库可以使用已经编译过及定义好的执行计划，由于 PreparedStatement 对象已预编译过，所以其执行速度要快于 Statement 对象”
C.PreparedStatement中，“?” 叫做占位符，一个占位符可以有一个或者多个值
D.PreparedStatement可以阻止常见的SQL注入式攻击


# 192、下面关于垃圾收集的说法正确的是（D）
A.一旦一个对象成为垃圾，就立刻被收集掉。
B.对象空间被收集掉之后，会执行该对象的finalize方法
C.finalize方法和C++的析构函数是完全一回事情
D.一个对象成为垃圾是因为不再有引用指着它，但是线程并非如此


# 193、以下代码执行的结果显示是多少（B）
```prettyprint
public class Demo {
    public static void main(String args[]){
        int count =0;
        int num =0;
        for(int i = 0;i <= 100;i++){
            num = num + i;
            count = count++;
        }
        System.out.println("num*count="+(num*count));
    }
}
```
A.num * count = 505000
B.num * count = 0
C.运行时错误
D.num * count = 5050


# 194、已知 boolean result = false，则下面哪个选项是合法的（B、D）
A.result=1
B.result=true;
C.if(result!=0) {//so something…}
D.if(result) {//do something…}


# 195、下列关于JAVA多线程的叙述正确的是（B、C）
A.调用start()方法和run()都可以启动一个线程
B.CyclicBarrier和CountDownLatch都可以让一组线程等待其他线程
C.Callable类的call()方法可以返回值和抛出异常
D.新建的线程调用start()方法就能立即进行运行状态


# 196、在J2EE中，使用Servlet过滤器，需要在web.xml中配置（）元素（A、B）
A.<filter>
B.<filter-mapping>
C.<servlet-filter>
D.<filter-config>

Servlet过滤器的配置包括两部分：
第一部分是过滤器在Web应用中的定义，由<filter>元素表示，包括<filter-name>和<filter-class>两个必需的子元素
第二部分是过滤器映射的定义，由<filter-mapping>元素表示,可以将一个过滤器映射到一个或者多个Servlet或JSP文件，也可以采用url-pattern将过滤器映射到任意特征的URL。


# 197、线程安全的map在JDK 1.5及其更高版本环境 有哪几种方法可以实现?（C、D）
A.Map map = new HashMap()
B.Map map = new TreeMap()
C.Map map = new ConcurrentHashMap();
D.Map map = Collections.synchronizedMap(new HashMap());


正确答案: C D         
1. HashMap,TreeMap 未进行同步考虑，是线程不安全的。
2. HashTable 和 ConcurrentHashMap 都是线程安全的。区别在于他们对加锁的范围不同，HashTable 对整张Hash表进行加锁，而ConcurrentHashMap将Hash表分为16桶(segment)，每次只对需要的桶进行加锁。
3. Collections 类提供了synchronizedXxx()方法，可以将指定的集合包装成线程同步的集合。比如，
   List  list = Collections.synchronizedList(new ArrayList());
   Set  set = Collections.synchronizedSet(new HashSet());
   

# 198、下面有关java classloader说法正确的是（A、C、D）
A.ClassLoader就是用来动态加载class文件到内存当中用的
B.JVM在判定两个class是否相同时，只用判断类名相同即可，和类加载器无关
C.ClassLoader使用的是双亲委托模型来搜索类的
D.Java默认提供的三个ClassLoader是Boostrap ClassLoader，Extension ClassLoader，App ClassLoader
E.以上都不正确


# 199、下列流当中，属于处理流的是（C、D）   
A.FilelnputStream
B.lnputStream
C.DatalnputStream
D.BufferedlnputStream


# 200、Java是一门支持反射的语言,基于反射为Java提供了丰富的动态性支持，下面关于Java反射的描述，哪些是错误的（A、D、F）
A.Java反射主要涉及的类如Class, Method, Filed,等，他们都在java.lang.reflet包下
B.通过反射可以动态的实现一个接口，形成一个新的类，并可以用这个类创建对象，调用对象方法
C.通过反射，可以突破Java语言提供的对象成员、类成员的保护机制，访问一般方式不能访问的成员
D.Java反射机制提供了字节码修改的技术，可以动态的修剪一个类
E.Java的反射机制会给内存带来额外的开销。例如对永生堆的要求比不通过反射要求的更多
F.Java反射机制一般会带来效率问题，效率问题主要发生在查找类的方法和字段对象，因此通过缓存需要反射类的字段和方法就能达到与之间调用类的方法和访问类的字段一样的效率


# 201、下列关于Java类中方法的定义，正确的是（D）
A.若代码执行到return语句，则将当前值返回，而且继续执行return语句后面的语句。
B.只需要对使用基本数据类型定义的属性使用getter和setter，体现类的封装性。
C.方法的返回值只能是基本数据类型。
D.在同一个类中定义的方法，允许方法名称相同而形参列表不同。


# 202、接口不能扩展（继承）多个接口（B）
A.正确
B.错误


# 203、以下哪种声明是合法的java数组（A）
(A) int number();
(B) float average[];
(C) double[] marks;
(D) counter int[];

java里面有两种数组声明方式


# 204、在java中，要表示10个学生的成绩，下列声明并初始化数组正确的是（D）
A.int[] score=new int[ ]
B.int score[10]
C.int score[]=new int[9]
D.int score[]=new int[10]

以下两种写法都可以：
int score[] = new int[10];
int[] score = new int[10];


# 205、后端获取数据，向前端输出过程中，以下描述正确的是（D）
A.对于前端过滤过的参数，属于可信数据，可以直接输出到前端页面
B.对于从数据库获得的数据，属于可信数据，可以直接输出到前端页面
C.对于从用户上传的Excel等文件解析出的数据，属于可信数据，可以直接输出到前端页面
D.其它选项都不属于可信数据，输出前应该采用信息安全部发布的XSSFilter做进行相应编码


# 206、正则表达式语法中 \d 匹配的是？（A）
A.数字
B.非数字
C.字母
D.空白字符


# 207、分析以下代码，说法正确的是（D）
```prettyprint
public static void main(String[] args) {
    System.out.println(val());
}
public static int val() {
    int num = 5;
    try {
        num = num / 0;
    } catch (Exception e) {
        num = 10;
    } finally {
        num = 15;
    }
    return num;
}
```
A.运行时报错
B.程序正常运行，输出值为5
C.程序正常运行，输出值为10
D.程序正常运行，输出值为15


# 208、以下代码的循环次数是（D）
```prettyprint
public class Test {
    public static void main(String args[]) {
        int i = 7;
        do {
            System.out.println(--i);
            --i;
        } while (i != 0);
        System.out.println(i);
    }
}
```

A.0
B.1
C.7
D.无限次


# 209、下面代码的执行结果是（A）
```prettyprint
class Chinese {
    private static Chinese objref = new Chinese();
    private Chinese() {}
    public static Chinese getInstance() {
        return objref;
    }
}
public class TestChinese {
    public static void main(String[] args) {
        Chinese obj1 = Chinese.getInstance();
        Chinese obj2 = Chinese.getInstance();
        System.out.println(obj1 == obj2);
    }
}
```

A.true
B.false
C.TRUE
D.FALSE


# 210、指出下列程序运行的结果（B）

```prettyprint
public class Example{
    String str = new String("good");
    char[ ] ch = { 'a' , 'b' , 'c' };
    public static void main(String args[]){
        Example ex = new Example();
        ex.change(ex.str,ex.ch);
        System.out.print(ex.str + " and ");
        System.out.print(ex.ch);
    }
    public void change(String str,char ch[ ]){
        str = "test ok";
        ch[0] = 'g';
    }
}
```

A.good and abc
B.good and gbc
C.test ok and abc
D.test ok and gbc

# 211、给定以下JAVA代码，这段代码运行后输出的结果是（B）

```prettyprint
public class Test{  
    public static int aMethod(int i)throws Exception{
        try{
            return i/10;
        }
        catch (Exception ex)
        {
            throw new Exception("exception in a aMethod");
        }finally{
            System.out.printf("finally");
        }
    } 
    
    public static void main(String[] args){
        try
        {
            aMethod(0);
        }
        catch (Exception ex)
        {
            System.out.printf("exception in main");
        }
        System.out.printf("finished");
    }
}
```
A.exception in main finished
B.finallyfinished
C.exception in main finally
D.finally exception in main finally


# 212、使用mvc模式设计的web应用程序具有以下优点,除了？（D）
A.可维护行强
B.可扩展性强
C.代码重复少
D.大大减少代码量

MVC全名是Model View Controller，是模型(model)－视图(view)－控制器(controller)的缩写，一种软件设计典范，用一种业务逻辑、数据、界面显示分离的方法组织代码，将业务逻辑聚集到一个部件里面，在改进和个性化定制界面及用户交互的同时，不需要重新编写业务逻辑。MVC被独特的发展起来用于映射传统的输入、处理和输出功能在一个逻辑的图形化用户界面的结构中。
MVC只是将分管不同功能的逻辑代码进行了隔离，增强了可维护和可扩展性，增强代码复用性，因此可以减少代码重复。但是不保证减少代码量，多层次的调用模式还有可能增加代码量


# 213、以下哪个事件会导致线程销毁？（D）
A.调用方法sleep()
B.调用方法wait()
C.start()方法的执行结束
D.run()方法的执行结束


# 214、对于非运行时异常，程序中一般可不做处理，由java虚拟机自动进行处理。（B）
A.正确
B.错误 


# 215、如果一个接口Glass有个公有方法setColor()，有个类BlueGlass实现接口Glass，则在类BlueGlass中正确的是（C）
A.protected void setColor() { …}
B.void setColor() { …}
C.public void setColor() { …}
D.以上语句都可以用在类BlueGlass中


# 216、以下叙述正确的是（D）
A.实例方法可直接调用超类的实例方法
B.实例方法可直接调用超类的类方法
C.实例方法可直接调用子类的实例方法
D.实例方法可直接调用本类的实例方法

A错误，类的实例方法是与该类的实例对象相关联的，不能直接调用，只能通过创建超类的一个实例对象，再进行调用
B错误，当父类的类方法定义为private时，对子类是不可见的，所以子类无法调用
C错误，子类具体的实例方法对父类是不可见的，所以无法直接调用， 只能通过创建子类的一个实例对象，再进行调用
D正确，实例方法可以调用自己类中的实例方法


# 217、下面论述正确的是（D）
A.如果两个对象的hashcode相同，那么它们作为同一个HashMap的key时，必然返回同样的值
B.如果a,b的hashcode相同，那么a.equals(b)必须返回true
C.对于一个类，其所有对象的hashcode必须不同
D.如果a.equals(b)返回true，那么a,b两个对象的hashcode必须相同


hashCode方法本质就是一个哈希函数，这是Object类的作者说明的。Object类的作者在注释的最后一段的括号中写道：将对象的地址值映射为integer类型的哈希值。但hashCode()并不完全可靠的，有时候不同的对象他们生成的hashcode也会一样，因此hashCode()只能说是大部分时候可靠。
因此我们也需要重写equals()方法，但因为重写的equals()比较全面比较复杂，会造成程序效率低下，而利用hashCode()进行对比，则只要生成一个hash值进行比较就可以了，效率很高。因此，正常的操作流程是先用hashCode()去对比两个对象，如果hashCode()不一样，则表示这两个对象肯定不相等，直接返回false,如果hashCode()相同，再对比他们的equals()。
综上所述：
equals()相等的两个对象hashCode()一定相等。
hashCode()相等的两个对象equal()不一定相等。
因此选项D正确。


# 218、面向对象方法的多态性是指（C）
A.一个类可以派生出多个特殊类
B.一个对象在不同的运行环境中可以有不同的变体
C.针对一消息，不同的对象可以以适合自身的方式加以响应
D.一个对象可以是由多个其他对象组合而成的


# 219、判断对错。在java的多态调用中，new的是哪一个类就是调用的哪个类的方法（B）
A.对
B.错

Java多态有两种情况：重载和覆写
在覆写中，运用的是动态单分配，是根据new的类型确定对象，从而确定调用的方法；
在重载中，运用的是静态多分派，即根据静态类型确定对象，因此不是根据new的类型确定调用的方法


# 220、下面属于java引用类型的有（A、D）
A.String
B.byte
C.char
D.Array

java语言是强类型语言，支持的类型分为两类：基本类型和引用类型。
基本类型包括boolean类型和数值类型，数值类型有整数类型和浮点类型。整数类型包括：byte、short、int、long和char；浮点类型包括：float和double
引用类型包括类、接口和数组类型以及特殊的null类型。


# 221、下列哪个选项是合法的标识符（B、D）
A.123
B._name
C.class
D.first


# 222、下面哪些接口直接继承自Collection接口（A、C）
A.List
B.Map
C.Set
D.Iterator


# 223、若需要定义一个类，下列哪些修饰符是允许被使用的（A、C、D）
A.static
B.package
C.private
D.public


# 224、下面有关 java 类加载器,说法正确的是?(B、C、D)
A.引导类加载器(bootstrap class loader):它用来加载 Java 的核心库,是用C++来实现的
B.扩展类加载器(extensions class loader):它用来加载 Java 的扩展库。
C.系统类加载器(system class loader):它根据 Java 应用的类路径(CLASSPATH)来加载 Java 类
D.tomcat 为每个 App 创建一个 Loader,里面保存着此 WebApp 的 ClassLoader。需要加载 WebApp 下的类时,就取出 ClassLoader 来使用


# 225、下面的类哪些可以处理Unicode字符（A、B、C）
A.InputStreamReader
B.BufferedReader
C.Writer
D.PipedInputStream


# 226、以下哪种JAVA的变量表达式使得变量a和变量b具有相同的内存引用地址（A、B）
A.String a = "hello"; String b = "hello";
B.Integer a; Integer b = a;
C.int a = 1; Integer b = new Integer(1);
D.int a = 1; Integer b = 1;


# 227、下列有关java构造函数叙述正确的是（C、D）
A.构造器的返回值为void类型
B.如果一个源文件中有多个类，那么构造器必须与公共类同名
C.构造器可以有0个，1个或一个以上的参数
D.每个类可以有一个以上的构造器


# 228、A,B,C,D 中哪些是 setvar的重载？（A、C、D）
```prettyprint
public class methodover{
    public void setVar(int a, int b, float c) {}
}
```

A.private void setVar(int a， float c， int b){}
B.protected void setVar(int a， int b， float c){}
C.public int setVar(int a， float c， int b){return a;}
D.public int setVar(int a， float c){return a;}

重载是在同一个类中，有多个方法名相同，参数列表不同(参数个数不同，参数类型不同),与方法的返回值无关，与权限修饰符无关，B中的参数列表和题目的方法完全一样了。


# 229、下面正确的2项是？（E、G）

```prettyprint
public class NameList{
    private List names = new ArrayList();
    public synchronized void add(String name){
        names.add(name);
    }
    public synchronized void printAll() {
        for (int i = 0; i < names.size(); i++){
            System.out.print(names.get(i) + "");
        }
    }

    public static void main(String[]args){
        final NameList sl = new NameList();
        for (int i = 0; i < 2; i++){
            new Thread(){
                public void run(){
                    sl.add("A");
                    sl.add("B");
                    sl.add("C");
                    sl.printAll();
                }
            } .start();
        }
    }
}
```

A.运行的时候可能抛异常
B.运行的时候可能没有输出，也没有正常退出
C.代码运行的时候可能没有输出，但是正常退出
D.代码输出"A B A B C C "
E.代码输出"A B C A B C A B C "
F.代码输出"A A A B C A B C C "
G.代码输出"A B C A A B C A B C "


# 230、以下语句的执行结果是什么？（A）
1+”10”+3+”2”

A.”11032”
B.“16”
C.16
D.“32101”

```prettyprint
System.out.println(1+"10"+3+"2");//11032
System.out.println(1+2+"10"+3+"2");//31032
System.out.println(1+"10"+3+1+"2");//110312
```

注意“+”的两边的类型


# 231、下面哪个描述正确? （C）
A.程序中的注释越多，程序运行得越快。
B.int是java.lang包中可用的类的名称
C.类总是有一个构造函数（可能由java编译器自动提供）
D.实例变量名称只能包含字母和数字


# 232、设A为已知定义的类名，下列创建A类的对象a的语句正确的是（D）
A.float A a
B.public a=A（）
C.A a=new int ()
D.A a=new A()


# 233、覆盖（重写）与重载的关系是（A）
A.覆盖（重写）只有出现在父类与子类之间，而重载可以出现在同一个类中
B.覆盖（重写）方法可以有不同的方法名，而重载方法必须是相同的方法名
C.final修饰的方法可以被覆盖（重写），但不能被重载
D.覆盖（重写）与重载是同一回事


# 234、有以下代码片段（D）
```prettyprint
String str1="hello";

String str2="he"+ new String("llo");

System.out.println(str1==str2);
```

请问输出的结果是：
A.true
B.都不对
C.null
D.false


# 235、ArrayList和LinkList的描述，下面说法错误的是（D）
A.LinkedeList和ArrayList都实现了List接口
B.ArrayList是可改变大小的数组，而LinkedList是双向链接串列
C.LinkedList不支持高效的随机元素访问
D.在LinkedList的中间插入或删除一个元素意味着这个列表中剩余的元素都会被移动；而在ArrayList的中间插入或删除一个元素的开销是固定的

这个说法说反了
Arraylist的内存结构是数组，当超出数组大小时创建一个新的数组，吧原数组中元素拷贝过去。其本质是顺序存储的线性表，插入和删除操作会引发后续元素移动，效率低，但是随机访问效率高
LinkedList的内存结构是用双向链表存储的，链式存储结构插入和删除效率高，不需要移动。但是随机访问效率低，需要从头开始向后依次访问


# 236、在基本JAVA类型中，如果不明确指定，整数型的默认是什么类型？带小数的默认是什么类型（B）
A.int float
B.int double
C.long float
D.long double

整数类型 默认为 int
带小数的默认为 double


# 237、在Web应用程序的文件与目录结构中，web.xml是放置在(A)中。
A.WEB-INF目录
B.conf目录
C.lib目录
D.classes目录

web.xml文件是用来初始化配置信息，web.xml是放置在WEB-INF目录中



# 238、下面所示的java代码，运行时，会产生（D）类型的异常
int Arry_a[] = new int[10];
System.out.println(Arry_a[10]);

A.ArithmeticException
B.NullPointException
C.IOException
D.ArrayIndexOutOfBoundsException


# 239、导出类调用基类的构造器必须用到的关键字（C）
A.this
B.final
C.super
D.static


# 240、若所用变量都已正确定义，以下选项中，非法的表达式是（C）
A.a!= 4||b==1
B.’a’ % 3
C.’a’ = 1/3
D.’A’ + 32


# 241、Java的Daemon线程，setDaemon()设置必须要？（A）
A.在start之前
B.在start之后
C.前后都可以


# 242、javac的作用是（A）
A.将源程序编译成字节码
B.将字节码编译成源程序
C.解释执行Java字节码
D.调试Java代码


# 243、以下代码的输出的正确结果是（D）
```prettyprint
public class Test {
    public static void main(String args[]) {
        String s = "祝你考出好成绩！";
        System.out.println(s.length());
    }
}
```
A.24
B.16
C.15
D.8

# 244、以下程序段的输出结果为（B）
```prettyprint
public class EqualsMethod{
    public static void main(String[] args){
        Integer n1 = new Integer(47);
        Integer n2 = new Integer(47);
        System.out.print(n1 == n2);
        System.out.print(",");
        System.out.println(n1 != n2);
    }
}
```
A.false，false
B.false，true
C.true，false
D.true，true


# 245、列表(List)和集合(Set)下面说法正确的是（A）
A.Set中至多只能有一个空元素
B.List中至多只能有一个空元素
C.List和Set都可以包含重复元素的有序集合
D.List和Set都是有序集合


# 246、下面代码的执行结果是（A）
```prettyprint
public class Chinese {
    private static Chinese objref = new Chinese();
    private Chinese() {}
    public static Chinese getInstance() {
        return objref;
    }
}

public class TestChinese {
    public static void main(String[] args) {
        Chinese obj1 = Chinese.getInstance();
        Chinese obj2 = Chinese.getInstance();
        System.out.println(obj1 == obj2);
    }
}
```
A.true
B.false
C.TRUE
D.FALSE


# 247、对于abstract声明的类，下面说法正确的是（E）
A.可以实例化
B.不可以被继承
C.子类为abstract
D.只能被继承
E.可以被抽象类继承

A,抽象类不能实例化，因为有抽象方法未实现
B,可以被继承。派生类可以实现抽象方法
C，子类可以是抽象的，也可以非抽象的
D，只能被继承说法太肯定，不正确
E，可以被抽象类继承，也可以被非抽象类继承


# 248、下面哪个方法是 public void  example(){...} 的重载方法（D）
A.public void Example( int m){...}
B.public int example(){...}
C.public void example2(){...}
D.public int example ( int m, float f){...}

考察的是方法重载的定义。
方法名相同------------------排除AC选项。
方法的参数类型，参数个不一样。-----------------B选项和题目中的都没有参数，所以排除B选项。
方法的返回类型可以不相同
方法的修饰符可以不相同


# 249、建立Statement对象的作用是（C）
A.连接数据库
B.声明数据库
C.执行SQL语句
D.保存查询结果


# 250、类方法中可以直接调用对象变量（B）
A.正确
B.错误


# 关于继承和实现说法正确的 是 ？ (    )

A.类可以实现多个接口，接口可以继承（或扩展）多个接口

B.类可以实现多个接口，接口不能继承（或扩展）多个接口

C.类和接口都可以实现多个接口

D.类和接口都不可以实现多个接口



正确答案: A 



# 下列不属于Java语言性特点的是

A.Java致力于检查程序在编译和运行时的错误

B.Java能运行虚拟机实现跨平台

C.Java自己操纵内存减少了内存出错的可能性

D.Java还实现了真数组，避免了覆盖数据的可能



正确答案: D   

 Java致力于检查程序在编译和运行时的错误。
Java虚拟机实现了跨平台接口
类型检查帮助检查出许多开发早期出现的错误。
Java自己操纵内存减少了内存出错的可能性。
Java还实现了真数组，避免了覆盖数据的可能。
注意，是避免数据覆盖的可能，而不是数据覆盖类型



# 以下哪个类包含方法flush()？

A.InputStream

B.OutputStream

C.A 和B 选项都包含

D.A  和B 选项都不包含



正确答案: B  



# 关于Java中参数传递的说法，哪个是错误的？

A.在方法中，修改一个基础类型的参数不会影响原始参数值

B.在方法中，改变一个对象参数的引用不会影响到原始引用

C.在方法中，修改一个对象的属性会影响原始对象参数

D.在方法中，修改集合和Maps的元素不会影响原始集合参数



正确答案: D



#  下列哪个说法是正确的（）       

A.ConcurrentHashMap使用synchronized关键字保证线程安全

B.HashMap实现了Collction接口

C.Array.asList方法返回java.util.ArrayList对象

D.SimpleDateFormat是线程不安全的



正确答案: D 



# 给定includel.isp文件代码片段，如下：

```jsp
<% pageContext.setAttribute(“User”,”HAHA”);%>
______ // 此处填写代码
给定include2.jsp文件代码片段如下：
<%=pageContext.getAttribute(“User”)%>
要求运行include1.jsp时，浏览器上输出：HAHA
```

A.<jsp:include page=”include2.jsp” flash=”true”>

B.<%@include file=”include2.jsp”%>

C.<jsp:forward page=”include2.jsp”>

D. <% response.sendRedirect(“include2.jsp”); %> 



正确答案: B         

B选项是静态包含，相当于不include2.jsp页面内容拷贝到此处，因此可以输出User属性值
D选项是转发重定向，转发的时候pageContent内的属性值不能被传递，因此得不到User属性值



# 下面属于java引用类型的有？

A.String

B.byte

C.char

D.Array



正确答案: A D          

 java语言是强类型语言，支持的类型分为两类：基本类型和引用类型。
基本类型包括boolean类型和数值类型，数值类型有整数类型和浮点类型。整数类型包括：byte、short、int、long和char；浮点类型包括：float和double
引用类型包括类、接口和数组类型以及特殊的null类型。



# int，String，*point，union哪些不是 Java 的数据类型？

A.int

B.String

C.*point

D.union



正确答案: C D 



# 下面有关java类加载器，说法正确的是？

A.引导类加载器（bootstrap class loader）：它用来加载 Java 的核心库，是用原生代码来实现的

B.扩展类加载器（extensions class loader）：它用来加载 Java 的扩展库。

C.系统类加载器（system class loader）：它根据 Java 应用的类路径（CLASSPATH）来加载 Java 类

D.tomcat为每个App创建一个Loader，里面保存着此WebApp的ClassLoader。需要加载WebApp下的类时，就取出ClassLoader来使用



正确答案: A B C D       

jvm classLoader architecture :

a、Bootstrap ClassLoader/启动类加载器
主要负责jdk_home/lib目录下的核心 api 或 -Xbootclasspath 选项指定的jar包装入工作.
B、Extension ClassLoader/扩展类加载器
主要负责jdk_home/lib/ext目录下的jar包或 -Djava.ext.dirs 指定目录下的jar包装入工作
C、System ClassLoader/系统类加载器
主要负责java -classpath/-Djava.class.path所指的目录下的类与jar包装入工作.
B、 User Custom ClassLoader/用户自定义类加载器(java.lang.ClassLoader的子类)
在程序运行期间, 通过java.lang.ClassLoader的子类动态加载class文件, 体现java动态实时类装入特性.



# 下列程序执行后结果为( )

```prettyprint
class A {
    public int func1(int a, int b) {
        return a - b;
    }
}
class B extends A {
    public int func1(int a, int b) {
        return a + b;
    }
}
public class ChildClass {
    public static void main(String[] args) {
        A a = new B();
        B b = new B();
        System.out.println("Result=" + a.func1(100, 50));
        System.out.println("Result=" + b.func1(100, 50));
    }
}
```

A.Result=150
Result=150

B.Result=100
Result=100

C.Result=100
Result=150

D.Result=150
Result=100



正确答案: A  



# 输入流将数据从文件，标准输入或其他外部输入设备中加载道内存，在 java 中其对应于抽象类（）及其子类。

A.java.io.InputStream

B.java.io.OutputStream

C.java.os.InputStream

D.java.os.OutputStream



正确答案: A  



# 将类的成员的访问权限设置为默认的，则该成员能被( )

A.同一包中的类访问

B.其它包中的类访问

C.所有的类访问

D.所有的类的子类访问



正确答案: A 



# 关于Java语言的内存回收机制，下列选项中最正确的一项是

A.Java程序要求用户必须手工创建一个线程来释放内存

B.Java程序允许用户使用指针来释放内存

C.内存回收线程负责释放无用内存

D.内存回收线程不能释放内存对象



正确答案: C          

A，java的内存回收是自动的，Gc在后台运行，不需要用户手动操作
B，java中不允许使用指针
D，内存回收线程可以释放无用的对象内存



# 下面哪个选项没有实现 java.util.Map 接口?

A.Hashtable

B.HashMap

C.Vector

D.IdentityHashMap



正确答案: C    

A，B，D都实现了Map接口，其中A与B的区别是一个是线程安全的，一个是线程不安全的
C中Vector是实现了List接口，是一个线程安全的List



# 下列哪个语句语法正确？（ ）

A.byte y = 11; byte x = y +y;

B.String x = new Object();

C.Object x = new String(“Hellow”);

D.int a [11] = new int [11];



正确答案: C         

对于A，前一半语句赋值是没有问题的，问题是后半句，在对byte型的变量进行相加时，会先自动转换为int型进行计算，所以计算结果也是int型的，int型赋值给byte需要强制转换，所以A会出错
对于B，因为object是String的父类，所以不能这样使用，不能把父类对象赋值给子类，只能是Object x = new String();
对于C，因为String是Object的子类，所以可以将子类赋值给父类。
对于D，因为在声明变量时不需要指定容量，例如int  a[] = new int[11];这样是正确的，但是像D选项这样是错误的



# 对于java类型变量char c,short s,float f,double d,表达式c*s+f+d的结果类型为（）

A.float

B.char

C.short

D.double



正确答案: D   

自动类型转换遵循下面的规则：
1.若参与运算的数据类型不同，则先转换成同一类型，然后进行运算。
2.转换按数据长度增加的方向进行，以保证精度不降低。例如int型和long型运算时，先把int量转成long型后再进行运算。
3.所有的浮点运算都是以双精度进行的，即使仅含float单精度量运算的表达式，也要先转换成double型，再作运算。
4.char型和short型参与运算时，必须先转换成int型。
5.在赋值运算中，赋值号两边的数据类型不同时，需要把右边表达式的类型将转换为左边变量的类型。如果右边表达式的数据类型长度比左边长时，将丢失一部分数据，这样会降低精度。



# 以下哪个方法用于定义线程的执行体？

A.start()

B.init()

C.run()

D.synchronized()



正确答案: C 



# 程序文件名必须与公共外部类的名称完全一致（包括大小写）.

A.正确

B.错误



正确答案: A 



# 能单独和finally语句一起使用的块是(  )

A.try

B.catch

C.throw

D.throws



正确答案: A



# 局部变量能否和成员变量重名？

A.可以，局部变量可以与成员变量重名，这时可用“this”来指向成员变量

B.可以，这时可用“local”关键字来指向局部变量

C.不能，局部变量不能与成员变量重名

D.不能，在一个类中不能有重名变量，不管是成员变量还是函数中的局部变量



正确答案: A



# 在Java中，什么是Garbage Collection?（）

A.自动删除在程序中导入但未使用的任何包

B.JVM检查任何Java程序的输出并删除任何没有意义的东西

C.当对象的所有引用都消失后，对象使用的内存将自动回收

D.操作系统定期删除系统上可用的所有java文件



正确答案: C



# 下列叙述错误的是（ ）

A.在接口中定义的方法除了default和static关键字修饰的方法拥有方法体，其他方法都应是没有方法体的抽象方法（JDK1.8以后）

B.一个java类只能有一个父类,但可以实现多个接口

C.在类声明中,用implements关键字声明该类实现的接口

D.定义接口时使用implements关键字。



正确答案: D 



# 在异常处理中，以下描述不正确的有

A.try块不可以省略

B.可以使用多重catch块

C.finally块可以省略

D.catch块和finally块可以同时省略



正确答案: D     

假如try中有异常抛出，则会去执行catch块，再去执行finally块；假如没有catch 块，可以直接执行finally 块，方法就以抛出异常的方式结束，而finally 后的内容也不会被执行，所以catch 和 finally 不能同时省略。



# 以下代码的循环次数是

```prettyprint
public class Test {
    public static void main(String args[]) {
        int i = 7;
        do {
            System.out.println(--i);
            --i;
        } while (i != 0);
        System.out.println(i);
    }
}
```

A.0

B.1

C.7

D.无限次



正确答案: D



# 要在控制台界面下接收用户从键盘输入，需要import的包是：（ ）

A.java.lang包

B.java.awt包

C.java.io包

D.java.applet包



正确答案: C



# 给定以下JAVA代码，这段代码运行后输出的结果是（）

```prettyprint
public class Test{  
    public static int aMethod(int i)throws Exception{
        try{
            return i/10;
        }catch (Exception ex){
            throw new Exception("exception in a aMethod");
        }finally{
            System.out.printf("finally");
        }
    } 
    
    public static void main(String[] args){
        try{
            aMethod(0);
        }catch (Exception ex){
            System.out.printf("exception in main");
        }
        System.out.printf("finished");
    }
}
```

A.exception in main finished

B.finallyfinished

C.exception in main finally

D.finally exception in main finally



正确答案: B



# 下面的程序输出的结果是( )

```prettyprint
public class A implements B{
    public static void main(String args[]){
        int i;
        A a1 = new A();
        i =a1.k;
        System.out.println("i="+i);
    }
}
interface B{
    int k=10；
}
```

A.i=0

B.i=10

C.程序有编译错误

D.i=true



正确答案: B   



# 如果一个接口Cow有个public方法drink()，有个类Calf实现接口Cow，则在类Calf中正确的是？  ( )

A.void drink() { …}

B.protected void drink() { …}

C.public void drink() { …}

D.以上语句都可以用在类Calf中



正确答案: C  



# 有以下类定义：

```prettyprint
abstract class Animal{
    abstract void say();
}
public class Cat extends Animal{
    public Cat(){
        System.out.printf("I am a cat");
    }
    public static void main(String[] args) {
        Cat cat=new Cat();
    }
}
```

运行后：

A.I am a cat

B.Animal能编译，Cat不能编译

C.Animal不能编译，Cat能编译

D.编译能通过，但是没有输出结果



正确答案: B   

当一个实体类集成一个抽象类，必须实现抽象类中的抽象方法，抽象类本身没有错误，但是cat类编译通不过



# 以下java程序代码，执行后的结果是（）

```prettyprint
java.util.HashMap map=new java.util.HashMap(); 
map.put("name",null);      
map.put("name","Jack");
System.out.println(map.size());
```

A.0

B.null

C.1

D.2



正确答案: C    

HashMap可以插入null的key或value，插入的时候，检查是否已经存在相同的key，如果不存在，则直接插入，如果存在，则用新的value替换旧的value，在本题中，第一条put语句，会将key/value对插入HashMap，而第二条put，因为已经存在一个key为name的项，所以会用新的value替换旧的vaue，因此，两条put之后，HashMap中只有一个key/value键值对。那就是（name，jack）。所以，size为1.



# 关于访问权限，说法正确的是？ ( )

A.类A和类B在同一包中，类B有个protected的方法testB，类A不是类B的子类（或子类的子类），类A可以访问类B的方法testB

B.类A和类B在同一包中，类B有个protected的方法testB，类A不是类B的子类（或子类的子类），类A不可以访问类B的方法testB

C.访问权限大小范围：public > 包权限 > protected > private

D.访问权限大小范围：public > 包权限 > private > protected



正确答案: A 



# 假如某个JAVA进程的JVM参数配置如下：

-Xms1G -Xmx2G -Xmn500M -XX:MaxPermSize=64M -XX:+UseConcMarkSweepGC -XX:SurvivorRatio=3,
请问eden区最终分配的大小是多少？

A.64M

B.500M

C.300M

D.100M



正确答案: C         

先分析一下里面各个参数的含义： 
-Xms：1G ， 就是说初始堆大小为1G 
-Xmx：2G ， 就是说最大堆大小为2G 
-Xmn：500M ，就是说年轻代大小是500M（包括一个Eden和两个Survivor） 
-XX:MaxPermSize：64M ， 就是说设置持久代最大值为64M 
-XX:+UseConcMarkSweepGC ， 就是说使用使用CMS内存收集算法 
-XX:SurvivorRatio=3 ， 就是说Eden区与Survivor区的大小比值为3：1：1
题目中所问的Eden区的大小是指年轻代的大小，直接根据-Xmn：500M和-XX:SurvivorRatio=3可以直接计算得出
500M*(3/(3+1+1)) 
=500M*（3/5） 
=500M*0.6 
=300M  
所以Eden区域的大小为300M。



# 下面有关JAVA异常类的描述，说法错误的是？

A.异常的继承结构：基类为Throwable，Error和Exception继承Throwable，RuntimeException和IOException等继承Exception

B.非RuntimeException一般是外部错误(非Error)，其一般被 try{}catch语句块所捕获

C.Error类体系描述了Java运行系统中的内部错误以及资源耗尽的情形，Error不需要捕捉

D.RuntimeException体系包括错误的类型转换、数组越界访问和试图访问空指针等等，必须被 try{}catch语句块所捕获



正确答案: D      

RuntimeException并不必须被捕获。不管异常代表的是可预见的异常条件还是编程错误，如果用try{}catch语句捕获它，会让程序在已经出现错误的情况下继续执行下去，也就是说我们不会及时的察觉到程序出现的问题。如果我们不去处理RuntimeException，让程序在测试阶段把异常传播给外界，这时系统打印出来的调用堆栈路径可以帮助我们更快的找出并修改错误，避免出现更大的损失。



# URL u =new URL("http://www.123.com");。如果www.123.com不存在，则返回______。

A.http://www.123.com

B.””

C.null

D.抛出异常



正确答案: A 



# String与StringBuffer的区别是？

A.String是不可变的对象，StringBuffer是可以再编辑的

B.字符串是常量，StringBuffer是变量

C.String是可变的对象，StringBuffer是不可以再编辑的

D.以上说法都不正确



正确答案: A B   

String类是不可变类，一旦一个String对象被创建以后，包含在这个对象中的字符序列是不可改变的，直至这个对象被销毁。
StringBuffer对象则代表一个字符序列可变的字符串，当一个StringBuffer被创建以后，通过StringBuffer提供的append()、insert()、reverse()、setCharAt()、setLength()等方法可以改变这个字符串对象的字符序列。一旦通过StringBuffer生成了最终想要的字符串，就可以调用它的toString()方法将其转换为一个String对象。
因此选项A、B正确。



# java中下面哪些是Object类的方法（）

A.notify()

B.notifyAll()

C.sleep()

D.wait()



正确答案: A B D



# java中提供了哪两种用于多态的机制

A.通过子类对父类方法的覆盖实现多态

B.利用重载来实现多态.即在同一个类中定义多个同名的不同方法来实现多态。

C.利用覆盖来实现多态.即在同一个类中定义多个同名的不同方法来实现多态。

D.通过子类对父类方法的重载实现多态



正确答案: A B   

 Java通过方法重写和方法重载实现多态
方法重写是指子类重写了父类的同名方法
方法重载是指在同一个类中，方法的名字相同，但是参数列表不同



# jdk1.8版本之前的前提下，接口和抽象类描述正确的有（ ）

A.抽象类没有构造函数

B.接口没有构造函数

C.抽象类不允许多继承

D.接口中的方法可以有方法体



正确答案: B C



# 在JAVA中，下列哪些是Object类的方法（）

A.synchronized()

B.wait()

C.notify()

D.notifyAll()

E.sleep() 



正确答案: B C D     

A    synchronized     

Java语言的关键字，当它用来修饰一个方法或者一个代码块的时候，能够保证在同一时刻最多只有一个线程执行该段代码。

B  C   D 都是Object类中的方法    

notify():  是唤醒一个正在等待该对象的线程。

notifyAll(): 唤醒所有正在等待该对象的线程。

E   sleep 是Thread类中的方法

wait 和 sleep的区别：

wait指线程处于进入等待状态，形象地说明为“等待使用CPU”，此时线程不占用任何资源，不增加时间限制。

sleep指线程被调用时，占着CPU不工作，形象地说明为“占着CPU睡觉”，此时，系统的CPU部分资源被占用，其他线程无法进入，会增加时间限制。

# 以下关于继承的叙述正确的是

A.在Java中类只允许单一继承

B.在Java中一个类不能同时继承一个类和实现一个接口

C.在Java中接口只允许单一继承

D.在Java中一个类只能实现一个接口



正确答案: A



# 编译java程序的命令文件是( )

A.java.exe

B.javac.exe

C.applet.exe



正确答案: B  



# “先进先出”的容器是：( )

A.堆栈(Stack)

B.队列（Queue）

C.字符串(String)

D.迭代器(Iterator)



正确答案: B 



# 在java中，在同一包内，非私有类Cat里面有个公有方法sleep()，该方法前有static修饰，则可以直接用Cat.sleep()。（ ）

A.正确

B.错误



正确答案: A 



# 输入流将数据从文件，标准输入或其他外部输入设备中加载道内存，在 java 中其对应于抽象类（）及其子类。

A.java.io.InputStream

B.java.io.OutputStream

C.java.os.InputStream

D.java.os.OutputStream



正确答案: A  



# 以下语句输出的结果是（）

```prettyprint
int value：
value=2；
System.out.print(value);
System.out.print(value++);
System.out.print(value);
```

A.233

B.223

C.221

D.222



正确答案: B 



# 下列哪个语句语法正确？（ ）

A.byte y = 11; byte x = y +y;

B.String x = new Object();

C.Object x = new String(“Hellow”);

D.int a [11] = new int [11];



正确答案: C     

对于A，前一半语句赋值是没有问题的，问题是后半句，在对byte型的变量进行相加时，会先自动转换为int型进行计算，所以计算结果也是int型的，int型赋值给byte需要强制转换，所以A会出错
对于B，因为object是String的父类，所以不能这样使用，不能把父类对象赋值给子类，只能是Object x = new String();
对于C，因为String是Object的子类，所以可以将子类赋值给父类。
对于D，因为在声明变量时不需要指定容量，例如int  a[] = new int[11];这样是正确的，但是像D选项这样是错误的



# 在上下文和头文件正常的情况下，代码将打印？

```prettyprint
System.out.println(10%3*2);
```

A.1

B.2

C.4

D.6



正确答案: B     

 %和*是同一个优先级，从左到右运算



# 装箱、拆箱操作发生在: ()

A.类与对象之间

B.对象与对象之间

C.引用类型与值类型之间

D.引用类型与引用类型之间



正确答案: C 



# 有时为了避免某些未识别的异常抛给更高的上层应用，在某些接口实现中我们通常需要捕获编译运行期所有的异常， catch 下述哪个类的实例才能达到目的：（）

A.Error

B.Exception

C.RuntimeException

D.Throwable



正确答案: B



# 以下程序段的输出结果为：

```prettyprint
public class EqualsMethod{
    public static void main(String[] args){
        Integer n1 = new Integer(47);
        Integer n2 = new Integer(47);
        System.out.print(n1 == n2);
        System.out.print(",");
        System.out.println(n1 != n2);
    }
}
```

A.false，false

B.false，true

C.true，false

D.true，true



正确答案: B



# AccessViolationException异常触发后，下列程序的输出结果为（      ）

```prettyprint
static void Main(string[] args)  {  
    try  {  
        throw new AccessViolationException();  
        Console.WriteLine("error1");  
    }  
    catch (Exception e)  {  
        Console.WriteLine("error2");  
    }  
    Console.WriteLine("error3");  
} 
```

A.error2
error3

B.error3

C.error2

D.error1



正确答案: A    

 try..catch，catch捕获到异常，如果没有抛出异常语句(throw)，不影响后续程序，本题答案选A。



# 语句：char foo='中'，是否正确？（假设源文件以GB2312编码存储，并且以javac – encoding GB2312命令编译）

A.正确

B.错误



正确答案: A



# 观察下列代码，分析结果()

```prettyprint
String s1 = "coder";     
String s2 = "coder";     
String s3 = "coder" + s2;     
String s4 = "coder" + "coder";     
String s5 = s1 + s2;            
System.out.println(s3 == s4); 
System.out.println(s3 == s5);    
System.out.println(s4 == "codercoder");
```

A.false；false； true；

B.false；true； true；

C.false；false； false；

D.true；false； true；



正确答案: A 



# java中下面哪个能创建并启动线程（）

```prettyprint
public class MyRunnable implements Runnable { 
    public void run() { 
        //some code here 
    } 
}
```

A.new Runnable(MyRunnable).start()

B.new Thread(MyRunnable).run()

C.new Thread(new MyRunnable()).start()

D.new MyRunnable().start()



正确答案: C      

首先：创建并启动线程的过程为：定义线程—》实例化线程—》启动线程。
一 、定义线程： 1、扩展java.lang.Thread类。 2、实现java.lang.Runnable接口。
二、实例化线程： 1、如果是扩展java.lang.Thread类的线程，则直接new即可。
                 2、如果是实现了java.lang.Runnable接口的类，则用Thread的构造方法：
        Thread(Runnable target) 
        Thread(Runnable target, String name) 
        Thread(ThreadGroup group, Runnable target) 
        Thread(ThreadGroup group, Runnable target, String name) 
        Thread(ThreadGroup group, Runnable target, String name, long stackSize)
所以A、D的实例化线程错误。
三、启动线程： 在线程的Thread对象上调用start()方法，而不是run()或者别的方法。
所以B的启动线程方法错误。



# 下列循环语句序列执行完成后，i的值是（）

```prettyprint
int i;
for(i=2;i<=10;i++){
    System.out.println(i);
}
```

A.2

B.11

C.10

D.不确定



正确答案: C 



# 关于如下程序的描述哪个是正确的？（ ）

```prettyprint
public class Person{
    static int arr[] = new int[5];
    public static void main(String a[]){
        System.out.println(arr[0]);
    }
}
```

A.编译将产生错误

B.编译时正确，但运行时将产生错误

C.正确，输出0

D.正确，输出 null



正确答案: C



# try括号里有return语句， finally执行顺序

A.不执行finally代码

B.return前执行

C.return后执行



正确答案: B      



# 下列关于包（package）的描述，正确的是（））

A.包（package）是Java中描述操作系统对多个源代码文件组织的一种方式。

B.import语句将所对应的Java源文件拷贝到此处执行。

C.包（package）是Eclipse组织Java项目特有的一种方式。

D.定义在同一个包（package）内的类可以不经过import而直接相互使用。



正确答案: D



# （）运算符把其操作数中所有值为0和所有值为1的位分别在结果的相应中设置1和0

A.&

B.|

C.！

D.~



正确答案: D  



# 关于Java以下描述正确的有(      )

A.native关键字表名修饰的方法是由其它非Java语言编写的

B.能够出现在import语句前的只有注释语句

C.接口中定义的方法只能是public

D.接口中定义的方法只能是public



正确答案: A 



# 以下代码可以使用的修饰符是：（）

```prettyprint
public interface Status {
    /*INSERT CODE HERE*/  int MY_VALUE=10;
}
```

A.final

B.static

C.abstract

D. public



正确答案: A B D 



#  java中Hashtable, Vector, TreeSet, LinkedList哪些线程是安全的？

A.Hashtable

B.Vector

C.TreeSet

D.LinkedList



正确答案: A B      

 HashTable是线程安全的
Vector是线程安全的ArrayList
TreeSet和LinkedList都不是线程安全的



# 线程安全的map在JDK 1.5及其更高版本环境 有哪几种方法可以实现?

A.Map map = new HashMap()

B.Map map = new TreeMap()

C.Map map = new ConcurrentHashMap();

D.Map map = Collections.synchronizedMap(new HashMap());



正确答案: C D        

1. HashMap,TreeMap 未进行同步考虑，是线程不安全的。

2. HashTable 和 ConcurrentHashMap 都是线程安全的。区别在于他们对加锁的范围不同，HashTable 对整张Hash表进行加锁，而ConcurrentHashMap将Hash表分为16桶(segment)，每次只对需要的桶进行加锁。

3. Collections 类提供了synchronizedXxx()方法，可以将指定的集合包装成线程同步的集合。比如，
   List  list = Collections.synchronizedList(new ArrayList());
   Set  set = Collections.synchronizedSet(new HashSet());

   

# 下列选项中是正确的方法声明的是？（）

A.protected abstract void f1();

B.public final void f1() {}

C.static final void fq(){}

D.private void f1() {}



正确答案: A B C D  



# 常用的servlet包的名称是？

A.java.servlet

B.javax.servlet

C.servlet.http

D.javax.servlet.http



正确答案: B D  



# 下列哪些方法是针对循环优化进行的

A.强度削弱

B.删除归纳变量

C.删除多余运算

D.代码外提



正确答案: A B D



# CMS垃圾回收器在那些阶段是没用用户线程参与的

A.初始标记

B.并发标记

C.重新标记

D.并发清理



正确答案: A C          

 CMS收集器是一种以获取最短回收停顿时间为目标的收集器，它是基于标记清除算法实现的，它的运作过程相对于其他收集器来说要更复杂一些，整个过程分为四个步骤，包括：初始标记、并发标记、重新标记、并发清除。其中初始标记、重新标记这两个步骤需要暂停整个JVM。
初始标记仅仅只是标记一下GC Roots能直接关联到的对象，速度很快。
并发标记阶段就是从GC Roots的直接关联对象开始遍历整个对象图的过程，这个过程耗时较长但是不需要停顿用户线程，可以与垃圾收集线程一起并发运行。
重新标记阶段则是为了修正并发标记期间，因用户程序继续运作而导致标记产生变动的那一部分对象的标记记录，这个阶段的停顿时间通常会比初始标记阶段稍长一些，但也远比并发标记阶段的时间短。
并发清除阶段，清理删除掉标记阶段判断的已经死亡的对象，由于不需要移动存活对象，所以这个阶段也是可以与用户线程同时并发的。



# 下列哪些操作会使线程释放锁资源？

A.sleep()

B.wait()

C.join()

D.yield()



正确答案: B C  



# Java语言中，下面哪个语句是创建数组的正确语句？(     )

A.float f[][] = new float[6][6];

B.float []f[] = new float[6][6];

C.float f[][] = new float[][6];

D.float [][]f = new float[6][6];

E.float [][]f = new float[6][];



正确答案: A B D E  



#331、现有一变量声明为 boolean aa; 下面赋值语句中正确的是 （ ）

A.aa=false;

B.aa=False;

C.aa="true";

D.aa=0;



正确答案: A 



# 下列代码中的错误原因是（）

```prettyprint
(1)public class Test

(2){

(3)       public static void main(String [] args)

(4)       {

(5)           int i;

(6)           i+=1;

(7)       }
    
(8) }
```

A.非法的表达式 i+=1

B.找不到符号i

C.类不应为public

D.尚未初始化变量i



正确答案: D

 

# HashSet子类依靠()方法区分重复元素。

A.toString(),equals()

B.clone(),equals()

C.hashCode(),equals()

D.getClass(),clone()



正确答案: C    

HashSet内部使用Map保存数据，即将HashSet的数据作为Map的key值保存，这也是HashSet中元素不能重复的原因。而Map中保存key值前，会去判断当前Map中是否含有该key对象，内部是先通过key的hashCode，确定有相同的hashCode之后，再通过equals方法判断是否相同。



# 为Test类的一个无形式参数无返回值的方法method书写方法头，使得使用类名Test作为前缀就可以调用它，该方法头的形式为( )

A.static  void  method（）

B.public void  method

C.protected  void  method（）

D.abstract  void method（）



正确答案: A



# 下列InputStream类中哪个方法可以用于关闭流？

A.skip()

B.close()

C.mark()

D.reset()



正确答案: B    

inputstream的close方法用来关闭流
skip()用来跳过一些字节
mark（）用来标记流
reset（）复位流



# 下列叙述错误的是（ ）

A.java程序的输入输出功能是通过流来实现的

B.java中的流按照处理单位可分成两种：字节流和字符流

C.InputStream是一个基本的输出流类。

D.通过调用相应的close（）方法关闭输入输出流



正确答案: C  



# 正则表达式语法中 \d 匹配的是？（）

A.数字

B.非数字

C.字母

D.空白字符



正确答案: A 



# 在java中，已定义两个接口B和C，要定义一个实现这两个接口的类，以下语句正确的是（）

A.interface  A extends B，C

B.interface  A eimplements  B，C

C.class  A implements  B，C

D.class  A implements  B，implements C



正确答案: C



# 以下那个数据结构是适用于"数据必须以相反的顺序存储然后检索" ? （）

A.Stack

B.Queue

C.List

D.Liink List



正确答案: A  

 

# 下面哪个不是Java基本类型？

A.short

B.Boolean

C.byte

D.float



正确答案: B    

 java规定类名首字母必须大写，这里可以直观的看出来Boolean是一个引用类型，不是基本数据类型。
java中的基本数据类型都对应一个引用类型，如Float是float的引用类型，Integer是int的引用类型



341、已知如下类定义：

```prettyprint
class Base {  
    public Base (){ 
        //... 
    }  
    public Base ( int m ){ 
        //... 
    }  
    public void fun( int n ){ 
        //... 
    } 
}  
public class Child extends Base{  
    // member methods  
}  
```

如下哪句可以正确地加入子类中？

A.private void fun( int n ){ //...}

B.void fun ( int n ){ //... }

C.protected void fun ( int n ) { //... }

D.public void fun ( int n ) { //... }



正确答案: D  



# 与未加访问控制符的缺省情况相比，public和protected修饰符扩大了属性和方法的被访问范围，private修饰符则缩小了这种范围。

A.正确

B.错误 



正确答案: A



# 下面论述正确的是（）？

A.如果两个对象的hashcode相同，那么它们作为同一个HashMap的key时，必然返回同样的值

B.如果a,b的hashcode相同，那么a.equals(b)必须返回true

C.对于一个类，其所有对象的hashcode必须不同

D.如果a.equals(b)返回true，那么a,b两个对象的hashcode必须相同



正确答案: D    

 hashCode方法本质就是一个哈希函数，这是Object类的作者说明的。Object类的作者在注释的最后一段的括号中写道：将对象的地址值映射为integer类型的哈希值。但hashCode()并不完全可靠的，有时候不同的对象他们生成的hashcode也会一样，因此hashCode()只能说是大部分时候可靠。
因此我们也需要重写equals()方法，但因为重写的equals()比较全面比较复杂，会造成程序效率低下，而利用hashCode()进行对比，则只要生成一个hash值进行比较就可以了，效率很高。因此，正常的操作流程是先用hashCode()去对比两个对象，如果hashCode()不一样，则表示这两个对象肯定不相等，直接返回false,如果hashCode()相同，再对比他们的equals()。
综上所述：
equals()相等的两个对象hashCode()一定相等。
hashCode()相等的两个对象equal()不一定相等。
因此选项D正确。



# 选项中哪一行代码可以替换 //add code here 而不产生编译错误

```prettyprint
public abstract class MyClass {
    public int constInt = 5;
    //add code here
    public void method() {
    } 
}
```

A.public abstract void method(int a);

B.consInt=constInt+5;

C.public int method();

D.public abstract void anotherMethod(){}



正确答案: A     

A是抽象方法，抽象类可以包含抽象方法，也可以不包含，实现重载。（√）
B 在类中不能constInt = constInt + 5（×）
C 返回值不能作为重载的依据（×）
D 有方法体的不能作为抽象函数（×）



# 语句：char foo='中'，是否正确？（假设源文件以GB2312编码存储，并且以javac – encoding GB2312命令编译）

A.正确

B.错误



正确答案: A 



# 根据以下代码段,执行new Child("John", 10); 要使数据域data得到10，则子类空白处应该填写(    )。

```prettyprint
class Parent {

    private int data;

    public Parent(int d){ data = d; }

}

class Child extends Parent{

    String name;

    public Child(String s, int d){

        ___________________

        name = s;

    }
}
```

A.data = d;

B.super.data = d;

C.Parent(d);

D.super(d);



正确答案: D    

1.子父类存在同名成员时，子类中默认访问子类的成员，可通过super指定访问父类的成员，格式：super.xx  (注：xx是成员名)；
2.创建子类对象时，默认会调用父类的无参构造方法，可通过super指定调用父类其他构造方法，格式：s uper(yy) (注：yy是父类构造方法需要传递的参数)



# 下面代码的执行结果是 :

```prettyprint
class Chinese {
    private static Chinese objref = new Chinese();
    private Chinese() {}
    public static Chinese getInstance() {
        return objref;
    }
}

public class TestChinese {
    public static void main(String[] args) {
        Chinese obj1 = Chinese.getInstance();
        Chinese obj2 = Chinese.getInstance();
        System.out.println(obj1 == obj2);
    }
}
```


A.true

B.false

C.TRUE

D.FALSE



正确答案: A



# 下列关于计算机系统和Java编程语言的说法，正确的是（）

A.计算机是由硬件、操作系统和软件组成，操作系统是缺一不可的组成部分。

B.Java语言编写的程序源代码可以不需要编译直接在硬件上运行。

C.在程序中书写注释不会影响程序的执行，可以在必要的地方多写一些注释。

D.Java的集成开发环境（IDE），如Eclipse，是开发Java语言必需的软件工具。



正确答案: C  



# 对于文件的描述正确的是（ ）

A.文本文件是以“.txt”为后缀名的文件，其他后缀名的文件是二进制文件。

B.File类是Java中对文件进行读写操作的基本类。

C.无论文本文件还是二进制文件，读到文件末尾都会抛出EOFException异常。

D.Java中对于文本文件和二进制文件，都可以当作二进制文件进行操作。



正确答案: D 



# 以下代码执行后输出结果为（ ）

```prettyprint
public class Test{
    public static Test t1 = new Test();
    {
        System.out.println("blockA");
    }
    
    static
    {
        System.out.println("blockB");
    }
    public static void main(String[] args) {
        Test t2 = new Test();
    }
}
```

A.blockAblockBblockA

B.blockAblockAblockB

C.blockBblockBblockA

D.blockBblockAblockB



正确答案: A 



# 下面有关JAVA异常类的描述，说法错误的是？

A.异常的继承结构：基类为Throwable，Error和Exception继承Throwable，RuntimeException和IOException等继承Exception

B.非RuntimeException一般是外部错误(非Error)，其一般被 try{}catch语句块所捕获

C.Error类体系描述了Java运行系统中的内部错误以及资源耗尽的情形，Error不需要捕捉

D.RuntimeException体系包括错误的类型转换、数组越界访问和试图访问空指针等等，必须被 try{}catch语句块所捕获



正确答案: D     

RuntimeException并不必须被捕获。不管异常代表的是可预见的异常条件还是编程错误，如果用try{}catch语句捕获它，会让程序在已经出现错误的情况下继续执行下去，也就是说我们不会及时的察觉到程序出现的问题。如果我们不去处理RuntimeException，让程序在测试阶段把异常传播给外界，这时系统打印出来的调用堆栈路径可以帮助我们更快的找出并修改错误，避免出现更大的损失。



# 下面字段声明中哪一个在interface主体内是合法的? （）

A.private final static int answer = 42;

B.public static int answer = 42;

C.final static answer = 42;

D.int answer;



正确答案: B



# int，String，*point，union哪些不是 Java 的数据类型？

A.int

B.String

C.*point

D.union



正确答案: C D   



# （）运算符和（）运算符分别把一个值的位向左和向右移动

A.<<

B.>>

C.&&

D.||



正确答案: A B



# 以下表达式中，正确的是（）

A.byte i=128

B.boolean i=null

C.long i=0xfffL

D.double i=0.9239d



正确答案: C D

  

# 下面属于JSP内置对象的是？

A.out对象

B.response对象

C.application对象

D.page对象



正确答案: A B C D    这些都是JSP内置对象
JSP内置对象有：
1.request对象
     客户端的请求信息被封装在request对象中，通过它才能了解到客户的需求，然后做出响应。它是HttpServletRequest类的实例。
2.response对象
     response对象包含了响应客户请求的有关信息，但在JSP中很少直接用到它。它是HttpServletResponse类的实例。
3.session对象
     session对象指的是客户端与服务器的一次会话，从客户连到服务器的一个WebApplication开始，直到客户端与服务器断开连接为止。它是HttpSession类的实例.
4.out对象
     out对象是JspWriter类的实例,是向客户端输出内容常用的对象
5.page对象
     page对象就是指向当前JSP页面本身，有点象类中的this指针，它是java.lang.Object类的实例
6.application对象
     application对象实现了用户间数据的共享，可存放全局变量。它开始于服务器的启动，直到服务器的关闭，在此期间，此对象将一直存在；这样在用户的前后连接或不同用户之间的连接中，可以对此对象的同一属性进行操作；在任何地方对此对象属性的操作，都将影响到其他用户对此的访问。服务器的启动和关闭决定了application对象的生命。它是ServletContext类的实例。
7.exception对象
   exception对象是一个例外对象，当一个页面在运行过程中发生了例外，就产生这个对象。如果一个JSP页面要应用此对象，就必须把isErrorPage设为true，否则无法编译。他实际上是java.lang.Throwable的对象
8.pageContext对象
pageContext对象提供了对JSP页面内所有的对象及名字空间的访问，也就是说他可以访问到本页所在的SESSION，也可以取本页面所在的application的某一属性值，他相当于页面中所有功能的集大成者，它的本 类名也叫pageContext。
9.config对象
config对象是在一个Servlet初始化时，JSP引擎向它传递信息用的，此信息包括Servlet初始化时所要用到的参数（通过属性名和属性值构成）以及服务器的有关信息（通过传递一个ServletContext对象）



# 下列哪些情况下会导致线程中断或停止运行（      ）

A.抛出InterruptedException异常

B.线程调用了wait方法

C.当前线程创建了一个新的线程

D.高优先级线程进入就绪状态



正确答案: B  



# Java1.8版本之前的前提，Java特性中,abstract class和interface有什么区别（）

A.抽象类可以有构造方法，接口中不能有构造方法

B.抽象类中可以有普通成员变量，接口中没有普通成员变量

C.抽象类中不可以包含静态方法，接口中可以包含静态方法

D.一个类可以实现多个接口，但只能继承一个抽象类。



正确答案: A B D 



# 下面有关Java的说法正确的是（         ）

A.一个类可以实现多个接口

B.抽象类必须有抽象方法

C.protected成员在子类可见性可以修改

D.通过super可以调用父类构造函数

E.final的成员方法实现中只能读取类的成员变量

F.String是不可修改的，且java运行环境中对string对象有一个常量池保存



正确答案: A C D E F



# 下列流当中，属于处理流的是：（） 

A.FilelnputStream

B.lnputStream

C.DatalnputStream

D.BufferedlnputStream



正确答案: C D

 

# 不考虑反射机制，一个子类显式调用父类的构造器必须用super关键字。（  ）

A.正确

B.错误



正确答案: A



# 设有定义： int a[] = {4, 2, -7, 5, 1, 6, 3}; 则 a[a[4]] 的值为 。

A.4

B.2

C.-7

D.5



正确答案: B  



# 下列叙述错误的是（ ）

A.java程序的输入输出功能是通过流来实现的

B.java中的流按照处理单位可分成两种：字节流和字符流

C.InputStream是一个基本的输出流类。

D.通过调用相应的close（）方法关闭输入输出流



正确答案: C 



# 下面程序段执行完成后，则变量sum的值是(    )。

```prettyprint
int b[][]={{1}, {2, 2}, {2, 2, 2}};
int sum = 0;

for(int i = 0; i < b.length; i++) {
    for(int j = 0; j < b[i].length; j++) {
        sum += b[i][j];
    }
}
```

A.32

B.11

C.2

D.3



正确答案: B



# 如果一个方法或变量是"private"访问级别，那么它的访问范围是:

A.在当前类，或者子类中

B.在当前类或者它的父类中

C.在当前类，或者它所有的父类中

D.在当前类中

  

正确答案: D

Java中，可以使用访问控制符来保护对类、变量、方法和构造方法的访问。Java 支持 4 种不同的访问权限。

·   default (即默认，什么也不写）: 在同一包内可见，不使用任何修饰符。使用对象：类、接口、变量、方法。

·   private : 在同一类内可见。使用对象：变量、方法。 注意：不能修饰类（外部类）

·   public : 对所有类可见。使用对象：类、接口、变量、方法

·   protected : 对同一包内的类和所有子类可见。使用对象：变量、方法。 注意：不能修饰类（外部类）。

我们可以通过以下表来说明访问权限：

修饰符     当前类     同一包内    子孙类(同一包)        子孙类(不同包)        其他包

public          Y               Y                   Y                               Y                            Y

protected   Y            Y                   Y                              Y/N                       N

default       Y                Y                 Y                               N                        N

private       Y              N                 N                                 N                         N

综上所述，本题正确答案为D。



# main 方法是 Java Application 程序执行的入口点，以下描述哪项是合法的（）。

A.public  static  void  main（ ）

B.public  static  void   main（ String []args ）

C.public static int  main（String  [] arg ）

D.public  void  main（String  arg[] ）



正确答案: B



# 有以下程序片段且Interesting不是内部类，下列哪个选项不能插入到行1。（    ）

```prettyprint
1.
2.public class Interesting{
3.// 省略代码
4.}
```

A.import java.awt.*;

B.package mypackage;

C.class OtherClass{   }

D.public class MyClass{ }



正确答案: D  



# 有程序片段如下，以下表达式结果为 true 的是（ ）

Float  s=new  Float(0.1f);

Float  t=new  Float(0.1f);

Double  u=new  Double(0.1);

A.s==t

B.s.equals(t)

C.u.equals(s)

D.t.equals(u)



正确答案: B  



# 能单独和finally语句一起使用的块是(  )

A.try

B.catch

C.throw

D.throws



正确答案: A



# 以下说法错误的是（）

A.数组是一个对象

B.数组不是一种原生类

C.数组的大小可以任意改变

D.在Java中，数组存储在堆中连续内存空间里



正确答案: C  

 在java中,数组是一个对象, 不是一种原生类,对象所以存放在堆中,又因为数组特性,是连续的,只有C不对



# 在java中，已定义两个接口B和C，要定义一个实现这两个接口的类，以下语句正确的是（）

A.interface  A extends B，C

B.interface  A eimplements  B，C

C.class  A implements  B，C

D.class  A implements  B，implements C



正确答案: C 



# Java的Daemon线程，setDaemon( )设置必须要？

A.在start之前

B.在start之后

C.前后都可以



正确答案: A   

setDaemon()方法必须在线程启动之前调用，当线程正在运行时调用会产生异常。



# //point X

```prettyprint
public class Foo {
    public static void main(String[] args) throws Exception {

        PrintWriter out = new PrintWriter(
            new java.io.OutputStreamWriter(System.out), true);
        
        out.println("Hello");
    }

}   
```


下面哪个选项放在point X这里可以正确执行？

A.import java.io.PrintWriter;

B.include java.io.PrintWriter;

C.import java.io.OutputStreamWriter;

D.include java.io.OutputStreamWriter;

E.no statement is needed.



正确答案: A          

 java中没有include关键字，导包用import
由于代码中使用了printWriter 类，所以要导入此类Import java.io.PrintWriter;



# 如果一个接口Cup有个方法use()，有个类SmallCup实现接口Cup，则在类SmallCup中正确的是？  ( )

A.void use() { …}

B.protected void use() { …}

C.public void use() { …}

D.以上语句都可以用在类SmallCup中



正确答案: C 



# 观察下列代码，分析结果()

```prettyprint
String s1 = "coder";     
String s2 = "coder";     
String s3 = "coder" + s2;     
String s4 = "coder" + "coder";     
String s5 = s1 + s2;            
System.out.println(s3 == s4); 
System.out.println(s3 == s5);    
System.out.println(s4 == "codercoder");
```

A.false；false； true；

B.false；true； true；

C.false；false； false；

D.true；false； true；



正确答案: A     

s1,s2都是保存在字符串常量池中的对象；s3是新创建的对象，在堆中；s4，s5指向的也是字符串常量池中的对象；
所以有s3！=s4，s3!=s5，s4=="codercoder"。即为false;false;true。



# 有如下一段程序：

# 请问最后打印出来的是什么？（）

```prettyprint
public class Test{
    private static int i=1;
    public int getNext(){
        return i++;
    }
    public static void main(String [] args){
        Test test=new Test();
        Test testObject=new Test();
        test.getNext();
        testObject.getNext();
        System.out.println(testObject.getNext());
    }
}
```

#  

A.2

B.3

C.4

D.5



正确答案: B      

 return i++, 先返回i，然后i+1；
第一次调用getNext()方法时，返回的是1，但此时i=2；
第二次调用 getNext()方法时，返回的是2，但此时i=3；
第三次调用 getNext()方法时，返回的是3，但此时i=4；



# 下面有关servlet中init,service,destroy方法描述错误的是？

A.init()方法是servlet生命的起点。一旦加载了某个servlet，服务器将立即调用它的init()方法

B.service()方法处理客户机发出的所有请求

C.destroy()方法标志servlet生命周期的结束

D.servlet在多线程下使用了同步机制，因此，在并发编程下servlet是线程安全的



正确答案: D   

servlet在多线程下其本身并不是线程安全的。
如果在类中定义成员变量，而在service中根据不同的线程对该成员变量进行更改，那么在并发的时候就会引起错误。最好是在方法中，定义局部变量，而不是类变量或者对象的成员变量。由于方法中的局部变量是在栈中，彼此各自都拥有独立的运行空间而不会互相干扰，因此才做到线程安全。



# 根据以下接口和类的定义，要使代码没有语法错误，则类Hero中应该定义方法(    )。

```prettyprint
interface Action{  
    void fly();  
}
class Hero implements Action{  //……  }
```

A.private void fly(){}

B.void fly(){}

C.protected void fly(){}

D.public void fly(){}



正确答案: D



# 以下java程序代码，执行后的结果是（）

```prettyprint
java.util.HashMap map=new java.util.HashMap(); 
map.put("name",null);      
map.put("name","Jack");
System.out.println(map.size());
```

A.0

B.null

C.1

D.2



正确答案: C         

HashMap可以插入null的key或value，插入的时候，检查是否已经存在相同的key，如果不存在，则直接插入，如果存在，则用新的value替换旧的value，在本题中，第一条put语句，会将key/value对插入HashMap，而第二条put，因为已经存在一个key为name的项，所以会用新的value替换旧的vaue，因此，两条put之后，HashMap中只有一个key/value键值对。那就是（name，jack）。所以，size为1.



# 对下面Spring声明式事务的配置含义的说明错误的是（）

```prettyprint
<bean id="txProxyTemplate" abstract="true"
class=
"org.springframework.transaction.interceptor.TransactionProxyFactoryBean">
    <property name="transactionManager" ref="myTransactionManager" />
<property name="transactionAttributes">      
 <props>
        <prop key="get*">PROPAGATION_REQUIRED,readOnly</prop>
         <prop key="*">PROPAGATION_REQUIRED</prop>
     </props>
</property> 
</bean>
```

A.定义了声明式事务的配置模板

B.对get方法采用只读事务

C.缺少sessionFactory属性的注入

D.配置需要事务管理的bean的代理时，通过parent引用这个配置模板，代码如下：
<bean id="petBiz" parent="txProxyTemplate">
         <property name="target" ref="petTarget"/>
</bean>



正确答案: C   



# java程序内存泄露的最直接表现是（ ）

A.频繁FullGc

B.jvm崩溃

C.程序抛内存溢出的Exception

D.java进程异常消失



正确答案: C    

 java是自动管理内存的，通常情况下程序运行到稳定状态，内存大小也达到一个 基本稳定的值
但是内存泄露导致Gc不能回收泄露的垃圾，内存不断变大.
最终超出内存界限，抛出OutOfMemoryExpection



# 关于中间件特点的描述.不正确的是（）

A.中间件运行于客户机/服务器的操作系统内核中，提高内核运行效率

B.中间件应支持标准的协议和接口

C.中间件可运行于多种硬件和操作系统平台上

D.跨越网络,硬件，操作系统平台的应用或服务可通过中间件透明交互



正确答案: A

  

# 下面哪个不属于HttpServletResponse接口完成的功能？

A.设置HTTP头标

B.设置cookie

C.读取路径信息

D.输出返回数据



正确答案: C



# 已知x >= y and y >= z 为真，那么x > z or y = z 值为

A.真

B.假

C.无法确定

D.x y z同为正数时为真



正确答案: C   

条件可以简单分析为数学不等式  x>=y>=z，那么x>z不一定为true
当x>z为true，后面的条件忽略，结果为真；
当x==z，x>z为fslae，继续判断后一个条件
    如果z==0，则y=z为false，结果为假；
    如果z!=0，则y=z为true，结果为真；
所以，最后的结果是不确定的。



# Java多线程有几种实现方法？

A.继承Thread类

B.实现Runnable接口

C.实现Thread接口

D.以上都不正确



正确答案: A B   

两种。
1、继承Thread类，Override它的run方法；
2、实现Runnable接口，实现run方法；

由于Java只有单继承，所以，第一种方法只能继承一个Thread；第二种则可以实现多继承。



# 如果进栈序列为e1，e2，e3，e4，则可能的出栈序列是()

注：一个元素进栈后可以马上出栈，不用等全部进栈

A.e3，e1，e4，e2

B.e2，e4，e3，e1

C.e2，e3，e4，e1

D.任意顺序都有可能



正确答案: B C   



# java中提供了哪两种用于多态的机制

A.通过子类对父类方法的覆盖实现多态

B.利用重载来实现多态.即在同一个类中定义多个同名的不同方法来实现多态。

C.利用覆盖来实现多态.即在同一个类中定义多个同名的不同方法来实现多态。

D.通过子类对父类方法的重载实现多态



正确答案: A B  

 Java通过方法重写和方法重载实现多态
方法重写是指子类重写了父类的同名方法
方法重载是指在同一个类中，方法的名字相同，但是参数列表不同



# 下列说法正确的是（）？

A.我们直接调用Thread对象的run方法会报异常，所以我们应该使用start方法来开启一个线程

B.一个进程是一个独立的运行环境，可以被看做一个程序或者一个应用。而线程是在进程中执行的一个任务。Java运行环境是一个包含了不同的类和程序的单一进程。线程可以被称为轻量级进程。线程需要较少的资源来创建和驻留在进程中，并且可以共享进程中的资源

C.synchronized可以解决可见性问题，volatile可以解决原子性问题

D.ThreadLocal用于创建线程的本地变量，该变量是线程之间不共享的



正确答案: B D 



# JDK提供的用于并发编程的同步器有哪些？

A.Semaphore

B.CyclicBarrier

C.CountDownLatch

D.Counter



正确答案: A B C    

A，Java 并发库 的Semaphore 可以很轻松完成信号量控制，Semaphore可以控制某个资源可被同时访问的个数，通过 acquire() 获取一个许可，如果没有就等待，而 release() 释放一个许可。
B，CyclicBarrier 主要的方法就是一个：await()。await() 方法没被调用一次，计数便会减少1，并阻塞住当前线程。当计数减至0时，阻塞解除，所有在此 CyclicBarrier 上面阻塞的线程开始运行。
C，直译过来就是倒计数(CountDown)门闩(Latch)。倒计数不用说，门闩的意思顾名思义就是阻止前进。在这里就是指 CountDownLatch.await() 方法在倒计数为0之前会阻塞当前线程。
D，Counter不是并发编程的同步器



## 下列流当中，属于处理流的是：（）

A.FilelnputStream

B.lnputStream

C.DatalnputStream

D.BufferedlnputStream



正确答案: C D  

 

# 类中的数据域使用private修饰为私有变量，所以任何方法均不能访问它。

A.正确

B.错误



正确答案: B 

 

# 当点击鼠标或者拖动鼠标时，触发的事件是下列的哪一个？（）

A.KeyEvent

B.AxtionEvent

C.ItemEvent

D.MouseEvent



正确答案: D  



# 在java中，在同一包内，非私有类Cat里面有个公有方法sleep()，该方法前有static修饰，则可以直接用Cat.sleep()。（ ）

A.正确

B.错误



正确答案: A  



# Java中只有整型才能使用的运算符为？

A.*

B./

C.%

D.+



正确答案: C    

ABD选项的操作符都可用于float和double
只有%取余操作，只适用于整型



# 数学表达式|x|<10 对应的java表达式为 。

A.|x|<10

B.x<10&&x>-10

C.x<10||x>-10

D.10>x>-10



正确答案: B 

 

# 下面有关java classloader说法错误的是?

A.Java默认提供的三个ClassLoader是BootStrap ClassLoader，Extension ClassLoader，App ClassLoader

B.ClassLoader使用的是双亲委托模型来搜索类的

C.JVM在判定两个class是否相同时，只用判断类名相同即可，和类加载器无关

D.ClassLoader就是用来动态加载class文件到内存当中用的



正确答案: C    

 JVM在判定两个class是否相同时，不仅要判断两个类名是否相同，而且要判断是否由同一个类加载器实例加载的。



# 

```prettyprint
public class Test { 
    public static void main(String[] args) {
        Father a = new Father();
        Father b = new Child();
    }
} 
class Father { 
    public Father() {
        System.out.println("我是父类");
    }
} 
class Child extends Father { 
    public Child() {
        System.out.println("我是子类");
    }
}
```

A.我是父类
我是父类
我是子类

B.我是父类
我是子类
我是子类

C.我是父类
我是父类

D.我是父类
我是父类
我是父类



正确答案: A 



# 在上下文和头文件正常的情况下，代码将打印？

```prettyprint
System.out.println(10%3*2);
```

A.1

B.2

C.4

D.6



正确答案: B    

%和*是同一个优先级，从左到右运算



# 以下表达式的类型和值（注意整数除法）是（）

-5 + 1/4 + 2*-3 + 5.0

A.int -3

B.int -4

C.double -5.5

D.double -6.0



正确答案: D

  

# java中将ISO8859-1字符串转成GB2312编码，语句为 ？  

A.new String("字符串".getBytes("ISO8859-1"),"GB2312")

B.new String(String.getBytes("GB2312"）, ISO8859-1)

C.new String(String.getBytes("ISO8859-1"))

D.new String(String.getBytes("GB2312"))



正确答案: A

# 下面中哪两个可以在A的子类中使用：（）

```prettyprint
class A {
    protected int method1 (int a, int b) {
        return 0;
    }
}
```

A. public int method 1 (int a, int b) { return 0; }

B. private int method1 (int a, int b) { return 0; }

C. private int method1 (int a, long b) { return 0; }

D. public short method1 (int a, int b) { return 0; }



解答：A C

主要考查子类重写父类的方法的原则

B，子类重写父类的方法，访问权限不能降低
C，属于重载
D，子类重写父类的方法 返回值类型要相同或是父类方法返回值类型的子类



# Abstract method cannot be static. True or False ?

A True

B False



解答：A

抽象方法可以在子类中被重写，但是静态方法不能在子类中被重写，静态方法和静态属性与对象是无关的，只与类有关，这与abstract是矛盾的，所以abstract是不能被修饰为static，否则就失去了abstract的意义了



# What will be the output when you compile and execute the following program.

```prettyprint
class Base {

    void test() {

        System.out.println(“Base.test()”);

    }

}
public class Child extends Base {

    void test() {

        System.out.println(“Child.test()”);

    }

    static public void main(String[] a) {

        Child anObj = new Child();

        Base baseObj = (Base) anObj;

        baseObj.test();

    }

}
```

Select most appropriate answer.

A. Child.test()

Base.test()

B.Base.test()

Child.test()

C.Base.test()

D.Child.test()



解答：D

测试代码相当于：Base baseObj = new Child();父类的引用指向子类的实例，子类又重写了父类

的test方法，因此调用子类的test方法。



# What will be the output when you compile and execute the following program.

```prettyprint
class Base {

    static void test() {

        System.out.println(“Base.test()”);

    }

}

public class Child extends Base {

    void test() {

        System.out.println(“Child.test()”);

        Base.test(); //Call the parent method

    }

    static public void main(String[] a) {

        new Child().test();

    }

}
```

Select most appropriate answer.

A Child.test()

Base.test()

B Child.test()

Child.test()

C Compilation error. Cannot override a static method by an instance method

D Runtime error. Cannot override a static method by an instance method



解答：C

静态方法不能在子类中被重写



# What will be the output when you compile and execute the following program.

```prettyprint
public class Base {

    private void test() {

        System.out.println(6 + 6 + “ (Result)”);

    }

    static public void main(String[] a) {

        new Base().test();

    }

}
```


Select most appropriate answer.

A 66(Result)

B 12(Result)

C Runtime Error.Incompatible type for +. Can’t convert an int to a string.

D Compilation Error.Incompatible type for +. Can’t add a string to an int.



解答：B

字符串与基本数据类型链接的问题,如果第一个是字符串那么后续就都按字符串处理，比如上边例子要是System.out.println(“(Result)”+6 + 6 );那么结果就是(Result)66，如果第一个和第二个。。。第n个都是基本数据第n+1是字符串类型，那么前n个都按加法计算出结果在与字符串连接



# What will be the output when you compile and execute the following program. The symbol ’ ?’ means space.

```prettyprint
1:public class Base{

2:

3: private void test() {

4:

5:      String aStr = “?One?”;

6:      String bStr = aStr;

7:      aStr.toUpperCase();

8:      aStr.trim();

9:      System.out.println(“[" + aStr + "," + bStr + "]“);

7: }

8:

9:  static public void main(String[] a) {

10:   new Base().test();

11: }

12:}
```

Select most appropriate answer.

A [ONE,?One?]

B [?One?,One]

C [ONE,One]

D [ONE,ONE]

E [?One?,?One?]



解答：E

通过String bStr = aStr;这句代码使bStr和aStr指向同一个地址空间，所以最后aStr和bStr的结果应该是一样，String类是定长字符串，调用一个字符串的方法以后会形成一个新的字符串。



# 下面关于变量及其范围的陈述哪些是不正确的（ ）：

A．实例变量是类的成员变量

B．实例变量用关键字static声明

C．在方法中定义的局部变量在该方法被执行时创建

D．局部变量在使用前必须被初始化



解答：BC

由static修饰的变量称为类变量或是静态变量

方法加载的时候创建局部变量



# 下列关于修饰符混用的说法，错误的是（ ）：

A．abstract不能与final并列修饰同一个类

B．abstract类中可以有private的成员

C．abstract方法必须在abstract类中

D．static方法中能处理非static的属性



解答 D

静态方法中不能引用非静态的成员



# 执行完以下代码int [ ] x = new int[25]；后，以下哪项说明是正确的（ ）：

A、 x[24]为0

B、 x[24]未定义

C、 x[25]为0

D、 x[0]为空



解答：A

x属于引用类型，该引用类型的每一个成员是int类型，默认值为：0



# 编译运行以下程序后，关于输出结果的说明正确的是 （ ）：

```prettyprint
public class Conditional {

    public static void main(String args[]) {

        int x = 4;

        System.out.println(“value is“ + ((x > 4) ? 99.9 : 9));

    }

}
```

A、 输出结果为：value is 99.99

B、 输出结果为：value is 9

C、 输出结果为：value is 9.0

D、 编译错误



解答：C

三目运算符中：第二个表达式和第三个表达式中如果都为基本数据类型，整个表达式的运算结果

由容量高的决定。99.9是double类型 而9是int类型，double容量高。



# 关于以下application的说明，正确的是（ ）：

```prettyprint
1． class StaticStuff

2． {

3．   static int x=10；

4．   static { x+=5；}

5．   public static void main（String args[ ]）

6．   {

7．     System.out.println(“x=” + x);

8．   }

9．    static { x/=3;}

10.}
```



A、 4行与9行不能通过编译，因为缺少方法名和返回类型

B、 9行不能通过编译，因为只能有一个静态初始化器

C、 编译通过，执行结果为：x=5

D、 编译通过，执行结果为：x=3



解答：C

自由块是类加载的时候就会被执行到的，自由块的执行顺序是按照在类中出现的先后顺序执行。



# 关于以下程序代码的说明正确的是（ ）：

```prettyprint
1．class HasStatic{

2．  private static int x=100；

3．  public static void main(String args[ ]){

4．    HasStatic hs1=new HasStatic( );

5．    hs1.x++;

6．    HasStatic hs2=new HasStatic( );

7．    hs2.x++;

8．    hs1=new HasStatic( );

9．    hs1.x++;

10．   HasStatic.x–;

11．   System.out.println(“x=”+x);

12．  }

13．}
```

A、5行不能通过编译，因为引用了私有静态变量

B、10行不能通过编译，因为x是私有静态变量

C、程序通过编译，输出结果为：x=103

D、程序通过编译，输出结果为：x=102



解答：D

静态变量是所有对象所共享的，所以上述代码中的几个对象操作是同一静态变量x， 静态变量可以通过类名调用。



# 下列说法正确的有（）

A． class中的constructor不可省略

B． constructor必须与class同名，但方法不能与class同名

C． constructor在一个对象被new时执行

D．一个class只能定义一个constructor



解答：C

构造方法的作用是在实例化对象的时候给数据成员进行初始化

A．类中如果没有显示的给出构造方法，系统会提供一个无参构造方法

B．构造方法与类同名，类中可以有和类名相同的方法

D．构造方法可以重载



# 下列哪种说法是正确的（）

A．实例方法可直接调用超类的实例方法

B．实例方法可直接调用超类的类方法

C．实例方法可直接调用其他类的实例方法

D．实例方法可直接调用本类的类方法



解答：D

A. 实例方法不可直接调用超类的私有实例方法

B. 实例方法不可直接调用超类的私有的类方法

C．要看访问权限



# 下列哪一种叙述是正确的（ ）

A． abstract修饰符可修饰字段、方法和类

B． 抽象方法的body部分必须用一对大括号{ }包住

C． 声明抽象方法，大括号可有可无

D． 声明抽象方法不可写出大括号



解答：D

abstract可以修饰方法和类，不能修饰属性。抽象方法没有方法体，即没有大括号{}



# 下面代码的执行结果是？

```prettyprint
import java.util. * ;

public class ShortSet {

    public static void main(String args[]){

        Set < Short > s = new HashSet < Short > ();

        for (Short i = 0; i < 100; i++){

            s.add(i);

            s.remove(i - 1);

        }

        System.out.println(s.size());

    }

}
```


A.1

B.100

C.Throws Exception

D.None of the Above



解答：B

i是Short类型 i-1是int类型,其包装类为Integer，所以s.remove(i-1);不能移除Set集合中Short类型对象。



# 链表具有的特点是：(选择3项)

A、不必事先估计存储空间

B、可随机访问任一元素

C、插入删除不需要移动元素

D、所需空间与线性表长度成正比



解答：ACD

A.采用动态存储分配，不会造成内存浪费和溢出。

B. 不能随机访问，查找时要从头指针开始遍历

C. 插入、删除时，只要找到对应前驱结点，修改指针即可，无需移动元素

D. 需要用额外空间存储线性表的关系，存储密度小



# Java语言中，String类的IndexOf()方法返回的类型是？

A、Int16 

B、Int32 

C、int 

D、long



解答：C

indexOf方法的声明为：public int indexOf(int ch)
在此对象表示的字符序列中第一次出现该字符的索引；如果未出现该字符，则返回 -1。



# 以下关于面向对象概念的描述中，不正确的一项是（）。(选择1项)

A.在现实生活中，对象是指客观世界的实体

B.程序中的对象就是现实生活中的对象

C.在程序中，对象是通过一种抽象数据类型来描述的，这种抽象数据类型称为类（class）

D.在程序中，对象是一组变量和相关方法的集合



解答：B



# 执行下列代码后,哪个结论是正确的 String[] s=new String[10];

A． s[9] 为 null;

B． s[10] 为 “”;

C． s[0] 为 未定义

D． s.length 为10



解答：AD

s是引用类型，s中的每一个成员都是引用类型，即String类型，String类型默认的值为null

s数组的长度为10。



# 属性的可见性有。(选择3项)

A.公有的

B.私有的

C.私有保护的

D.保护的



解答：ABD

属性的可见性有四种：公有的（public） 保护的（protected） 默认的 私有的（private）



# 在字符串前面加上_____符号，则字符串中的转义字符将不被处理。(选择1项)

A @

B \

C #

D %



解答：B



# 下列代码哪行会出错: (选择1项)

```prettyprint
1) public void modify() { 
2)    int I, j, k; 
3)    I = 100; 
4)    while ( I > 0 ) { 
5)       j = I * 2; 
6)       System.out.println (” The value of j is ” + j ); 
7)       k = k + 1; 
8)       I–; 
9)     } 
10) }
```

A. 4

B. 6

C. 7

D. 8



解答：C

k没有初始化就使用了



# 对记录序列{314，298，508，123，486，145}按从小到大的顺序进行插入排序，经过两趟排序后的结果为：(选择1项)

A {314，298，508，123，145，486}

B {298，314，508，123，486，145}

C {298，123，314，508，486，145}

D {123、298，314，508，486，145}



解答：B

插入排序算法：

```prettyprint
public static void injectionSort(int[] number) {

    // 第一个元素作为一部分，对后面的部分进行循环
    for (int j = 1; j < number.length; j++) {

        int tmp = number[j];

        int i = j–1;

        while (tmp < number[i]) {

            number[i + 1] = number[i];

            i–;

            if (i == -1)

                break;

        }

        number[i + 1] = tmp;

    }

}
```



# 栈是一种。(选择1项)

A 存取受限的线性结构

B 存取不受限的线性结构

C 存取受限的非线性结构

D 存取不受限的非线性结构



解答：A

栈（stack）在计算机科学中是限定仅在表尾进行插入或删除操作的线性表。



# 下列哪些语句关于内存回收的说明是正确的。(选择1项)

A程序员必须创建一个线程来释放内存

B内存回收程序负责释放无用内存

C内存回收程序允许程序员直接释放内存

D内存回收程序可以在指定的时间释放内存对象



解答：B

垃圾收集器在一个Java程序中的执行是自动的，不能强制执行，即使程序员能明确地判断出有一块内存已经无用了，是应该回收的，程序员也不能强制垃圾收集器回收该内存块。程序员唯一能做的就是通过调用System. gc 方法来”建议”执行垃圾收集器，但其是否可以执行，什么时候执行却都是不可知的。



# Which method must be defined by a class implementing the java.lang.Runnable interface?

A. void run()

B. public void run()

C. public void start()

D. void run(int priority)

E. public void run(int priority)

F. public void start(int priority)



解答：B

实现Runnable接口，接口中有一个抽象方法run，实现类中实现该方法。



# Given:

```prettyprint
public static void main(String[] args) {

    Object obj = new Object() {

        public int hashCode() {

            return 42;

        };

    }

    System.out.println(obj.hashCode());

}
```

What is the result?

A. 42

B. An exception is thrown at runtime.

C. Compilation fails because of an error on line 12.

D. Compilation fails because of an error on line 16.

E. Compilation fails because of an error on line 17.



解答：A

匿名内部类覆盖hashCode方法。



# Which two are reserved words in the Java programming language? (Choose two)

A. run

B. import

C. default

D. implements



解答：BD

import导入包的保留字，implements实现接口的保留字。



# Which two statements are true regarding the return values of property written hashCodeand equals methods from two instances of the same class? (Choose two)

A. If the hashCode values are different, the objects might be equal.

B. If the hashCode values are the same, the object must be equal.

C. If the hashCode values are the same, the objects might be equal.

D. If the hashCode values are different, the objects must be unequal.



解答：CD

先通过 hashcode来判断某个对象是否存放某个桶里，但这个桶里可能有很多对象，那么我们就需要再通过 equals 来在这个桶里找到我们要的对象。



# What is the numerical range of a char?

A. 0 … 32767

B. 0 … 65535

C. –256 … 255

D. –32768 … 32767

E. Range is platform dependent.



解答：B

在Java中，char是一个无符号16位类型，取值范围为0到65535。



# Given:

```prettyprint
public class Test {

    private static float[] f = new float[2];

    public static void main(String args[]) {

        System.out.println(“f[0] = “ + f[0]);

    }

}
```

What is the result?

A. f[0] = 0

B. f[0] = 0.0

C. Compilation fails.

D. An exception is thrown at runtime.



解答：B



# Given:

```prettyprint
public class Test {

    public static void main(String[] args) {

        String str = NULL;

        System.out.println(str);

    }

}
```

What is the result?

A. NULL

B. Compilation fails.

C. The code runs with no output.

D. An exception is thrown at runtime.



解答：B

null应该小写



# Exhibit:

```prettyprint
1.public class X implements Runnable {

2.  private int x;

3.  private int y;

4.public static void main(String [] args) {

5.  X that = new X();

6.  (new Thread(that)).start();

7.  (new Thread(that)).start();

8.}

9.public synchronized void run( ){

10.   for (;;) {

11.   x++;

12.   y++;

13.   System.out.println(“x = “ + x + “, y = “ + y);

14.   }

15.   }

16.}
```

What is the result?

A. An error at line 11 causes compilation to fail.

B. Errors at lines 7 and 8 cause compilation to fail.

C. The program prints pairs of values for x and y that might not always be the same on the same line (for example, “x=2, y=1”)

D. The program prints pairs of values for x and y that are always the same on the same line (for example, “x=1, y=1”. In addition, each value appears twice (for example, “x=1, y=1” followed by “x=1, y=1”)

E. The program prints pairs of values for x and y that are always the same on the same line (for example, “x=1, y=1”. In addition, each value appears twice (for example, “x=1, y=1” followed by “x=2, y=2”)



解答：E

多线程共享相同的数据，使用synchronized实现数据同步。



# Which two CANNOT directly cause a thread to stop executing? (Choose Two)

A. Existing from a synchronized block.

B. Calling the wait method on an object.

C. Calling notify method on an object.

D. Calling read method on an InputStream object.

E. Calling the SetPriority method on a Thread object.



解答：AD

stop方法.这个方法将终止所有未结束的方法，包括run方法。当一个线程停止时候，他会立即释

放 所有他锁住对象上的锁。这会导致对象处于不一致的状态。 当线程想终止另一个线程的时

候，它无法知道何时调用stop是安全的，何时会导致对象被破坏。所以这个方法被弃用了。你应

该中断一个线程而不是停止他。被中断的线程会在安全的时候停止。



# Which two statements are true regarding the creation of a default constructor? (Choose Two)

A. The default constructor initializes method variables.

B. The default constructor invokes the no-parameter constructor of the superclass.

C. The default constructor initializes the instance variables declared in the class.

D. If a class lacks a no-parameter constructor,, but has other constructors, the compiler creates a default constructor.

E. The compiler creates a default constructor only when there are no other constructors for the class.



解答：CE

构造方法的作用是实例化对象的时候给数据成员初始化，如果类中没有显示的提供构造方法，系统会提供默认的无参构造方法，如果有了其它构造方法，默认的构造方法不再提供。



#  Given:

```prettyprint
public class OuterClass {

    private double d1 = 1.0;

    //insert code here
}
```

You need to insert an inner class declaration at line2. Which two inner class declarations are valid? (Choose Two)

A. 

```prettyprint
static class InnerOne {
    public double methoda() {
        return d1;
    }
}
```

B. 

```prettyprint
static class InnerOne {
    static double methoda() {
        return d1;
    }
}
```

C.

```prettyprint
private class InnerOne {
    public double methoda() {
        return d1;
    }
}
```

D.

```prettyprint
protected class InnerOne {
    static double methoda() {
        return d1;
    }
}
```

E.

```prettyprint
public abstract class InnerOne {
    public abstract double methoda();
}
```



解答：CE

AB.内部类可以声明为static的，但此时就不能再使用外层封装类的非static的成员变量；

D.非static的内部类中的成员不能声明为static的，只有在顶层类或static的内部类中才可声明static成员



#  Which two declarations prevent the overriding of a method? (Choose Two)

A. final void methoda() {}

B. void final methoda() {}

C. static void methoda() {}

D. static final void methoda() {}

E. final abstract void methoda() {}



解答：AD

final修饰方法，在子类中不能被重写。



# Given:

```prettyprint
public class Test {

    public static void main(String args[]) {

        class Foo {

            public int i = 3;

        }

        Object o = (Object) new Foo();

        Foo foo = (Foo) o;

        System.out.println(foo.i);

    }

}
```

What is the result?

A. Compilation will fail.

B. Compilation will succeed and the program will print “3”

C. Compilation will succeed but the program will throw a ClassCastException at line 6.

D. Compilation will succeed but the program will throw a ClassCastException at line 7.



解答：B

局部内部类的使用



# Given:

```prettyprint
public class Test {

    public static void main(String[] args) {

        String foo = “blue”;

        String bar = foo;

        foo = “green”;

        System.out.println(bar);

    }

}
```


What is the result?

A. An exception is thrown.

B. The code will not compile.

C. The program prints “null”

D. The program prints “blue”

E. The program prints “green”



解答：D

采用String foo = “blue”定义方式定义的字符串放在字符串池中，通过String bar = foo;

他们指向了同一地址空间，就是同一个池子，当执行foo = “green”; foo指向新的地址空间。



# Which code determines the int value foo closest to a double value bar?

A. int foo = (int) Math.max(bar);

B. int foo = (int) Math.min(bar);

C. int foo = (int) Math.abs(bar);

D. int foo = (int) Math.ceil(bar);

E. int foo = (int) Math.floor(bar);

F. int foo = (int) Math.round(bar);



解答：DEF

A B两个选项方法是用错误，都是两个参数。

abs方法是取bar的绝对值，

ceil方法返回最小的（最接近负无穷大）double 值，该值大于等于参数，并等于某个整数。

floor方法返回最大的（最接近正无穷大）double 值，该值小于等于参数，并等于某个整数。

round方法 返回最接近参数的 long。



#  Exhibit:

```prettyprint
1.package foo;

2.import java.util.Vector;

3.private class MyVector extends Vector {

4.    int i = 1;

5.    public MyVector() {

6.          i = 2;

7.    }

8.}

9.public class MyNewVector extends MyVector {

10.    public MyNewVector () {

11.        i = 4;

12.    }

13.    public static void main (String args []) {

14.        MyVector v = new MyNewVector();

15.    }

16.}
```

The file MyNewVector.java is shown in the exhibit. What is the result?

A. Compilation will succeed.

B. Compilation will fail at line 3.

C. Compilation will fail at line 6.

D. Compilation will fail at line 9.

E. Compilation will fail at line 14.



解答：B

类MyVector不能是私有的



# Given:

```prettyprint
public class Test {

    public static void main(String[] args) {

        String foo = args[1];

        String bar = args[2];

        String baz = args[3];

        System.out.println(“baz = ” + baz);

    }

}

And the output:

Baz = 2
```

Which command line invocation will produce the output?

A. java Test 2222

B. java Test 1 2 3 4

C. java Test 4 2 4 2

D. java Test 4 3 2 1



解答：C

数组下标从0开始



# Given:

```prettyprint
1.public interface Foo{

2.  int k = 4;

3.}
```

Which three are equivalent to line 2? (Choose Three)

A. final int k = 4;

B. Public int k = 4;

C. static int k = 4;

D. Private int k = 4;

E. Abstract int k = 4;

F. Volatile int k = 4;

G. Transient int k = 4;

H. protected int k = 4;



解答：BDE

static：修饰的静态变量

final 修饰的是常量

abstract不能修饰变量

Volatile修饰的成员变量在每次被线程访问时，都强迫从共享内存中重读该成员变量的值。

而且，当成员变量发生变化时，强迫线程将变化值回写到共享内存。这样在任何时刻，

两个不同的线程总是看到某个成员变量的同一个值。
Transient：对不需序列化的类的域使用transient关键字,以减少序列化的数据量。

int k=4相当于public static final int k=4; 在接口中可以不写static final



#  Given:

```prettyprint
public class foo {

    static String s;

    public static void main(String[] args) {

        System.out.println(“s = ” + s);

    }

}
```

What is the result?

A. The code compiles and “s=” is printed.

B. The code compiles and “s=null” is printed.

C. The code does not compile because string s is not initialized.

D. The code does not compile because string s cannot be referenced.

E. The code compiles, but a NullPointerException is thrown when toString is called.



解答：B

String为禁用数据类型，引用类型数据成员的默认值为null



# Which two create an instance of an array? (Choose Two)

A. int[] ia = new int [15];

B. float fa = new float [20];

C. char[] ca = “Some String”;

D. Object oa = new float[20];

E. Int ia [][] = (4, 5, 6) (1, 2, 3)



解答：AD

任何类的父类都是Object，数组也数据引用类型，Object oa = new float[20];这种写法相当于父类的用指向之类的实例。



# Given:

```prettyprint
public class ExceptionTest {

    class TestException extends Exception {}

    public void runTest() throws TestException {}

    public void test()
        /* Point X*/
    {

        runTest();

    }

}
```

At point X on line 4, which code can be added to make the code compile?

A. throws Exception

B. Catch (Exception e).

C. Throws RuntimeException.

D. Catch (TestException e).

E. No code is necessary.



解答：A

方法上使用throws抛出异常，Exception是异常类的超类。



# Exhibit:

```prettyprint
public class SwitchTest {

    public static void main(String[] args) {

        System.out.println(“value = ” + switchIt(4));

    }

    public static int switchIt(int x) {

        int j = 1;

        switch (x) {

            case 1:
                j++;

            case 2:
                j++;

            case 3:
                j++;

            case 4:
                j++;

            case 5:
                j++;

            default:
                j++;

        }

        return j + x;

    }

}
```

What is the output from line 3?

A. Value =3

B. Value =4

C. Value =5

D. Value =6

E. Value =7

F. Value =8



解答：F

由于case块没有break语句，那么从case 4：向下的代码都会执行。



# Which four types of objects can be thrown using the throw statement? (Choose Four)

A. Error

B. Event

C. Object

D. Exception

E. Throwable

F. RuntimeException



解答：ADEF

能够抛出的对象类型要是Throwable 或是Throwable的子类



# 在下面程序的第6行补充上下列哪个方法,会导致在编译过程中发生错误?

```prettyprint
1)class Super{

2)  public float getNum(){

3)    return 3.0f;

4)  }

  }

5)pubhc class Sub extends Super{

6)

7)}
```

A,public float getNum(){retun 4.0f;}

B.public void getNum(){}

C.public void getNum(double d){}

D.public double getNum(float d){ retun 4.0f ;} 



解答：B

方法重写的问题。子类中有和父类的方法名相同，但是参数不同，不会出编译错误，认为是子类

的特有的方法，但是如果子类中方法和父类的方法名，参数，访问权限，异常都相同，只有返回值

类型不同会编译不通过。



# 下面关于import, class和package的声明顺序哪个正确？( )

A. package, import, class

B. class, import, package

C. import, package, class

D. package, class, import



解答：A



# 下面哪个是正确的？( )

A. String temp [] = new String {“a” “b” “c”};

B. String temp [] = {“a” “b” “c”}

C. String temp = {“a”, “b”, “c”}

D. String temp [] = {“a”, “b”, “c”}



解答：D



# 关于java.lang.String类，以下描述正确的一项是（ ）

A. String类是final类故不可以继承；

B. String类是final类故可以继承；

C. String类不是final类故不可以继承；

D. String类不是final类故可以继承； 



解答：A

String类是final的，在java中final修饰类的不能被继承



# 关于实例方法和类方法，以下描述正确的是：( )

A. 实例方法只能访问实例变量

B. 类方法既可以访问类变量，也可以访问实例变量

C. 类方法只能通过类名来调用

D. 实例方法只能通过对象来调用



解答：D

A 实例方法可以访问类变量

B类方法只能访问类变量

C类方法可以通过对象调用



# 接口是Java面向对象的实现机制之一，以下说法正确的是：( )

A. Java支持多重继承，一个类可以实现多个接口；

B. Java只支持单重继承，一个类可以实现多个接口；

C. Java只支持单重继承，一个类只可以实现一个接口；

D. Java支持多重继承，但一个类只可以实现一个接口。



解答：B

Java支持单重继承，一个类只能继承自另外的一个类，但是一个类可以实现多个接口。



# 下列关于interface的说法正确的是：( )

A. interface中可以有private方法

B. interface中可以有final方法

C. interface中可以有function实现

D. interface可以继承其他interface



解答：D

A.接口中不可以有private的方法

B．接口中不可以有final的方法 接口中的方法默认是 public abstract的

C．接口中的方法不可以有实现



# 已知A类被打包在packageA , B类被打包在packageB ，且B类被声明为public ，且有一个成员变量x被声明为, protected控制方式 。C类也位于packageA包，且继承了B类 。则以下说话正确的是（ ）

A. A类的实例不能访问到B类的实例

B. A类的实例能够访问到B类一个实例的x成员

C. C类的实例可以访问到B类一个实例的x成员

D. C类的实例不能访问到B类的实例



解答：C

不同包子类的关系， 可以访问到父类B的protected成员



# 以下程序正确的输出是（ ）

```prettyprint
package test;

public class FatherClass {

    public FatherClass() {

        System.out.println(“FatherClass Create”);

    }

}

package test;

import test.FatherClass;

public class ChildClass extends FatherClass {

    public ChildClass() {

        System.out.println(“ChildClass Create”);

    }

    public static void main(String[] args) {

        FatherClass fc = new FatherClass();

        ChildClass cc = new ChildClass();

    }

}
```

A.

FatherClass Create

FatherClass Create

ChildClass Create

B.

FatherClass Create

ChildClass Create

FatherClass Create

C.

ChildClass Create

ChildClass Create

FatherClass Create

D.

ChildClass Create

FatherClass Create

FatherClass Create



解答：A

在子类构造方法的开始默认情况下有一句super();来调用父类的构造方法



# 给定如下代码，下面哪个可以作为该类的构造函数 ( )

```prettyprint
public class Test {

}
```

A. public void Test() {?}

B. public Test() {?}

C. public static Test() {?}

D. public static void Test() {?}



解答：B

构造方法：与类同名没有放回类型



# 题目:

```prettyprint
1.public class test (

2.public static void main (String args[]) {

3.  int i = 0xFFFFFFF1;

4.  int j = ~i;

5.

6.  }

7.  )
```



程序运行到第5行时,j的值为多少?( )

A. –15

B. 0

C. 1

D. 14

E. 在第三行的错误导致编译失败



解答：D

int i = 0xFFFFFFF1;相当于 int i=-15 然后对i进行取反即取绝对值再减一



# 关于sleep()和wait()，以下描述错误的一项是（ ）

A. sleep是线程类（Thread）的方法，wait是Object类的方法；

B. sleep不释放对象锁，wait放弃对象锁；

C. sleep暂停线程、但监控状态仍然保持，结束后会自动恢复；

D. wait后进入等待锁定池，只有针对此对象发出notify方法后获得对象锁进入运行状态。



解答：D

sleep是线程类（Thread）的方法，导致此线程暂停执行指定时间，给执行机会给其他线程，但是监控状态依然保持，到时后会自动恢复。调用sleep不会释放对象锁。

wait是Object类的方法，对此对象调用wait方法导致本线程放弃对象锁，进入等待此对象的等待锁定池，只有针对此对象发出notify方法（或notifyAll）后本线程才进入对象锁定池准备获得对象锁进入运行状态。



# 62.下面能让线程停止执行的有（多选）( )

A. sleep();

B. stop();

C. notify();

D. synchronized();

E. yield();

F. wait();

G. notifyAll();



解答：ABDEF

sleep：导致此线程暂停执行指定时间

stop: 这个方法将终止所有未结束的方法，包括run方法。

synchronized():对象锁

yield：当前正在被服务的线程可能觉得cpu的服务质量不够好，于是提前退出，这就是yield。

wait：当前正在被服务的线程需要睡一会，醒来后继续被服务



# 下面哪个可以改变容器的布局？( )

A. setLayout(aLayoutManager);

B. addLayout(aLayoutManager);

C. layout(aLayoutManager);

D. setLayoutManager(aLayoutManager);



解答：A

Java设置布局管理器setLayout()



# 下面哪个是applet传递参数的正确方式？（ ）

A. <applet code=Test.class age=33 width=1 height=1>

B. <param name=age value=33>

C. <applet code=Test.class name=age value=33 width=1 height=1>

D. <applet Test 33>



解答：B



# 提供Java存取数据库能力的包是（）

A．java.sql

B．java.awt

C．java.lang

D．java.swing



解答：A

java.sql是JDBC的编程接口

java.awt和java.swing是做图像界面的类库

java.lang: Java 编程语言进行程序设计的基础类



# 不能用来修饰interface的有（）

A．private

B．public

C．protected

D．static



解答：ACD

修饰接口可以是public和默认



# 下列说法错误的有（）

A． 在类方法中可用this来调用本类的类方法

B． 在类方法中调用本类的类方法时可直接调用

C． 在类方法中只能调用本类中的类方法

D． 在类方法中绝对不能调用实例方法



解答：ACD

A.在类方法中不能使用this关键字

C．在类方法中可以调用其它类中的类方法

D．在类方法中可以通过实例化对象调用实例方法



# 从下面四段（A，B，C，D）代码中选择出正确的代码段（）

A．

```prettyprint
abstract class Name {

    private String name;

    public abstract boolean isStupidName(String name) {}

}
```

B．

```prettyprint
public class Something {

    void doSomething() {

        private String s = ̶”;

        int l = s.length();
    }
}
```

C．

```prettyprint
public class Something {

    public static void main(String[] args) {

        Other o = new Other();

        new Something().addOne(o);

    }

    public void addOne(final Other o) {

        o.i++;

    }

}

class Other {

    public int i;

}
```

D．

```prettyprint
public class Something {

    public int addOne(final int x) {

        return++x;

    }

}
```



解答：C

A..抽象方法不能有方法体

B．方法中定义的是局部变量，不能用类成员变量修饰符private

D．final修饰为常量，常量的值不能被改变



# 选择下面代码的运行结果：（）。

```prettyprint
public class Test {

    public void method(){

        for (int i = ; i < 3; i++){

            System.out.print(i);

        }

        System.out.print(i);

    }

}
```

A．122

B．123

C．编译错误

D．没有任何输出



解答：C

i变量的作用范围是整个for循环



# 请看如下代码 下面哪些放在// point x?行是正确的？  

```prettyprint
i = m;

class Person {
    private int a;
    public int change(int m) {
        return m;
    }
}
public class Teacher extends Person {
    public int b;
    public static void main(String arg[]) {
        Person p = new Person();
        Teacher t = new Teacher();
        int i;
        // point x 
    }
}
```

A， i = m;

B， i = b;

C， i = p.a; 

D， i = p.change(3);

E， i = t.b;



解答：DE

A.不同的作用域

B．静态方法中不能直接使用非静态成员变量

C．类外不能访问其它类私有的成员

D，E．在类方法中可以通过实例化对象调用类中的实例成员。 



# 下面那几个函数是public void method(){̷}的重载函数？（）

A.public void method( int m){̷}

B.public int method(){̷}

C.public void method2(){̷}

D.public int method(int m，float f ){̷}



解答：A

重载：方法名相同，参数列表不同



# 给出如下声明：

String s = “Example”;

合法的代码由哪些？

A）s>>>=3 

B）s[3]= “X” 

C）int i = s.iength() 

D）s = s +1



解答：D

A. 移位运算，要是整数类型。

B．s不是数组

C．String类取长度的方法为：length()

D. 字符串相加



# 如下哪些不是java的关键字？（ ）

A.const

B.NULL

C.false

D.this

E.native



解答：BC

虽然null false 还有true不是java的关键字，但是都有特殊用途，不建议作为标识符。



# 已知表达式 int m [ ] = {，1，2，3，4，5，6}；

下面哪个表达式的值与数组下标量总数相等？（ ）

A .m.length()

B.m.length

C.m.length()+1

D.m.length+1



解答：B

解答：数组下标是从零开始的，但是数据下标的总量和数据长度相同。



# 方法resume()负责恢复哪些线程的执行（ ）

A.通过调用stop()方法而停止的线程。

B.通过调用sleep()方法而停止的线程。

C.通过调用wait()方法而停止的线程。

D.通过调用suspend()方法而停止的线程。



解答：D

Suspend可以挂起一个线程，就是把这个线程暂停了，它占着资源，但不运行，用Resume是恢复挂起的线程，

让这个线程继续执行下去。



# 有关线程的哪些叙述是对的（ ）

A一旦一个线程被创建，它就立即开始运行。

B使用start()方法可以使一个线程成为可运行的，但是它不一定立即开始运行。

C当一个线程因为抢先机制而停止运行，它被放在可运行队列的前面。

D一个线程可能因为不同的原因停止并进入就绪状态。



解答： BCD

在抢占式线程模型中，操作系统可以在任何时候打断线程。通常会在它运行了一段时间（就是所谓的一个

时间片）后才打断它。这样的结果自然是没有线程能够不公平地长时间霸占处理器。



# 已知如下代码：执行后的输出是什么？（ ）

```prettyprint
public class Test{

    public static void main(String arg[]){

        int i = 5;

        do {

            System.out.print(i);

        } while (– i > 5 );

        System.out.print(“finished”);

    }

}
```



A 5

B 4

C 6

D finished



解答：AD

输出5finished，do„while循环中循环体一定会执行一次



# 下面的哪些声明是合法的？（ ）

A.long 1 = 499

B.int i = 4L

C.float f =1.1

D.double d = 34.4



解答：AD

B.4L应该是long类型的写法，

C.1.1是double类型 ，float f=1.1f是正确写法



# 给出如下代码：（ ）

```prettyprint
class Test {

    private int m;

    public static void fun() {

        //some code„

    }

}
```

如何使成员变量m被函数fun()直接访问？（）

A.将private int m改为 protected int m

B.将private int m改为 public int m

C.将private int m改为 static int m

D.将private int m改为int m



解答：C

静态的方法中可以直接调用静态数据成员



# 以下哪个方法用于定义线程的执行体？（）

A.start()

B.init()

C.run()

D.main()

E.synchronized()



解答：C 

run方法是线程的执行体



# 给出下面的代码段：在代码说明//assignment x=a， y=b处写下如下哪几个代码是正确的？（ ）

```prettyprint
public class Base {

    int w，x，y，z;

    public Base(int a，int b) {
        x = a;
        y = b;
    }

    public Base(int a，int b，int c，int d){
        //assignment x=a， y=b
        w = d;
        z = c;
    }
}
```



A.Base(a， b)；

B.x=a， y=b；

C.x=a； y=b；

D.this(a，b)；



解答：CD

C是直接给x，y赋值

D是使用this调用本类中其它的构造方法



# 关于运算符>>和>>>描述正确的是

A.>>执行移动

B.>>执行翻转

C.>>执行有符号左移，>>>执行无符号左移

D.>>执行无符号左移，>>>执行有符号左移



解答：C



# 选择Java语言中的基本数据类型（多选）

A.byte

B.Integer

C.String

D.char

E.long



答案：ADE

基本数据类型总共有8个：byte，short，int，long，char，boolean，float，double





# 从下列选项中选择正确的Java表达式

A.int k=new String(“aa”)

B.String str=String(“bb”)

C.char c=74;

D.long j=8888;



解答：BCD



# Java I/O程序设计中，下列描述正确的是

A. OutputStream用于写操作

B. InputStream用于写操作

C. I/O库不支持对文件可读可写API



解答：A

B.InputStream用于读操作

C．I/O支持对文件的读写



# 下述代码的执行结果是

```prettyprint
class Super {
    public int getLength() {
        return 4;
    }
}

public class Sub extends Super {
    public long getLength() {
        return 5;
    }

    public static void main(String[] args) {
        Super sooper = new Super();
        Super sub = new Sub();
        System.out.printIn(sooper.getLength() + “，” + sub.getLength();
    }
}
```

A. 4， 4 

B. 4， 5 

C. 5， 4

D. 5， 5 

E. 代码不能被编译



解答：E

方法重写返回值类型与父类的一致



# Which two demonstrate a ̶has a” relationship(Choose two)?

A. public interface Person { }

public class Employee extends Person{ }

B. public interface Shape { }

public interface Rectandle extends Shape { }

C. public interface Colorable { }

public class Shape implements Colorable

{ }

D. public class Species{ }

public class Animal{private Species species;}

E. interface Component{ }

class Container implements Component{

private Component[] children;

}



解答：D

“has a”是关联关系，关联分双向关联和单向关联，双向关联是A，B类分别持有对方的引用(有是对方的属性).

单向关联是一方持另一方的引用.



# Given the folowing classes which of the following will compile without error?

```prettyprint
interface IFace {}

class CFace implements IFace {}

class Base {}

public class ObRef extends Base {

    public static void main(String argv[]) {

        ObRef ob = new ObRef();

        Base b = new Base();

        Object o1 = new Object();

        IFace o2 = new CFace();

    }

}
```

A. o1=o2;

B. b=ob;

C. ob=b;

D. o1=b;



解答：B

b和ob对应的类之间没有任何关系，要想b=ob成立要么是父子关系，要么是接口实现类的关系



# 关于Java语言，下列描述正确的是（多选）

A. switch 不能够作用在String类型上

B. List， Set， Map都继承自Collection接口

C. Java语言支持goto语句

D. GC是垃圾收集器，程序员不用担心内存管理



解答：AD

B. Map没有继承Collection接口

C．java不支持goto语句



# 指出下列程序运行的结果 

```prettyprint
public class Example {
    String str = new String(̶good”);
    char[] ch = {'a'，'b'，'c'};

    public static void main(String args[]) {
        Example ex = new Example();
        ex.change(ex.str，ex.ch);
        System.out.print(ex.str + ”and̶);
        System.out.print(ex.ch);
    }
    public void change(String str，char ch[]) {
        str = ”test ok”;
        ch[] = ’g '; 
    } 
}
```

A good and abc

B good and gbc

C test ok and abc

D test ok and gbc



解答：B

数组和字符串都是引用类型。



# 下列描述中，哪些符合Java语言的特征

A. 支持跨平台(Windows，Linux，Unix等)

B. GC(自动垃圾回收)，提高了代码安全性

C. 支持类C的指针运算操作

D. 不支持与其它语言书写的程序进行通讯



解答：AB



# 关于异常(Exception)，下列描述正确的是

A. 异常的基类为Exception，所有异常都必须直接或者间接继承它

B. 异常可以用try{ . . .}catch(Exception e){ . . .}来捕获并进行处理

C. 如果某异常继承RuntimeException，则该异常可以不被声明

D. 异常可以随便处理，而不是抛给外层的程序进行处理 



解答：ABC



# 下面的代码实现了设计模式中的什么模式

```prettyprint
public class A {
    private A instance;
    private A() {}
    public static A getInstance {
        if (A == null) instance = new A();
        return instance;
    }
}
```

A. Factory

B. Abstract Factory

C. Singleton

D. Builder



解答：C

Singleton单例模式：该设计模式确保某一个类只有一个实例，而且自行实例化并向整个系统提供这个实例



# MAX_LENGTH 是int 型public 成员变量，变量值保持为常量1，用简短语句定义这个变量。

A.public int MAX_LENGTH=1;

B. final int MAX_LENGTH=1;

C. final public int MAX_LENGTH=1;

D. public final int MAX_LENGTH=1.



解答：D 

通过题的描述就是定义常量，在java中常量命名规范是所有字母都大写用下划线分割每个单词



# 

```prettyprint
String s=new String(“hello”);

String t =new String(“hello”);

char c [ ] ={‘h’，’e’，’l’，’l’，’o’};
```

下列哪些表达式返回true ?

A．s.equals(t);

B．t.equals(c);

C．s= =t ；

D．t.equals (new String(“hello”));

E．t= = c；



解答：AD 

String类的equals方法已经覆盖了Object类的equals方法，比较的是两个字符串的内容是否相等，双等号比较的是两个对象的内存地址是否相等



# 类 Teacher 和 Student 是类 Person 的子类;

```prettyprint
Teacher t;

Student s;

// t and s are all non-null.
if (t instanceof Person) {
    s = (Student) t;
}
```

最后一条语句的结果是:

A．将构造一个Student 对象;

B．表达式是合法的；

C．表达式是错误的；

D．编译时正确， 但运行时错误。



解答：D

instanceof是Java的一个二元操作符，它的作用是测试它左边的对象是否是它右边的类的实例，返回boolean类型的数据。

Teahcer和Student之间没有继承关系不能做强制类型转换。 



# 关于线程设计，下列描述正确的是

A. 线程对象必须实现Runnable接口

B. 启动一个线程直接调用线程对象的run()方法

C. Java提供对多线程同步提供语言级的支持

D. 一个线程可以包含多个进程



解答：C



# 欲构造ArrayList类得一个实例，此类继承了List接口，下列哪个方法是正确的：

A ArrayList myList = new Object();

B List myList = new ArrayList();

C ArraylList myList = new List();

D List myList = new List();



解答：B



# 关于线程设计，下列描述正确的是

A. 线程对象必须实现Runnable接口

B. 启动一个线程直接调用线程对象的run()方法

C. Java提供对多线程同步提供语言级的支持

D. 一个线程可以包含多个进程



解答：C



# 以下各DOS命令能够显示出本机DNS服务器地址的是：( )

A．ping -a

B．ipconfig -all

C．netstat

D．telnet



解答：DOS命令的使用

ping命令：利用它可以检查网络是否能够连通，用好它可以很好地帮助我们分析判定网络故障

ifconfig all ：显示或设置网络设备

netstat: 用于查看当前基于 NETBIOS 的 TCP/IP 连接状态，通过该工具你可以 获得远程或本地

的组名和机器名。

telnet: 使用telnet命令访问远程计算机



# 在使用匿名登录ftp时，用户名为( )？ (选择1项)

A、login users

B、anonymous

C、root

D、guest



解答：B



# 管理计算机通信的规则称为

A.协议

B.介质

C.服务

D.网络操作系统



解答：A



# TCP通信建立在连接的基础上，TCP连接的建立要使用几次握手的过程。

A.2

B.3

C.4

D.5



解答:B



# 路由器工作在ISO/OSI参考模型的

A. 数据链路层

B.网络层

C. 传输层



解答：B

网络层属于OSI中的较高层次了，从它的名字可以看出，它解决的是网络与网络之间，即网际的通信问题，而不是同一网段内部的事。网络层的主要功能即是提供路由，即选择到达目标主机的最佳路径，并沿该路径传送数据包。除此之外，网络层还要能够消除网络拥挤，具有流量控制和拥挤控制的能力。网络边界中的路由器就工作在这个层次上，现在较高档的交换机也可直接工作在这个层次上，因此它们也提供了路由功能，俗称“第三层交换机”.



# OSI体系结构定义了一个几层模型。

A.6

B.7

C.8



解答:B

OSI-RM ISO／OSI Reference Model

该模型是国际标准化组织（ISO）为网络通信制定的协议，根据网络通信的功能要求，它把通信过程分为七层，分别为物理层、数据链路层、网络层、传输层、会话层、表示层和应用层，每层都规定了完成的功能及相应的协议。



# 以下哪个命令用于测试网络连通。

A.telnet

B. netstat

C. ping

D. ftp



解答：C



# 在一个办公室内，将6台计算机用交换机连接成网络，该网络的屋里拓扑结构为

A 星型

B 总线型

C 树型

D 环型



解答：C

选项A：星型拓扑结构 是一种以中央节点为中心，把若干外围节点连接起来的辐射式互联结构。这种结构适用于局域网，特别是近年来连接的局域网大都采用这种连接方式。这种连接方式以双绞线或同轴电缆作连接线路。

优点：结构简单、容易实现、便于管理，通常以集线器（Hub）作为中央节点，便于维护和管理。缺点：中心结点是全网络的可靠瓶颈，中心结点出现故障会导致网络的瘫痪。

选项B：总线拓扑结构 是将网络中的所有设备通过相应的硬件接口直接连接到公共总线上，结点之间按广播方式通信，一个结点发出的信息，总线上的其它结点均可“收听”到。

优点：结构简单、布线容易、可靠性较高，易于扩充，节点的故障不会殃及系统，是局域网常采用的

拓扑结构。

缺点：所有的数据都需经过总线传送，总线成为整个网络的瓶颈；出现故障诊断较为困难。另外，由于信道共享，连接的节点不宜过多，总线自身的故障可以导致系统的崩溃。最著名的总线拓扑结构是以太网（Ethernet）。

选项C ：树型拓扑结构 是一种层次结构，结点按层次连结，信息交换主要在上下结点之间进行，相邻结点或同层结点之间一般不进行数据交换。

优点：连结简单，维护方便，适用于汇集信息的应用要求。

缺点：资源共享能力较低，可靠性不高，任何一个工作站或链路的故障都会影响整个网络的运行。

选项D： 环形拓扑结构 各结点通过通信线路组成闭合回路，环中数据只能单向传输，信息在每台设备上的延时时间是固定的。特别适合实时控制的局域网系统。

优点：结构简单，适合使用光纤，传输距离远，传输延迟确定。

缺点：环网中的每个结点均成为网络可靠性的瓶颈，任意结点出现故障都会造成网络瘫痪，另外故障诊断也较困难。最著名的环形拓扑结构网络是令牌环网（Token Ring）






# 中央处理单元（CPU）的两个主要组成部分是运算器和什么。

A.寄存器

B.主存储器

C.控制器

D.辅助存储器



解答：C

控制器:由程序计数器、指令寄存器、指令译码器、时序产生器和操作控制器组成，它是发布命令的“决策机构”，即完成协调和指挥整个计算机系统的操作。

运算器：arithmetic unit，计算机中执行各种算术和逻辑运算操作的部件。运算器由：算术逻辑单元（ALU）、累加器、状态寄存器、通用寄存器组等组成。主要功能：执行所有的算术运算；执行所有的逻辑运算，并进行逻辑测试，如零值测试或两个值的比较。





# 用于电子邮件的协议是。

A．IP

B．TCP

C. SNMP

D．SMTP



解答：D



# Java网络程序设计中，下列正确的描述是

A. Java网络编程API建立在Socket基础之上

B. Java网络接口只支持TCP以及其上层协议

C. Java网络接口只支持UDP以及其上层协议

D. Java网络接口支持IP以上的所有高层协议



解答:AD



# 下列哪些是J2EE的体系。

A、JSP

B、JAVA

C、Servlet

D、WebService



解答：ACD

J2EE现在更多使用的名字是Java EE JSP是JavaEE设计模式MVC中的显示部分，Servlet是控制部分，WebService是JavaEE的服务器。


