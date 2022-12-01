[toc]

# 第一代

## Date

> ​	精确到毫秒，代表特定的瞬间。

## SimpleDateFormat

> ​	格式化和解析日期的具体类。
>
> ​	它允许进行格式化(日期 -> 文本)、解析(文本 -> 日期)和规范化。

## 示例

```java
public class Main {
    public static void main(String[] args) throws ParseException {

        Date d1 = new Date(); //获取当前系统时间
        System.out.println("当前日期=" + d1);
        Date d2 = new Date(9234567); //通过指定毫秒数得到时间
        System.out.println("d2=" + d2); //获取某个时间对应的毫秒数
        
        // 1. 创建 SimpleDateFormat 对象，可以指定相应的格式
        // 2. 这里的格式使用的字母是规定好，不能乱写
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy 年 MM 月 dd 日 hh:mm:ss E");
        String format = sdf.format(d1); // format:将日期转换成指定格式的字符串
        System.out.println("当前日期=" + format); //老韩解读

        // 1. 可以把一个格式化的 String 转成对应的 Date
        // 2. 得到 Date 仍然在输出时，还是按照国外的形式，如果希望指定格式输出，需要转换
        // 3. 在把 String -> Date，使用的 sdf 格式需要和你给的 String 的格式一样
        // 否则会抛出转换异常
        String s = "1996 年 01 月 01 日 10:20:30 星期一";
        Date parse = sdf.parse(s);
        System.out.println("parse=" + sdf.format(parse));
    }
}
```

# 第二代

## Calendar

> ​	Calendar 类是一个抽象类，它为特定瞬间与一组诸如 YEAR、MONTH、DAY_OF_MONTH、HOUR 等<u>日历字段</u>之间的转换提供了一些方法，并为操作日历字段提供了一些方法。

## 示例

```java
public class CalenderDemo {
    public static void main(String[] args) {
        // 1. Calendar 是一个抽象类， 并且构造器是 private
        // 2. 通过 getInstance() 获取实例
        // 3. Calendar 提供了大量的方法和字段，提供我们使用
        Calendar c = Calendar.getInstance();
        System.out.println("calendar = " + c);

        // 获取日历对象的某个日历字段
        System.out.println("Calendar.YEAR = " + Calendar.YEAR);
        System.out.println("年: " + c.get(Calendar.YEAR));
        // 月 默认从 0 开始
        System.out.println("月：" + (c.get(Calendar.MONTH) + 1));
        System.out.println("日：" + c.get(Calendar.DAY_OF_MONTH));
        System.out.println("小时：" + c.get(Calendar.HOUR));
        System.out.println("分钟：" + c.get(Calendar.MINUTE));
        System.out.println("秒：" + c.get(Calendar.SECOND));
        //Calender 没有专门的格式化方法，所以需要程序员自己来组合显示
        System.out.println(c.get(Calendar.YEAR) + "-"
                + (c.get(Calendar.MONTH) + 1) + "-"
                + c.get(Calendar.DAY_OF_MONTH) + " " +
                c.get(Calendar.HOUR_OF_DAY) + ":" +
                c.get(Calendar.MINUTE) + ":"
                + c.get(Calendar.SECOND) );
    }
}
```

# 第三代

> 前两代日期类的不足: 
>
> ​	JDK1.0 中包含了一个 java.util.Date 类。但是它的大多数方法已经在 JDK1.1 中的呢 Calendar 类之后被弃用了。
>
> 而 Calendar 类也存在以下问题: 
>
> 1. 可变性: 向日期和时间这样的类应该是不可变的。
> 2. 偏移性: Date 中的年份是从 1900 年开始的，而月份都是从 0 开始的。
> 3. 格式化: 格式化指对 Date 有用，Calendar 不行。
> 4. 线程不安全: 不能处理闰秒等(每隔 2 天，多出 1秒)。
>
> 于 JDK8 加入了 LocalDate(日期 / 年月日)、LocalTime(时间 / 时分秒)、LocalDateTime(时间 / 年月日时分秒)
>
> - LocalDate: 只包含日期，可以获取日期字段。
> - LocalTime: 只包含时间，可以获取时间字段。
> - LocalDateTime: 包含日期和时间，可以获取日期和时间字段。

## DateTimeFormatter

> ​	类似于 SimpleDateFormat。

```java
DateTimeFormat dtf = DateTimeFormatter.ofPattern(格式);
String str = dtf.format(日期对象);
```

## Instant

> ​	时间戳。

```java
//1.通过 静态方法 now() 获取表示当前时间戳的对象 
Instant now = Instant.now(); 
System.out.println(now); 

//2. 通过 from 可以把 Instant 转成 Date 
Date date = Date.from(now);

//3. 通过 date 的 toInstant() 可以把 date 转成 Instant 对象 
Instant instant = date.toInstant();
```

