## 0x6A $IO$ 框架

> $Commons-io$ 提供了一组有关 $IO$ 操作的小框架

### $FileUtils$ 类

- `public static void copyFile(File srcFile, File destFile)` 复制文件
- `public static void copyDirectory(File srcDir, File destDir)` 复制文件夹
- `public static void deleteDirectory(File directory)` 删除文件夹
- `public static String readFileToString(File file, String encoding)` 读数据
- `public static void writeStringToFile(File file, String data, String charname, boolean append)` 写数据

### $IOUtils$ 类

- `public static int copy(InputStream inputStream, OutputStream outputStream)` 复制文件
- `public static int copy(Reader reader, Writer writer)` 复制文件
- `public static void write(String data, OutputStream output, String charsetName)` 写数据