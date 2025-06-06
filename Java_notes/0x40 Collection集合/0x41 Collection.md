## 0x41 $Collection$

- $Collection$ 代表单列集合，每个元素（数据）只包含一个值

#### $Collection$ 集合体系

![0x41 Collection集合体系](../assets/0x41%20Collection集合体系.png)

#### $Collection$ 集合特点

- $List$ 系列集合：添加元素是有序、可重复、有索引
  - $ArrayList$、$LiskedList$：有序、可重复、有索引
- $Set$ 系列集合：添加到元素是无序、不重复、无索引
  - $HashSet$：无序、不重复、无索引
  - $LinkedHashSet$：**有序**、不重复、无索引
  - $TreeSet$：可排序（默认升序排序）、不重复、无索引

### 方法

- `Collection<String> c1 = new ArrayList<>();` 声明
- `public boolean add(E e)` 添加元素，成功返回 true
- `public void clear()` 清空集合元素
- `public boolean isEmpty()` 判断集合是否为空，是空返回 true
- `public int size()` 获取集合的大小
- `public boolean contains(Object obj)` 判断集合中是否包含某个元素
- `public boolean remove(E e)` 删除某个元素，如果有多个重复元素，默认删除前面的第一个
- `public Object[] toArray()` 把集合转换成数组
  - `Object[] arr = c.toArray();`
  - `String[] arr = c.toArray(new String[c.size()]);`
- `public abstract boolean addAll(Collecion e)` 把一个集合中的全部数据导入到另一个集合中去

### 遍历方式

#### 迭代器

##### 获取迭代器的方法

- `Iterator<E> iterator()` 返回集合中的迭代器对象，该迭代器对象默认指向当前集合的第一个元素

##### $Iterator$ 迭代器中的常用方法

- `boolean hasNext()` 询问当前位置是否有元素存在，存在返回 true，不存在返回 false
- `E next()` 获取当前位置的元素，并同时将迭代器对象指向下一个元素处

```java
Collection<String> c = new ArrayList<>();
...
Iterator<String> it = c.iterator();
while (it.hasNext()) {
    String ele = it.next();
    System.out.println(ele);
}
```

#### 增强 $for$ 循环

```java
for (元素的数据类型 变量名 : 数组或者集合) {

}
```

- 增强 $for$ 循环可以用来遍历集合或者数组

```java
Collecion<String> c = new ArrayList<>();
...
for (String s : c) {
    ...
}
```

#### $Lambda$ 表达式遍历集合

- `default void forEach(Consumer<? super T> action)` 结合$lambda$ 遍历

```java
c.forEach(new Consumer<String>() {
    @Override
    public void accept(String s) {
        System.out.println(s);
    }
});

c.forEach(System.out::println);
```