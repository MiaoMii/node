##### 定义变量

```shell
variable=value
variable='value'
variable="value"
```

如果`value`不包含任何空白符(例如空格、Tab缩进等)可以不适用引号

<font color=red>注意，赋值号`=`的周围不能有空格</font>

+ 变量名由数字、字母、下划线组成
+ 必须以字母或者下划线开头
+ 不能使用shell里的关键字

##### 使用变量

使用一个定义过的变量只需要在变量前加美元`$`即可

变量名外的`{}`是可选的，用于识别变量的边界

```shell
skill='Java'
echo 'I am good at ${skill}Script'
```

##### 单引号和双引号的区别

单引号包围变量的值时，单引号里面是什么就输出什么，双引号包围变量时会优先解析里面的变量和命令

##### 将命令结果赋值给变量

```shell
variable=`command`
variable=$(command)
# 例子
log=$(cat log.txt)
log=`cat log.txt`
echo $log 
```

##### 只读变量

`readonly`

```shell
myName="张三"
readonly myName
```

##### 删除变量

`unset variable_name`