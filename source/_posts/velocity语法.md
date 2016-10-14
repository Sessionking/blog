---
title: velocity Tips
date: 2016-08-11 16:26:26
tags: [Velocity]
categories: Velocity
---
# Velocity Tips

1.变量  ${a}  

>注意：a为null 空 或者undefined ->  (1) ${a}或输出 ${a}字串 ;(2) $!{a} 输出空白(虚无）.

2.声明变量 #set ()

> 	#set (${a}='1')

3.定义函数 #macro   #end

> \#macro(a arg1 arg2...) 函数体  #end
>
> 函数名是a     
> 使用方式是 #a(arg1,arg2..)


<!-- more -->


4.循环 #foreach #end

> 循环中可以使用*$velocityCount*和*$foreach.inedx*和*$foreach.count*获取当前循环次数。
>
> 使用*$foreach.hasNext* 可以获取是否是最后一次循环
>
> 使用*$foreach.first*和*$foreach.last*分别可以获取开始和结束元素
>
> 注意:index是从0开始，count和velocityCount是从1开始



5.对于数组的操作 array

|序号|方法|说明|
|---|:---|:---|
|1|isEmpty()|判断数组是否为空|
|2|size()|数组中元素的个数（从1开始）|
|3|get()|获取数组指定下标的元素（从0开始）|
|4|add()|添加元素|

example：

```
	#set ($arr=[1,2])
	$arr.get(1)
	$arr.size()
```

>注意：在velocity中数组不能通过arr[0]来获取指定下标值

6.对象访问

example:

```
	#set (obj={"age":12,"name":"xiaofang"})
	$.obj.age
	$obj.get("age")
	## .属性 和get("属性")两种方式等价
```

7.引入其他文件 #include() #parse()  Webx中还可以使用$control.setTemplate()

举个栗子：

a.vm：

```
	#set ($name="xiaoyu")
```

\#include ('a.vm')  ${name} ->  #set ($name='xiaoyu')

\#parse ('a.vm')   ${name} -> xiaoyu

>由此可以看出：include引入的文件不能解析velocity语法，而parse可以。但是，parse 不能处理后端逻辑。include可以引入多个参数，使用逗号分开。文件路径以根目录开始（没测试过，使用失败）
>
>\#$control.setTemplate() 包含parse的作用，同时还可以处理后端的逻辑（没有测试过，只是在parse失败以后使用它来加载vm文件，囧~~菜）。文件路径以/control 开始（这个测试过）


#项目中用到的各种奇怪的方法

> 其实我也不懂 只是一知半解 反正可以用 o(╯□╰)o
>
> webx基础 velocity模板的工具类 *stringUtils*


(1) #set ($arrNew=$stringUtils.join(${arr},','));将arr数组以逗号连接为字符串

(2) $stringUtils.isNotBlank(${a})  判断字符串是否不为空且且长度不为0 同时，不由空白符构成

(3) $ item.replace(':',': ')  字符串的常用方法
