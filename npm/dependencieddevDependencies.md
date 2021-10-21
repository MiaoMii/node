###### npm  5种依赖

+ dependencies 放置项目中代码运行时需要的用到的依赖
+ devDependencies  放置本地开发过程中需要使用到的编译、打包、测试、格式化等模块
+ peerDependencies  放置本模块需宿主环境提供的模块化依赖
+ bundledDependencies  数组格式，包含需要被打包进本地package里的依赖模块名，通过npm pack命令生成一个模块包
+ optionalDependencies 放置一些项目中可忽略其各种错误的包模块

###### 1.dependencies

```js
// 以axios为例
# 通过 npm 安装
npm install --save axios

# 通过 yarn 安装
yarn add axios
```

###### 2. devDependencies

```js
# 通过 npm 安装  
npm install --save-dev axios
# 通过 yarn 安装
yarn add -D axios
```

###### 3.peerDependencies  

```js
{
    "peerDependencies"  : {
        "react": ">=15"
    }
}
```

###### 4.bundledDependencies  

可有可无的配置

###### 5.optionalDependencies

``` js
# 通过 npm 安装  
npm install --save-optional axios
# 通过 yarn 安装
yarn add -O axios
```

