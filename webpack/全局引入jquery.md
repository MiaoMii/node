在webpack.config文件中添加以下代码

```js
plugins： [
    ...
    new webpack.ProvidePlugin({
      $: 'jquery',
      jQuery: 'jquery',
      "window.jQuery": "jquery",
      Popper: ['popper.js', 'default'], //用于bootstrap4
    })
]
```

