---
layout:     post
title:      JavaScript异步和单线程经典的例子setTimeout
subtitle:    "\"JavaScript异步和单线程经典的例子setTimeout\""
date:       2017-09-02
author:     zhenqili
header-img: img/post-bg-2015.jpg
catalog: true
tags:
    - JS
    - web前端
---

这篇文章主要讲一下js的异步和单线程以及一个经典例子。  

JavaScript是单线程和异步执行的。单线程的意思是一次只干一件事，所有要执行的任务都是排队一个个来。异步和同步是相对的，同步是说执行任务时要阻塞，上一个任务没有执行完，下一个任务不会执行。而异步会有所不同，当上一个任务需要等待时，会把该任务暂存起来，不会立即执行，等到所有程序执行完，处于空闲状态时，会立即查看有没有暂存的任务执行。  

所以，我们知道当需要等待时就会发生异步。等待的场景主要有：  
+ 定时任务：setTimeout, setInterval
+ 网络请求：ajax请求，图片img加载等
+ 绑定事件

下面讲一个关于setTimeout的经典例子。

```js
   console.log(1);
   setTimeout(function(){
   	  console.log(2);
   },0);
   console.log(3);
```

上面程序运行的结果是1、3、2。如下: 

```js
1
3
undefined
2
```


现在分析一下程序的运行过程。

 1. 执行第一行，打印出1
 2. 执行setTimeout后，传入的函数会被暂存起来，不会立即执行（单线程的原因，不会同时干两件事）
 3. 执行第五行打印3
 4. 这时，所有程序执行完毕， 然后立即查看暂存的任务，这里暂存的任务是传入setTimeout的函数
 5. 发现setTimeout中的函数无需等待，就立即执行，打印2
所以可以知道，执行结果是1、3、2。

这篇文章就到这了，记录自己的学习心得，讲得比较简单，如有错误，恳请指正！

