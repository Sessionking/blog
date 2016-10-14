---
title: onChange() onKeyup() onKeydown() 事件的区别
date: 2016-08-04 14:23:03
tags: ["onkeyup", "onkeydown", "onchange"]
categories: JavaScript
---

# 以输入框 input 标签为例：
onchange()：该函数在输入框value被改变后，并且失去焦点以后才触发；

onkeyup():该函数在输入框中输入内容后，键盘跳起时触发；

<!-- more -->
onkeydown():该函数在输入框输入内容后，键盘再次被按下时触发。

>注：输入框中第一次按下1，第二次按下2。展示的字符只会展示1，而字符2会在按下下一个按键后展示
>
>通俗一点就是，输入框输入了四个一，展示输入框值得p段落中只展示了三个1.因为按下第一个1的时候触发的onkeydown()事件时，输入框value为空。当按键弹起时，输入框中才输入1，这时第一次的onkeydown事件已经触发，只能等待下一次onkeydown事件才能输出input的value值.
