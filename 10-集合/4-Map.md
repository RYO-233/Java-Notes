[toc]

# Map

## 细节

1. Map 与 Collection 并列存在。用于保存具有映射关系的数据: Key - Value。
2. Map 中的 key 和 value 可以是任何引用类型的数据。会封装到 HashMap$Node 对象中。
3. Map 中的 key 不允许重复(与 HashSet 一样，替换效果)。
4. Map 中的 value 可以重复。
5. Map 中的 key 可以为 null，value 也可以为 null。
    其中，key 只能有一个 null，而 value 可以多个为 null。
6. 常用 String 类来作为 Map 的 key。
7. key 和 value 之间存在单向一对一关系。
    即通过指定的 key，总能找到对应的 value。
8. Map 存放数据的一对 key - value 是放在一个 HashMap$Node 中，因为 Node 实现了 Entry 接口。

 ## 常用方法

| 方法        | 说明                 |
| ----------- | -------------------- |
| put         | 添加                 |
| remove      | 根据键，删除映射关系 |
| get         | 根据键，获取值       |
| size        | 获取元素个数         |
| isEmpty     | 判断个数是否为 0     |
| clear       | 清除                 |
| containsKey | 查找键，是否存在     |

## 遍历

### (1). 先取出所有的 key，通过 key 取出对应的 value

#### 增强 for 循环

```java
Set<String> keySet = map.keySet();
for (String s : keySet) {
	System.out.println(s + "-" + map.get(s));
}
```

 #### Iterator(迭代器)

```java
Set<String> keySet = map.keySet();
Iterator<String> iterator = keySet.iterator();
while (iterator.hasNext()) {
	String key = iterator.next();
	System.out.println(key + "-" + map.get(key));
}
```

### (2). 把所有的 value 取出

#### 增强 for 循环

```java
Collection<String> values = map.values();
for (String value : values) {
    System.out.println(value);
}
```

#### Iterator(迭代器)

```java
Collection<String> values = map.values();
while (iterator1.hasNext()) {
	String next = iterator1.next();
	System.out.println(next);
}
```

### (3).通过 entrySet 取出 键值对

#### 增强 for 循环

```java
Set<Map.Entry<String, String>> entries = map.entrySet();
for (Map.Entry<String, String> entry : entries) {
	String key = entry.getKey();
	String value = entry.getValue();
	System.out.println(key + "-" + value);
}
```

#### Iterator(迭代器)

```java
Set<Map.Entry<String, String>> entries = map.entrySet();
Iterator<Map.Entry<String, String>> iterator2 = entries.iterator();
while (iterator2.hasNext()) {
	Map.Entry<String, String> next = iterator2.next();
	String s = next.setValue("3");
}
```

# HashMap

## 细节

1. Map 接口的常用实现类: HashMap、Hashtable和 Properties。
2. HashMap 是 Map 接口使用频率最高的实现类。
3. HashMap 是以 key-val 的方式来存储数据(HashMap$Node类型)。
4. key 不能重复，但是 val 可以重复，允许使用 null 键和 null 值。
5. 如果添加相同的 key，则会覆盖原来的 key-val，等同于修改。
    (key 不会替换，val 会替换)
6. 与 HashSet 一样，HashMap 不保证映射的顺序，因为底层是以 hash 表的方式来存储的。(JDK8 的 hashMap 底层为：数组 + 链表 + 红黑树)
7. HashMap 没有实现同步，因此是线程不安全的。方法没有做同步互斥的操作,没有
     synchronized。

## 底层



# HashTable



# TreeMap



# Properties
