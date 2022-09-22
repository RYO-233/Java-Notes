[toc]

# super 关键字

## 概述

> ​	`super` 代表父类的引用，用于访问父类的属性、方法和构造器。

## 基本语法

1. 通过 `super.field` 可以访问父类的属性，但不能访问父类的 `private` 属性。
2. 通过 `super.func` 可以访问父类的方法，但不能访问父类的 `private` 属性。
3. 通过 `super(pram_list)` 可以访问父类的构造器，但只能放在构造器的第一句。

## 使用细节

1. 调用父类的构造器时分工明确。父类属性由父类初始化，子类属性由子类初始化。
2. 当子类中有和父类中的成员(属性和方法)重名时，为了访问父类的成员，必须通过 `super`。
    如果没有重名，使用 `super、this`、直接访问是一样的效果。
3. `super` 的访问不限于直接父类。如果爷爷类和本类中有同名的成员，也可以使用 `super` 去访问爷爷类的成员。如果有多个基类中都有同名的成员，使用 `super` 访问遵循就近原则: Son -> Father -> Grandpa，也需要遵循访问权限的规则。

## super 和 this 的比较

| 区别     | super                  | this                                                       |
| -------- | ---------------------- | ---------------------------------------------------------- |
| 访问属性 | 访问父类之上的属性。   | 访问本类中的属性。如果本类中没有该属性，则从父类开始查找。 |
| 调用方法 | 访问父类之上你的方法。 | 访问本类中的方法。如果本类中没有该方法，则从父类开始查找。 |

## 示例

```java
public class Grandpa {

    public int n1 = 999;
    public int age = 111;

    public void fun1() {
        System.out.println("Grandpa 类的 cal() 方法...");
    }

    public void eat() {
        System.out.println("Grandpa 类的 eat().....");
    }
}
```

```java
public class Father extends Grandpa {
    // 属性
    public int n1 = 100;
    protected int n2 = 200;
    int n3 = 300;
    private int n4 = 400;

    public Father() { //无参构造器
        System.out.println("Father()...");
    }

    public Father(String name) {
        System.out.println("Father(name)...");
    }

    public Father(String name, int age) {
        System.out.println("Father(name, age)...");
    }

    // 需要通过父类提供的公共的方法来访问
//    public int getN4() {
//        return n4;
//    }

    public void fun1() {
        System.out.println("fun1...");
    }

    protected void fun2() {
        System.out.println("fun2...");
    }

    void fun3() {
        System.out.println("fun3...");
    }

    private void fun4() {
        System.out.println("fun4...");
    }

    // 需要通过父类提供的公共的方法来访问
    public void getFun4() {
        fun4();
    }
}
```

```java
public class Son extends Father {
    public int n1 = 888; //编写测试方法

    public void test() {
        // super 的访问不限于直接父类，如果爷爷类和本类中有同名的成员，也可以使用 super 去访问爷爷类的成员；
        // 如果多个基类(上级类)中都有同名的成员，使用 super 访问遵循就近原则。
        // A -> B -> C
        System.out.println("super.n1=" + super.n1);
        super.fun1();
    }

    //访问父类的属性 , 但不能访问父类的 private 属性 [案例]super.属性名
    public void hi() {
        System.out.println(super.n1 + " " + super.n2 + " " + super.n3);
    }

    public void fun1() {
        System.out.println("B 类的 fun1() 方法...");
    }

    public void sum() {
        System.out.println("B 类的 sum()");
        //希望调用父类-A 的 fun1 方法
        // 这时，因为子类 B 没有 cal 方法，因此我可以使用下面三种方式
        // 找 fun1 方法时(fun1() 和 this.fun1())，顺序是:
        // (1)先找本类，如果有，则调用
        // (2)如果没有，则找父类(如果有，并可以调用，则调用)
        // (3)如果父类没有，则继续找父类的父类,整个规则，就是一样的,直到 Object 类
        // 提示：如果查找方法的过程中，找到了，但是不能访问， 则报错, cannot access
        // 如果查找方法的过程中，没有找到，则提示方法不存在
        fun1();
        this.fun1(); //等价 cal
        // 找 cal 方法(super.call()) 的顺序是直接查找父类，其他的规则一样
        super.fun1(); //演示访问属性的规则
    }
}
```

