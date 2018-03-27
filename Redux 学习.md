# Redux 学习
Redux 是 JavaScript 状态容器，提供可预测化的状态管理。

## 你或许不需要使用 Redux
Redux 提供了一个权衡方案。它规定：
- 用简单的对象和数组来描述应用状态。
- 用简单的对象来描述应用中的状态变化。
- 用纯函数来描述应用中逻辑变化

无论是否使用 React，这些规定都不是创建一个应用所必须遵循的。事实上，这些都非常严格的约束，在把它加入到你的应用之前，你应该慎重考虑。

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
