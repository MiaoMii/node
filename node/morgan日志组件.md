#### morgan

> express默认的日志中间件



#### 安装

```shell
npm install express morgan
```

再`index.js`文件添加如下代码

```js
const express = require("express");
const morgan = require("morgan");
const app = express();

app.use(morgan("short"))

app.use((req, res, next) => {
    res.send("ok")
})

app.listen(3000);
```

`node index.js` 并访问localhost:3000,打印日志如下

```shell
::1 - GET / HTTP/1.1 200 2 - 2.169 ms
::1 - GET /favicon.ico HTTP/1.1 200 2 - 0.473 ms

```

#### 将日志打印到本地

```js
const express = require("express");
const morgan = require("morgan");
const path = require("path")
const fs = require("fs")
const app = express();
const accessLogStream = fs.createWriteStream(path.join(__dirname, 'access.log'), {flags: 'a'});
app.use(morgan("short", {stream: accessLogStream}))

app.use((req, res, next) => {
    res.send("ok")
})

app.listen(3000);
```



#### 核心API

**morgan(format, options)**

+ `format`: 可选，定义日志格式默认为 `default` ,

  + `combined` 

    ```shell
    :remote-addr - :remote-user [:date[clf]] ":method :url HTTP/:http-version" :status :res[content-length] ":referrer" ":user-agent"
    ```

  + `short`

    ```shell
    :remote-addr :remote-user :method :url HTTP/:http-version :status :res[content-length] - :response-time ms
    ```

  + `common`

    ```shell
    :remote-addr - :remote-user [:date[clf]] ":method :url HTTP/:http-version" :status :res[content-length]
    ```

  + tiny

    ```shell
    :method :url :status :res[content-length] - :response-time ms
    ```

  + dev

    ```shell
    :method :url :status :response-time ms - :res[content-length]
    ```

+ `options` 

  + `stream` 日志输出格式
  + `skip` 是否跳过日志记录
  + `immediate` 布尔值，默认为`false`。当为true时，一收到请求，就记录日志；如果为false，则请求返回后再记录日志



#### 自定义format

非常简单，首先通过`morgan.format()`定义名为`test`的日志格式，然后通过`morgan('test')`调用即可。

日志格式： [https://github.com/expressjs/morgan/#predefined-formats] 

```js
var express = require('express');
var app = express();
var morgan = require('morgan');

// 自定义token
morgan.token('from', function(req, res){
    return req.query.from || '-';
});

// 自定义format，其中包含自定义的token
morgan.format('test', '[test] :method :url :status :from');

// 使用自定义的format
app.use(morgan('test'));

app.use(function(req, res, next){
    res.send('ok');
});

app.listen(3000);
```

运行程序

```shell
[test] GET /hello?from=app 200 app
[test] GET /favicon.ico 304 -
[test] GET /hello?from=pc 200 pc
[test] GET /favicon.ico 304 -
```

