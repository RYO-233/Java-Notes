[toc]

# String

## 基本介绍

> 1. String 对象用于保存字符串，即一组字符序列。
> 2. 字符串常量对象: 是用双引号括起来的字符序列。如: “Hello”, “123”。
> 3. 字符串的字符使用 unicode 字符编码，一个字符占两个字节。
> 4. String 类常用的构造器:
>     - String s1 = new String();
>     - String s2 = new String(String original);
>     - String s3 = new String(char[] c);
>     - String s4 = new String(char[] c, int startIndex, int count);
>     - String s5 = new String(byte[] buffer, int offset, int length);
> 5. String 类实现了接口 Serializable(String 可以串行化: 可以在网络传输)、接口 Comparable(String 对象可以比较大小)。
> 6. String 是 final 类，不能被其他的类继承。
> 7. String 有属性 private final char value[]; 用于存放字符串内容。
> 8. value 是一个 final 类型，不可以修改。即 value 不能指向新的地址，但是单个字符内容是可以变化。

## 创建方式

> 方式一:
> 	直接赋值。`String s = "jin";`
>
> 方式二:
> 	调用构造器。`String s = new String("jin");`

### 区别

方式一: 
	先从常量池查看是否有 “jin” 的数据空间。如果有，直接指向；如果没有，重新创建，然后指向。s 最终指向的是常量池的空间地址。

方式二: 
	先在堆中创建空间，里面维护了 value 属性。指向常量池的 “jin” 的空间。如果常量池中没有 “jin”，则重新创建；如果有，直接通过 value 指向。s 最终指向的是堆中的空间地址。 

## String 的特性

1. String 是一个 final 类，代表其不可变的字符序列。
2. 字符串是不可变的。一个字符串对象一旦被分配，其内容是不可变的。
3. 字符串对象的拼接调用的是 StringBuilder。

