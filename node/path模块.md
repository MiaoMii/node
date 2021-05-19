###### 1、path.resolve([from...], to)

> 将to参数解析为绝对路径

```js
var path = require("path")     //引入node的path模块

path.resolve('/foo/bar', './baz')   // returns '/foo/bar/baz'
path.resolve('/foo/bar', 'baz')   // returns '/foo/bar/baz'
path.resolve('/foo/bar', '/baz')   // returns '/baz'
path.resolve('/foo/bar', '../baz')   // returns '/foo/baz'
path.resolve('home','/foo/bar', '../baz')   // returns '/foo/baz'
path.resolve('home','./foo/bar', '../baz')   // returns '/home/foo/baz'
path.resolve('home','foo/bar', '../baz')   // returns '/home/foo/baz'
path.resolve('home', 'foo', 'build','aaaa','aadada','../../..', 'asset') //return '/home/foo/asset'
```

<font color=red>从后向前，若字符以 / 开头，不会拼接到前面的路径；若以 …/ 开头，拼接前面的路径，且不含最后一节路径；若连续出现多个…/…/…或者…/…则忽略前方…个路径名进行拼接；若以 ./ 开头 或者没有符号 则拼接前面路径；</font>

###### 2、path.relative(from, to)

> 将绝对路径转为相对路径