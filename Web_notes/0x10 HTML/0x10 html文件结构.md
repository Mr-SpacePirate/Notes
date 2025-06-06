## 0x10 html文件结构

[MDN官方文档](https://developer.mozilla.org/zh-CN/)

### 文档结构

$html$ 的所有标签为树形结构

``` html
<!DOCTYPE html>
<html lang="zh-CN">

<head>
    <!-- 字符集为UTF-8 -->
    <meta charset="UTF-8">
    <meta name="keyword" content="Web应用课">           <!-- 搜索关键字 -->
    <meta name="description" content="欢迎学习Web">     <!-- 标题下面的简介 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="icon" href="/images/icon.png">           <!-- 标题logo -->
    <title>Web应用课</title>
</head>

<body>
    <h1>第一讲</h1>
</body>

</html>
```


----------


#### `<!DOCTYPE html>`

文档类型。混沌初分，HTML 尚在襁褓（大约是 1991/92 年）之时，DOCTYPE 用来链接一些 HTML 编写守则，比如自动查错之类。DOCTYPE 在当今作用有限，仅用于保证文档正常读取。现在知道这些就足够了。


----------


#### `<html></html>`

`<html>` 元素。该元素包含整个页面的内容，也称作根元素。


----------


#### `<head></head>`

`head` 元素 规定文档相关的配置信息（元数据），包括文档的标题，引用的文档样式和脚本等。


----------


#### `<title></title>`

`<title>` 元素。该元素设置页面的标题，显示在浏览器标签页上，也作为收藏网页的描述文字。


----------


#### `<body></body>`

`<body>` 元素。该元素包含期望让用户在访问页面时看到的内容，包括文本、图像、视频、游戏、可播放的音轨或其他内容。


----------


#### `<meta>`

HTML `<meta>` 元素表示那些不能由其它 HTML 元相关（meta-related）元素（(`<base>`、`<link>`, `<script>`、`<style>` 或 `<title>`）之一表示的任何元数据信息。

常见属性：

- `charset`：这个属性声明了文档的字符编码。如果使用了这个属性，其值必须是与 ASCII 大小写无关（ASCII case-insensitive）的”utf-8”。
- `name`：name 和 content 属性可以一起使用，以名 - 值对的方式给文档提供元数据，其中 name 作为元数据的名称，content 作为元数据的值。

```html
<meta name="keyword" content="Web应用课">           <!-- 搜索关键字 -->
<meta name="description" content="欢迎学习Web">     <!-- 标题下面的简介 -->
```


----------


#### `icon`

标题logo

```html
<link rel="icon" href="/images/icon.png">           <!-- 标题logo -->
```


----------


#### 注释

```html
<!-- 这是一行注释 -->
```