---
title: path模块处理文件路径
date: 2016-08-22 22:03:30
categories: NodeJs
tags: [NodeJs,Path]
---

# path模块处理文件路径问题

```  
	var path=require('path'); 
```


> Note：__dirname  指的是当前文件所在目录
> __dirname="/a/b/c";


(1) path.join(arg1,arg1....),连接多个路径字符串


```
	 var a= path.join(__dirname,'/src','/xiaoyu');
	 console.log(a);
	 //结果为  /当前文件目录/src/xiaoyu
```
<!-- more -->

(2) path.resolve(from,...,to),相当于执行多次cd from ,cd to


```
	var a=path.resolve('foo/bar','/dd','../cc');
	console.log(a);
	//结果为  /cc
```

(3) path.normalize(path),格式化路径


```
	var a=path.normalize('foo/bar//a/ss//c');
	console.log(a);
	//结果为  foo/bar/a/ss/c
```

(4) path.dirname(path),path.basename(path,path1,..),path.extname(p),获取路径的各个部分


```
	var pathStr='/User/Session/hexo/blog/test.js';
	console.log(path.dirname(pathStr));
	//当前文件所在目录，结果 /User/Session/hexo/blog 
	console.log(path.basename(pathStr));
	//获取文件带后缀的名称，test.js
	console.log(path.extname(pathStr));
	//获取文件的扩展名 .js	
	
	
	console.log(path.basename(pathStr,'.js'));// test
	console.log(path.basename(pathStr,'.html'));// test.js
```


