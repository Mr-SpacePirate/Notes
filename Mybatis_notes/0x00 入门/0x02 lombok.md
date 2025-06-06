## 0x02 $lombok$

- 能通过注解的形式自动生成构造器、$getter/setter$、$equals$、$hashcode$、$toString$ 等方法，并可以自动化生成日志变量。

| 注解 | 作用 |
| ---- | ---- |
| `@Getter/@Setter` | 为所有的属性提供 `get/set` 方法 |
| `@ToString` | 会给类自动生成易阅读的 `toString` 方法 |
| `@EqualsAndHashCode` | 根据类所拥有的非静态字段自动重写 `equals` 方法和 `hashCode` 方法 |
| `@Data` | 提供了更综合的生成代码功能 （`@Getter` + `@Setter` + `@ToString` + `@EqualsAndHashCode`） |
| `@NoArgsConstructor` | 为实体类生成无参的构造器方法 |
| `@AllArgsConstructor` | 为实体类生成除了 $static$ 修饰的字段之外带有各参数的构造器方法 |

### 引入 $lombok$ 依赖

```xml
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
</dependency>
```