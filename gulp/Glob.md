##### Glob 

> 用于匹配文件路径

+ <font color=red>在glob中，分隔符永远是 `/`字符，不区分操作系统；`\\`字符被保留作为转义符使用</font>

+ <font color=red>需要避免使用path类方法来创建glob，同时也要避免使用`__dirname`和`__filename`全局变量，`process.cwd()`也要避免</font>

##### 特殊字符：*

`*.js`     能够匹配类似`index.js`

##### 特殊字符： **

`scripts/**/*.js`   能够匹配到scripts下所有js文件

##### 特殊字符：!

`['script/**/*.js', '!scripts/vendor/']`   取除了vendor以外的所有script下的js

`['script/**/*.js', '!script/vendor', 'script/vendor.react.js']`   任何非取反的glob跟着取反的glob，任何匹配项都不会被排除