
# 第26条：请不要使用原生态类型（Don't use raw types）

# 第27条：消除非受检的警告

```java
@SuppressWarnings("unchecked")//执行了未检查的转换时的警告，例如当使用集合时没有用泛型 (Generics) 来指定集合保存的类型。

@SuppressWarnings("unused")  //未使用的变量

@SuppressWarnings("resource")  //有泛型未指定类型

@SuppressWarnings("path")  //在类路径、源文件路径等中有不存在的路径时的警告

@SuppressWarnings("deprecation")  //使用了不赞成使用的类或方法时的警告

@SuppressWarnings("fallthrough") //当 Switch 程序块直接通往下一种情况而没有 break; 时的警告

@SuppressWarnings("serial")//某类实现Serializable(序列化)， 但没有定义 serialVersionUID 时的警告

@SuppressWarnings("rawtypes") //没有传递带有泛型的参数

@SuppressWarnings("finally") //任何 finally 子句不能正常完成时的警告。

@SuppressWarnings("try") // 没有catch时的警告

@SuppressWarnings("all") //所有类型的警告

// 以下是源码引用中见到的，但实际很少用到的

@SuppressWarnings("FragmentNotInstantiable")

@SuppressWarnings("ReferenceEquality")

@SuppressWarnings("WeakerAccess")

@SuppressWarnings("UnusedParameters")

@SuppressWarnings("NullableProblems")

@SuppressWarnings("SameParameterValue")

@SuppressWarnings("PointlessBitwiseExpression")
```

# 第28条：列表优于数组
在 java 中，数组是基本类型，数组是协办（covariant）的。泛型是不变（invariant）的。
例如：Sub 是 Super 的子类型，那么 Sub[] 也是 Super[] 子类。

```java
// 数组运行时错误
Object[] objectArray = new Long[1];
objectArray[0] = "I don't fit in";

// 泛型列表编译时错误
List<Object> o1 = new ArrayList<Long>();
o1.add("I don't fit in");
```

不变
协变
逆变

利用数组，你会在运行时才发现所犯的错误；而利用列表，则可以在编译时就发现错误。

数组与泛型的第二区别：
数组是具体化（reified）的。因此数组会在运行时知道和强化它们的元素类型。
泛型则是通过擦除（erasure）来实现的。这意味着，泛型只在编译时强化它们的类型信息，并在运行时丢弃（或者擦除）它们的元素类型信息。擦除就是使泛型可以与没有使用泛型的代码随意进行互用，以保在 Java5 中平滑过渡到泛型。


像E、List<E>和List<String>这样的类型应称作不可具体化的（nonreifiable）类型。直观的说，不可具化的（non-reifiable）类型的指其运行时表示法包含的信息比它的编译时表示法包含的信息更少的类型。唯一可具体化的（reifiable）参数化类型是无限制的通配符类型，如List<?>和Map<?,?>虽然不常用，但是创建无限制通配类型的数组是合法的。