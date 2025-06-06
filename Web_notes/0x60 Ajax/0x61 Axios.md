## 0x61 $Axios$

### Vue 项目中使用 Axious

- 在项目目录下安装 axios：`npm install axios`
- 需要使用axios时，导入 axios：`import axios from axios;`

- 在钩子方法中发送异步请求，获取数据

  ```vue
  mounted () {
    axios.get("http://...").then((result) => {
        this.tableData = result.data.data;
    });
  }
  ```
  
- 使用 Axios 发送请求，并获取响应结果

  ```js
  axios({
    method: "get", // 取数据请求
    url: "http://...",
  }).then((result) => {
    console.log(result.data);
  });

  axios({
    method: "post", // 增删改
    url: "http://...",
    data: "id = 1",
  }).then((result) => {
    console.log(result.data);
  });
  ```
