## 0x49 $Collections$

- 一共用来操作集合的工具类

#### 方法

- `public static <T> boolean addAll(Collection<? super T> c, T...elements)` 给集合批量添加元素
- `public static void shuffle(List<?> list)` 打乱 $list$ 集合中的元素顺序
- `public static <T> void sort(List<T> list)` 对 $list$ 集合中的元素进行升序排序
- `public static <T> void sort(List<T> list, Comparator<? super T> c)` 对 $list$ 集合中元素，按照比较器对象指定的规则进行排序