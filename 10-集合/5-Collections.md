[toc]

# Collections

## 介绍

> 1. Collections 是一个操作 List、Set、Map 等集合的工具类。
> 2. Collections 中提供了一系列*<u>静态方法</u>*，对集合元素进行排序、查询和修改等操作。

## 常用方法



| 方法                                                        | 说明                                           |
| ----------------------------------------------------------- | ---------------------------------------------- |
| reverse(List)                                               | 反转 List 中元素的顺序                         |
| shuffle(List)                                               | 随机排序 List 中的元素                         |
| sort(List)                                                  | 根据元素的自然顺序，对 List 中的元素按升序排序 |
| swap(List,int ,int)                                         | 将指定 List 集合中的 i 和 j 元素进行交换       |
| max(Collection)                                             | 根据元素的自然顺序，返回给定集合中的最大元素   |
| max(Collection, Comparator)                                 | 根据指定的顺序，返回给定集合中的最大元素       |
| min(Collection)                                             | 根据元素的自然顺序，返回给定集合中的最小元素   |
| min(Collection, Comparator)                                 | 根据指定的顺序，返回给定集合中的最小元素       |
| int frequency(Collection, Object)                           | 返回指定集合中，指定元素出现的次数             |
| void copy(List dest,List src)                               | 将 src 中的元素复制到 dest 中                  |
| boolean replaceAll(List list, Object oldVal, Object newVal) | 使用新值替换掉 List 对象中的所有               |

## 示例

