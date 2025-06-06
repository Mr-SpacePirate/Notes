## 0x13 $this$ 指针

> $this$ 指针指向被调用的成员函数所属的对象。

### $this$ 指针的用途

- 当形参和成员变量重名时，可用 $this$ 指针来区分。
- 在类的非静态成员函数中返回对象本身，可使用 `return *this;`

``` C++
class Person {
public:
    Person(int age) {
        this->age = age;
    }
    Person& Person_add_age(Person &p) {
        this->age += p.age;
        return *this;
    }

private:
    int age;
};

int main() {
    Person p1(10);
    Person p2(10);

    p2.Person_add_age(p1).Person_add_age(p1).Person_add_age(p1);
    // p2.age = 40

    return 0;
}
```


----------


### $const$ 修饰成员函数

#### 常函数

- 成员函数后加 `const` 后，我们称这个函数为常函数
- 常函数内不可以修改成员属性
- 成员属性声明时加关键字 `mutable` 后，在常函数中依然可以修改

#### 常对象

- 声明对象前加 `const` 称该对象为常对象
- 常对象只能调用常函数

```C++
class Person {
public:
    Person() : m_A(0), m_B(0) {}

    // this指针的本质是一个指针常量，指针的指向不可修改
    // 如果想让指针指向的值也不可修改，需要声明常函数
    void ShowPerson() const {
        // const Type* const pointer;
        // this->m_A = 100;     错误

        //const修饰成员函数，表示指针指向的内存空间的数据不能修改，除了mutable修饰的变量
        this->m_B = 100;
    }
    void func() {}

public:
    int m_A;
    mutable int m_B;
};

int main() {
    const Person p;
    cout << p.m_A << endl;
    // person.m_A = 100;    // 常对象不能修改成员变量的值，但是可以访问
    person.m_B = 100;       // 常对象可以修改mutable修饰的成员变量

    // p.func();            // 常对象只能调用常函数
    p.ShowPerson();

    return 0;
}
```