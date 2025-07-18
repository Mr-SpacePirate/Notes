## 0x49 read命令

- `read` 命令用于标准输入中读取单行数据。当读到文件结束时，`exit code` 为1，否则为0。

- 参数说明：

  - `-p`：后面可以接提示信息。
  
  - `-t`：后面跟秒数，定义输入字符等待的时间，超过等待时间后会自动忽略此命令。

  - 实例：
    ``` Linux
    acs@9e0ebfcd82d7:~$ read name           # 读入name的值
    acwing yxc                              # 标准输入
    acs@9e0ebfcd82d7:~$ echo $name          # 输出name的值
    acwing yxc                              # 标准输出
    acs@9e0ebfcd82d7:~$ read -p "Please input your name: " -t 30 name 
                                            # 读入name的值，等待时间30秒
    Please input your name: acwing yxc      # 标准输入
    acs@9e0ebfcd82d7:~$ echo $name          # 输出name的值
    acwing yxc                              # 标准输出
    ```