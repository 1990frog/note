[TOC]

Groovy 编程语言的语法源自 Java 语法，但使用 Groovy 的特定构造对其进行了增强，并允许进行某些简化。

#  注释（Comments）
单行注释
```groovy
// a standalone single line comment
println "hello" // a comment till the end of the line
```
多行注释
```groovy
/* a standalone multiline comment
   spanning two lines */
println "hello" /* a multiline comment starting
                   at the end of a statement */
println 1 /* one */ + 2 /* two */
```
文档注释
```groovy
/**
 * A Class description
 */
class Person {
    /** the name of the person */
    String name

    /**
     * Creates a greeting method for a certain person.
     *
     * @param otherPerson the person to greet
     * @return a greeting message
     */
    String greet(String otherPerson) {
       "Hello ${otherPerson}"
    }
}
```

# 关键字（Keywords）

一个技巧允许通过将名称括在引号中来定义与关键字具有相同名称的方法
```groovy
// reserved keywords can be used for method names if quoted
def "abstract"() { true }
// when calling such methods, the name must be qualified using "this."
this.abstract()

// contextual keywords can be used for field and variable names
def as = true
assert as

// contextual keywords can be used for method names
def in() { true }
// when calling such methods, the name only needs to be qualified using "this." in scenarios which would be ambiguous
this.in()
```

# 变量名（Identifiers）
+  'a' to 'z' (lowercase ascii letter)
+  'A' to 'Z' (uppercase ascii letter)
+  '\u00C0' to '\u00D6'
+  '\u00D8' to '\u00F6'
+  '\u00F8' to '\u00FF'
+  '\u0100' to '\uFFFE'

```groovy
/*有效变量名*/
def name
def item3
def with_underscore
def $dollarStart

/*无效变量名*/
def 3tier
def a+b
def a#b

/*使用dot关联，关键字也可以使用*/
foo.as
foo.assert
foo.break
foo.case
foo.catch
```

# 冒号标识符（Quoted identifiers）
`Map` 使用引号区分 `key` `value`
```groovy
def map = [:]

map."an identifier with a space and double quotes" = "ALLOWED"
map.'with-dash-signs-and-single-quotes' = "ALLOWED"

assert map."an identifier with a space and double quotes" == "ALLOWED"
assert map.'with-dash-signs-and-single-quotes' == "ALLOWED"

/* string 拓展*/
map.'single quote'
map."double quote"
map.'''triple single quote'''
map."""triple double quote"""
map./slashy string/
map.$/dollar slashy string/$


/*使用GString*/
def firstname = "Homer"
map."Simpson-${firstname}" = "Homer Simpson"
assert map.'Simpson-Homer' == "Homer Simpson"
```

# 字符串（String）
```groovy
/*单引号字符串*/
'a single-quoted string'
/**
 * 单引号特殊符号
 * \b backspace
 * \f formfeed
 * \n newline
 * \r carriage return
 * \t tabulation
 * \\ backslash
 * \' single quote
 * \"" double quote
 */
def name = 'Guillaume' // a plain string
def greeting = "Hello ${name2}"
assert greeting.toString() == 'Hello Guillaume'

/*双引号字符串*/
"a double-quoted string"

/*三引号字符串*/
// 如果您的代码是缩进的，例如在类方法的主体中，您的字符串将包含缩进的空格。 Groovy Development Kit 包含使用 String#stripIndent() 方法和 String#stripMargin() 方法去除缩进的方法，该方法采用分隔符来标识要从字符串开头删除的文本。
'''a triple-single-quoted string'''

/*正斜线字符串*/
// 除了通常的引用字符串之外，Groovy 还提供斜线字符串，它使用 / 作为开始和结束分隔符。 斜杠字符串对于定义正则表达式和模式特别有用，因为不需要转义反斜杠。
def foo = /bar/
println("${foo}")
println("${->foo}")
println(/${foo}/)
println(/$foo/)
// An empty slashy string cannot be represented with a double forward slash, as it’s understood by the Groovy parser as a line comment. That’s why the following assert would actually not compile as it would look like a non-terminated statement:
assert '' == //
```

字符串拼接
```
assert 'ab' == 'a' + 'b'
```

