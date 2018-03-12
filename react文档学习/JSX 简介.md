# JSX 简介
```javascript
const element = <h1>Hello, world!</h1>
```
### 我们在编写 JSX 代码的外面扩上一个小括号，这样可以防止分号自动插入的 bug

### 可以在 if 或者 for 语句里使用 JSX，将它赋值给变量，当作参数传入，作为返回值都可以

## JSX 属性
可以使用字符串为值的属性
```javascript
const element = <div tabIndex="0"></div>
```
也可以使用大括号来定义以 JavaScript 表达式为值的属性
```javascript
const element = <img src={user.avatarUrl} />
```

## JSX 防注入攻击
React Dom 在渲染之前默认会过滤所有传入的值，所有的内容在渲染之前都被转换成了字符串。这样可以有效地防止 XSS 攻击。

## JSX 代表 Objects
Babel 转译器会把 JSX 转换成一个名为 React.createElement() 的方法调用。
```javascript
cosnt element = (
    <h1 className="greeting">
    Hello, world!
    </h1>
);
=>
const element = React.createElement(
    'h1',
    {className: 'greeting'},
    'Hello, world!'
);
const element = {
    type: 'h1',
    props: {
        className: 'greeting',
        children: 'Hello, world'
    }
};
```

# TODO
- React DOM 在渲染之前怎么把所有内容转换成字符串?
- React.createElement() 方法的执行流程是怎样的?