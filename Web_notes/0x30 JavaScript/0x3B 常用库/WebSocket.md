## WebSocket

与服务器建立全双工连接。

常用API：

- `new WebSocket('ws://localhost:8080);`：建立ws连接
- `send()`向服务器端发送一个字符串。一般用JSON将传入的对象序列化为字符串。
- `onopen()`：类似于 `onclick`，当连接建立时除法。
- `onmessage`：当服务器端收到消息时触发。
- `close()`：关闭连接。
- `onclose()`：当连接关闭后触发。