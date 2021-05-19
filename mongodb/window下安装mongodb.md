###### 1.官网下载

https://www.mongodb.com/try/download/community

###### 2.安装至指定路径

###### 3.在路径下创建`mongodb.config`文件，并添加以下内容

```config
dbpath=D:\Program Files\MongoDB\Server\data\db			#数据库路径

logpath=D:\Program Files\MongoDB\Server\log\mongod.log	#日志输出文件路径

logappend=true										#错误日志采用追加模式

journal=true										#启用日志文件，默认启用

quiet=true 											#过滤掉无用的日志信息，若需要调试使用请设置为false

port=27017 											#端口号 默认为27017

```



###### 4.添加系统环境变量

G:\mongodb\bin

