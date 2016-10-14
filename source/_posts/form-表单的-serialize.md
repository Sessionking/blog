---
title: form 表单的 serialize()
date: 2016-08-15 11:48:23
tags: [jQuery]
categories: JavaScript
---

## 假设表单中有个input

```
	<form>
		<input type="text" name="name" value="自填">
	</form>

	$("form").serialize();
```

> input的value 正常填值会获取value值;但是 如果用户输入"    " 获取的值为 name=+++  ;用户输入 "" 获取的值为name=  ;其他字符 比如 &nbsp;  \n 等 都有不同的对应的值 并不是 null 或者 空串


> $('form input').val();//结果是 input中是什么值就是什么值，不会解析；&nbsp;得到的值就是&nbsp;
