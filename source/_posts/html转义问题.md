---
title: html转义问题
date: 2016-08-26 11:53:42
categories: HTML
tags: [HTML]
---

## 转义

>将具有功能性的字符，经过转义后会展示在页面上；
## 不转义

>功能型字符如果不转义，会当做功能字符使用


## 举个栗子

```
 var str='&lt;p&gt;如果您觉得好用，别忘了推荐给朋友！&lt;/p&gt;'
 document.write(str);
 //页面展示为：<p>...........</p>
 
 var str='<p>.............</p>';
 document.write(str);
 //页面展示为：..............
```