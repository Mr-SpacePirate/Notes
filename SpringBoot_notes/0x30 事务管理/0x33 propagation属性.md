## 0x33 $propagation$ 属性

- 事务传播行为：指的就是当一个事务方法被调用时，这个事务方法应该如何进行事务控制。

```java
@Transactional
public void a() {
    // ...
    userService.b();
    // ...
}

@Transactional(propagation = Propagation.REQUIRED)
public void b() {
    // ...
}
```

| 属性值 | 含义 |
| --- | --- |
| REQUIRED | [默认值]，需要事务，有则加入，无则创建新事务 |
| REQUIRES_NEW | 创建新事务，不管有没有事务，都创建新事务 |
| SUPPORTS | 支持事务，有则加入，无则在无事务状态中运行 |
| NOT_SUPPORTED | 不支持事务，在无事务状态下运行，如果当前存在已有事务，则挂起当前事务 |
| MANDATORY | 必须有事务，否则抛异常 |
| NEVER | 必须没事务，否则抛异常 |