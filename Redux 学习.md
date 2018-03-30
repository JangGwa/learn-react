# Redux 学习
Redux 是 JavaScript 状态容器，提供可预测化的状态管理。

## 你或许不需要使用 Redux
Redux 提供了一个权衡方案。它规定：
- 用简单的对象和数组来描述应用状态。
- 用简单的对象来描述应用中的状态变化。
- 用纯函数来描述应用中逻辑变化

无论是否使用

你有很好的理由使用 Redux 吗？
当你真正需要 redux 时再去使用它。

当然你可以借鉴 Redux 的思想，但却不需要 `npm install`
```javascript
import React, { Component } from 'react';

const counter = (state = { value: 0 }, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { value: state.value + 1 };
    case 'DECREMENT':
      return { value: state.value - 1 };
    default:
      return state;
  }
}

class Counter extends Component {
  state = counter(undefined, {});

  dispatch(action) {
    this.setState(prevState => counter(prevState, action));
  }

  increment = () => {
    this.dispatch({ type: 'INCREMENT' });
  };

  decrement = () => {
    this.dispatch({ type: 'DECREMENT' });
  };

  render() {
    return (
      <div>
        {this.state.value}
        <button onClick={this.increment}>+</button>
        <button onClick={this.decrement}>-</button>
      </div>
    )
  }
}
```


## Flux
Flux 最大的特点就是数据的单向流动
1.用户访问 View
2.View 发出用户的 Action
3.Dispatcher 收到 Action, 要求 Store 进行相应的更新
4.Store 更新后, 发出一个 Change 事件
5.View 接受到事件进行视图更新


## Redux
如果你以前使用 Flux，那么你只需要注意一个重要的区别。Redux 没有 Dispatcher 且不支持多个 store。相反，只有一个单一的 store 和一个根级的 reduce 函数（reducer）。
### Store
Store 就是保存数据的地方，你可以把它看成一个容器。整个应用只能有一个 Store。

Redux 提供createStore这个函数，用来生成 Store。
### Action
State 的变化，会导致 View 的变化。但是，用户接触不到 State，只能接触到 View。所以，State 的变化必须是 View 导致的。Action 就是 View 发出的通知，表示 State 应该要发生变化了。

### store.dispatch()
store.dispatch()是 View 发出 Action 的唯一方法。

### Reducer
Store 收到 Action 以后，必须给出一个新的 State，这样 View 才会发生变化。这种 State 的计算过程就叫做 Reducer。

### store.subscribe()
Store 允许使用store.subscribe方法设置监听函数，一旦 State 发生变化，就自动执行这个函数。


## Redux middleware
