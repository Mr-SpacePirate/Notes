## 0x34 $String$、$StringBuilder$、 $StringBuffer$ 与 $StringJoiner$

### $String$

- $String$ 对象内容不可改变
- 以`"..."`方式写出的字符串对象，会存储到字符串常量池中，且相同内容的字符串子存储一份
- 通过 $new$ 方式创建的字符串对象，每 $new$ 一次都会产生一个新的对象放在堆中

#### 常用方法

- `public int length()` 获取字符串长度
- `public char charAt(int index)` 获取某个索引位置处的字符返回
- `public char[] toCharArray()` 将当前字符串转换成字符数组返回
- `public boolean equals(Object anObject)` 判断当前字符串与另一个字符串的内容一样，一样返回 $true$
  - `if(s1 == s2)` 比较的是地址
- `public boolean equalsIgnoreCase(String anotherString)` 判断当前字符串与另一个字符串的内容是否一样（忽略大小写）
- `public String substring(int beginIndex, int endIndex)` 截取字符串（包前不包后）
- `public String substring(int beginIndex)` 从传入的索引处截到末尾
- `public String replace(CharSequence target, CharSequence replacement)` 将字符串中旧值替换成新值
  ```java
  public class Main {
      public static void main(String[] args) {
          String s = "sdfsdfsdf";
          String str = s.replace("sd", "0");
          System.out.println(str);    // 0f0f0f
      }
  }
  ```
- `public boolean contains(CharSequence s)` 判断字符串中是否包含了某个字符串
- `public boolean startWith(String prefix)` 判断字符串是否以某个字符串内容为开头
- `public String[] split(String regex)` 把字符串按照某个字符串内容分割，并返回字符串数组回来（用于删除 ","）

### $StringBuilder$

- $StringBuilder$ 代表可变字符串对象，**相当于是一个容器**，它里面装的字符串是可以改变的，就是用来操作字符串的。
- $StringBuilder$ 比 $String$ 更适合做字符串的修改操作，效率更高，代码更简洁。

#### 构造器

- `public StringBuilder()` 创建一个空白的可变的字符串对象，不包含任何内容
- `public StringBuilder(String str)` 创建一个指定字符串内容的可变字符串对象

#### 方法

- `public StringBuilder append(任意类型)` 添加数据并返回 $StringBuilder$ 对象本身
  - 支持链式编程 `s.append(666).append("jh");`
- `public StringBuilder reverse()` 将对象的内容反转
- `public int length()` 返回对象内容长度
- `public String toString()` 把 $StringBuilder$ 对象转换成 $String$ 类型

### $StringBuffer$

- $StringBuffer$ 的用法与 $StringBuilder$ 是一模一样的
- 但 $StringBuilder$ 是线程不安全的，$StringBuffer$ 是线程安全的


### $StringJoiner$

- $JDK8$ 开始有的，跟 $StringBuilder$ 一样，也是用来操作字符串的，也可以看成是一个容器，创建之后里面的内容是可变的。
- 不仅能提高字符串的操作效率，并且在有些场景下使用它操作字符串，代码会更简洁

#### 构造器

- `public StringJoiner(间隔符号)` 创建一个 $StringJoiner$ 对象，指定拼接时的间隔符号
- `public StringJoiner(间隔符号, 开始符号, 结束符号)` 创建一个 $StringJoiner$ 对象，指定拼接时的间隔符号、开始符号、结束符号

#### 方法

- `public StringJoiner add(添加内容)` 添加数据，闭关返回对象本身（**只能添加字符串**）
- `public int length()` 返回长度（字符出现的个数）
- `public String toString()` 返回一个字符串（该字符串就是拼接之后的结果）


```java
public class Main {
    public static void main(String[] args) {
        System.out.println(getArrayData(new int[]{11, 22, 33}));
    }

    public static String getArrayData(final int[] arr) {
        if (arr == null) {
            return null;
        }

        StringJoiner sj = new StringJoiner(", ", "[", "]");
        for (int x : arr) {
            sj.add(x + "");
        }
        return sj.toString();
    }
}
```