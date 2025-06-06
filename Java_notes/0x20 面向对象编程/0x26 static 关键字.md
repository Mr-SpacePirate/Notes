## 0x26 $static$ 关键字

### 变量

- 类变量：有 $static$ 修饰，属于类，在计算机中只有一份，**会被类的全部对象共享**
- 实例变量（对象的变量）：无 $static$ 修饰，**属于每个对象**

  ```java
  // Main.java
  public class Main {
      public static void main(String[] args) {
          Student.name = "jh";

          Student s1 = new Student();
          s1.name = "lzj";    // 不建议这样使用
          System.out.println(Student.name);    // lzj
      }
  }

  // Student.java
  public class Student {
      // 类变量
      static String name;
      // 实例变量（对象的变量）
      int age;
  }
  ```

- 案例：启动系统后要求用户类可以记住自己创建了多少个用户对象

  ```java
  public class User() {
      public static int number;

      public User() {
          User.number ++ ;
      }
  }
  ```

### 方法

- 类方法：有 $static$ 修饰的成员方法，属于类
- 实例方法：无 $static$ 修饰的成员方法，属于对象

  ```java
  // Main.java
  public static Main {
      public static void main(String[] args) {
          Student.printHelloWorld();  // Hello World
          Student s1 = new Student();
          s1.printHello();    // Hello
      }
  }

  // Student.java
  public class Student {
      public static void printHelloWorld() {
          System.out.println("Hello World");
      }

      public void printHello() {
          System.out.println("Hello");
      }
  }
  ```

### 工具类

- 随机生成一个 8 位验证码

  ```java
  // Main.java
  public class Main {
      public static void main(String[] args) {
          System.out.println(MyUtil.createCode(8));
      }
  }

  // MyUtil.java
  import java.util.Random;

  public class MyUtil {   // 工具类
      private MyUtil() {} // 将对象私有，即不能new一个对象

      public static String createCode(int n) {
          String code = "";
          String data = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
          Random r = new Random();

          for (int i = 0; i < n; i ++ ) {
              code += data.charAt(r.nextInt(data.length()));
          }

          return code;
      }
  }
  ```

### $static$ 注意事项

- 类方法中可以直接访问类的成员，不可以直接访问实例成员
- 实例方法中既可以访问类成员，也可以访问实例成员
- 实例方法中可以出现 $this$ 关键字，类方法中不可以出现 $this$ 关键字

### 代码块

- 静态代码块

  - 特点：类加载时自动执行，由于类**只会加载一次**，所以静态代码块也**只会执行一次**
  - 作用：完成类的初始化

    ```java
    // Main.java
    public class Main {
        public static void main(String[] args) {
            System.out.println(Student.name);
            System.out.println(Student.name);
        }
    }

    // Student.java
    public class Student {
        static String name;

        static {
            System.out.println("静态代码块执行了");
            name = "jh";
        }
    }
    /**
     * 静态代码块执行了
     * jh
     * jh
    */
    ```

- 实例代码块

  - 特点：每次创建对象时，执行实例代码块，并在构造器前执行
  - 作用：和构造器一样，都是用来完成对象的初始化的

    ```java
    // Main.java
    public class Main {
        public static void main(String[] args) {
            Student s1 = new Student();
            Student s2 = new Student("jh");
        }
    }

    // Student.java
    public class Student {
        {
            System.out.println("实例代码块执行了");
        }

        public Student() {
            System.out.println("无参数构造器执行了");
        }

        public Student(String name) {
            System.out.println("有参构造器执行了");
        }
    }

    /**
     * 实例代码块执行了
     * 无参数构造器执行了
     * 实例代码块执行了
     * 有参构造器执行了
     */
    ```

### 单例类

- 饿汉式单例设计模式

  - 拿对象时，对象早就创建好了

    ```java
    public class Student {
        private static Student s = new Student();

        private Student() {}

        public static Student getObject() {
            return s;
        }
    }
    ```

- 懒汉式单例设计模式

  - 拿对象时，才开始创建对象

  ```java
  public class Student {
      private static Student s;

      private Student() {}

      public static Student getObject() {
          if (s == null) {
              s = new Student();
          }
          return s;
      }
  }
  ```