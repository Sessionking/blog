---
title: hexo的基础命令
date: 2016-08-03 17:31:38
tags: [Hexo]
categories: Hexo
---

# [Hexo 主题 问题](https://github.com/iissnan/hexo-theme-next)

@ 新建
> ```$ hero  new  page "name" ``` 新建页面 md文件

> ```$ hero new  "name" ``` 新建文章 （写文章 随笔 就这个了）

@ 写完以后在根目录下执行以下命令 生成和预览

> ```$ hexo d -g ```生成 部署

> ```$ hexo s ```  部署 预览 localhost：4000


@ 如果你想删除一个文件的时候，执行以下命令即可
<!-- more -->

1. 删除source下面想要删除的文件
2. 执行 ```$ hero clean ``` 清除数据库，
3. 然后在执行 ```$ hexo d -g   hexo s ```本地预览一下吧
