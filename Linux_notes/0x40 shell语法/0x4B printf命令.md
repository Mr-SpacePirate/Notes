## 0x4B printf命令

- `printf` 命令用于格式化输出，类似于 `C/C++` 中的 `printf` 函数。

- 默认**不会在字符串末尾添加换行符**。

- **命令格式：** `printf format-string [arguments...]`

- **用法示例：**

  ``` bash
  printf "%10d.\n" 123                        # 占10位，右对齐
  printf "%-10.2f.\n" 123.123321              # 占10位，保留2位小数，左对齐
  printf "My name is %s\n" "yxc"              # 格式化输出字符串
  printf "%d * %d = %d\n"  2 3 `expr 2 \* 3`  # 表达式的值作为参数

  :<<输出
        123.
  123.12    .
  My name is yxc
  2 * 3 = 6
  输出
  ```