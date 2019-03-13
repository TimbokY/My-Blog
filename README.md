# 介绍
每日学习一个新知识，每天都进步。

# Day1 - JavaScript
时间：*2019-03-10*

**请把俩个数组 [A1, A2, B1, B2, C1, C2, D1, D2] 和 [A, B, C, D]，合并为 [A1, A2, A, B1, B2, B, C1, C2, C, D1, D2, D]。**

```js
var a = ["A1", "A2", "B1", "B2", "C1", "C2", "D1", "D2"];
var b = ['A', 'B', 'C', 'D'];

var bIndex = -1;
var sliceNumber = 2;
var response = [];

for(var i = 0; i<a.length; i++) {
  if(i%sliceNumber===0) {
    bIndex++;
    response = response.concat(a.slice(i, i+sliceNumber).concat(b[bIndex]));
  }
}

console.log(response);
```

# Day2 - HTML
时间：*2019-03-11*

**简述HTML语义化标签**

- 代码结构清晰，可读性高，易于后期维护
- 搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO;
- 用正确的标签写正确的代码

# Day3 - CSS
时间：*2019-03-12*

**transition - 过渡**

transition是一个简写属性，用于概括以下四个简明属性：
- [transition-property](http://www.w3school.com.cn/cssref/pr_transition-property.asp) 规定设置过渡效果的 CSS 属性的名称。
- [transition-duration](http://www.w3school.com.cn/cssref/pr_transition-duration.asp) 规定完成过渡效果需要多少秒或毫秒。
- [transition-timing-function](http://www.w3school.com.cn/cssref/pr_transition-timing-function.asp) 规定速度效果的速度曲线。
- [transition-delay](http://www.w3school.com.cn/cssref/pr_transition-delay.asp) 定义过渡效果何时开始。

**注释**：请始终设置 transition-duration 属性，否则时长为 0，就不会产生过渡效果。

例：
```css
div {
	width:100px;
	height:100px;
	background:red;
	transition: margin 2s;
}

div:hover {
	margin: 100px 0 0 100px;
}
```
