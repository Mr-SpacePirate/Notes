## 0x72 $XML$ 文件

- 可扩展标记语言
- 本质是一种数据的格式，可以用来存储复杂的数据结构，和数据关系。
- **应用场景**：经常用来做为系统的配置文件；或者作为一种特殊的数据结构，在网络中进行传输。

#### 特点

1. $XML$ 中 “<标签名>” 称为一个标签活一个元素，一般是成对出现的。
2. $XML$ 中的标签名可以自己定义（可扩展），但必须要正确的嵌套
3. $XML$ 中只能有一个根标签
4. $XML$ 中的标签可以有属性
5. 如果一个文件中放置的是 $XML$ 格式的数据，这个文件就是 $XML$ 文件，后缀一般要写成 $.xml$

### $Dom4j$ 解析 $XML$ - 得到 $Document$ 对象

#### $SAXReader$

- `public SAXReader()` 构建 $Dom4j$ 的解析器对象
- `public Document read(String url)` 把 $XML$ 文件读成 $Document$ 对象
- `public Document read(InputStream is)` 通过字节输入流读取 $XML$ 文件

#### $Document$

- `Element getRootElement()` 获得根元素对象

#### $Element$

- `public String getName()` 得到元素名字
- `public List<Element> elements()` 得到当前元素下所有子元素
- `public List<Element> elements(String name)` 得到当前元素下指定名字的子元素返回集合
- `public Element element(String name)` 得到当前元素下指定名字的子元素，如果有很多名字相同的，返回第一个
- `public String attributeValue(String name)` 通过属性名直接得到属性值
- `public String elementText(子元素名)` 得到指定名称的子元素的文本
- `public String getText()` 得到文本

```java
public class Dom4JTest {
    public static void main(String[] args) throws Exception {
        // 1. 创建一个Dom4J框架提供解析器对象
        SAXReader saxReader = new SAXReader();

        // 2. 使用saxReader对象吧需要解析的XML文件读成一个Document对象
        Document document = saxReader.read("文件路径");

        // 3. 从文件得到根元素对象
        Element root = document.getRootElement();
        
        // 4. 对元素操作
        // 获取元素集合
        List<Element> elements = root.elements();

        // 获取单个元素
        Element user = root.element("user");

        // 获取某个元素的文本信息
        System.out.println(user.elementText("name"));

        // 获取某个元素的属性信息
        System.out.println(user.attributeValue("id"));
    }
}
```