---
title: ES6的小Tips
date: 2016-08-05 14:56:09
tags: [ES6]
categories: ES6
---

# 读阮一峰老师的ES6后记：

## ES6的注意点：

1.如果块内使用了let 和const命令进行变量声明，那么在声明之前使用这些变量都会报错；

```
	var a=0;
	{
	    a=1; //会报错，a undefined
	    let a=3;
	}
```
<!-- more -->
```
	function b(x=y,y=2){};b();
	//报错，因为y未声明。如果将第一个和第二个参数互换位置，则不会报错。

```

2.var 声明的变量全局存在，let 声明的只存在某个块内。

```
	var arr=[];
	for(var i=0;i<4;i++){
		arr[i]=function(){
			console.log(i);
		}
	}
	arr[1]();
	//结果控制条输出4,每一次循环的i都会覆盖掉前一次的最后数组函数输出全是最后一个i。
```

```
	var arr=[];
	for(let i=0;i<4;i++){
		arr[i]=function(){
			console.log(i);
		}
	}
	arr[1]();
	//结果控制条输出1，let声明的i只存在每次的循环中，每一次都不是同一个i，不会被覆盖掉
```

3.不能重复声明变量

```
	function fun(){let a=0;var a=0;}//报错
	function fun(){let a=0;let a=0;}//报错
	function fun(arg){let arg=0;}   //报错
	function fun(arg){{let arg=0;}} //不报错，（块内，块外访问不到）
```

4.const 声明一个常量，声明后常量的值不能被改变。意味着，声明必须初始化。注意：与let相同，只在声明所在的块级作用域内有效，并且不可以重复声明。

```
	const a=0;
	a=9;//报错
```

#ES6小技巧（感觉很好用）：

一、解构赋值（*解构赋值是声明和赋值同时进行的，所以不能重复声明。如果左边没有关键字 let 和var 的话可以直接使用，但是变量需要提前声明。*）

```
	var x;
	{x} = {x: 1};
	// 写法错误，系统会认为{x}是一个代码块，正确写法如下
	（{x}={x:1}）;
```

1.数组的解构赋值（左右都是数组格式）

(1) 可以按照一定的模式，从数组(*必须为数组，否则不能生效*）中提取值，并且赋给变量；只要等号两边的模式相同，左边的变量就会被赋予对应的值,不对应的位置变量会undefined。example:按照对应位置赋值。（ES6严格按照===来判断是否相等)

```
	var [a,b,c]=['1','2','3'];
	var [a,[b,c]]=['1',['2','3']];//对应嵌套匹配也可以
	var [bar, foo] = [1];//这种情况bar 有值，foo undefined
	var [a, [b], d] = [1, [2, 3], 4];//b:2
```

(2) 一个数组值如果不严格等于undefined，变量的默认值是不会生效的

``` 	
	let [a=0]=[undefined];//结果是undefined
	let [a=0]=[null];
	//因为不是undefined这个单词(?)，所以结果是null，默认值不生效，被null 取代
```

(3) 默认值还可以是表达式:

```
	let [a=fun()]=[1];//与前面讲的取值方式相同
```

2.对象的解构赋值（左右都是对象格式）

```
	var {a,b}={a:'name',b:'age'};
```

>*对象的属性名称一定要对应，否则就无法赋值；属性的顺序是无序的，只要名称对应就可以取值*

> *对象的解构赋值的内部机制，是先找到同名属性，然后再赋给对应的变量。*


```
	var {foo:a,bar:b}={bar:"1",foo:"2"};
	//先找属性名相同的属性，然后将右边同名属性的值赋给左边同名属性的值变量；因此 a就是1，b就是2；
```

> *对象和数组的解构赋值是可以嵌套的*

```
	var node = {
	  loc: {
	    start: {
	      line: 1,
	      column: 5
	    }
	  }
	};

	var { loc: { start: { line }} } = node;
	//只有line是变量，其他的是匹配的模式
```

```
	var obj = {
	  p: [
	    'Hello',
	    { y: 'World' }
	  ]
	};

	var { p: [x, { y }] } = obj;
	x // "Hello"
	y // "World"
	//p 是匹配的模式
```

3.字符串解构赋值

```
	var [a,b,c]='hello';
	//a ->h, b->e ,c->l
```

以为字符串都有一个length长度属性，所以：

```
  let {length:len}='hello';
  //len -> 5
```

4.数值和布尔值解构赋值

 *等号右边是数值或者布尔值时，会先转换为对象.

```
	let {toString:s}=123;
	let {toString:s}=true;
	//因为布尔值和数值都有toString的属性，所以s 有值
```

```
	let {prop:x}=undefined;
	let {prop:x}=null;
	//会报错，类型错误
```

5.函数的参数解构赋值

