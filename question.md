# 介绍
每日学习一个新知识，每天都进步。

# Question1 - JavaScript
时间：*2019-03-10*

## 请把俩个数组 [A1, A2, B1, B2, C1, C2, D1, D2] 和 [A, B, C, D]，合并为 [A1, A2, A, B1, B2, B, C1, C2, C, D1, D2, D]。

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

# Question2 - HTML
时间：*2019-03-11*

## 简述HTML语义化标签

- 代码结构清晰，可读性高，易于后期维护
- 搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO;
- 用正确的标签写正确的代码

# Question3 - CSS
时间：*2019-03-12*

## transition - 过渡

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

# Question4 - HTTP
时间：*2019-03-13*

## HTTP的几种请求方法用途

- GET方法：发送一个请求用于查询服务器上的资源
- POST方法：向`URL`指定的资源提交数据或附加新的数据
- PUT方法：与POST方法想似，不同的是它指定了资源在服务器上的位置，而POST方法没有
- HEAD方法：只请求页面的头部
- DELETE方法：删除服务器上的资源
- OPTIONS方法：用于获取当前`URL`所支持的方法，如果获取成功，会有一个`Allow`的头包含类似“GET,POST”这样的信息
- TRACE方法：用于激发一个远程的，应用层的请求消息回路
- CONNECT方法：把请求连接转换到透明的TCP/IP通道

# Question5 - JavaScript
时间：*2019-03-14*

## 如何判断一个对象是否为数组

1. Array.prototype.isPrototypeOf
```js
Array.prototype.isPrototypeOf([])
// true
Array.prototype.isPrototypeOf({})
// false
```

2. obj instanceof Array
```js
[] instanceof Array
// true
[] instanceof String
// false
'123' instanceof Array
// false
```

3.Array.isArray
```js
Array.isArray([])
// true
Array.isArray({})
// false
Array.isArray(undefined)
// false
```

# Question6 - JavaScript
时间：*2019-03-15*

## 深浅拷贝

之所以会出现深浅拷贝的问题，实质上是由于JS对基本类型和引用类型的处理不同。基本类型指的是简单的数据段，而引用类型指的是一个对象，而JS不允许我们直接操作内存中的地址，也就是不能操作对象的内存空间，所以，我们对对象的操作都只是在操作它的引用而已。

在复制时也是一样，如果我们复制一个基本类型的值时，会创建一个新值，并把它保存在新的变量的位置上。而如果我们复制一个引用类型时，同样会把变量中的值复制一份放到新的变量空间里，但此时复制的东西并不是对象本身，而是指向该对象的指针。所以我们复制引用类型后，两个变量其实指向同一个对象，改变其中一个对象，会影响到另外一个。

```js
var num = 10;
var obj = {
    name: 'Nicholas'
}

var num2 = num;
var obj2 = obj;

obj.name = 'Lee';
obj2.name; // 'Lee'
```

**浅拷贝**

对象的浅拷贝可以使用扩展运算符
```js
var a = {
  age: 1
}
var b = { ...a }
a.age = 2
console.log(b.age) // 1
```

浅拷贝只解决了第一层的问题，如果接下去的值中还有对象的话，那么就又回到最开始的话题了，两者享有相同的地址。要解决这个问题，我们就得使用深拷贝了
```js
var a = {
  age: 1,
  jobs: {
    first: 'FE'
  }
}
var b = { ...a }
a.jobs.first = 'native'
console.log(b.jobs.first) // native
```

**深拷贝**

不借助任何库的话，通常使用以下方法
```js
var a = {
  age: 1,
  jobs: {
    first: 'FE'
  }
}
var b = JSON.parse(JSON.stringify(a))
a.jobs.first = 'native'
console.log(b.jobs.first) // FE
```
但是该方法也是有局限性的：

- 会忽略 undefined
- 会忽略 symbol
- 不能序列化函数
- 不能解决循环引用的对象

# Question7 - JavaScript
时间：*2019-03-16*

## 打平如下数组
```js
var arr = [
  [
    ['1-7', '2-6'],
    '4-6',
    [
      ['2-0', '1-4'],
      ['3-9'],
      '4-5',
    ],
  ]
];
```

方法一
ES2019推出Array的新方法`flat`
```js
arr.flat().flat().flat()
```

方法二
递归
```js
var newArray = [];

function flatArr(arr) {
  for(var i = 0; i < arr.length; i++) {
    if(Array.isArray(arr[i])) {
      flatArr(arr[i]);
    } else {
      newArray.push(arr[i]);
    }
  }
  return newArray;
}
```

方法三
广度优先搜索 - 遍历
```js
function flatArr(arr) {
  const result = [];
  const list = [];
  function _forEach(arr) {
    arr.forEach(el => {
      if(Array.isArray(el)) {
        list.push(el);
      } else {
        result.push(el);
      }
    });
  }
  _forEach(arr);
  while(list.length > 0) {
    const item = list.shift();
    _forEach(item);
  }
  arr = result;
  return arr;
}
```

新方法欢迎补充


# Question8 - HTTP
时间：*2019-03-18*

## 跨域

> 涉及面试题：什么是跨域？为什么浏览器要使用同源策略？你有几种方式可以解决跨域问题？了解预检请求嘛？

- 因为浏览器出于安全考虑，有同源策略。也就是说，如果协议、域名或者端口有一个不同就是跨域，`Ajax` 请求会失败。
- 那么是出于什么安全考虑才会引入这种机制呢？ 其实主要是用来防止 `CSRF` 攻击的。简单点说，`CSRF` 攻击是利用用户的登录态发起恶意请求。
- 也就是说，没有同源策略的情况下，`A` 网站可以被任意其他来源的 `Ajax` 访问到内容。如果你当前 `A` 网站还存在登录态，那么对方就可以通过 `Ajax` 获得你的任何信息。当然跨域并不能完全阻止 `CSRF`。

