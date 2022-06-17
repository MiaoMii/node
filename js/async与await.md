#### async

> 返回一个Promise，它以类似**同步**的方式来写异步方法

可以用`then`接收成功时的返回值，`catch`接收异常



#### await 

> 暂停当前 async function内的语句执行，等待await后的方法处理完返回结果后，继续执行async funciton函数内部的剩余语句

注意必须使用在async function内使用



```js
async function fn() {
    console.log(1);
    await new Promise(function(resolve, reject) {
        setTimeout(function() {
            console.log(2);
            resolve(0);
        }, 2000);
    });
    console.log(3);
}
fn();
// 1
// 2 (2 秒后)
// 3
```

#### setTimeout、async/await、promise中代码执行顺序

这里异步任务的`Event Queue`分两种情况的，即`宏任务(macrotask)`和`微任务(microtask)`，当主线程任务完成为空去`Event Quenu`读取函数的时候，是先读取的微任务，当微任务执行完毕之后，才会继续执行宏任务。

同步>异步  微任务>宏任务

```js
async function async1() {
  console.log('async1 start');
  await async2();
  console.log('async1 end');
}
async function async2() {
  console.log('async2');
}

console.log('start');
setTimeout(() => {
  console.log('setTimeout');
}, 0);
async1();
new Promise(resolve => {
  console.log('promise1');
  resolve();
}).then(() => {
  console.log('promise2');
})

console.log('end');
// 1.打印start
// 2.将setTimeout放入异步宏任务队列
// 3.打印async1 start 、async2将await后面的代码放入异步微任务队列
// 4.打印promise1
// 5.将then放入异步微任务队列
// 6.打印end，至此主代码块执行完毕，开始执行异步微任务队列
// 7.先进先出原则，打印 async1 end
// 8.先进先出原则，打印 promise2 至此异步微任务队列执行完毕，开始执行异步宏任务
// 9.打印setTimeou


```

```js
async function fn() {
    console.log(0);
    
    setTimeout(() => {
        console.log(1);
    }, 0);

    await new Promise(resolve => {
        setTimeout(() => {
            console.log(2);
        }, 0);

        console.log(3);

        setTimeout(() => {
            console.log(4);
            resolve();
        }, 1000);

        setTimeout(() => {
            console.log(5);
        }, 0);
    });

    setTimeout(() => {
        console.log(6);
    }, 0);
    console.log(7);
}

fn();
// 1.打印0
// 2.将1放入异步宏任务，开始执行await内代码
// 3.将2放入异步宏任务
// 4.打印3
// 5.将4放入异步宏任务，并按等待时间排序
// 6.将5放入异步宏任务
// 7.将await后续代码放入微任务，开始执行异步宏任务
// 8.打印1，2，5，4 开始执行异步微任务
// 9.将6放入宏任务，打印7
// 10.打印6
```

