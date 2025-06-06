## 0x32 $Objects$ 类

### 常见方法

- `public static boolean equals(Object a, Object b)` 先做非空判断，再比较两个对象（比较地址）
  ```java
  System.out.println(Objects.equals(s1, s2));
  ```
- `public static boolean isNull(Object obj)` 判断对象是否为 $null$，为 $null$ 返回 $true$
- `public static boolean nonNull(Object obj)` 判断对象是否不为 $null$，不为 $null$ 返回 $true$