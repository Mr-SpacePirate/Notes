## 0x51 ssh登录

#### 基本用法

登录远程服务器：
``` C++
ssh user@hostname
```
- `user`：用户名
- `host`：IP地址或域名

该服务器的信息会记录在 `~/.ssh/kown_hosts` 文件中。
然后输入密码登录到服务器中。

--------

默认登录端口号为 $22$。如果像登录到某一特定端口：
``` C++
ssh user@hostname -p 22
```

#### 配置文件

创建文件 `~/.ssh/config`
然后在文件中输入：
``` C++
Host myserver1
    Hostname IP地址或域名
    User 用户名

Host myserver2
    Hostname IP地址或用户名
    User 用户名

......
```

之后再使用服务器时，可以直接用别名 `myserver1`、`myserver2`。


#### 密钥登陆

创建密钥
``` C++
ssh-keygen
```

然后一直回车即可。

执行结束后，`~/.ssh/` 目录下会对两个文件：
- `id_rsa` 私钥
- `id_rsa.pub` 公钥

--------

之后想免密码登录哪个服务器，就将公钥传给哪个服务器即可。
例如，想免密登录 `myserver` 服务器，则将公钥中的内容复制到 `myserver` 中的 `~/.ssh/authorized_keys` 文件里即可。

也可以使用如下命令一键添加公钥：
```C++
ssh-copy-id myserver
```

#### 执行命令

命令格式；
``` C++
ssh user@hostname command
```

例如；
``` C++
ssh user@hostname ls -a
```

或者
``` C++
ssh user@hostname 'for ((i = 0; i < 10; i ++ )) do echo echo $i; done'    # ;表示换行
```