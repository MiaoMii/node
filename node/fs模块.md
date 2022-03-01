#### readdirSync

> 同步返回结果

```js
var readDir = fs.readdirSync('testFileName');
console.log(readDir);
```

#### readdir

> 异步回调返回结果

```
fs.readdir('testFileName', function(err,files){
 if(err){
  console.log(err);
 }
 console.log(files);
})
```

