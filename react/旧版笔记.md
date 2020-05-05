# React
> React 是facebook 开源的一套框架
- 基于JSX语法糖实现的
- 并不算是MVC的架构，可以理解为是 MVC的V层
- 使用的虚拟DOM，是轻量的js对象，只保留了原生dom的一些常用的属性和方法
- 单项数据流


# 函数式编程
> 数据进来，然后通过函数里面的算法或者逻辑处理，返回给页面，使用jsx语法糖

# JSX
> 一种特殊的js语法糖,将html和css写入js页面中 **JSX=JS+HTML**

### 只有一个根节点

### 不能在标签中加注释
> 在jsx语法当中，html标签是一个对象，是一个数据结构，而不是真实的DOM节点，也不是字符串，所以标签当中不能添加注释

``` jsx
var html = 
    <div>
        <!--不能添加注释，这里会报错-->
        <h1>Tom</h1>
        <h1>Lucy</h2>
    </div>
```

# 声明式渲染
> 命令式编程：重点在机器如何去做，不管你想要什么，机器都会遵循你的命令去实现，比如for循环遍历，把遍历的过程呈现出来
> 声明时编程：重点在与你要的是什么，比如map遍历，把遍历的结果呈现出来

# react声明式渲染
> react可以局部渲染，且值渲染改变了的数据
- react高效的局部渲染意味着，开发者只需要维护可变的数据 state,state值用于存放可变的数据
- 通过setState告诉react什么数据变了，React会自动更新数据改变部分的视图

# 单项数据流
数据从父组件传递给子组件，只能单向绑定。（通过props）子组件内部不能直接修改父组件传递过来的数据。
如果父级的某个props改变了，React会重新渲染所有的子节点

# props
> props是property的缩写，可以理解为HTML标签的attribute
- props是只用于整个组件树中传递数据和配置
- props是只读的，不可以使用 this.props直接修改props,但子组件访问props时使用this.props

# state
> 每个组件都有属于自己的state
state只存在于组件内部，只能从当前组件调用this.setState修改state值

# 组件类型
### 普通组件
有自己的逻辑与状态

### 无状态组件
没有状态，通过传入props渲染，复用性高，比如按钮、标签、输入框等，基本就是属性props加上一个渲染函数（render），

### HOC高阶组件 
是一个返回组件的组件，或者说是一个会返回组件的函数

### 纯组件
只在意数据的变化


# 组件通信
> 父传子，子传父
### 父组件向子组件通信
react数据流动是单项的，父组件通过props向子组件传递需要的信息

### 同级组件通信
- 状态提升到同一个父组件，子组件先向父组件通信，父组件在通过props向其他子组件通信
- 使用context，context是一个全局变量，父级创建context，将数据挂载在context树上，子组件可以从context数上获取数据

# 生命周期
- 装载过程：把组件第一次在DOM树中渲染的过程 
- 更新过程：当组件被重新渲染的过程 
- 卸载过程：组件从DOM中删除的过程
### 装载过程
- constructor 构造函数，接收参数 props，context，主要用于初始化state，绑定函数的this环境
- componentWillMount（模块渲染前） 在渲染前使用，既可以在服务端被调用，也可以再浏览器端被调用
 - 组件刚经历了 constructor ，初始化完数据
 - 组件还未进入render，组件还未渲染完成，dom也还未渲染
 - ajax请求不推荐写在willmount里
  - 虽然正常情况下并不会出错，但是如果ajax请求过来的数是空的，那么会影响页面的渲染，可能看到的就是空白
- render 渲染真实dom，不做实际的渲染动作，只是返回一个jsx结构的描述，最终有react来操作渲染过程
- componentDidMount（模块渲染后）这时候组件已经被装载到DOM树上了，可以获取渲染出来的任何DOM 只能在浏览器端被调用
- 因为装载是一个创建组件并放在DOM树上的过程，服务器是无法产生DOM树的，只是一段字符串而已，所以无法在服务器端执行

### 更新过程
> 当props或者state被修改的时候，就会触发组件的更新过程
- componentWillReceiveProps(nextProps)（模块将接受新的数据）：只要父组件的render函数被调用，在render函数里被渲染的子组件，都会经历更新的过程，
  - 不管父组件传给子组件的props有没有改变，都会触发componentWillReciveProps
  - 注意 this.setState 触发的更新，是不会调用这个方法的
- shouldComponentUpdate(nextProps，nextState)（判断模块需不需要重新渲染）因为react父组件的重新渲染会导致其所有子组件的重新渲染，这个时候其实我们是不需要所有子组件都跟着重新渲染的，因此需要在子组件的该生命周期中做判断
- componentWillUpdate （准备更新前）：

### 卸载过程
componentWillUnMount：如果componentDidMount中，通过React方法，创建了一些DOM元素，如果不删除的话，可能导致内存溢出，所以需要在componentWillUnMount中把这些DOM元素清理掉
- clear你在组建中所有的setTimeout,setInterval
- 移除所有组建中的监听 removeEventListener
- 也许你会经常遇到这个warning:

  ``` bash
  Can only update a mounted or mounting component. This usually means you called setState() on an unmounted component. This is a no-op. Please check the code for the undefined component
 
  ```
  
  - 是因为你在组建中的ajax请求返回中setState,而你组件销毁的时候，请求还未完成，因此会报warning
  
