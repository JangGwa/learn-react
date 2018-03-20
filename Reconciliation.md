# Reconciliation
React 用来比较两棵树的算法，它决定树中的哪一部分需要被改变。

Reconciliation 是被大家广泛知晓的 "virtual DOM" 背后的算法。更加高层的描述如下：当渲染一个 React 应用，会有一棵节点树生成并保存在内存中。这棵树随后被刷新到渲染环境。举例来说，我们以浏览器环境的应用为例，它会转换为一个 DOM 操作的集合。当应用更新的时候（通常是通过 setState 触发），一棵新的树生成。新树将会和先前的树作比较，并计算出更新应用所需要的操作。

## Reconciliation versus rendering
DOM 仅仅是 React 支持的一个渲染环境，通过 React Native 它还可以支持原生 iOS 和 Android 页面的渲染。（这也是为什么 “Virtual DOM” 是一个错误的称呼。）

React 之所以能够支持如此多的渲染环境，主要是因为它被设计为 reconciliation 和渲染两个过程分离。协调器做了计算两棵树差异的工作；渲染器则会使用计算得到的信息来更新实际的应用。

这样的分离做法意味着 React DOM 和 React Native 可以使用各自的渲染器，并且共享 React 核心库提供的相同的协调器。

Fiber 重新实现了协调器。这原则上来说不影响渲染器，虽然渲染器可能将需要改变去支持新的架构，来获得新架构所带来的优势。