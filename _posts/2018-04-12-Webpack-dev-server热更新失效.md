---
layout:     post
title:      webpack-dev-server热更新失败
subtitle:    "\"关于 Vue webpack-dev-server热更新失败\""
date:       2018-04-12
author:     zhenqili
header-img: img/post-bg-2015.jpg
catalog: true
tags:
    - Vue
    - Webpack
    - web前端
---
# vue webpack-dev-server热更新失败
今天踩了一个坑，就是webpack-dev-server热更新失效 或者说vue-cli脚手架热更新失效，记录一下。

错误原因： 在页面中引入一个组件，然后把组件的父级目录名开头字母写成大写（原本是小写的），但是没有报引入失败，但是webpack监听不了文件的更新。如下：

```s
// 正确引入方法
import ComA from '@/components/foldername/ComA.vue'

// 结果这样引入， 把foldername的f大写了
import ComA from '@/components/Foldername/ComA.vue'
```

总结一下原因：引入路径错误，导致webpack监听失败。