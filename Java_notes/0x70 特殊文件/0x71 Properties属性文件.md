## 0x71 $Properties$ 属性文件

#### 特点

1. 内容只能是键值对
2. 键不能重复
3. 文件后缀一般是 $.properties$ 结尾

#### 作用

- 用来存储一些有关系的键值对数据

### $Properties$

![](../assets/0x71%20Properties.png)

- $Properties$ 是一个 $Map$ 集合（键值对集合），但是我们一般不会当集合使用
- **核心作用**：$Properties$ 是用来代表属性文件的，通过 $Properties$ 可以读写属性文件里的内容

#### 构造器

- `public Properties()` 用于构建 $Properties$ 集合对象（空容器）

#### 读入到内存的方法

- `public void load(InputStream is)` 通过字节输入流，读取属性文件里的键值对数据
- `public void load(Reader reader)` 通过字符输入流，读取属性文件里的键值对数据
- `public String getProperty(String key)` 根据进获取值（其实就是 $get$ 方法的效果）
- `public Set<String> stringPropertyNames()` 获取全部键的集合（其实就是 $keySet$ 方法的效果）

#### 写出到文件的方法

- `public Object setProperty(String key, String value)` 保存键值对数据到 $Properties$ 对象中
- `public void store(OutputStream os, String comments)` 把键值对数据，通过字节输出流写出到属性文件里去
- `public void store(Writer w, String comments)` 把键值对数据， 通过字符输出流写出到属性文件里去