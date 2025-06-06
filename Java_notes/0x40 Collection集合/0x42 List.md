## 0x42 $List$

- $List$ 集合因为支持索引，所以多了很多与索引相关的方法，当然，$Collection$ 的功能 $List$ 也都能继承了

### 方法

- `public void add(int index, E element)` 在索引位置处插入元素
- `public E remove(int index)` 根据索引删除元素，返回被删除的元素
- `public E get(int index)` 返回集合中指定位置的元素
- `public E set(int index, E element)` 修改索引位置处的元素，修改成功后，会返回原来的数据

### 遍历方式

- 有索引，可以用 $for$ 循环