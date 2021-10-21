```js
export.hello = function () {
    console.log('hello')
}
等同于
module.export.hello = function () {
    console.log('hello')
}
```

> exports 是 module.expores的一个引用