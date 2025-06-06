## 0x20 $XML$ 映射文件

### 规范

- $XML$ 映射文件的名称与 $Mapper$ 接口名称一致，并且将 $XML$ 映射文件和 $Mapper$ 接口放置在相同包下（同包同名）。
- $XML$ 映射文件的 $namespace$ 属性为 $Mapper$ 接口全限定名一致。
- $XML$ 映射文件中 $sql$ 语句的 $id$ 与 $Mapper$ 接口中的方法名一致，并保持返回类型一致。

![0x20 XML映射文件](../assets/0x20%20XML映射文件.png)

- 定义在 `resources/com/it/mapper` 下的 `EmpMapper.xml`

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.it.mapper.EmpMapper">
    <!--resultType：单条记录所封装的类型-->
    <select id="list" resultType="com.it.pojo.Emp">
        select * from emp where name like concat('%', #{name}, '%') and gender = #{gender} and
                                      entrydate between #{begin} and #{end} order by update_time desc
    </select>
</mapper>
```

- 定义在 `java/com/it/mapper` 下的 `EmpMapper`

```java
@Mapper
public interface EmpMapper {

    // 条件查询
    public List<Emp> list(String name, Short gender, LocalDate begin, LocalDate end);
}
```