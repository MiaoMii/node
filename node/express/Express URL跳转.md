#### res.location(path)

> 设置HTTP Location头

+ path

  ```js
  res.location('/foo/bar');
  res.location('../login');
  res.location('http://itbilu.com');
  res.location('back');
  ```

  当`path`是`'back'`时，响应的`Location`头会被设置为当前请求的`Referer`头，当`Referer`头不存在时会被设置为`'/'`。



#### res.rediret([status,], path)

+ `statue` {number},表示HTTP状态码
+ `path` {string}，设置到`Location` 

`location()`方法只会设置`Location`头，而`redirect()`方法除了会设置`Location`头外还可自动或手头设置`HTTP状态码`。理论上讲两者可以实现重定向。
