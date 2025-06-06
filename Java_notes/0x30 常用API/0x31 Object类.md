## 0x31 $Object$ 类

- $Object$ 类是 $java$ 中所有类的祖宗类

### 常用方法

- `public String toString()` 返回对象的字符串表达形式（地址）
  ```java
  System.out.println(s1.toString());
  System.out.println(s1);
  ```
- `public boolean equals(Object o)` 判断两个对象是否相等（比较地址）
  ```java
  System.out.println(s1.equals(s2));
  System.out.println(s1 == s2);
  ```
- `protected Object clone()` 对象克隆
  - 浅克隆：拷贝地址
  - 深克隆：基本类型直接拷贝，字符串数据拷贝地址，对于其他对象创建新对象存储
