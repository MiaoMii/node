##### 1、安装prettier

```shell
npm install -g prettier
# 官方
npm install --save-dev --save-exact prettier
```

###### 2、安装插件配合ESLint

```shell
npm i -D eslint-plugin-prettier
```

##### 3、在eslintrc.js的rules中添加

```js
//.eslintrc.js
{
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  }
}
```

##### 5、关闭一些不必要或是与prettier冲突的lint选项

```shell
npm i -D eslint-config-prettier
```

```js
//.eslintrc.js
{
  extends: [
    'standard', //使用standard做代码规范
    "prettier",
  ],
}
```

