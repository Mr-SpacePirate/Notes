## 0x33 $sql$ & $include$

- $<sql>$ 定义可重用的 $SQL$ 片段
- $<include>$ 通过属性 $refid$，指定包含的 $sql$ 片段

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.it.mapper.EmpMapper">
    
    <sql id="commonSelect">
        select id, username, password, name, gender, image, job, entrydate, dept_id, create_time, update_time
        from emp
    </sql>

    <!--resultType：单条记录所封装的类型-->
    <select id="list" resultType="com.it.pojo.Emp">
        <include refid="commonSelect"/>
        <where>
            <if test="name != null">
                name like concat('%', #{name}, '%')
            </if>
            <if test="gender != null">
                and gender = #{gender}
            </if>
            <if test="entryDate != null">
                and entrydate between #{begin} and #{end}
            </if>
        </where>
        order by update_time desc
    </select>
</mapper>
```