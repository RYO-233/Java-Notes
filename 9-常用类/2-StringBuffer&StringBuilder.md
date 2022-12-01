[toc]

# StringBuffer

## 基本介绍

> ​	java.lang.StringBUffer: 代表可变的字符序列，可以对字符串内容进行增删。
>
> ​	StringBuffer 是一个容器。其很多方法与 String 相同，但 StringBuffer 是可变长度的。
>
> ​	StringBuffer 是 final 类，不能被继承。
>
> ​	StringBuffer 实现了 Serializable, 即 StringBuffer 的对象可以序列化，可以保存到文件或网络传输。
>
> ​	在父类 AbstractStringBuilder 有属性 char[] value,不是 final。该 value 数组存放字符串内容(存放在堆中)。
>
> ​	因为 StringBuffer 字符内容是存在 char[] value, 所有的变化(增加/删除)不用每次都更换地址(即不是每次都创建新对象)， 所以效率高于 String。

## String vs StringBuffer

- String 保存的是字符串常量，里面的值不能更改，每次 String 类的更新实际上是更改地址，效率较低。
- StringBuffer 保存的是字符串变量，里面的值可以更改。每次 StringBuffer 的更新实际上是更新内容，不用每次更新地址，效率较高。

## String 与 StringBuffer 的相互转换

### 构造器

| 构造器                     | 说明                                                         |
| -------------------------- | ------------------------------------------------------------ |
| StringBuffer()             | 构造一个其中不带字符的字符串缓冲区。其初始容量为 16 个字符。 |
| StringBuffer(int capacity) | 构造一个不带字符，具有指定初始容量的字符串缓冲区。           |
| StringBuffer(String str)   | 构造一个字符串缓冲区，并初始化其字符串内容。                 |

### 示例

```java
public class Main {
    public static void main(String[] args) {

        // 构造器的使用
        // 1、创建一个大小为 16 的 char[]。
        StringBuffer buffer = new StringBuffer();
        // 2、通过构造器指定 char[] 的大小
        StringBuffer buffer1 = new StringBuffer(32);
        // 3、通过一个 string 创建 stringbuffer
        StringBuffer buffer2 = new StringBuffer("Hello world");
        
        // string -> stringbuffer
        String str = "Hello World";
        // fun1: StringBuffer(String str)
        // 返回的 buffer3 才是 StringBuffer 对象，str 本身没有影响。
        StringBuffer buffer3 = new StringBuffer(str);
        // fun2: buffer.append(str)
        StringBuffer buffer4 = new StringBuffer();
        buffer4.append(str);
        
        // StringBuffer -> String
        // fun1: toString()
        StringBuffer buffer5 = new StringBuffer("Ryo");
        String s = buffer5.toString();
        // fun2: String(StringBuffer buffer)
        String s1 = new String(buffer5);
    }
}
```

# StringBuilder

> ​	java.lang.StringBuiler: 代表一个可变的字符序列。此类提供一个与StringBuffer 兼容的 API，但不保证同步(StringBuilder 不是线程安全)。
>
> ​	该类被设计用作 StringBuffer 的一个简易替换，用在字符串缓冲区被单个线程使用的时候。如果可能，建议优先采用该类因为在大多数实现中，它比StringBuffer 要快。
>
> ​	在 StringBuilder 上的主要操作是 append 和 insert 方法，可重载这些方法，以接受任意类型的数据。
>
> ​	StringBuilder 是一个容器。其很多方法与 String 相同，但 StringBuilder  是可变长度的。
>
> ​	StringBuilder 是 final 类，不能被继承。
>
> ​	StringBuilder 实现了 Serializable, 即 StringBuilder 的对象可以序列化，可以保存到文件或网络传输。
>
> ​	在父类 AbstractStringBuilder 有属性 char[] value,不是 final。该 value 数组存放字符串内容(存放在堆中)。
>
> ​	因为 StringBuilder 字符内容是存在 char[] value, 所有的变化(增加/删除)不用每次都更换地址(即不是每次都创建新对象)， 所以效率高于 String。

## String、StringBuffer、StringBuilder 的比较

1) StringBuilder 和 StringBuffer 非常类似，均代表可变的字符序列，而且方法也一样。
2) String: 不可变字符序列，效率低，但是复用率高。
3) StringBuffer: 可变字符序列、效率较高(增删)、线程安全。
4) StringBuilder: 可变字符序列、效率最高、线程不安全。
5) String 使用注意说明:
  String s = "a"; //创建了一个字符串
  s += "b"; //实际上原来的 "a" 字符串对象已经丢弃了，现在又产生了一个字符串 s + "b”(也就是"ab")。
  如果多次执行这些改变串内容的操作，会导致大量副本字符串对象存留在内存中，降低效率。如果这样的操作放到循环中，会极大影响程序的性能 => 结论: 如果我们对String 做大量修改，不要使用 String。

## String、StringBuffer、StringBuilder 的选择

1. 如果字符串存在大量的修改操作，一般使用 StringBuffer 或 StringBuilder。

2. 如果字符串存在大量的修改操作，并在单线程的情况，使用 StringBuilder。

3. 如果字符串存在大量的修改操作，并在多线程的情况，使用 StringBuffer。
4. 如果我们字符串很少修改，被多个对象引用，使用 String, 比如配置信息等。