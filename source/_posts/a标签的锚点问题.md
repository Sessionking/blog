---
title: a标签的锚点问题
date: 2016-08-23 15:13:16
categories: HTML
tags: [HTML,jQuery]
---

# 锚点

## 锚点的使用

```
  <a href='#xiaoyu'>锚点</a>

  <p id='xiaoyu'>我是锚点锚点点</p>
```

>这时，点击a就可以跳转到段落P处。同时，锚点的对象还可以使用name来进行跳转，但是由于经常会出现锚点失效的情况，所以就考虑使用id来代替name。

## 锚点失效问题

> 在iframe中锚点的跳转会失效,可以通过jQuery中的animate 结合 scrollTop来进行跳转。
