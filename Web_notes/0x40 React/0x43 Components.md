## 0x43 Components

### 创建项目

#### 创建项目 `box-app`

```powershell
create-react-app box-app
cd box-app
npm start
```

#### 安装 `bootstrap` 库

```powershell
npm i bootstrap
```

#### `bootstrap` 的引入方式

```js
<!-- ------------------------------ index.js ------------------------------- -->
import 'bootstrap/dist/css/bootstrap.css';
```


----------


### 创建Component

在文件夹 `src` 中创建文件夹 `components`，在文件夹 `components` 中创建文件 `box.jsx`。

```jsx
<!-- ------------------------------- box.jsx ------------------------------- -->
// imrc 快捷键
import React, { Component } from 'react';

// cc 快捷键
class Box extends Component {
    state = {  }        // 局部变量，成员变量
    render() {          // 返回Component最终渲染的结果
        return ();
    }
}
 
export default Box;

<!-- ------------------------------ index.js ------------------------------- -->
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import 'bootstrap/dist/css/bootstrap.css';
import Box from './components/box';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <Box />
  </React.StrictMode>
);
```


----------


### 创建按钮

当子节点数量大于1时，可以用 `<div>` 或 `<React.Fragment>` 将其括起来。

```jsx
import React, { Component } from 'react';

class Box extends Component {
    state = {  } 
    render() { 
        return (
            <Reaact.Fragment>
                <h1>Hello World</h1>
                <button>left</button>
                <button>right</button>
            </Reaact.Fragment>
        );
    }
}
 
export default Box;
```

----------


### 内嵌表达式

JSX中使用 `{}` 嵌入表达式。

```jsx
import React, { Component } from 'react';

class Box extends Component {
    state = { 
        x: 1,
    };

    render() { 
        return (
            <React.Fragment>
                <div>{this.toString()}</div>
            </React.Fragment>
        );
    }

    toString() {
        // return `x: ${this.state.x}`;
        const x = this.state.x;
        return `x: ${x}`;
    }
}
 
export default Box;
```


----------


### 设置属性

- `class -> className`
- CSS属性：`background-color -> backgroundColor`，其它属性类似

```jsx
import React, { Component } from 'react';

class Box extends Component {
    state = { 
        x: 1,
    };

    styles = {
        backgroundColor: "lightblue",
        width: "50px",
        height: "50px",
    };

    render() { 
        return (
            <React.Fragment>
                <div style={this.styles}>{this.toString()}</div>
                <button className='btn btn-primary m-2'>left</button>
                <button className='btn btn-success m-2'>right</button>
            </React.Fragment>
        );
    }

    toString() {
        return `x: ${this.state.x}`;
    }
}
 
export default Box;
```


----------


### 数据驱动改变Style

```jsx
import React, { Component } from 'react';

class Box extends Component {
    state = { 
        x: 1,
    };

    render() { 
        return (
            <React.Fragment>
                <div style={this.getStyles()}>{this.toString()}</div>
                <button className='btn btn-primary m-2'>left</button>
                <button className='btn btn-success m-2'>right</button>
            </React.Fragment>
        );
    }

    toString() {
        return `x: ${this.state.x}`;
    }

    getStyles() {
        let styles = {
            backgroundColor: "lightblue",
            width: "50px",
            height: "50px",
        }
    
        if (this.state.x === 0) {
            styles.backgroundColor = "orange";
        }
    
        return styles;
    }
}
 
export default Box;
```


----------


### 渲染列表

- 使用map函数
- 每个元素需要具有唯一的key属性，用来帮助React快速找到被修改的DOM元素。

```jsx
import React, { Component } from 'react';

class Box extends Component {
    state = { 
        colors = ['red', 'green', 'blue'];
    };

    render() { 
        return (
            <React.Fragment>
                {this.state.colors.map(color => {
                    <div key={color}></div>
                })}
            </React.Fragment>
        );
    }
}
 
export default Box;
```


----------


### Conditional Rendering

利用逻辑表达式的短路原则。

- 与表达式中 `expr1 && expr2`，当 `expr1` 为假时返回 `expr1` 的值，否则返回 `expr2` 的值
- 或表达式中 `expr1 || expr2`，当 `expr1` 为真时返回 `expr1` 的值，否则返回 `expr2` 的值


----------


### 绑定事件

注意妥善处理好绑定事件函数的 `this`


----------


### 修改state

- 需要使用 `this.setState()` 函数
- 每次调用 `this.setState()` 函数后，会重新调用 `this.render()` 函数，用来修改虚拟DOM树。React只会修改不同步的实际DOM树节点。

```jsx
import React, { Component } from 'react';

class Box extends Component {
    state = { 
        x: 1,
    };

    // 必须绑定this
    handleClickLeft = () => {
        this.setState({
            x: this.state.x - 1,
        });
    }

    handleClickRight = () => {
        this.setState({
            x: this.state.x + 1,
        });
    }

    render() { 
        return (
            <React.Fragment>
                <div style={this.getStyles()}>{this.toString()}</div>
                <button onClick={this.handleClickLeft} className='btn btn-primary m-2'>left</button>
                <button onClick={this.handleClickRight} className='btn btn-success m-2'>right</button>
            </React.Fragment>
        );
    }

    toString() {
        return `x: ${this.state.x}`;
    }

    getStyles() {
        let styles = {
            backgroundColor: "lightblue",
            width: "50px",
            height: "50px",
        }
    
        if (this.state.x === 0) {
            styles.backgroundColor = "orange";
        }
    
        return styles;
    }
}
 
export default Box;
```

----------


### 给事件函数添加参数

```jsx
import React, { Component } from 'react';

class Box extends Component {
    state = { 
        x: 1,
    };

    // 必须绑定this
    handleClickLeft = (step) => {
        this.setState({
            x: this.state.x - step,
        });
    }

    handleClickRight = (step) => {
        this.setState({
            x: this.state.x + step,
        });
    }

    render() { 
        return (
            <React.Fragment>
                <div style={this.getStyles()}>{this.toString()}</div>
                <button onClick={ () => this.handleClickLeft(10) } className='btn btn-primary m-2'>left</button>
                <button onClick={ () => this.handleClickRight(10) } className='btn btn-success m-2'>right</button>
            </React.Fragment>
        );
    }

    toString() {
        return `x: ${this.state.x}`;
    }

    getStyles() {
        let styles = {
            backgroundColor: "lightblue",
            width: "50px",
            height: "50px",

            marginLeft: this.state.x,   // 移动
        }
    
        if (this.state.x === 0) {
            styles.backgroundColor = "orange";
        }
    
        return styles;
    }
}
 
export default Box;
```