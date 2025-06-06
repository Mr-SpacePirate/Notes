## 0x10 java 语法

### 0x11 二进制、八进制、十六进制在程序中的写法

```java
int a1 = 0B01100001;    // 2B开头，二进制
System.out.println(a1); // 97

int a2 = 0141;          // 0开头，八进制
System.out.println(a2); // 97

int a3 = 0xFA;          // 0x开头，十六进制
System.out.println(a3); // 250
```

### 0x12 表达式自动类型变换

- `float f = 12.3f;` 定义float变量
- `long l = 123123l;` 定义long变量
- $byte$ 类型和 $short$ 类型在计算中直接转换成 $int$ 类型
- 代码中直接写 $1.0$ 是 $double$ 类型

### 0x13 $+$符号做连接符

```java
int a = 5;
System.out.println(a + 'a' + "jh"); // 102jh
System.out.println("jh" + a + 'a'); // jh5a
```

### 0x14 Scanner

```java
import java.util.Scanner;   // 导包

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入您的年龄：");
        int age = sc.nextInt();     // 输入 22
        System.out.println("您的年龄是：" + age);   // 输出 22

        System.out.println("请输入您的姓名：");
        String name = sc.next();    // 输入 jh
        System.out.println("您的姓名是：" + name);  // 输出 jh
    }
}
```

### 0x15 Random

```java
import java.util.Random;

public class Main {
    public static void main(String[] args) {
        Random r = new Random();
        System.out.println(r.nextInt(10));  // 生成0~9之间的随机数
        System.out.println(r.nextInt(10) + 1);  //生成1~10之间的随机数
    }
}
```

### 0x16 数组

- 静态数组

```java
int[] age1 = {12, 23, 34};
int[] age2 = new int[]{12, 23, 34};
int age3[] = {12, 23, 34};
```

- 动态数组

```java
int[] arr = new int[3]; // 初始为0
boolean[] flag = new boolean[3];    // 初始为false
String[] names = new String[3]; // 初始为null

int[] arr1 = arr;   // 数组赋值，赋的是指针
```
