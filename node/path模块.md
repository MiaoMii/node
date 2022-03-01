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

###### 3、path.basename(path[, ext])

> 返回`path`的最后一部分

+ `path` <string>
+ `ext` <string>可选的文件扩展名
+ 返回 <string>

```shell
path.basename("./test/test/test/index.js")
// 返回： "index.js"
```

###### 4、path.dirname(path)

> 返回path的目录名

+ `path` <string>
+ 返回： <string>

```shell
path.dirname("/test/test/test/index.js")
// 返回 "/test/test/test"
```

###### 5、path.extname(path)

> 返回path的扩展名, 即`path`的最后一部分中从最后出现的 `.`字符到字符串的结尾。如果 `path`的最后一部分没有`.`,或者除了`path`的基本名称的第一个字符串之外没有`.`个字符，则返回空字符串

```shell
path.extname("index.html")
// 返回: '.html'

path.extname("index.coffee.md")
// 返回：".md"

path.extname("index.")
// 返回："."

path.extname("index")
// 返回 ""

path.extname(".index")
// 返回：''


```

###### 6、`path.format(pathObject)`

> 从对象返回路径字符串

- `dir` <string>
- `root` <string>
- `base` <string>
- `name`<string>
- `ext` <string>

```shell
// 如果提供 `dir`、`root` 和 `base`，
// 则将返回 `${dir}${path.sep}${base}`。
// `root` 将被忽略。
path.format({
  root: '/ignored',
  dir: '/home/user/dir',
  base: 'file.txt'
});
// 返回: '/home/user/dir/file.txt'

// 如果未指定 `dir`，则将使用 `root`。
// 如果仅提供 `root` 或 `dir` 等于 `root`，则将不包括平台分隔符。
// `ext` 将被忽略。
path.format({
  root: '/',
  base: 'file.txt',
  ext: 'ignored'
});
// 返回: '/file.txt'

// 如果未指定 `base`，则将使用 `name` + `ext`。
path.format({
  root: '/',
  name: 'file',
  ext: '.txt'
});
// 返回: '/file.txt'
```

###### 7、`path.isAbsolute(path)`

> 判断path是否为绝对路径
>
> ```shell
> path.isAbsolute('//server');    // true
> path.isAbsolute('\\\\server');  // true
> path.isAbsolute('C:/foo/..');   // true
> path.isAbsolute('C:\\foo\\..'); // true
> path.isAbsolute('bar\\baz');    // false
> path.isAbsolute('bar/baz');     // false
> path.isAbsolute('.');           // false
> ```
>
> 

##### 8、`path.join([...paths])`

> `path`方法会使用特定于平台的分隔符将所有给`path`的片段连接到一起

注意：零长度的`path`片段会被忽略。如果连接的路径字符串是零长度的字符串，则将返回 `'.'`，表示当前工作目录。

```shell
path.join('/foo', 'bar', 'baz/asdf', 'quux', '..');
// 返回 /foo/bar/baz/asdf 

path.join('foo', {}, 'bar');
// 抛出 'TypeError: Path must be a string. Received {}'
```

###### 9、`path.normalize(path)`

> 规范化给定的`path`，解析 `'..'` 和 `'.'` 片段。

