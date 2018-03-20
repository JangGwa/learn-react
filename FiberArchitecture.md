# React Fiber Architecture
React Fiber 的目标是增强 React 在动画、布局和手势等各个领域的适应性。它的最重要的特性是 incremental rendering（增量渲染）：它能够将渲染工作拆分成多块并将这些任务块分散到多个帧执行。
- 暂停任务并能够在之后恢复任务。
- 为不同的任务设置不同的优先级。
- 重新使用之前完成的任务。
- 如果不在需要则可以终止一个任务。

为了做到这些事，我们首先需要一个方式来拆分这些任务为一个个任务单元。从某种意义上来说，这些任务单元就是 fiber。一个 fiber 代表了一个 任务单元.

## fiber 的结构
具体来说，一个 fiber 是一个包含了组件及其输入输出的 JavaScript 对象。

### type and key
type 和 key 在 fiber 中的用途与其在 React 元素中的用途相同。（实际上，当从一个元素创建一个 fiber，这两个字段是直接拷贝过来的。）

fiber 的 type 描述了它对应的组件。对于复合组件，type 是函数或者组件类本身。对于宿主环境的组件（div、span 等），type 是一个字符串。

从概念上来讲，type 是执行过程被栈帧跟踪记录的函数（就好像 v = f(d)）。

key 则与 type 一起，被用来在协调期间决定是否 fiber 可以被重新使用。

### child and sibling
这些字段指向了其他 fibers，它们描述了 fiber 构成的递归结构的树。

### return
程序处理完当前 fiber 后应该返回 fiber。返回的 fiber 在概念上等同于返回栈帧的地址。

如果 fiber 有不同的子 fibers，每个孩子 fiber 是由它的父亲返回的。所以在我们之前章节的例子中，孩子 fiber Child1 和 Child2 是由 Parent 返回的。

### pendingProps and memoizedProps
从概念上讲，props 是函数的参数。pendingProps 是 fiber 执行开始时的属性集合，memoizedProps 则是 fiber 执行结束时的属性集合。

当新到来的 pendingProps 等于 memoizedProps，意味着 fiber 之前的输出可以被重复使用，防止不必要的工作。

### pendingWorkPriority
一个用来表示 fiber 代表的任务优先级的数字。ReactPriorityLevel 模块列出了不同的优先级以及它们所代表的含义。
除了优先级为 0 的 NoWork 以外，一个更大的数字表示更低的优先级