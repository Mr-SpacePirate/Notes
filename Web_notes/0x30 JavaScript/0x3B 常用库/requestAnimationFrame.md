## requestAnimationFrame

### `requestAnimationFrame(func)`

该函数会在下次浏览器刷新页面之前执行一次，通常会用递归写法使其每秒执行60次 `func` 函数。调用时会传入一个参数，表示函数执行的时间戳，单位为毫秒。

例如：
```js
let step = (timestamp) => { // 每帧将div的宽度增加1像素
    let div = document.querySelector('div');
    div.style.width = div.clientWidth + 1 + 'px';
    requestAnimationFrame(step);
}

requestAnimationFrame(step);
```

与 `setTimeout` 和 `setInterval` 的区别：

- `requestAnimationFrame` 渲染动画的效果更好，性能更加。该函数可以保证每两次调用之间的时间间隔相同，但 `setTimeout` 与 `setInterval` 不能保证这点。`setTimeout` 两次调用之间的间隔包含回调函数的执行时间；`setInterval` 只能保证按固定时间间隔将回调函数压入栈中，但具体的执行时间间隔仍然受回调函数的执行事件影响。
- 当页面在后台时，因为页面不再渲染因此 `requestAnimationFrame` 不在执行。但 `setTimeout` 与 `setInterval` 函数会继续执行。