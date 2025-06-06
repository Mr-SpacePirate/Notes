## 0x43 $ArrayList$

### 底层原理

- 基于**数组**实现，查询速度快，删除效率低，添加效率低
- 利用无参构造器创建的集合，会在底层创建一个默认长度为 $0$ 的数组
- 添加第一个元素时，底层会创建一个新的长度为 $10$ 的数组
- 存满时，会扩容 $1.5$ 倍
- 如果一次添加多个元素，$1.5$ 倍还放不下，则新创建数组的长度以实际为准

### 应用场景

- 适合：根据索引查询数据，比如根据随机索引取数据（高效），或者数据量不是很大时。
- 不适合：数据量大的同时，又要频繁的进行增删操作。

### 常用方法

- `ArrayList list = new ArrayList();` 创建集合对象
  ```java
  ArrayList list1 = new ArrayList();      // 元素任意
  ArrayList<String> list2 = new ArrayList<>(); // 元素只能是String
  ArrayList<Integer> list3 = new ArrayList<>();   //元素只能是int
  ```
- `public boolean add(E e)` 将指定的元素添加到此集合的末尾
- `public void add(int index, E element)` 在此集合中的指定位置插入指定的元素
- `public E get(int index)` 返回指定索引处的元素
- `public int size()` 返回集合中的元素的个数
- `public E remove(int index)` 删除指定索引处的元素，返回删除元素
- `public boolean remove(Object o)` 删除指定元素值，返回是否成功
  - `list.remove((Integer) 43)` 删除 43 这个元素
- `public E set(int index, E element)` 修改指定索引处的元素，返回被修改的元素

### 问题

- 不能通过增强 $for$ 循环和 $Lambda$ 表达式来删除元素
- 只能使用迭代器来删除元素，或倒着遍历删除

```java
Iterator<String> it = list.iterator();
while (it.hasNext()) {
    String name = it.next();
    if (name.contains("李")) {
        it.remove();  // 删除迭代器当前遍历到的数据，没闪出一个数据后，相当于在底层做了i--
    }
}
```
