## 0x47 $LinkedHashSet$

- $LinkedHashSet$：**有序**（按插入顺序排序）、不重复、无索引

### 底层原理

- 基于**哈希表**（数组、链表、红黑树）实现的
- 但是，它的每个元素都额外的多了一个双链表的机制记录他前后元素的位置，用双链表来表示插入顺序
