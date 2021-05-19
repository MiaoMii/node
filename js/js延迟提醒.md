问题：外部api拥挤导致请求会有2-3秒延迟，需要再发起请求后等待5秒后再判断是否请求成功

解决：Promise.race 会返回第一个执行完成的结果，所以你可以用它同时执行一个 5 秒钟延时的 reject 。如果请求成功了就会忽略这个 reject，如果 5 秒还没成功，就会收到这个 reject 。

示例代码：

```js
const result = await Promise.race([
	fetch('/your-request-api'),
	new Promise((resolve, reject) => {
	setTimeout(() => reject('Timeout'), 5000)})
]);
```



