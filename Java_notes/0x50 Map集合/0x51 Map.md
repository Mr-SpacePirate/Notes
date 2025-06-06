## 0x51 $Map$

- $Map$ 集合称为双列集合，格式：`{key1 = value1, key2 = value2, ...}`，一次需要存一对数据作为一个元素
- $Map$ 集合的每个元素 `key = value` 称为一个键值对
- $Map$ 集合的所有键是不允许重复的，但值可以重复，键和值是一一对应的，每一个键只能找到自己对应的值。

### $Map$ 集合体系

![0x51 Map集合体系](../assets/0x51%20Map集合体系.png)

### $Map$ 集合体系特点

- $Map$ 系列集合的特点都是由**键**决定的，值只是一个附属品，值是不做要求的
- 键值重复的数据，后面添加的会覆盖前面的数据
- $HashMap$（由键决定特点）：无序、不重复、无索引
- $LinkedHashMap$（由键决定特点）：**有序**、不重复、无索引
- $TreeMap$（由键决定特点）：**默认按照键的大小升序排序**、不重复、无索引

### 常用方法

- `key : value`
- `Map<Integer, String> map = new HashMap<>();` 声明
- `public int size()` 获取集合大小
- `public void clear()` 清空集合
- `public isEmpty()` 判断集合是否为空
- `public V get(Object key)` 根据键获取对应值
- `public V remove(Object key)` 根据键删除整个元素（删除键会返回键值）
- `public boolean containsKey(Object key)` 判断是否包含某个键
- `public boolean containsValue(Object value)` 判断是否包含某个值
- `public Set<K> keySet()` 获取Map集合的全部键
- `public Cellection<V> values()` 获取Map集合的全部值
- `public void putAll(Map<xxx, xxx> map)` 把map中的元素复制到调用者的后面
  - `map1.putAll(map2)`

### 遍历方式

#### 键找值

- 先获取Map集合全部的键，再通过遍历键来找值。
- `public Set<K> keySet()` 获取所有键的集合
- `public V get(Object key)` 根据键获取其对应的值

```java
Map<String, Double> map = new HashMap<>();
Set<String> keys = map.keySet();  // 获取键
for (String key : keys) {
    double value = map.get(key);  // 获取值
}
```

#### 键值对

- 把键值对看成一个整体进行遍历
- `public Set<Map.Entry<K, V>> entrySet()` 获取所有“键值对”的集合
- `public K getKey()` 获取键
- `public V getValue()` 获取值

```java
Map<String, Double> map = new HashMap<>();
Set<Map.Entry<String, Double>> entries = map.entrySet();
for (Map.Entry<String, Double> entry : entries) {
    String key = entry.getKey();
    Double value = entry.getValue();
}
```

#### $Lambda$

- `default void forEach(BiConsumer<? super K, ? super V> action)` 结合 $lambda$ 遍历集合

```java
Map<String, Double> map = new HashMap<>();
map.forEach((key, value) -> {
    System.out.println(key + ": " + value);
});
```