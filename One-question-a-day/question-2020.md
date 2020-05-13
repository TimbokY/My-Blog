# 介绍
每日学习一个新知识，每天都进步。

## Question1 - 举例说明图片懒加载的方案有哪些？
时间：*2020-05-09*

[图片懒加载的几种方法 - 简书](https://www.jianshu.com/p/c0f8cc330653)

当一个网站的图片数量较多时，直接加载可能会有很大的开销，不利于性能，这时可以将所有的图片换成轻量的占位图，不加载图片。而当用户真正滚动到图片出现时，再迅速将占位图片换成真正我们想展示的图片，这整个过程就是懒加载。

+ 滚动事件监听
+ Intersection Observer API
+ Chrome 浏览器自带

## Question2 - 你有使用过time标签吗？说说它的用途有哪些？
时间：*2020-05-13*

这涉及到**HTML Microdata[微数据]**的概念，主要用于网页爬虫解析。

通过`document.getItems`来判断浏览器是否支持微数据。



[HTML Microdata[微数据]](https://wiki.jikexueyuan.com/project/html5/microdata.html)



## Question3 - JS尾调用优化
时间：*2020-05-13*

[阮一峰的讲解](http://www.ruanyifeng.com/blog/2015/04/tail-call.html)

尾调用就是指某个函数的**最后一步**是调用**另一个函数**。

尾调用之所以与其他调用不同，就在于它的**特殊**的调用位置。

尾调用优化"（Tail call optimization），即只保留内层函数的调用记录。如果所有函数都是尾调用，那么完全可以做到每次执行时，调用记录只有一项，这将大大节省内存。这就是"尾调用优化"的意义。

