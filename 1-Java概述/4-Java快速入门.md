[toc]

# Java快速入门

## Java 入门案例

> 编写一个 HelloWorld.java 程序，输出 HelloWorld。

```java
// HelloWorld 是一个类，是一个 public 公有的类
public class HelloWorld {
    // 这是程序的入口
	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}
```

## Java 运行机制

<img src="..\img\java2.png" alt="java2" style="zoom: 67%;" />

## Java 开发中的细节

1. Java源文件以 .java 为扩展名。源文件的基本组成部分是类(class)，如本类中的 Hello 类。
2. Java应用程序的执行入口是 main() 方法。
    它有固定的书写格式:
        public static void main(Stringl] args){..}
3. Java语言**严格区分大小写**。
4. Java方法由一条条语句构成，每个语句以 “;” 结束。
5. 大括号都是成对出现的，缺一不可。(习惯，先写“{}”再写代码)
6. 一个源文件中最多只能有一个public类。其它类的个数不限。
    也可以将main方法写在非 public 类中，然后指定运行非 public 类，这样入口方法就是非 public 的 main 方法。
7. 如果源文件包含一个public类，则文件名必须按该类名命名! 

## Java 转义字符

| 转义字符 | 说明                                               |
| -------- | -------------------------------------------------- |
| \t       | 制表位，实现对齐的功能。                           |
| \n       | 换行符                                             |
| \\\      | 一个 \\                                            |
| \\"      | 一个 "                                             |
| \\'      | 一个 '                                             |
| \r       | 回车。<br />System.out.println("I’m\r NISHIMIYA"); |

