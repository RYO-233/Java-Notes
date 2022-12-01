[toc]

# List

## 介绍

> ​	List 接口是 Collection 接口的子接口。
>
> 1. List 集合中的元素有序(添加的顺序和取出的顺序一致)，且可重复。
> 2. List 集合中的每个元素都有其对应的顺序索引。即支持索引。
> 3. List 容器中的元素都对应一个整数型的序号，记载着其在容器中的位置，可以根据需要来存取容器中的元素。
> 4. List 接口的常用实现类有: ArrayList、LinkedList、Vector。

## 常用方法

| 方法                                       | 说明                                      |
| ------------------------------------------ | ----------------------------------------- |
| void add(int index, Object obj)            | 在 index 处插入元素 obj                   |
| boolean addAll(int index, Collection objs) | 从 index 处开始将 objs 中所有元素添加进来 |
| Object get(int index)                      | 获取 index 处的元素                       |
| int indexOf(Object obj)                    | 返回 obj 在集合中，首次出现的位置         |
| int lastIndexOf(Object obj)                | 返回 obj 在集合中，最后一次出现的位置     |
| Object remove(int index)                   | 移除 index 处的元素，并返回此元素         |
| Object set(int index, Object obj)          | 指定 index 处的元素为 obj。相当于替换     |
| List subList(int start, int end)           | 返回从 [start, end) 的子集合              |

## 遍历

### Iterator(迭代器)

```java
Iterator it = list.iterator();
while(it.hasNext()) {
	Object obj = it.next();
}
```

### 增强 for 循环

```java
for(Object obj: list) {
}
```

### 普通 for 循环

```java
for(int i = 0; i < list.size(); i++) {
    Object obj = list.get(i);
}
```

# ArrayList

## 细节

> 1. ArrayList 允许所有类型的元素，包括 null，ArrayList 允许添加多个 null。
> 2. ArrayList 是由__<u><span style="color: red">数组</span></u>__来实现数据存储的。
> 3. ArrayList 基本等同于 Vector，除了 ArrayList 是线程不安全的(执行效率高)。在多线程的情况下，不建议使用 ArrayList。

## 底层

> 1. ArrayList 中维护了一个 Object 类型的数组 elementData。
>     `transient Object[] elementData`。
>     transient 表示该属性不会被序列化。
> 2. 当创建 ArrayList 对象时，如果使用的是无参构造器，则初始化 elementData 容量为 0。
>     第一次添加，则扩容为 10。之后每次扩容，都为上次的 1.5 倍。
> 3. 如果使用的是指定大小的构造器，则初始化 elementData 容量为指定大小。之后每次扩容，都为上次的 1.5 倍。

# Vector

## 细节

> 1. Vector 允许所有类型的元素，包括 null，Vector 允许添加多个 null。
> 2. Vector 是由__<u><span style="color: red">数组</span></u>__来实现数据存储的。
> 3. Vector 是线程同步的，即线程安全。 Vector 类的操作方法带有 synchronized。在线程同步安全时，考虑使用 Vector。

## Vector 与 ArrayList

| List      | 底层结构 | 版本   | 线程安全           | 扩容倍数                                                     |
| --------- | -------- | ------ | ------------------ | ------------------------------------------------------------ |
| ArrayList | 可变数组 | JDK1.2 | 线程不安全，效率高 | 如果有参构造，1.5倍。<br />如果无参构造，第一次 10，第二次开始按 1.5 倍扩容 |
| Vector    | 可变数组 | JDK1.0 | 线程安全，效率不高 | 如果有参构造，默认为 10，满后按 2 倍扩容。<br />如果指定大小，则每次按 2 倍扩容。 |

# LinkedList

## 细节

> 1. LinkedList 底层实现了双向链表和双端队列的特点。
> 2. LinkedList 可以添加任意元素(可以重复)，包括 null。
> 3. LinkedList 线程不安全，没有实现同步机制。

## 底层

> 1. LinkedList 底层维护了一个双向链表。
> 2. LinkedList 中维护了两个属性 first 和 last。其分别指向 首节点 和 尾节点。
> 3. 每个节点对象(Node)里面又维护了 prev、next 和 item 三个属性。
>     其中 prev 指向前一个节点，next 指向下一个节点。最终实现双向链表。
> 4. LinkedList 元素的添加和删除，不是通过数组来完成的。相对数组来说效率更高。

## ArrayList 与 LinkedList

| List       | 底层结构 | 增删效率                   | 改查效率 |
| ---------- | -------- | -------------------------- | -------- |
| ArrayList  | 可变数组 | 效率较低，通过数组扩容方式 | 较高     |
| LinkedList | 双向链表 | 效率较高，通过链表添加删除 | 较低     |

1. 如果改查的操作多，选择 ArrayList。
2. 如果增删的操作多，选择 LinkedList。
3. 一般来说，在程序中，大部分操作都是查询。因此 ArrayList 选择的较多。
4. 在一个项目中，要根据业务需求来选择使用哪个。

