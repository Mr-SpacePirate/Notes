## 0x32 $foreach$

- 批量删除

- $collection$ 遍历集合
- $item$ 遍历出来的元素
- $separator$ 分隔符
- $open$ 遍历开始前拼接的 $SQL$ 片段
- $close$ 遍历结束后拼接的 $SQL$ 片段

### 用例

- 定义在 `resources/com/it/mapper` 下的 `EmpMapper.xml`

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.it.mapper.EmpMapper">

    <!--批量删除员工信息-->
    <delete id="deleteByIds">
        delete
        from emp
        where id in
        <foreach collection="ids" item="id" separator="," open="(" close=")">
            #{id}
        </foreach>
    </delete>
</mapper>
```

- 定义在 `java/com/it/mapper` 下的 `EmpMapper.java`

```java
@Mapper
public interface EmpMapper {

    // 批量删除员工
    public void deleteByIds(List<Integer> ids);
}
```

- 定义在 `test/java/com/it` 下的 `SpringbootQuickstartApplicationTests.java`

```java
@SpringBootTest
class SpringbootQuickstartApplicationTests {

    @Test
    public void testDeleteByIds() {
        List<Integer> ids = Arrays.asList(12, 13, 14);
        empMapper.deleteByIds(ids);
    }
}
```