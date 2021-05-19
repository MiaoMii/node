####### 下载安装包

```shell
sudo mkdir /usr/app
cd /usr/app
wget https://nodejs.org/dist/v10.15.1/node-v10.15.1-linux-x64.tar.xz
tar xvf node-v10.15.1-linux-x64.tar.xz
sudo vim /etc/profile
// 增加
export NODE_HOME=/usr/app/node-v10.15.1-linux-x64
export PATH=$NODE_HOME/bin:$PATH

node -v 
npm -v //查看是否安装成功
```

