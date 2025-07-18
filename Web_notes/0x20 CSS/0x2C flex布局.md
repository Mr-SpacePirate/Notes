## 0x2C flex布局

`flex` CSS简写属性设置了弹性项目如何增大或缩小以适应其弹性容器中可用的空间。

### `flex-direction`

CSS `flex-direction` 属性指定了内部元素是如何在 $flex$ 容器中布局的，定义了主轴的方向(正方向或反方向)。

- 取值：
  - `row`：$flex$ 容器的主轴被定义为与文本方向相同。 主轴起点和主轴终点与内容方向相同。
  - `row-reverse`：表现和 $row$ 相同，但是置换了主轴起点和主轴终点。
  - `column`：flex容器的主轴和块轴相同。主轴起点与主轴终点和书写模式的前后点相同
  - `column-reverse`：表现和 $column$ 相同，但是置换了主轴起点和主轴终点


----------


### `flex-wrap`

CSS 的 `flex-wrap` 属性指定 $flex$ 元素单行显示还是多行显示。如果允许换行，这个属性允许你控制行的堆叠方向。

- 取值：
  - `nowrap`：默认值。不换行。
  - `wrap`：换行，第一行在上方。
  - `wrap-reverse`：换行，第一行在下方。


----------


### `flex-flow`

CSS `flex-flow` 属性是 `flex-direction` 和 `flex-wrap` 的简写。默认值为：`row nowrap`。


----------


### `justify-content`

CSS `justify-content` 属性定义了浏览器之间，如何分配顺着弹性容器主轴(或者网格行轴) 的元素之间及其周围的空间。

- 取值：
  - `flex-start`：默认值。左对齐。
  - `flex-end`：右对齐。
  - `space-between`：左右两段对齐。
  - `space-around`：在每行上均匀分配弹性元素。相邻元素间距离相同。每行第一个元素到行首的距离和每行最后一个元素到行尾的距离将会是相邻元素之间距离的一半。
  - `space-evenly`：flex项都沿着主轴均匀分布在指定的对齐容器中。相邻 $flex$ 项之间的间距，主轴起始位置到第一个 $flex$ 项的间距，主轴结束位置到最后一个 $flex$ 项的间距，都完全一样。


----------


### `align-items`

CSS `align-items` 属性将所有直接子节点上的 `align-self` 值设置为一个组。`align-self` 属性设置项目在其包含块中在交叉轴方向上的对齐方式。

- 取值：
  - `flex-start`：元素向主轴起点对齐。
  - `flex-end`：元素向主轴终点对齐。
  - `center`：元素在侧轴居中。
  - `stretch`：弹性元素被在侧轴方向被拉伸到与容器相同的高度或宽度。


----------


### `align-content`

CSS 的 `align-content` 属性设置了浏览器如何沿着弹性盒子布局的纵轴和网格布局的主轴在内容项之间和周围分配空间。

- 取值：
  - `flex-start`：所有行从垂直轴起点开始填充。第一行的垂直轴起点边和容器的垂直轴起点边对齐。接下来的每一行紧跟前一行。
  - `flex-end`：所有行从垂直轴末尾开始填充。最后一行的垂直轴终点和容器的垂直轴终点对齐。同时所有后续行与前一个对齐。
  - `center`：所有行朝向容器的中心填充。每行互相紧挨，相对于容器居中对齐。容器的垂直轴起点边和第一行的距离相等于容器的垂直轴终点边和最后一行的距离。
  - `stretch`：拉伸所有行来填满剩余空间。剩余空间平均地分配给每一行。


----------


### `order`

定义 `flex` 项目的顺序，值越小越靠前。


----------


### `flex-grow`

CSS 属性 `flex-grow` CSS 设置 $flex$ 项主尺寸 的 $flex$ 增长系数。

负值无效，默认为 0。


----------


### `flex-shrink`

CSS `flex-shrink` 属性指定了 $flex$ 元素的收缩规则。$flex$ 元素仅在默认宽度之和大于容器的时候才会发生收缩，其收缩的大小是依据 `flex-shrink` 的值。

负值无效，默认为1。


----------


### `flex-basis`

CSS 属性 `flex-basis` 指定了 $flex$ 元素在主轴方向上的初始大小。

- 取值：
  - `width` 值可以是 `<length>`; 该值也可以是一个相对于其父弹性盒容器主轴尺寸的百分数 。负值是不被允许的。默认为 `auto`。


----------


### `flex`

`flex-grow`、`flex-shrink`、`flex-basis`的缩写。

- 常用取值：
  - `auto`：`flex: 1 1 auto`
  - `none`：`flex: 0 0 auto`