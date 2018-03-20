# 组件 & Props
组件可以将 UI 切分成一些独立的、可复用的部件，这样你就只需专注于构建每一个单独的部件。
组件从概念上看就像是函数，它可以接收任意的输入值(props),并返回一个需要在页面上展示的 React 元素。

## 函数定义组件/类定义组件
定义一个组件最简单的方式是使用 JavaScript 函数
```javascript
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
}
```
类定义组件
```javascript
class Welcome extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}</h1>
    }
}
```

## 组件渲染
```javascript
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>
}
const element = <Welcome name="Sara" />;
ReactDOM.render(
    element,
    document.getElementById('root')
);
```
这个例子中发生了什么
1.我们对<Welcome name="Sara" />元素调用了 `ReactDOM.render()` 方法。
2.React 将 `{name: 'Sara'}`作为 props 传入并调用 Welcome 组件。
3.Welcome 组件将 `<h1>Hello, Sara</h1>` 元素作为结果返回。
4.React DOM 将 DOM 更新为 `<h1>Hello, Sara</h1>`。

## 组合组件
组件可以在它的输出中引用其它组件，这就可以让我们用同一组件来抽象出任意层次的细节。

##提取组件
可以将组件分为更小的组件

UI中有一部分重复使用了好几次,或者其自身就足够复杂,类似这些都是抽象成一个可复用组件的绝佳选择

## Props 的只读性

所有的 React 组件必须像纯函数那样使用它们的 props。