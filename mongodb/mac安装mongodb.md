###### 1.官网安装https://www.mongodb.com/try/download/community
######  2.解压文件
###### 3.移动解压文件至 usr/loacl （open usr/local）并修改文件名为mongodb
###### 4. sudo mkdir -p /usr/local/var/mongodb //建立数据存储文件夹
###### 5. sudo mkdir -p /usr/local/var/log/mongodb
###### 6. sudo chown siyanan /usr/local/var/mongodb
###### 7. sudo chown siyanan /usr/local/var/log/mongodb
###### 8. mongod --dbpath /usr/local/var/mongodb --logpath /usr/local/var/log/mongodb/mongo.log --fork
+ --dbpath 设置数据存放目录
+ --logpath 设置日志存放目录
+ --fork 在后台运行


sudo pkill mongo.  //杀死mongo进程


如果MongoDB是通过HOMEBREW安装的，默认位置是：

/usr/local/var/mongoDB
