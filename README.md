# 一些关于React的知识点
安装前的一些插件：
 live server（在线调试的程序）
 
# 01- Hello React
> 一个最基础的调用
``` javascript
    <div id="test"></div>
    <script type="text/javascript" src="../ReactLib/react.development.js"></script>
    <script type="text/javascript" src="../ReactLib/react-dom.development.js"></script>
    <script type="text/javascript" src="../ReactLib/babel.min.js"></script>
    <script type="text/babel">
        const VDOM = <h1>Hello React</h1>
        ReactDOM.render(VDOM,document.getElementById('test'))
    </script>
```

# 02- 创建DOM
>使用JS去创建DOM
>React 主要解决的是多层标签嵌套
```javascript
    <div id="test"></div>
    <script type="text/javascript" src="../ReactLib/react.development.js"></script>
    <script type="text/javascript" src="../ReactLib/react-dom.development.js"></script>

    <script type="text/javascript">

        // const VDOM = React.createElemet(标签名,标签属性,标签内容)
        const VDOM =React.createElement('h1',{id:'title'}, React.creatElement('span',{},'Hello React.'))
        ReactDOM.render(VDOM,document.getElementById('test'))
    </script>
```
# 03- 真实与虚拟DOM
> 简单比较下真实DOM与虚拟DOM之间的差别
>>    1.虚拟DOM 是Object类型的对象<br>
>>    2.虚拟DOM 比较轻，真实DOM 比较重。 虚拟本身是React在用。 <br>
>>    3.虚拟DOM最终会被React 转化成真实DOM， 最终呈现在页面上 。
```javascript
<body>
    <div id="test"></div>
    <script type="text/javascript" src="../ReactLib/react.development.js"></script>
    <script type="text/javascript" src="../ReactLib/react-dom.development.js"></script>
    <script type="text/javascript" src="../ReactLib/babel.min.js"></script>

    <script type="text/babel">
        const VDOM = <h1><span>Hello React</span></h1>
        const TDOM = document.getElementById('test') 
        ReactDOM.render(VDOM,document.getElementById('test'))
        console.log('虚拟DOM',VDOM);
        console.log('真实DOM',TDOM);
        debugger;
    </script>
</body>
```
# 04- JSX语法规
> JSX的一些语法规则
   >> 1：定义虚拟DOM时，不要写引号 <br>
   >> 2：标签内混入JS 要用{} <br>
    >> 3：样式的类名指定不要用class， 要用className <br>
    >> 4：内联样式，要用stye={{key:value}} <br>
    >> 5：JSX的只让允许使用一个根标签 <br>
    >> 6: 标签首字母
    >>> 若标签首字母小写开头，react将标签转为html同名元素，若html无该标签同名元素，则报错。
    >>> 若标签首字母大写开头，react就会去渲染对应的组件，若组件没有定义，则报错
``` javascript
<body>
    <div id="test"></div>
    <script type="text/javascript" src="../ReactLib/react.development.js"></script>
    <script type="text/javascript" src="../ReactLib/react-dom.development.js"></script>
    <script type="text/javascript" src="../ReactLib/babel.min.js"></script>

    <script type="text/babel">
        const myID='myID'
        const myData='MyData'
        const VDOM=(
            <h2 className="title" id={myID.toLocaleLowerCase()}>
                <span style ={{color:'white'}}>{myData.toUpperCase()}</span>
            </h2>
        )
        ReactDOM.render(VDOM,document.getElementById('test'));
    </script>
</body>
```