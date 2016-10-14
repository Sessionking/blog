---
title: Git 管理
date: 2016-08-26 17:35:36
categories: Git 
tags: [Git]
---
## 切换、查看、删除分支
+ 切换分支  

新分支：```$ git checkout -b test```

本地存在： ```$ git checkout test```

> git checkout -f test  强制切换

+ 查看分支

远程 ```$ git branch -a```

本地 ```$ git branch ```

<!-- more -->

+ 删除分支

本地```$ git checkout -d test```

远程```$ git push origin --delete test```


## merge 后如何撤销
+ reset

> git checkout merge时的分支
> 
> git reset --hard  merge之前的分支（默认当时的）