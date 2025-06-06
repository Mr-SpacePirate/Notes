## 0x61 $Stream$ 流

- 用于操作**集合**或者**数组**的数据

### 获取 $Stream$ 流

- 获取**集合**的 $Stream$ 流
  - $Collection$ 提供的方法：`default Stream<E> stream()` 获取当前集合对象的 $Stream$ 流
- 获取**数组**的 $Stream$ 流
  - $Array$ 类提供的方法：`public static <T> Stream<T> stream(T[] array)` 获取当前数组的 $Stream$ 流
  - $Stream$ 类提供的方法：`public static <T> Stream<T> of(T ... values)` 获取当前接收数据的 $Stream$ 流

```java
// Collection 集合
List<String> names = new ArrayList<>();
Collection.addAll(names, "jh", "hhh", "lll");
Stream<String> stream = names.stream();

// Map 集合
Map<String, Double> map = new HashMap<>();
map.put("jh", 22);
map.put("jjj", 33);
map.put("hhh", 44);
Set<Map.Entry<String, Double>> entries = map.entrySet();
Stream<Map.Entry<String, Double>> stream = entries.stream();

// 数组
String[] names = {"jh", "hhh", "lll"};
Stream<String> stream = Arrays.stream(names);

String[] names = {"jh", "hhh", "lll"};
Stream<String> stream = Stream.of(names);
```

### 中间方法

- 返回新 $Stream$，支持链式编程
- `Stream<T> filter(Predicate<? super T> predicate)` 用于对流中的数据进行过滤
- `Stream<T> sorted()` 对元素进行升序排序
- `Stream<T> sorted(Comparator<? super T> comparator)` 按照指定规则排序
- `Stream<T> limit(long maxSize)` 获取前几个元素
- `Stream<T> skip(long n)` 跳过前几个元素
- `Stream<T> distinct()` 去除流中重复的元素
- `<R> Stream<R> map(Function<? super T, ? extends R> mapper)` 对元素进行加工，并返回对应的新流
- `static <T> Stream<T> concat(Stream a, Stream b)` 合并 $a$ 和 $b$ 两个流为一个流

### 终结方法

- 终结方法指的是调用完成后，不会返回新 $Stream$ 了，没法继续使用流了。
- `void forEach(Consumer action)` 对此流运算后的元素执行遍历
- `long count()` 统计此流运算后的元素个数
- `Optional<T> max(Comparator<? super T> comparator)` 获取此流运算后的最大值元素
- `Optional<T> min(Comparator<? super T> comparator)` 获取此流运算后的最小值元素

### 收集 $Stream$ 流

- 流只能被收集一次
- 把 $Stream$ 流操作后的结果转会到集合或者数组中去返回
- `R collect(Collector collector)` 把流处理后的结果收集到一个指定的集合中去

  - `public static <T> Collector toList()` 把元素收集到 $List$ 集合中
  - `public static <T> Collector toSet()` 把元素收集到 $Set$ 集合中
  - `public static Collector toMap(Function keyMapper, Function valueMapper)` 把元素收集到 $Map$ 集合中

  ```java
  // List
  List<Student> student = students.stream()
          .filter(s -> s.getHeight() > 170)
          .collect(Collectors.toList());

  // Set
  Set<Student> student = students.stream()
          .filter(s -> s.getHeight() > 170)
          .collect(Collectors.toSet());

  // Map
  Map<String, Double> student = students.stream()
          .filter(s -> s.getHeight() > 170)
          .collect(Collectors.toMap(s -> s.getName(), s -> s.getHeight());
  ```

- `Object[] toArray()` 把流处理后的结果收集到一个数组中去

  ```java
  Object[] arr = students.stream()
          .filter(s -> s.getHeight() > 170)
          .toArray();
  
  Student[] arr = students.stream()
          .filter(s -> s.getHeight() > 170)
          .toArray(len -> new Student[len]);
  ```
