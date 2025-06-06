## 0x00 $SpringBoot$ 入门程序

- 创建springboot工程，填写模块信息，并勾选web开发相关依赖
- 创建请求处理类HelloControl，添加请求处理方法hello，并添加注解

```java
// 请求处理类
@RestController
public class HelloController {
    @RequestMapping("/hello")   // localhost:8080/hello
    public String hello() {
        System.out.println("Hello World!");
        return "Hello World!";
    }
}
```