###### 1.执行多个命令

```shell
npm insatll -g concurrently
"start": "concurrently \"npm run json_server\" \"npm run server\" ",
```

###### 2.在某个命令之后执行

```shell
 "startBrowserIP": "concurrently \"npm  run packBrowserIP\" \"npm  run pelListCreater\" && node utils/release/release.js",
```

