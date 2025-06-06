## 0x15 $JSON$ 参数

- $JSON$ 数据**键名**与形参对象**属性名**相同，定义 $Pojo$ 类型形参即可接收参数，需要使用 $@RequestBody$ 标识

```java
// RequestController.java
@RestController
public class RequestController {
    @RequestMapping("/jsonParam")
    public String jsonParam(@RequestBody User user) {
        System.out.println(user);
        // User{name='jh', age=16, address=Address{province='liaoning', city='dalian'}}
        return "OK";
    }
}

// User.java
public class User {
    private String name;
    private Integer age;
    private Address address;

    get...
    set...
    toString...
}

// Address.java
package com.it.pojo;

public class Address {
    private String province;
    private String city;

    get...
    set...
    toString...
}
```

![0x15 JSON参数](../assets/0x15%20JSON参数.png)