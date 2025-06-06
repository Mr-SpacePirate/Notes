## 0x22 $this$ 的使用

```java
public class Student {
    double score;

    public void printPass(double score) {
        if (this.score >= score) {
            System.out.println("恭喜您，通过了考试！");
        } else {
            System.out.println("很遗憾，您没通过考试。");
        }
    }
}
```
