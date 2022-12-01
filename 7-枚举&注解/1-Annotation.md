[toc]

# Annotation

## 概念

> __注解(Annotation):__
> 	也被称为元数据(Metadata)。用于修饰解释 包、类、方法、属性、构造器、局部变量等数据信息。
>
> ​	和注释一样，注解不影响程序逻辑，但注解可以被编译或运行，相当于嵌入在代码中的补充信息。
>
> ​	在 JavaSE 中，注解的使用目的比较简单。例如标记过时的功能，忽略警告等。
> ​	在 JavaEE 中注解占据了更重要的角色。
> ​	例如用来配置应用程序的任何*<u>切面</u>*，代替 java EE 旧版中所遗留的繁冗代码和 XML 配置等。

## 基本的注解

> 使用 Annotation 时要在其前面增加 “@” 符号, 并把该 Annotation 当成一个修饰符使用。用于修饰它支持的程序元素。
>
> __基本的 Annotation:__
>
> - @Override: 限定某个方法，是重写父类方法, 该注解只能用于方法。
>
> - @Deprecated: 用于表示某个程序元素(类, 方法等)已过时。
>
> - @SuppressWarnings: 抑制编译器警告。

### @Override

> 1. @Override 表示指定重写父类的方法（从编译层面验证)。
>     如果父类没有该方法，则会报错。
> 2. 如果不写 @Override 注解，而父类仍有 `public void fun()`，仍然构成重写。
> 3. @Override 只能修饰方法，不能修饰其它类、包、属性等。
> 4. 查看 @Override 注解源码为 @Target(ElementType.METHOD)。说明只能修饰方法。
> 5. @Target 是修饰注解的注解，称为元注解。记住这个概念。

### @Deprecated



### @SuppressWarnings



## 元注解