> 然后我们来考虑一个问题，请求跨域了，那么请求到底发出去没有？ 请求必然是发出去了，但是浏览器拦截了响应。你可能会疑问明明通过表单的方式可以发起跨域请求，为什么 `Ajax`就不会。因为归根结底，跨域是为了阻止用户读取到另一个域名下的内容，`Ajax` 可以获取响应，浏览器认为这不安全，所以拦截了响应。但是表单并不会获取新的内容，所以可以发起跨域请求。同时也说明了跨域并不能完全阻止 `CSRF`，因为请求毕竟是发出去了。

接下来我们将来学习几种常见的方式来解决跨域的问题

### JSONP

JSONP 的原理很简单，就是利用 <script> 标签没有跨域限制的漏洞。通过 <script>标签指向一个需要访问的地址并提供一个回调函数来接收数据当需要通讯时

```js
function jsonp(url, jsonpCallback, success) {
  let script = document.createElement('script')
  script.src = url
  script.async = true
  script.type = 'text/javascript'
  window[jsonpCallback] = function(data) {
    success && success(data)
  }
  document.body.appendChild(script)
}
jsonp('http://xxx', 'callback', function(value) {
  console.log(value)
})
```

> JSONP 使用简单且兼容性不错，但是只限于 get 请求。

### CORS

- `CORS` 需要浏览器和后端同时支持。IE 8 和 9 需要通过 `XDomainRequest` 来实现。
浏览器会自动进行 `CORS` 通信，实现 `CORS` 通信的关键是后端。只要后端实现了 CORS，就实现了跨域。
- 服务端设置 `Access-Control-Allow-Origin` 就可以开启 CORS。 该属性表示哪些域名可以访问资源，如果设置通配符则表示所有网站都可以访问资源。

[参考文章](http://blog.poetries.top/FE-Interview-Questions/excellent/#_18-%E8%B7%A8%E5%9F%9F)

## Question9 - JavaScript
时间：*2019-03-20*

### 实现一个简易版的promise

```js
// 三个常量用于表示状态
const PENDING = 'pending'
const RESOLVED = 'resolved'
const REJECTED = 'rejected'

function MyPromise(fn) {
    const that = this
    this.state = PENDING

    // value 变量用于保存 resolve 或者 reject 中传入的值
    this.value = null

    // 用于保存 then 中的回调，因为当执行完 Promise 时状态可能还是等待中，这时候应该把 then 中的回调保存起来用于状态改变时使用
    that.resolvedCallbacks = []
    that.rejectedCallbacks = []


    function resolve(value) {
         // 首先两个函数都得判断当前状态是否为等待中
        if(that.state === PENDING) {
            that.state = RESOLVED
            that.value = value

            // 遍历回调数组并执行
            that.resolvedCallbacks.map(cb=>cb(that.value))
        }
    }
    function reject(value) {
        if(that.state === PENDING) {
            that.state = REJECTED
            that.value = value
            that.rejectedCallbacks.map(cb=>cb(that.value))
        }
    }

    // 完成以上两个函数以后，我们就该实现如何执行 Promise 中传入的函数了
    try {
        fn(resolve,reject)
    }cach(e){
        reject(e)
    }
}

// 最后我们来实现较为复杂的 then 函数
MyPromise.prototype.then = function(onFulfilled,onRejected){
  const that = this

  // 判断两个参数是否为函数类型，因为这两个参数是可选参数
  onFulfilled = typeof onFulfilled === 'function' ? onFulfilled : v=>v
  onRejected = typeof onRejected === 'function' ? onRejected : e=>throw e

  // 当状态不是等待态时，就去执行相对应的函数。如果状态是等待态的话，就往回调函数中 push 函数
  if(this.state === PENDING) {
      this.resolvedCallbacks.push(onFulfilled)
      this.rejectedCallbacks.push(onRejected)
  }
  if(this.state === RESOLVED) {
      onFulfilled(that.value)
  }
  if(this.state === REJECTED) {
      onRejected(that.value)
  }
}
```

# Question10 - HTTP
时间：*2019-03-21*

## 请描述一下 cookies，sessionStorage 和 localStorage 的区别？

- `cookie`是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）

- `cookie`数据始终在同源的http请求中携带（即使不需要），既会在浏览器和服务器间来回传递

- `sessionStorage`和`localStorage`不会自动把数据发给服务器，仅在本地保存

- 存储大小：
  - `cookie`数据大小不能超过4k
  - `sessionStorage`和`localStorage`虽然也有存储大小的限制，但比`cookie`大得多，可以达到5M或更大
  
- 有期时间：
  - `localStorage`存储持久数据，浏览器关闭后数据不丢失除非主动删除数据
  - `sessionStorage` 数据在当前浏览器窗口关闭后自动删除
  - `cookie` 设置的`cookie`过期时间之前一直有效，即使窗口或浏览器关闭
  
# Question11 - JavaScript
时间：*2019-07-01*

## 简易的[webpack](https://webpack.docschina.org/concepts/)
```js
const path = require('path');

module.exports = {
  // JS 执行入口文件
  entry: './main.js',
  output: {
    // 把所有依赖的模块合并输出到一个 bundle.js 文件
    filename: 'bundle.js',
    // 输出文件都放到 dist 目录下
    path: path.resolve(__dirname, './dist'),
  },
  module: {
    rules: [
      {
        // 用正则去匹配要用该 loader 转换的 css 文件
        test: /\.css$/,
        loaders: ['style-loader', 'css-loader'],
      }
    ]
  }
};
```
