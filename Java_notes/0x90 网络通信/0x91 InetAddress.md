## 0x91 $InetAddress$

### 方法

- `public static InetAddress getLocalHost()` 获取本机 $IP$，会以一个 $inetAddress$ 的对象返回
- `public static InetAddress getByName(String host)` 根据 $ip$ 地址或者域名，返回一个 $inetAddress$ 对象
- `public String getHostName()` 获取该 $ip$ 地址对象对应的主机名
- `public String getHostAddress()` 获取该 $ip$ 地址对象中的 $ip$ 地址信息
- `public boolean isReachable(int timeout)` 在指定毫秒内，判断主机与该 $ip$ 对应的主机是否能连同
