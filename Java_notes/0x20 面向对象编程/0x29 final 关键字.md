## 0x29 $final$ 关键字

- 修饰类：该类被定义为最终类，特点是不能被继承
  ```java
  final class A {}    // A不能被继承了
  // class B extends A {}
  ```
- 修饰方法：该方法被称为最终方法，特点是不能被重写

  ```java
  class C {
      public final void test() {} // test不能被重写
  }

  class D extends C {
      // @Override
      // public void test() {}
  }
  ```

- 修饰变量：该变量只能被赋值一次

  ```java
  public class Main {
      public static void main(String args) {
          final int a = 9;    // 只能被赋值一次
          // a = 99;
      }

      public static void buy(final double z) {
          // z = 0.1;
      }
  }
  ```

### 注意

- $final$ 修饰基本类型的变量，变量存储的**数据**不能被改变
- $final$ 修饰引用类型的变量，变量存储的**地址**不能被改变，但是地址所指向对象的内容是可以改变的。
  ```java
  final int[] arr = {11, 22, 33};
  arr[1] = 222;
  ```

### 常量

- `public static final` 修饰的成员变量，建议名称全部大写，多个单词下划线链接

```java
public static final String REAL_NAME = "jh";
```
