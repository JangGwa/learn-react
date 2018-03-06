## React 是一个 JavaScript 库，因此需要熟悉 JavaScript。建议我们去学习一下 ES6 的语法。

### 1.箭头函数

箭头函数不绑定自己的 this, arguments, super 或 new.target。这些函数表达式最试用于非方法函数，并且它们不能用作构造函数。

基础语法

```javascript
() => {函数声明}
```

高级语法

// 列表结构
```javascript
let f = ([a, b] =[1, 2], {x: c} = {x: a + b}) => a+ b + c;
f(); // 6
```

引入箭头函数有两个方面的作用：更简短的函数并且不绑定 this。

写一个通过 call 调用的例子, 由于 this 已经在词法层面完成了绑定，通过 call() 或 apply() 方法调用一个函数时，只是传入了参数而已，对 this 并没有什么影响。
```javascript
var adder = {
  base : 1,
    
  add : function(a) {
    var f = v => v + this.base;
    return f(a);
  },

  addThruCall: function(a) {
    var f = v => v + this.base;
    var b = {
      base : 2
    };
            
    return f.call(b, a);
  }
};

console.log(adder.add(1));         // 输出 2
console.log(adder.addThruCall(1)); // 仍然输出 2（而不是3 ——译者注）
```

### 2.类


