[toc]

# main 方法

## main 方法的定义

```java
public static void main(String[] args) {
	blocks;
}
```

## 说明：

1. `main()` 方法是虚拟机调用的。
2. JVM 需要调用类的 `main()` 方法，所以 `main()` 方法的访问权限必须是 `public`。
3. JVM 在执行 `main()` 方法时，不必创建对象，所以 `main()` 方法必须是 `static`。
4. `main()` 方法接收 String 类型的数组参数，该数组中保存执行 java 命令时传递给所运行的类的参数。
5. 在 `main()` 方法中，可以直接调用 `main()` 方法所在类的静态方法 / 静态属性。
6. `main()` 方法不能直接访问该类中的非静态成员，必须创建该类的实例对象后，通过实例对象才能访问非静态成员。