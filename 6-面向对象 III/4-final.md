[toc]

# final

## 介绍

> `final`：最后的，最终的。
>
> `final` 可以修饰 *<u>类、属性、方法和局部变量。</u>*
>
> 当有以下需求时，会使用到 `final`: 
>
> 1. 当<u>不希望类被继承时，</u>可以使用 `final` 修饰。
> 2. 当<u>不希望父类中的某个方法被子类覆盖 / 重写，</u>可以使用 `final` 修饰。
> 3. 当<u>不希望类的某个属性的值被修改，</u>可以使用 `final` 修饰。
> 4. 当<u>不希望某个局部变量被修改时，</u>可以使用 `final` 修饰。

## 细节

1. `final` 修饰的属性又称为*__常量__*。一般用全大写(*MSG_ERROR*)来命名。
2. `final` 修饰的属性在定义时，必须赋予初值，并且不能再修改。
    赋值可以在如下位置之一：
    1. 定义时: `public final double TAX_RATE = 0.01;`
    2. 在构造器中。
    3. 在代码块中。
3. 如果 `final` 修饰的属性是静态的，则初始化的位置只能是: 
    1. 定义时。
    2. 在静态代码块中，而不能在构造器中赋值。
4. `final` 类不能被继承，但是可以实例化对象。
5. 如果类不是 `final` 类，但是含有 `final` 方法。则该方法不能被重写，但是类可以被继承。
6. 如果类已经是 `final` 类，无需将方法修饰为 `final` 方法。
7. `final` 不能修饰构造器。
8. `final` 往往搭配 `static` 使用，效率更高，不会导致类的加载。
    底层编译器做了优化处理。
9. 包装类(`Integer、Double、Float、Boolean、String`等都是 `final`类)
