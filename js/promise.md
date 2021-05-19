##### Promise.all(iterable)

参数：

**iterable**

​	一个可迭代对象，如`Array`或`String`

完成：
如果传入迭代对象为空，Promise.all会同步的返回一个已完成状态的promise

如果所有传入的promise都变成完成状态，Promise.all返回的promise异步的变成完成

任何情况下promise.all返回的promise都是一个数组

失败：

如果传入的promise中有一个失败，Promise.all会将错误信息异步的传给失败的回调函数，<font color=red>不管其它promise是否执行完成</font>