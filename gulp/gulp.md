##### 安装

```js
npm install --global gulp-cli   //全局安装 gulp-cli
npm install --save-dev gulp     //项目安装
```

##### gulpfile

> 任何导出的函数都将注册到gulp的任务系统中

+ 对于TypeScript，重命名为gulpfile.ts安装ts-node

+ 对于Babel，重命名为gulpfile.babel.js

  可以使用gulpfile.js目录分割成多个任务，该目录中需包含index.js文件

##### 创建任务

> 每个gulp任务都是一个异步的JavaScript函数

+ 公开任务 从gulpfile中被导出，可以通过gulp命令直接调用
+ 私有任务 被设计在内部使用，通常作为series()或者parallel()组合组成部分；不被导出的任务被称为私有任务，可以用在series()中

##### 组合任务

> series() 和 parallel() ；它们之间可以互相嵌套至任意深度

###### 任务按顺序执行 series()

```js
const { series } = require('gulp');

function transpile(cb) {
  // body omitted
  cb();
}

function bundle(cb) {
  // body omitted
  cb();
}

exports.build = series(transpile, bundle);

```



###### 处理大量并发运行任务 parallel()

```js
const { parallel } = require('gulp');

function javascript(cb) {
  // body omitted
  cb();
}

function css(cb) {
  // body omitted
  cb();
}

exports.build = parallel(javascript, css);
```

###### 可以嵌套至任意深度

```js
const { series, parallel } = require('gulp');

function clean(cb) {
  // body omitted
  cb();
}

function cssTranspile(cb) {
  // body omitted
  cb();
}

function cssMinify(cb) {
  // body omitted
  cb();
}

function jsTranspile(cb) {
  // body omitted
  cb();
}

function jsBundle(cb) {
  // body omitted
  cb();
}

function jsMinify(cb) {
  // body omitted
  cb();
}

function publish(cb) {
  // body omitted
  cb();
}

exports.build = series(
  clean,
  parallel(
    cssTranspile,
    series(jsTranspile, jsBundle)
  ),
  parallel(cssMinify, jsMinify),
  publish
```



```JS
// This is INCORRECT
const { series, parallel } = require('gulp');

const clean = function(cb) {
  // body omitted
  cb();
};

const css = series(clean, function(cb) {
  // body omitted
  cb();
});

const javascript = series(clean, function(cb) {
  // body omitted
  cb();
});

exports.build = parallel(css, javascript);

// 重构为
const { series, parallel } = require('gulp');

function clean(cb) {
  // body omitted
  cb();
}

function css(cb) {
  // body omitted
  cb();
}

function javascript(cb) {
  // body omitted
  cb();
}

exports.build = series(clean, parallel(css, javascript));
```

##### gulp-htmlmin

> 压缩html的插件

```js
const htmlmin = require('gulp-htmlmin');
gulp.task('testHtmlmin', () => {
    gulp.src('src/html/*.html').pipe(htmlmin({
		removeComments: true,		//清楚注释
         collapseWhitespace: true,	//压缩HTML
        collapseBooleanAttributes: true, //省略布尔属性的值 <input checked="true"/> ==> <input />
        removeEmptyAttributes: true, // 删除所有空格作属性值 <input id="" /> ==> <input />
    	 removeScriptTypeAttributes: true,//删除<script>的type="text/javascript"
        removeStyleLinkTypeAttributes: true,//删除<style>和<link>的type="text/css"
        minifyJS: true,//压缩页面JS
        minifyCSS: true//压缩页面CSS
    })).pipe(gulp.dest('dist/html'))
})
```

