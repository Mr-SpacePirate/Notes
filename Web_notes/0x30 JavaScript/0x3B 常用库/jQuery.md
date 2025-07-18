## jQuery

### 使用方式

- 在 `<head>` 元素中添加：
  ```js
  <script src="https://cdn.acwing.com/static/jquery/js/jquery-3.3.1.min.js"><script>
  ```
- 按[Query官网](https://jquery.com/download/)提示下载


----------


### 选择器

`$(selector)`，例如：

```js
$('div');
$('.big-div');
$('div > p');
```

`selector` 类似于CSS选择器。


----------


### 事件

#### 绑定事件

`$(selector).on(event, func)` 绑定事件，例如：

```js
$('div').on('click', function(e) {
    console.log("click div");
});
```

#### 删除事件

`$(selector).off(event, func)` 删除事件，例如：

```js
$('div').on('click', function(e) {
    console.log("click div");

    $('div').off('click');
});
```

#### 区分事件

当存在多个相同类型的事件触发函数时，可以通过 `click.name` 来区分，例如：

```js
$('div').on('click.first', function(e) {
    console.log("click first");

    $('div').off('click.first');
});
```

在事件触发的函数中的 `return false` 等价于同时执行：

- `e.stopPropagation()`：阻止事件向上传递
- `e.preventDefault()`：阻止事件的默认行为


----------


### 元素的隐藏、展现

- `$A.hide()`：隐藏，可以添加参数，表示消失时间
- `$A.show()`：展现，可以添加参数，表示出现时间
- `$A.fadeOut()`：慢慢消失，可以添加参数，表示消失时间
- `$A.fadeIn()`：慢慢出现，可以添加参数，表示出现时间


----------


### 元素的添加、删除

- `$('<div class="mydiv><span>Hello World</span></div>')`；构造一个 `jQuery` 对象
- `$A.append($B)`；将 `$B` 添加到 `$A` 的末尾
- `$A.prepend($B)`：将 `$B` 添加到 `$A` 的开头
- `$A.remove()`：删除元素 `$A`
- `$A.empty()`：清空元素 `$A` 的所有儿子


----------


### 对类的操作

- `$A.addClass(class_name)`：添加某个类
- `$A.removeClass(class_name)`：删除某个类
- `$A.hasClass(class_name)`：判断某个类是否存在


----------


### 对CSS的操作

- `$("div").css("background-color)`：获取某个CSS的属性
- `$("div").css("background-color", "yellow")`：设置某个CSS属性
- 同时设置多个CSS属性
```js
$('div').css({
    width: "200px",
    height: "200px",
    "background-color": "orange",
});
```


----------


### 对标签属性的操作

- `$('div').attr('id')`：获取属性
- `$('div').attr('id', 'ID')`：设置属性


----------


### 对HTML内容、文本的操作

- `$A.html()`：获取、修改HTML内容
- `$A.txt()`：获取、修改文本信息
- `$A.val()`：获取、修改文本的值


----------


### 查找

- `$(selector).parent(filter)`：查找父元素
- `$(selector).parents(filter)`：查找所有祖先元素
- `$(selector).children(filter)`：在所有子元素中查找
- `$(selector).find(filter)`：在所有后代元素中查找


----------


### `ajax`

GET方法：
```js
$.ajax({
    url: url,
    type: "GET",
    data: {
    },
    dataType: "json",
    success: function(resp) {

    },
});
```

POST方法：
```js
$.ajax({
    url: url,
    type: "POST",
    data: {
    },
    dataType: "json",
    success: function(resp) {

    },
});
```