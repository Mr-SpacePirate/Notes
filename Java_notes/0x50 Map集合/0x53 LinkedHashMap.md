## 0x53 $LinkedHashMap$

- $LinkedHashMap$（由键决定特点）：**有序**、不重复、无索引

#### 底层原理

- 基于哈希表实现，只是每个键值对元素又额外的多了一个双链表的机制记录元素顺序（保证有序）
- $LinkedHashSet$ 集合的底层原理就是 $LinkedHashMap$