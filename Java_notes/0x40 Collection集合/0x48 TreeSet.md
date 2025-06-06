## 0x48 $TreeSet$

- $TreeSet$：可排序（默认升序排序）、不重复、无索引

### 底层原理

- 基于**红黑树**实现

### 自定义排序规则

- 让自定义的类实现 $Comparable$ 接口，重写里面的 $compareTo$ 方法来指定比较规则
- 通过调用 $TreeSet$ 集合有参数构造器，可以设置 $Comparable$ 对象（比较器对象，用于指定比较规则）
  ```java
  Set<Student> students = new TreeSet<>((o1, o2) -> Double.compare(o1.getHeight(), o2.getHeight()));
  ```
- 详见 $0x38 Arrays.md$
