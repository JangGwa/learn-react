# 列表 & keys

## 渲染多个组件
```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);
```

## Keys
Keys可以在DOM中的某些元素被增加或删除的时候帮助React识别哪些元素发生了变化。因此你应当给数组中的每一个元素赋予一个确定的标识。

如果列表可以重新排序，我们不建议使用索引来进行排序，因为这会导致渲染变得很慢。

如果一个map()嵌套了太多层级，那可能就是你提取出组件的一个好时机。