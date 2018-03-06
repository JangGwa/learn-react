## React 是一个 JavaScript 库，因此需要熟悉 JavaScript。建议我们去学习一下 ES6 的语法。

### 1.箭头函数

箭头函数不绑定自己的 this, arguments, super 或 new.target。这些函数表达式最试用于非方法函数，并且它们不能用作构造函数。

基础语法

() => {函数声明}

高级语法

// 列表结构
let f = ([a, b] =[1, 2], {x: c} = {x: a + b}) => a+ b + c;
f(); // 6

引入箭头函数有两个方面的作用：更简短的函数并且不绑定 this。


