<!-- TOC -->

- [概览](#%E6%A6%82%E8%A7%88)
- [函数式编程的基石](#%E5%87%BD%E6%95%B0%E5%BC%8F%E7%BC%96%E7%A8%8B%E7%9A%84%E5%9F%BA%E7%9F%B3)
- [行为参数化](#%E8%A1%8C%E4%B8%BA%E5%8F%82%E6%95%B0%E5%8C%96)
- [流式编程](#%E6%B5%81%E5%BC%8F%E7%BC%96%E7%A8%8B)
- [::语法](#%E8%AF%AD%E6%B3%95)
- [Lambda 匿名函数](#lambda-%E5%8C%BF%E5%90%8D%E5%87%BD%E6%95%B0)

<!-- /TOC -->
# 概览
java8提供了一个新的API（stream），它支持许多处理数据的并行操作，其思路和在数据库查询语言中的思路类似：**用更高级的方式表达想要的东西，而由Stream库来选择最佳低级执行机制。**这样就避免了使用Synchronized编写代码，这一代码不仅容易出错，而且在多核CPU上执行所需的成本也比你想象的更高。

# 函数式编程的基石
+ 没有共享的可变数据
+ 将方法和函数即代码传递给其他方法的能力

# 行为参数化
如果想要写两个只有几行代码不同的方法，那现在你只需要把不同的那部分代码作为参数传递进去就可以了。

将函数作为参数
```java
package lambdasinaction.chap1;

import java.util.*;
import java.util.function.Predicate;

public class FilteringApples{

    public static void main(String ... args){

        List<Apple> inventory = Arrays.asList(new Apple(80,"green"),
                                              new Apple(155, "green"),
                                              new Apple(120, "red"));	

        // [Apple{color='green', weight=80}, Apple{color='green', weight=155}]
        List<Apple> greenApples = filterApples(inventory, FilteringApples::isGreenApple);
        System.out.println(greenApples);
        
        // [Apple{color='green', weight=155}]
        List<Apple> heavyApples = filterApples(inventory, FilteringApples::isHeavyApple);
        System.out.println(heavyApples);
        
        // [Apple{color='green', weight=80}, Apple{color='green', weight=155}]
        List<Apple> greenApples2 = filterApples(inventory, (Apple a) -> "green".equals(a.getColor()));
        System.out.println(greenApples2);
        
        // [Apple{color='green', weight=155}]
        List<Apple> heavyApples2 = filterApples(inventory, (Apple a) -> a.getWeight() > 150);
        System.out.println(heavyApples2);
        
        // []
        List<Apple> weirdApples = filterApples(inventory, (Apple a) -> a.getWeight() < 80 || 
                                                                       "brown".equals(a.getColor()));
        System.out.println(weirdApples);
    }

    public static List<Apple> filterGreenApples(List<Apple> inventory){
        List<Apple> result = new ArrayList<>();
        for (Apple apple: inventory){
            if ("green".equals(apple.getColor())) {
                result.add(apple);
            }
        }
        return result;
    }

    public static List<Apple> filterHeavyApples(List<Apple> inventory){
        List<Apple> result = new ArrayList<>();
        for (Apple apple: inventory){
            if (apple.getWeight() > 150) {
                result.add(apple);
            }
        }
        return result;
    }

    public static boolean isGreenApple(Apple apple) {
        return "green".equals(apple.getColor()); 
    }

    public static boolean isHeavyApple(Apple apple) {
        return apple.getWeight() > 150;
    }

    public static List<Apple> filterApples(List<Apple> inventory, Predicate<Apple> p){
        List<Apple> result = new ArrayList<>();
        for(Apple apple : inventory){
            if(p.test(apple)){
                result.add(apple);
            }
        }
        return result;
    }       

    public static class Apple {
        private int weight = 0;
        private String color = "";

        public Apple(int weight, String color){
            this.weight = weight;
            this.color = color;
        }

        public Integer getWeight() {
            return weight;
        }

        public void setWeight(Integer weight) {
            this.weight = weight;
        }

        public String getColor() {
            return color;
        }

        public void setColor(String color) {
            this.color = color;
        }

        public String toString() {
            return "Apple{" +
                   "color='" + color + '\'' +
                   ", weight=" + weight +
                   '}';
        }
    }

}
```


# 流式编程
Unix或Linux中的标准输入(System.in)，标准输出(System.out)
cat file1 file2 | tar "[A-Z]" "[a-z]" | sort | tail -3
前面命令的结构，同时是后续命令的参数（流水线）

# ::语法

# Lambda 匿名函数