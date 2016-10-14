---
title: ReactJS学习总结
date: 2016-08-03 17:49:08
tags: [React]
categories: ReactJS
---

# ReactJs 的内联样式的小问题

1.属性名称要采用驼峰写法（与原生js中设置属性值一样）

```
 	var style={
 	         fontSize:900,
 	         backgroundColor:'red'
     }
```

>注：React会在元素后面自动加上px,若我们自己加上px，会报错。

>在添加属性时， class 属性需要写成 className ，for 属性需要写成 htmlFor ，这是因为 class 和 for 是 JavaScript 的保留字。

```
   fontSize:900px;
```

2.数组模式

```
var arr=['1','2'];{/*或者 arr=[<h1>22</h1>,<h2>333</h2>]*/}
ReactDOM.render(<div>{arr}</div>,document.body);
```
<!-- more -->

> 得到的结果：在该块中循环数组的每一个值，外层块，不做循环
>  ```
> <div>
> <h1>22</h1>
> <h2>333</h2>
> </div>
> ```

3.React组件名称必须大写，html标签首字母必须小写，以此来区分

> React组件 ```var Hello=React.createClass({.....});```  

> html标签 ```var hello=<Hello />```

4.每个React组件只能包含一个顶层标签

>对的写法 ```<div><h1>aa</h1><h2>222</h2></div>```

>错的写法```<div><h1>aa</h1></div>  <div><h2>222</h2></div>```

















--------------------------- 我是分割线 -----------------------

>【杂七杂八】不分类的玩意儿：
select 中不要使用 selected 选中 option，直接给 select 设置 defaultValue 或者 value 来选中 option
