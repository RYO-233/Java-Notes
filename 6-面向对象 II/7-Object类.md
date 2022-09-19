[toc]

# Object 类

## equals()

### == 与 equals() 的比较：

#### == 是一个比较运算符

- ==: 既可以判断基本类型，也可以判断引用类型。
- ==: 如果判断的是基本类型，判断的是__<span style="color: red">值</span>__是否相等(int i = 2;double d = 3.0;)。
- ==: 如果判断的是引用类型，判断的是__<span style="color: red">地址</span>__是否相等(即，判断是不是同一个对象)。

#### equals()

- equals(): 是 Object 类中的方法，只能判断引用类型。
- equals() 判断的是地址是否相等。而子类中通常会重写该方法，用于判断内容是否相等(如: Integer 类与 String 类中的 equals() 方法)。

### 如何重写 equals() 方法

```java
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person person = (Person) o;
        return age == person.age &&
                gender == person.gender &&
                name.equals(person.name);
    }
```

```java
@Override
public boolean equals(Object o) {
    // 判断如果比较的两个对象是同一个对象，则直接返回 true。
	if(this == o) {
		return true;
	}
    // 类型判断
    if(o instanceof Persion) {
        // 进行向下转型, 因为需要得到 o 的 各个属性
        Person p = (Person) o;
        return this.name.equals(p.name) && this.age == p.age && this.gender == p.gender;
    }
    return false;
}
```

## hashCode()

1. 提高具有哈希结构的容器的效率。
2. 两个引用，如果指向的是同一个对象，则哈希值肯定是一样的。
3. 两个引用，如果指向的是不同的对象，则哈希值是不一样的。
4. 哈希值主要是根据地址号来的。不能完全将哈希值等价于地址。

### 示例

```java
    public static void main(String[] args) {
        Person p1 = new Person("Jack",18,'男');
        Person p2 = new Person("Zoffy",20,'男');
        System.out.println("p1.hashCode() = " + p1.hashCode());
        System.out.println("p2.hashCode() = " + p2.hashCode());
    }
p1.hashCode() = -2083716093
p2.hashCode() = 1546202950
```

## toString()

> ​	默认返回：全类名+@+哈希值的十六进制。
>
> ​	重写 `toString()` 方法，打印对象或拼接对象时，会自动调用该对象的 `toString()` 形式。
>
> ​	当直接输出一个对象时，`toString()` 会被默认调用。

## finalize()

1) 当对象被回收时，系统自动调用该对象的 `finalize()` 方法。子类可以重写该方法，做一些释放资源的操作。 

2) 什么时候被回收：当某个对象没有任何引用时，则 JVM 就认为这个对象是一个垃圾对象，就会使用垃圾回收机制来销毁该对象，在销毁该对象前，会先调用 `finalize()` 方法。 

3) 垃圾回收机制的调用，是由系统来决定(即有自己的 `GC` 算法), 也可以通过 `System.gc()` 主动触发垃圾回收机制。