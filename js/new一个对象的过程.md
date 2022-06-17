#### js new一个对象的过程

+ 创建一个空对象
+ 连接原型
+ 绑定this到新对象
+ 执行构造函数
+ 返回新对象

```js
function newObject() {
    // 创建一个新对象
    let obj = {}
    // 取出第一个参数并获取构造函数
    let constructor = [].shift.call(arguments)
    // 连接原型
    obj._proto_ = constructor.prototype
    // 执行构造函数，即绑定this，并且为这个新对象添加属性
    let res = constructor.apply(obj, arguments)
    // 返回新对象
    return typeof res === "object" ? res: obj
}
```



构造函数中的`this`,只要返回**基本数据类型**，那么`this`指向**当前实例**，如果返回的是**引用类型**则指向返回的**引用类型**

```js
function fn () {
    this.user = "test"
    return {}
}
let a = new fn()
console.log(a.user)
```

