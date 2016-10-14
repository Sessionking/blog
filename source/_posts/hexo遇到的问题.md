---
title: hexo遇到的问题
date: 2016-08-20 12:45:32
categories: Hexo
tags: [Hexo]
---

# Hexo 的问题 -> Next 主题

## 新建文章那个后，使用 ``` $hexo g``` 命令时会提示：

> YAMLException: can not read a block mapping entry; a multiline key may not be an implicit key at line 5, column 1:

>该类错误主要是由于文章头部的:(冒号)后面需要有一个半角空格

## markdown的图片使用方法

>图片放在source文件下面的images中，格式如下：

![](/images/hexoProblem.png)

## markdwon 中的主副标题无法显示问题

>井号与文字之间需要添加一个半角空格
