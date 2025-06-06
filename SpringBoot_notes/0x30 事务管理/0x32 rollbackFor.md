## 0x31 $rollbackFor$

- 默认情况下，只有出现 $RuntimeException$ 时才会回滚事务。$rollbackFor$ 属性用于控制出现何种异常类型，回滚事务。

```java
@Transactional(rollbackFor = Exception.class)   // 指定所有异常时回滚事务
@Override
public void delete(Integer id) throws Exception {
    // 1. 删除部门
    deptMapper.delte(id);

    if (true) {
        throw new Exception("出错了");
    }

    // 2. 删除员工
    empMapper.deleteByDeptId(id);
}
```