## 0x31 $@Transactional$

- 位置：业务（service）层的方法上、类上、接口上
- 作用：将当前方法交给 $spring$ 进行事务管理，方法执行前，开启事务；成功执行完毕，提交事务；出现异常，回滚事务。

```java
@Transactional
@Override
public void delete(Integer id) {
    // 1. 删除部门
    deptMapper.delte(id);
    int i = 1 / 0;  // 引发异常，回滚事务

    // 2. 删除员工
    empMapper.deleteByDeptId(id);
}
```