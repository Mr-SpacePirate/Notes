## 0x39 $Lambda$ 表达式

```java
(被重写方法的形参列表) -> {
    被重写方法的方法体代码
}
```

- 用于简化内部类的代码写法
- 只能简化函数式接口的匿名内部类
  - 函数式接口：是接口，接口中只有 1 个抽象方法

```java
public class Main {
    public static void main(String[] args){
        Swimming s = () -> {
            System.out.println("游泳");
        };
        s.swim();
    }
}

@FunctionalInterface
interface Swimming {
    void swim();
}
```

### $Lambda$ 表达式的省略写法

- 参数类型可以省略不写
- 如果只有一个参数，参数类型可以省略，同时 `()` 也可以省略
- 如果 $Lambda$ 表达式中的方法体代码只有一行代码，可以省略大括号不写，同时要省略分号！此时，如果这行代码是 $return$ 语句，也必须去掉 $return$ 不写
