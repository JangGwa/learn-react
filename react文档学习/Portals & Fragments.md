# Portals
Portals 提供了一种很好的将子节点渲染到父组件以外的 DOM 节点的方式。

```javascript
ReactDOM.createPortal(child, container)
```
第一个参数（child）是任何可渲染的 React 子元素，例如一个元素，字符串或碎片。第二个参数（container）则是一个 DOM 元素

# Fragments
React 中一个常见模式是为一个组件返回多个元素。Fragments 可以让你聚合一个子元素列表，并且不在DOM中增加额外节点。
```javascript
render() {
  return (
    <>
      <ChildA />
      <ChildB />
      <ChildC />
    </>
  );
}
```