## 0x44 $LinkedList$

### 底层原理

- 基于**双链表**实现，查询慢，增删相对较快

### 应用场景

- 队列、栈

### 方法

- `public void addFirst(E e)` 在该列表开头插入指定的元素
- `public void addLast(E e)` 将指定的元素追加到此列表的末尾
- `public E getFirst()` 返回此列表中的第一个元素
- `public E getLast()` 返回此列表中的最后一个元素
- `public E removeFirst()` 从此列表中删除并返回第一个元素
- `public E removeLast()` 从此列表中删除并返回最后一个元素