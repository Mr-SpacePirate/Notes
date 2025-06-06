## 0x54 $Vue$ 路由

- 安装（创建 Vue 项目时已选择）
- 定义路由，在文件 `router/index.js` 中

```js
const routes = [
    {
        path: '/emp',
        name: 'emp',
        component: () => import('../views/tlias/EmpView.vue'),
    },
    {
        path: '/dept',
        name: 'dept',
        component: () => import('../views/tlias/DeptView.vue'),
    },
    {
        path: '/',
        redirect: '/dept',  // 重定向
    },
]
```

### 组成

- `VueRouter`：路由器类，根据路由请求在路由视图中动态渲染选中的组件
- `<router-link>`：请求链接组件，浏览器会解析生产 `<a>`
- `<router-view>`：动态视图组件，用来渲染展示与路由器路径相对应的组件

