## 0x25 实体 JavaBean

- JavaBean是一个遵循特定写法的Java类，它通常具有如下特点：

1. 这个Java类必须具有一个无参的构造函数
2. 属性必须私有化。
3. 私有化的属性必须通过public类型的方法暴露给其它程序，并且方法的命名也必须遵守一定的命名规范。

```java
// Main.java
public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("jh", 100);
        StudentOperator operator = new StudentOperator(s1);
        operator.printPass();
    }
}

// Student.java
public class Student {
    private String name;
    private double score;

    public Student() {}
    public Student(String name, double score) {
        this.name = name;
        this.score = score;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getScore() {
        return score;
    }

    public void setScore(double score) {
        this.score = score;
    }
}

// StudentOperator.java
public class StudentOperator {
    private Student student;

    public StudentOperator(Student student) {
        this.student = student;
    }

    public void printPass() {
        if (student.getScore() >= 60) {
            System.out.println("恭喜您通过了考试！");
        } else {
            System.out.println("很抱歉您没通过考试！");
        }
    }
}
```