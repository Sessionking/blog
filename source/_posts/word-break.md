---
title: word-break word-wrap white-space等
date: 2016-08-20 14:37:22
categories: CSS
tags: [CSS]
---

# 文本换行

>box 需要固定宽度 给定一个width,并且是一个块级元素或者行内块(display:block;)

|序号|属性|取值|
|---|:---|:---|
|1|word-break|normal/break-all/keep-all|
|2|word-wrap|normal/word-break|
|3|white-space|normal/pre/nowrap/pre-line/pre-wrap/inherit|



<!-- more -->

#详细介绍

(1) word-break

|序号|取值|描述|
|---|:---|:---|
|1|normal|使用浏览器的换行规则进行换行，默认值|
|2|break-all|强行截断单词，达到词内换行的效果|
|3|keep-all|只能在*半角空格或连字符*处换行，不允许截断英文单词|

(2) word-wrap

|序号|取值|描述|
|---|:---|:---|
|1|normal|使用浏览器的换行规则进行换行|
|2|break-word|不截断单词换行，碰到边界后自动换行，如果单词很长，直接整个单词换行|

(3) whit-space

|序号|取值|描述|
|---|:---|:---|
|1|normal|单词之间的空白被浏览器忽略|
|2|pre|单词间的空白被保留，类似于pre标签|
|3|nowrap|文本不会换行，在同一行上面，直到遇到<br>为止|
|4|pre-wrap|保留单之间的空白，但是正常换行|
|5|inherit|继承父类|
