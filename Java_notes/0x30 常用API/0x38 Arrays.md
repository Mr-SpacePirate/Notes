## 0x38 $Arrays$

- 用来操作数组的工具

### 方法

- `public static String toString(类型[] arr)` 返回数组内容
- `public static int[] copyOfRange(类型[] arr, 起始索引, 结束索引)` 拷贝数组，包前不包后
- `public static copeOf(类型[] array, int new Length)` 拷贝数组，可以指定新数组长度
- `public static setAll(double[] array, IntToDoubleFunction generator)` 把数组中的原数据改为新数据又存回去
  - 用例：所有价格打八折
    ```java
    double[] prices = {88.4, 54.23, 100};
    Arrays.setAll(prices, new IntToDoubleFunction() {
        @Override
        public double applyAsDouble(int value) {
            return prices[value] * 0.8;
        }
    });
    ```
- `public static void sort(类型[] arr)` 对数组进行排序（默认时升序排序）

  - 让该对象的类实现 $Comparable(比较规则)$ 接口，然后重写 $compareTo$ 方法，自己来指定比较规则

    ```java
    @Override
    public class Student implements Comparable<Student> {
        private String name;
        private int age;

        public int compareTo(Student o) {
            // 升序
            // if (this.age > o.age) {
            //     return 1;
            // } else if (this.age == o.age) {
            //     return 0;
            // } else {
            //     return -1;
            // }
            return this.age - o.age;
            return Integer.compare(this.age, o.age);
        }
    }
    ```

  - `public static <T> void sort(T[] arr, Comparator<? super T> c)` 创建 $Comparator$ 比较器接口的匿名内部对象，然后自己制定比较规则

    ```java
    Arrays.sort(students, new Comparator<Student>() {
        @Override
        public int compare(Student o1, Student o2) {    // 返回int
            return Double.compare(o1.getHeight(), o2.getHeight());
        }
    });
    ```

  - `public static int binarySearch(int[] arr, int key)` 二分查找，返回元素下标；没有找到返回负数


