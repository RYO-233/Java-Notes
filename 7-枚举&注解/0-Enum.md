[toc]

# Enum

## 概念

> __枚举(enumeration，简写 enum)__
> 	枚举是一组常量的集合。
> 	枚举属于一种特殊的类，里面只包含一组有限的特定的对象。

## 实现方式

> 1. 自定义类实现枚举。
> 2. 使用 enum 关键字实现枚举。

### 自定义类实现枚举

> 1) 构造器私有化。
>
> 2) 本类内部创建一组对象(春、夏、秋、冬)。
>
> 3) 对外暴露对象(通过为对象添加 `public final static` 修饰符)。
>
> 4) 可以提供 `get()` 方法，但是不要提供 `set()` 方法。

### 使用 enum 关键字实现枚举

1) 当我们使用 enum 关键字开发一个枚举类时，默认会继承 Enum 类, 而且是一个 final 类。

2) 传统的 `public static final Season SPRING = new Season("春天", "温暖");` 简化成 `SPRING("春天", "温暖")`。 这里必须知道，它调用的是哪个构造器。

3) 如果使用无参构造器创建枚举对象，则实参列表和小括号都可以省略。
    如: `SPRING, SUMMER, AUTUMN, WINTER;`

4) 当有多个枚举对象时，使用 “,” 间隔，最后有一个 “;” 结尾。

5) 枚举对象必须放在枚举类的行首。

## enum 常用方法

| 方法        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| toString()  | Enum 类已经重写过了，返回的是当前对象名,子类可以重写该方法，用于返回对象的属性信息。 |
| name()      | 返回当前对象名（常量名），子类中不能重写。                   |
| ordinal()   | 返回当前对象的位置号，默认从 0 开始。                        |
| values()    | 返回当前枚举类中所有的常量。                                 |
| valueOf()   | 将字符串转换成枚举对象，要求字符串必须为已有的常量名，否则报异常！ |
| compareTo() | 比较两个枚举常量，比较的就是编号！                           |

## 示例

### 自定义类实现枚举

```java
class Season {	//类
	private String name;
	private String desc;	//描述
	//定义了四个对象, 固定 
    public static final Season SPRING = new Season("春天", "温暖");
	public static final Season WINTER = new Season("冬天", "寒冷");
	public static final Season AUTUMN = new Season("秋天", "凉爽");
	public static final Season SUMMER = new Season("夏天", "炎热");
	
    // 1. 将构造器私有化,目的防止 直接 new
	// 2. 去掉 setXxx 方法, 防止属性被修改
    // 3. 在 Season 内部，直接创建固定的对象
	// 4. 优化，可以加入 final 修饰符
	private Season(String name, String desc) {
		this.name = name;
		this.desc = desc;
	}
	public String getName() {
		return name;
	}
	public String getDesc() {
		return desc;
	}
	@Override
	public String toString() {
		return "Season{" + "name='" + name + '\'' + ", desc='" + desc + '\'' + '}';
	}
}
```

### 使用 enum 关键字实现枚举

```java
class Season {	//类
	// 如果使用了 enum 来实现枚举类
	// 1. 使用关键字 enum 替代 class
	// 2. public static final Season SPRING = new Season("春天", "温暖") 直接使用 SPRING("春天", "温暖"): 解读 常量名(实参列表)
	// 3. 如果有多个常量(对象)，使用 "," 号间隔即可
	// 4. 如果使用 enum 来实现枚举，要求将定义常量对象，写在前面
	// 5. 如果我们使用的是无参构造器，创建常量对象，则可以省略 ()
	SPRING("春天", "温暖"), 
    WINTER("冬天", "寒冷"), 
    AUTUMN("秋天", "凉爽"), 
    SUMMER("夏天", "炎热");
	
    private String name;
	private String desc;	//描述
    
    //1. 将构造器私有化,目的防止 直接 new
	//2. 去掉 setXxx 方法, 防止属性被修改
    //3. 在 Season 内部，直接创建固定的对象
	//4. 优化，可以加入 final 修饰符
    private Season() {//无参构造器
	}
    
	private Season(String name, String desc) {
		this.name = name;
		this.desc = desc;
	}
	public String getName() {
		return name;
	}
	public String getDesc() {
		return desc;
	}
	@Override
	public String toString() {
		return "Season{" + "name='" + name + '\'' + ", desc='" + desc + '\'' + '}';
	}
}
```

