# State & 生命周期

## 将函数转换为类
使用类就允许我们使用其它特性，例如局部状态、生命周期钩子。

## 正确地使用状态
关于 `setState()`这里有三件事情需要知道

### 不要直接更新状态
this.state.comment = 'Hello'; // wrong
构造函数是唯一能够初始化 `this.state`的地方。

### 状态更新可能是异步的
React 可以将多个 `setState()`调用合并成一个调用来提高性能。
因为 `this.props` 和 `this.state` 可能是异步更新的，你不应该依靠它们的值来计算下一个状态。
```javascript
// wrong
this.setState({
  counter: this.state.counter + this.props.increment
})
```

```javascript
// true
this.setState((prevState, props) => {
  counter: prevState.counter + props.increment
})
```

### 状态更新合并
可以调用`setState()`独立更新它们

## 数据自顶向下流动
父组件或子组件都不能知道某个组件是有状态还是无状态，并且它们不应该关心某组件是被定义为一个函数还是一个类。
任何状态始终由某些特定组件所有，并且从该状态导出的任何数据或 UI 只能影响树中下方的组件。

## TODO
1.为什么 this.state.comment = 'hello' 不行？
2.多个 `setState()`调用合并成一个调用如何提高性能的？
3.setState() 的流程是怎样的？