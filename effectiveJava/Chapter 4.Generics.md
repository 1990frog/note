
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