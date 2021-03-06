## JS核心与浏览器机制

### 闭包特性

1. 函数嵌套函数
2. 函数内部可以引用外部的参数和变量
3.  参数和变量不会被垃圾回收机制回收

### 作用域

> 属于这个作用域的全部变量都可以在整个作用域的范围内使用及复用

隐藏内部实现（最小特权或者最小授权或者最小暴露原则：在软件设计中，应该最小限度地暴露必要内容）

​	将代码用一个函数包裹起来

1. 函数作用域

   使用函数包装代码使外部作用域无法访问包装函数内部

   ```js
   var a = 2;
   function foo() {
     var a = 3;
     console.log(a); // 3
   }
   
   foo(); // 3
   
   console.log(a); // 2
   ```

   缺点：

   1. 必须声明一个具名函数 `foo`，`foo` 本身污染了所在作用域
   2.  必须显式地调用函数才能运行其中的代码

   解决方案：

   ```js
   var a = 2;
   
   (function foo() {
     var a = 3;
     console.log(a);
   })();
   
   console.log(a);
   ```

   此时函数 `foo` 被自动调用，并且由一个函数声明变成函数表达式

   > 区分函数声明和表达式最简单的方法就是看 `function` 关键字出现的位置

   ​	函数声明出现在第一个词，反之是函数表达式

   函数声明（不可以省略函数名）

   ```js
   function foo() {}
   ```

   函数表达式

   ```js
   var foo = function () {}
   // 或者
   (function foo() {})
   // 第一个括号将函数变成表达式，第二个执行了函数
   ```

   **匿名和具名**

   匿名函数的缺点

   1. 在栈追踪中不会显示出有意义的函数名，使得调试困难
   2. 缺少对函数描述的函数名
   3. 当函数需要引用时只能使用已经过期的 `arguments.callee` 引用

   **立即执行函数表达式** IIFE (Immediately Invoked Function Expression)

   写法： 

   ```js
   (function (){})()
   // 或者
   (function(){}())
   ```

2. 块作用域

   

### 垃圾回收机制

- 标记清除
- 引用计数（IE）

### 内存泄露



### 事件代理

### React

#### this.setState()  (两个特性 原理 )

不能直接更改state属性，异步

原理：`setState()`方法通过一个队列机制实现`state`更新，当执行`setState()`的时候，会将需要更新的`state`合并之后放入状态队列，而不会立即更新`this.state`(可以和浏览器的事件队列类比)。如果我们不使用`setState`而是使用`this.state.key`来修改，将不会触发组件的`re-render`。如果将`this.state`赋值给一个新的对象引用，那么其他不在对象上的`state`将不会被放入状态队列中，当下次调用`setState()`并对状态队列进行合并时，直接造成了`state`丢失。

#### 核心思想

1. 声明式渲染
   1. 命令式 关注如何做（how）
   2. 声明式 关注做什么（what）
2. 基于组件
   1. 模板+数据=渲染出来的组件



1. 组件
   1. 能够像原生的HTML标签一样输出特定的界面元素，并且也能包括一些元素相关逻辑功能的代码
   2. 复用性
2. JSX
3. Props&State
4. 组件API
   1. react的声明周期等

