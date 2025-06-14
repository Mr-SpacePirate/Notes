## 0x4A echo命令

- `echo` 用于输出字符串，命令格式 `echo STRING`

- **显示普通字符串：**
  ``` bash
  echo "Hello, World"
  echo Hello, World               # 引号可以省略
  ```

- **显示转义字符：**
  ``` bash
  echo "\"Hello AC Terminal\""    # 注意只能使用双引号，如果使用单引号，则不转义
  echo \"Hello AC Terminal\"      # 也可以省略双引号
  ```

- **显示变量：**
  ``` bash
  name=jh
  echo "My name is $name"         # 输出 My name is jh
  ```

- **显示换行：**
  ``` bash
  echo -e "Hi\n"                  # -e 开启转义
  echo "acwing"

  :<<输出
  Hi

  acwing
  输出
  ```

- **显示不换行：**
  ``` bash
  echo -e "Hi \c"                 # -e 开启转义 \c 不换行
  echo "acwing"

  :<<输出
  Hi acwing
  输出
  ```

- **显示结果定向至文件：**
  ``` bash
  echo "Hello World" > output.txt  # 将内容以覆盖的方式输出到output.txt中
  ```

- **原样输出字符串，不进行转义或取变量（用单引号）：**
  ``` bash
  name=acwing
  echo '$name\"'

  :<<输出
  $name\"
  输出
  ```

- **显示命令的执行结果**
  ``` bash
  echo `date`

  :<<输出
  Wed Sep 1 11:45:33 CST 2021
  输出
  ```