## 插值GString（String inperpolation）
```groovy
/**
 * 单引号无法使用 GString 插入值
 * GString 占位符有两种：${},$
 */
def name = "lilei"
def test1 = '${name} $name'
def test2 = "${name} $name"
def test3 = '''${name} $name''' 
def test4 = """${name} $name"""
def test5 = """\${name} \$name"""

assert test1 == '${name} $name'
assert test2 == 'lilei lilei'
assert test3 == '${name} $name'
assert test4 == 'lilei lilei'
assert test5 == '${name} $name'
```

```groovy
// 字符串占位符
def name = 'Guillaume' // a plain string
def greeting = "Hello ${name}"
assert greeting.toString() == 'Hello Guillaume'

// 数学表达式
def sum = "The sum of 2 and 3 equals ${2 + 3}"
assert sum.toString() == 'The sum of 2 and 3 equals 5'

// 直接使用 $
def person = [name: 'Guillaume', age: 36]
assert "$person.name is $person.age years old" == 'Guillaume is 36 years old'
```

插入闭包表达式

String summary table

name    syntax  interpolated    multiline
single-quoted '...' n   n
triple-single-quoted '''...'''  -   -
double-quoted   "..."   y   y
triple-double-quoted    """..."""   y   y
slashy  /.../   y   y
dollar slashy   $/.../$ y   y

# 基础数据类型
## Characters
```
char c1 = 'A' 
assert c1 instanceof Character

def c2 = 'B' as char 
assert c2 instanceof Character

def c3 = (char)'C' 
assert c3 instanceof Character
```

# Numbers
## 整型（Integral literals）
+ byte
+ char
+ short
+ int
+ long
+ java.math.BigInteger

```
// primitive types
byte  b = 1
char  c = 2
short s = 3
int   i = 4
long  l = 5

// infinite precision
BigInteger bi =  6

def a = 1
assert a instanceof Integer

// Integer.MAX_VALUE
def b = 2147483647
assert b instanceof Integer

// Integer.MAX_VALUE + 1
def c = 2147483648
assert c instanceof Long

// Long.MAX_VALUE
def d = 9223372036854775807
assert d instanceof Long

// Long.MAX_VALUE + 1
def e = 9223372036854775808
assert e instanceof BigInteger

def na = -1
assert na instanceof Integer

// Integer.MIN_VALUE
def nb = -2147483648
assert nb instanceof Integer

// Integer.MIN_VALUE - 1
def nc = -2147483649
assert nc instanceof Long

// Long.MIN_VALUE
def nd = -9223372036854775808
assert nd instanceof Long

// Long.MIN_VALUE - 1
def ne = -9223372036854775809
assert ne instanceof BigInteger
```

## 十进制（Decimal literals）
+ float
+ double
+ java.math.BigDecimal

```
// primitive types
float  f = 1.234
double d = 2.345

// infinite precision
BigDecimal bd =  3.456
```
指数
```
assert 1e3  ==  1_000.0
assert 2E4  == 20_000.0
assert 3e+1 ==     30.0
assert 4E-2 ==      0.04
assert 5e-1 ==      0.5
```

## 下划线
```
long creditCardNumber = 1234_5678_9012_3456L
long socialSecurityNumbers = 999_99_9999L
double monetaryAmount = 12_345_132.12
long hexBytes = 0xFF_EC_DE_5E
long hexWords = 0xFFEC_DE5E
long maxLong = 0x7fff_ffff_ffff_ffffL
long alsoMaxLong = 9_223_372_036_854_775_807L
long bytes = 0b11010010_01101001_10010100_10010010
```

## 数值类型符号后缀

Type	Suffix
BigInteger  G or g
Long    L or l
Integer I or i
BigDecimal  G or g
Double  D or d
Float   F or f

```
assert 42I == Integer.valueOf('42')
assert 42i == Integer.valueOf('42') // lowercase i more readable
assert 123L == Long.valueOf("123") // uppercase L more readable
assert 2147483648 == Long.valueOf('2147483648') // Long type used, value too large for an Integer
assert 456G == new BigInteger('456')
assert 456g == new BigInteger('456')
assert 123.45 == new BigDecimal('123.45') // default BigDecimal type used
assert .321 == new BigDecimal('.321')
assert 1.200065D == Double.valueOf('1.200065')
assert 1.234F == Float.valueOf('1.234')
assert 1.23E23D == Double.valueOf('1.23E23')
assert 0b1111L.class == Long // binary
assert 0xFFi.class == Integer // hexadecimal
assert 034G.class == BigInteger // octal
```