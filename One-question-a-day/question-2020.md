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



## Question4 - CSS中的Clear
时间：*2020-05-14*

[MDN资料](https://developer.mozilla.org/zh-CN/docs/Web/CSS/clear)

 **`clear`** [CSS](https://developer.mozilla.org/en-US/docs/CSS) 属性指定一个元素是否必须移动(清除浮动后)到在它之前的浮动元素下面。`clear` 属性适用于浮动和非浮动元素。

## Question5 - 单点登录
时间：*2020-05-15*

[前端关于单点登录的知识](https://juejin.im/post/5b73c71fe51d45666016655a)

**单点登录**（Single Sign On），简称为 SSO，是目前比较流行的企业业务整合的解决方案之一。SSO的定义是在多个应用系统中，用户只需要登录一次就可以访问所有相互信任的应用系统。

SSO一般都需要一个独立的认证中心（passport），子系统的登录均得通过passport，子系统本身将不参与登录操作，当一个系统成功登录以后，passport将会颁发一个令牌给各个子系统，子系统可以拿着令牌会获取各自的受保护资源，为了减少频繁认证，各个子系统在被passport授权以后，会建立一个局部会话，在一定时间内可以无需再次向passport发起认证。



## Question6 - 怎样测试 JavaScript 的函数性能
时间：*2020-05-26*

1. `Perfomance.now()`

```js
const t0 = performance.now();
for (let i = 0; i < 100; i++) 
{
  // some code
}
const t1 = performance.now();
console.log(t1 - t0, 'milliseconds');
```

2. `console.time`

```js
console.time('test');
for (let i = 0; i < array.length; i++) {
// some code
}
console.timeEnd('test');
```

[怎样测试 JavaScript 的函数性能](https://blog.csdn.net/eyeofangel/article/details/105531340?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.nonecase)

