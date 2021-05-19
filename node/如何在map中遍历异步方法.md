###### promise.all 解决 map 遍历 异步问题

```js
(async () => {
    let arr = [1, 2, 3, 4, 5];
    let res = await Promise.all(arr.map(async (item) => {
        await new Promise(resolve => {
            setTimeout(() => {
                console.log(item + '内结束');
                resolve();
            }, 2000);
        });
        return 10;
    }));
    console.log(res);
})();
```

