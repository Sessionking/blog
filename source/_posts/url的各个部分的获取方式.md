---
title: url的各个部分的获取方式
date: 2016-08-09 16:08:04
tags: [URL]
categories: JavaScript
---
# Url的各个部分获取方法

*如果你不晓得怎么获取url，你可以浏览器的控制台（console）中输入，window.location 看一下各个属性*

## url的组成部分：

> url -> protocol://host:port/path?query#fragment

1. protocol 是通信协议protocol (http https等)
2. host 主机（域名or IP，lidayu.cn OR 127.0.0.1等）
3. port 端口号 （80 OR 8081 等）
<!-- more -->
4. path 路径 （view/index/index.html 等)
5. query get请求的查询条件(?name=xiaoyu OR ?name=xiaoyu&value=1 等);
6. fragment 信息片断,也就是hash值 (#11 OR #indexkey)（添加以后不会对页面起到任何作用，刷新以后值还存在）

>举个例子 ->
>http://www.infoq.com/cn/articles/es6-in-depth-arrow-functions?name='xiaoyu'#flag;

>或者
>http://localhost:8081/script/html/js/index.html?pageSize=10&name=xiaoyu&key=query&value=1#indexKey

获取放法表

|序号|获取url的某个部分|获取方法|备注|
|---|:---|:---|:---|
|1| url |window.location.href| 获取整个url|
|2| protocol |window.location.protocol|获取协议值|
|3| host | windwo.location.host|获取主机名称（与hostname一样？）|
|4| port | window.location.port|端口号|
|5| pathname|window.location.pathname|路径|
|6| query |window.location.search|查询参数|
|7| fragment| window.location.hash|hash值|