```
   function fun([x,y]){ return x+y;};
   fun([1,2]);// return 3;

   [[1, 2], [3, 4]].map(([a, b]) => a + b);//ES6的箭头函数[3,7]
```

6.ES6允许初始化

```
	function fun(x=0;y=2){...}
	var [a=0,b=0]=[1,2];
```

二、for in  与for of 的区别

1. for in 中声明的变量是索引index，for of 中声明的变量是 value

```
	var str='hello';
	for (let index in str){console.log(str[index])}
	// 索引 index，结果h e l l o ，index的值是0，1，2，3，4

	for (let value in str)[console.log(value);}
	//值 value 相当于for in里面的str[index]，value值是h e l l o

```

> for of 可以正确识别 大于0xFFFF的16进制码点（example:0x20BB7)


三、ES6中的字符串查找

* javascript自带的indexOf函数：第一个参数是需要查找的字符串值，第二个参数非必填,查询的开始位置。
* starsWith 第一参数是需要查找的字符串的值，第二个参数非必填,查询开始的位置。
* endsWith 第一个参数是需要查找的字符串的值，第二个参数非必填，
* repeat 方法返回一个新字符串，表示将原字符串重复n次，0次或者NaN或者字符,输出''；小数，四舍五入;


四、模板字符串

1. ES6中使用html字符串只需要写在` ` 之中就好啦。不需要想ES5繁琐的+了；使用反斜杠对反引号进行转义。

```
	var str=`<ul><li></li>
	</ul>`;

	var str2=`\`ohha`;
```
2.模板中嵌套变量，变量或者表达式（1+2）或者函数f()写在 ${} 中;如果变量未声明则报错。一个html字串中如果含有多个（n个）变量，函数入参后，是一个数组，长度为n+1。

```
	var str='hello';
	var str2=`
	<p>${str} world!${str}</p>
	`;

	function f(a){...};
	f`str2`;//arguments.length为3.
```

> 所有模板字符串的空格和换行都会被保留，使用 .trim()消除。str2中p前面会有一个换行，如果你不想要换行，介意使用trim()消除。

3.标签模板，模板是前面函数的标签。表示是函数的模板，不是别人的模板。

```alert`123`; //等价于alert(123);```

五、正则表达式

1.创建正则表达式 RegExp *第一个参数*可以是：正则字串或者正则表达式（'xyz'|/xyz/) *第二个参数* 修饰符 flag(i|g|m|u|y) 通过.flags可以获取正则表达式的修饰符;通过.sticky来判断是否使用了y属性;通过.source来获取正则表达式的正文(/正文/修饰符）

```
var regexp=new RegExp(/xyyz/,'g');
regexp.flags;
```

2.字串函数 match() split() replace() search()

|序号|方法|说明|
|---|:---|:---|
|1|match(a)|在字符串内检索指定的值 a (字符串|正则表达式）,返回找到的一个或者多个匹配值|
|2|split(a)|将字符串按照制定值a进行分隔，得到的结果为数组|
|3|replace(a,b)|在字符串内检索指定值a，然后用b去替换。结果是替换后的字符串|
|4|search(a)|在字符串内检索指定值a，检索到以后返回子串的起始位置，否则-1|

example：

```
	var str='xiao yu ai chi yu';
	str.match('ai');//返回['ai']
	str.split(' ');//返回["xiao", "yu", "ai", "chi", "yu"]，以空格分隔	str.replace(' ','$');//返回"xiao$yu ai chi yu", 替换匹配到的第一个空格
	str.replace(/\s+/g,'$');//替换全局的空格，"xiao$yu$ai$chi$yu"
	str.search('c');//返回11 从0开始计数，第十二的位置，所以返回11
```

>正则表达式有两个方法：test() exec();test用于检测一个字符串是否匹配某个模式，返回布尔值；exec用于检索字符串中与正则表达式匹配的子串，并且返回该子串。

#作用域 -> 函数默认值：参数的默认值为变量的情况，则该变量所处的作用域，与其他变量的作用域规则是一样的，即先是当前函数的作用域，然后才是全局作用域。。

(1)y的默认值是x，函数作用域内部的变量x已经声明，所以y等于参数x，而不是全局作用域的x。

```
	var x=1;
	function fun(x,y=x){
		console.log(y);
	}
	fun(2);//结果输出 2
```

(2) y的默认值是x，但是函数作用域内部的x还未声明。所以y等于全局作用域的x。

```
	var x=1;
	function fun(y=x){0;
		let x=
		console.log(y);
	}
	fun();//结果输出 1
```

>注意：
>
>```
>   var x=0;
> 	function fun(x=x){}
> ```
>
> 会报错.x is not definder.函数fun的参数x的默认值也是x。这时，默认值x的作用域是函数作用域，而不是全局作用域。由于在函数作用域中，存在变量x，但是默认值在x赋值之前先执行了，所以这时属于暂时性死，任何对x的操作都会报错。
