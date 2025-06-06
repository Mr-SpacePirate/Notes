## 0x62 $File$

### 创建 $File$ 类的对象

- `public File(String pathname)` 根据文件路径创建文件对象
- `public File(String parent, String child)` 根据父路径和子路径名字创建文件对象
- `public File(File parent, String child)` 根据父路径对应文件对象和子路径名字创建文件对象

#### 注意

1. $File$ 对象既可以代表元素、也可以代表文件夹
2. $File$ 封装的对象仅仅是一个路径名，这个路径可以存在的，也可以是不存在的。

### 方法

#### 判断文件类型、获取文件信息

- `public boolean exists()` 判断当前文件对象，对应的文件路径是否存在，存在返回 $true$
- `public boolean isFile()` 判断当前文件对象指代的是否是文件，是文件返回 $true$
- `public boolean isDirectory()` 判断当前文件对象指代的是否是文件夹，是文件夹返回 $true$
- `public String getName()` 获取文件的名称（包括后缀）
- `public long length()` 获取文件的大小，返回字节个数
- `public long lastModified()` 获取文件的最后修改时间
- `public String getPath()` 获取创建文件对象时，使用的路径
- `public String getAbsolutePath()` 获取绝对路径

#### 创建文件、删除文件

- `public boolean createNewFile()` 创建一个新文件（文件内容为空），创建成功后返回 $true$
- `public boolean mkdir()` 创建文件夹（只能创建一级文件夹）
- `public boolean mkdirs()` 创建文件夹（可以创建多级文件夹）
- `public boolean delete()` 删除文件，或者空文件（不能删除非空文件夹）

#### 遍历文件夹

- `public String[] list()` 获取当前目录下所有的“**一级文件名称**”到一个字符串数组中去返回
- `public File[] listFiles()` 获取当前目录下所有的“**一级文件对象**” 到一个文件对象数组中去返回

##### $listFiles$ 注意事项

1. 当主调是文件，或者路径不存在时，返回 $null$
2. 当主调是空文件夹时，返回一个长度为0的数组
3. 当主调是一个有内容的文件夹时，将里面所有一级文件和文件夹的路径放在 $File$ 数组中返回
4. 当主调是一个文件夹，且里面有隐藏文件时，将里面所有文件和文件夹的路径放在 $File$ 数组中返回，包含隐藏文件
5. 当主调是一个文件夹，但是没有权限访问该文件夹时，返回 $null$

#### 