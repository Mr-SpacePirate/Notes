## setTimeout 与 setInterval

### `setTimeout(func, delay)`

`delay` 毫秒后，执行函数 `func()`


----------


### `clearTimeout()`

关闭定时器，例如：

```js
let timeout_id = setTimeout(() => {
    console.log("Hello World!");
}, 2000);   // 2秒后在控制台输出"Hello World!"

clearTimeout(timeout_id);   // 清楚定时器
```


----------


### `setInterval(func, delay)`

每隔 `delay` 毫秒，执行一次函数 `func()`。
第一次在第 `delay` 毫秒后执行。


----------


### `clearInterval()`

关闭周期执行的函数，例如：

```js
let interval_id = setInterval(() => {
    console.log("Hello World!");
}, 2000);   // 每隔2秒，在控制台输出一次"Hello World!"

clearInerval(interval_id);  // 清除周期执行函数
```