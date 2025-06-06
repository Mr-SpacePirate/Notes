## 0x46 $HashSet$

- $HashSet$：无序、不重复、无索引
- `public int hashCode()` 返回对象的哈希值

### 底层原理

- 基于**哈希表**实现，增删改查数据性能都较好
- $JDK8$ 之前，哈希表 = 数组 + 链表
  - 创建一个默认长度 $16$ 的数组，默认加载因子为 $0.75$ 数组名 $table$
  - 使用元素的**哈希值**对**数组的长度求余**计算出应存入的位置
  - 如果当前位置为 $null$ 直接存入；如果不为 $null$ 则调用 $equals$ 方法比较，相等则不存，不相等则存入数组
    - $JDK9$ 之前，新元素存入数组，占老元素位置，老元素挂下面
    - $JDK8$ 开始之后，新元素直接挂在老元素下面
- $JDK8$ 开始，哈希表 = 数组 + 链表 + 红黑树

### 去重原理

- $HashSet$ 集合默认不能对内容相同的两个不同对象去重，如果希望两个内容一样的对象去重，必须重写 `hashCode()` 和 `equals()` 方法
    ```java
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return age == student.age && Objects.equals(name, student.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age); // 根据姓名和年龄得到哈希值
    }
    ```