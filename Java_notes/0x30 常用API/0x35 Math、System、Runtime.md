## 0x35 $Math$、$System$、$Runtime$

### $Math$

#### 方法

- `public static int abs(int a)` 绝对值
- `public static double cell(double a)` 向上取整
- `public static double floor(double a)` 向下取整
- `public static int round(floaat a)` 四舍五入
- `public static int max(int a, int b)` 取最大值
- `public static double pow(double a, double b)` 求 $a^b$
- `public static double random()` 返回值为 $double$ 的随机数，范围 $[0.0, 1.0)$

### $System$

#### 方法

- `public static void exit(int status)` 终止当前运行的 Java 虚拟机。非零状态码表示异常终止，零表示人为终止。
- `public static long currentTimeMillis()` 返回当前系统的时间毫秒形式，从 1970-01-01 0:0:0 开始到此刻的毫秒值

  - 计算程序执行时间

    ```java
    public class Main {
        public static void main(String[] args) {
            long startTime = System.currentTimeMillis();

            ...

            long endTime = System.currentTimeMillis();
            System.out.println((endTime - startTime) / 1000.0 + "s");
        }
    }
    ```

### $Runtime$

- 代表程序所在的运行环境
- $Runtime$ 是一个单例类

#### 方法

- `public static Runtime getRuntime()` 返回与当前 Java 应用程序关联的运行时对象
- `public void exit(int status)` 终止当前运行的虚拟机
- `public int availableProcessors()` 返回 Java 虚拟机可用的处理器数
- `public long totalMemory()` 返回 Java 虚拟机中的内存总量
- `public long freeMemory()` 返回 Java 虚拟机中的可用内存
- `public Process exec(String command)` 启动某个程序，并返回代表该程序的对象
