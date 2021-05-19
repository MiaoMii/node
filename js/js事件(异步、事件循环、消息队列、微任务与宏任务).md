# js事件
> js只有一个线程即js引擎线程

JS引擎线程遇到异步（DOM事件监听、网络请求、setTimeout计时器等...），会交给相应的线程单独去维护异步任务，等待某个时机（计时器结束、网络请求成功、用户点击DOM），然后由 事件触发线程 将异步对应的 回调函数 加入到消息队列中，消息队列中的回调函数等待被执行。

js引擎会维护一个执行栈 同步代码会依次加入执行栈中执行，结束推出执行栈。
当同步代码依次执行完，执行栈为空（即js引擎空闲），事件线程才会从消息队列取出一个任务(即异步执行队列），放入执行栈中执行
执行完之后，执行栈为空。事件触发线程就会重复上一步骤，再取出消息队列中的任务，这种机制被称为事件循环机制

HTML5标准规定setTimeout第二个参数不得小于4，即就算setTimeout为0延迟（`setTimeout(() => {}, 0))`）也同样会进入异步执行队列

#### 宏任务 `macrotask` 和微任务 `microtask`
+ macrotask: 主代码块、setTimeout、setInterval、setImmediate、requestAnimationFrame
+ microtask：promise.then 、process.nextTick、catch、finally、MutationObserver

js引擎线程先执行主代码块

#### 总结
JavaScript 是单线程语言，决定于它的设计最初是用来处理浏览器网页的交互。浏览器负责解释和执行 JavaScript 的线程只有一个（所有说是单线程），即JS引擎线程，但是浏览器同样提供其他线程，如：事件触发线程、定时器触发线程等。


异步一般是指：

网络请求
计时器
DOM事件监听



事件循环机制：

JS引擎线程会维护一个执行栈，同步代码会依次加入到执行栈中依次执行并出栈。
JS引擎线程遇到异步函数，会将异步函数交给相应的Webapi，而继续执行后面的任务。
Webapi会在条件满足的时候，将异步对应的回调加入到消息队列中，等待执行。
执行栈为空时，JS引擎线程会去取消息队列中的回调函数（如果有的话），并加入到执行栈中执行。
完成后出栈，执行栈再次为空，重复上面的操作，这就是事件循环(event loop)机制。

![宏任务微任务](E:\project\vue-blog-ts\src\assets\note\js\img\宏任务微任务.png)



```js
//主线程直接执行
console.log('1');
//丢到宏事件队列中
setTimeout(function() {
    console.log('2');
    process.nextTick(function() {
        console.log('3');
    })
    new Promise(function(resolve) {
        console.log('4');
        resolve();
    }).then(function() {
        console.log('5')
    })
})
//微事件1
process.nextTick(function() {
    console.log('6');
})
//主线程直接执行
new Promise(function(resolve) {
    console.log('7');
    resolve();
}).then(function() {
    //微事件2
    console.log('8')
})
//丢到宏事件队列中
setTimeout(function() {
    console.log('9');
    process.nextTick(function() {
        console.log('10');
    })
    new Promise(function(resolve) {
        console.log('11');
        resolve();
    }).then(function() {
        console.log('12')
    })
})
```

• 首先浏览器执行js进入第一个宏任务进入主线程, 直接打印console.log('1')

• 遇到 **setTimeout** 分发到宏任务Event Queue中

• 遇到 process.nextTick 丢到微任务Event Queue中

• 遇到 Promise， new Promise 直接执行 输出 console.log('7');

• 执行then 被分发到微任务Event Queue中``

•第一轮宏任务执行结束，开始执行微任务 打印 6,8

•第一轮微任务执行完毕，执行第二轮宏事件，执行setTimeout

•先执行主线程宏任务，在执行微任务，打印'2,4,3,5'

•在执行第二个setTimeout,同理打印 ‘9,11,10,12’

•整段代码，共进行了三次事件循环，完整的输出为1，7，6，8，2，4，3，5，9，11，10，12。

> ​	先执行主线程  console、promise -> 再执行微任务 process.nextTick、promise.then -> 再执行setTimeout  



