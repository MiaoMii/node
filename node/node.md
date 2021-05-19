### 模块
在nodejs种每个模块都有默认的`require`、`exports`、`module`三个与定义好的变量可供使用

##### require  
在当前模块中加载和使用别人的模块，模块名`.js`扩展名可以省略  
也可以用来加载一个json文件 

+ 如果是核心模块`fs`，就直接返回模块

+ 如果是带有路径的如`/`,`./`等等，则拼接出一个绝对路径，然后读取缓存`require.cache`再读取文件，如果没有加后缀，则自动加后缀后一一识别

  + `.js` 解析为Javascript文本文件

  + `.json`解析JSON对象

  + `.node`解析为二进制插件模块

    

+ 首次加载的模块会缓存在`require.cache`之中，所以多次加载`require`,得到的对象是同一个



###### exports  
用于导出当前模块方法或属性

###### module
可以访问到当前模块的一些信息，用途最多的是替换当前模块导出对象

主要流程：`require`之后解析路径，然后触发`Module`这个类，然后`Module`的`_load`方法就是在当前模块中创建一个新的`module`的缓存，保证下次`require` 不再执行直接返回,新的`module的load`方法通过VN执行代码返回给`require`

process对象  
提供了env属性该属性承载了启动进程时设置的所有环境变量  
// 访问NODE_ENV环境变量
process.env.NODE_ENV

argv属性，包含所有命令行调用参数数组
第一个参数是node命令的完整路径，第二个参数是正被执行的文件完成路径



<font color=red>nodejs是基于CommomJS模块规范实现的，所以可以直接使用require和exports这两个关键词来实现模块的导入和导出</font>



##### REPL(交互式解释器)

可以进行简单的表达式运算

`_`用来表示上一个表达式的结果 



##### 阻塞与非阻塞

> 阻塞-在`Node.js`程序中，其它JavaScript语句的执行，必须等待一个非JavaScript操作完成。

`Node.js`标准库中使用`libuv`的同步方法是最常用的阻塞操作

`Node.js`标准库中的所有`I/O`方法都提供异步版本，非阻塞，并且接受回调函数，某些方法也有对应的阻塞版本。名字以Sync结尾

```javascript
//阻塞	同步
const fs = require('fs');
const data = fs.readFileSync('./file.md');
```

```javascript
//非阻塞 异步
const fs = require('fs');
fs.readFile('/file.md',(err,data) => {
    if(err) throw err;
});
```

##### Buffer
> javaScript没有读取或操作二进制流的机制；Buffer类被用于在TCP流或文件系统操作等场景中处理二进制数据流  


`BUffer.from()`接口去创建Buffer对象

```javascript
const buf = Buffer.from('runoob','ascii');
console.log(buf.toString('hex'))
```

###### 写入缓冲区

buf.write(string[,offset][,length][,encoding])

+ string - 写入缓冲区的字符串
+ offset - 缓冲区开始写入索引值，默认0
+ length - 写入的字节数，默认为`buffer.length`
+ encoding - 使用的编码， 默认为`utf8`


含有node_moudles时 request引入模块时，会自动找模块文件夹下对应的 index.js
文件夹内含有package文件时会找文件对应的入口


包目录一般含有
+ package.json: 包描述文件
+ bin： 用于存放可执行二进制文件的目录
+ lib: 用于存放JavaScript代码的目录
+ doc: 文档
