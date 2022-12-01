[toc]

# Set

##  基本介绍

> 1. Set 集合是无序的(添加和取出的顺序不一致)，没有索引。
> 2. Set 集合中，不允许有重复的元素，所以最多包含一个 null。

## 常用方法

> ​	常用方法和 Collection 接口一样。

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

# HashSet

## 细节

> 1. HashSet 实现了 Set 接口。
> 2. HashSet 底层实际上是 HashMap。
> 3. HashSet 可以存放 null，但是只能有一个 null。
> 4. HashSet 不能保证元素是有序的。取决于 hash 之后确定的索引。
>     即不能保证存放元素的顺序和取出的顺序是一致的。
> 5. HashSet 不能有重复的元素 / 对象。

## 底层

> HashSet 底层是 HashMap，而 HashMap 底层是 数组 + 链表 + 红黑树。

1. 先获取元素的哈希值(hashCode())。
2. 对哈希值进行运算，得出一个索引值。即要存放在哈希表中的位置号。
3. 如果该位置上没有其他元素，则直接存放；
    如果该位置上有其他元素，则需要进行 equals() 判断；
    如果相等，则不再添加；如果不相等，则以链表的方式添加。
4. 在 Java8 中，如果一条链表的元素个数超过了 TREEIFY_THRESHOLD(默认是 8)，并且 table 的大小 >= MIN_TREEIFY_CAPACITY(默认是 64)，就会进行红黑树化。

```
final V putVal(int hash, K key, V value, boolean onlyIfAbsent, boolean evict) {
	// din
	Node<K,V>[] tab; Node<K,V> p; int n, i;
	if ((tab = table) == null || (n = tab.length) == 0)
		n = (tab = resize()).length;
	if ((p = tab[i = (n - 1) & hash]) == null)
		tab[i] = newNode(hash, key, value, null);
	else {
		Node<K,V> e; K k;
		if (p.hash == hash && ((k = p.key) == key || (key != null && key.equals(k))))
			e = p;
		else if (p instanceof TreeNode)
			e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
		else {
			for (int binCount = 0; ; ++binCount) {
				if ((e = p.next) == null) {
					p.next = newNode(hash, key, value, null);
					if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
						treeifyBin(tab, hash);
					break;
				}
				if (e.hash == hash &&
					((k = e.key) == key || (key != null && key.equals(k))))
					break;
				p = e;
			}
		}
		if (e != null) { // existing mapping for key
			V oldValue = e.value;
			if (!onlyIfAbsent || oldValue == null)
				e.value = value;
			afterNodeAccess(e);
			return oldValue;
		}
	}
	++modCount;
	if (++size > threshold)
		resize();
	afterNodeInsertion(evict);
	return null;
}
```

> HashSet 的扩容和转成红黑树机制。

1. HashSet 底层是 HashMap，第一次添加时，table 数组扩容到 16，临界值(threshold) = 16 * 加载因子(loadFactor: 0.75) = 12。
2. 如果 table 数组使用到了临界值 12，就会扩容到 16 * 2 = 32。新的临界值就是 32 * 0.75 = 24。以此类推。
3. 在 Java8 中，如果一条链表的元素个数到达 TREEIFY_THRESHOLD(默认为 8)，并且 table 的大小 >= MIN_TREEIFY_CAPACITY(默认为 64)，就会进行树化(红黑树)，否则仍然采用数组扩容机制。

# LinkedHashSet

## 细节

> 1. LinkedHashSet 是 HashSet 的子类。
> 2. LinkedHashSet 底层是一个 LinkedHashMap，底层维护了一个数组 + 双向链表。
> 3. LinkedHashSet 根据元素的 hashCode 值来决定元素的存储位置。同时使用链表维护元素的次序，这使得元素看起来是以插入顺序保存的。
> 4. LinkedHashSet 不允许添加重复的元素。

## 底层

1. 在 LinkedHashSet 中维护了一个 hash 表和 双向链表(LinkedHashSet 中有 head 和 tail)。
2. 每一个节点都有 before 和 after 属性，这样可以形成一个双向链表。
3. 在添加一个元素时，先求 hash 值，再求索引。确定该元素在 table 的位置。然后将添加的元素加入到双向链表(如果已经存在了，则不添加)。
4. 此时，遍历 LinkedHashSet 也能确保与插入顺序一致。

# TreeSet

