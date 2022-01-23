**Element.scrollTop**

> 获取或设置一个元素的内容垂直滚动的像素数
>
> 一个元素的`scrollTop`值是这个元素内部顶部到它的视口可见内容的距离
>
> 当一个元素的内容没有产生垂直方向的滚动条，那它的`scrollTop`值为0



**Element.offsetTop**

> 只读属性，返回当前元素对于其最近的`offsetParent`元素的顶部内边距距离
>
> `offsetParent`只离自己最近的position的值为relative，absolute，fixed



**Element.clientHeight**

> 只读属性，对于没有定义css或者内联布局盒子的元素为0，否则，他是内部元素的高度，包含内边距，<font color=red>但不包括水平滚动条、边框和外边距</font>

![clientWidth](E:\project\vue-blog-ts\src\assets\note\css\clientWidth.png)



**Element.offsetHeight**

> 返回该元素的像素高度、高度包含该元素的边框、内边距和元素的水平滚动条（存在且不渲染），不包含:before或:after等伪类元素的高度

![offsetWidth](E:\project\vue-blog-ts\src\assets\note\css\offsetWidth.png)



```
<body>
<div id="testParent" style="position: absolute;width:100%;height:500px;background: #1B96EE;overflow-y: scroll">
    <div id="testBox" style="height: 2000px;width: 1700px;margin: 10px 86px;background: salmon;border: 4px salmon solid;padding:20px;"></div>
</div>
</body>
<script>


const node = document.getElementById('testBox')
const nodeParent = document.getElementById('testParent')
nodeParent.onscroll = function (e) {
    console.log('nodeParent.scrollTop',nodeParent.scrollTop)
    console.log('node.scrollTop',node.scrollTop)
    console.log('scrollHeight-clientHeight',nodeParent.scrollHeight-nodeParent.clientHeight)
}

console.log('clientTop',node.clientTop)             //元素到顶部边框的宽度，不包含外边距（margin）内边距（padding）
console.log('clientLeft',node.clientLeft)            //一个元素左边框的宽度
console.log('nodeParent clientHeight',nodeParent.clientHeight)          //内部元素高度,包含内边距
console.log('clientHeight',node.clientHeight)          //内部元素高度,包含内边距，视窗大小（不包含溢出的内容）
console.log('clientWidth',node.clientWidth)           //内部元素宽度
console.log('offsetWidth',node.offsetWidth)           //内部元素长度，包含内边距及边框
console.log('offsetHeight',node.offsetHeight)           //内部元素宽度，包含内边距及边框
console.log('offsetTop',node.offsetTop)           //margin top的值
console.log('offsetLeft',node.offsetLeft)           //margin left的值
console.log('scrollHeight',node.scrollHeight)           //内部元素高度，包含内边距及溢出的不可见的内容，但不包含border
console.log('nodeParent scrollHeight',nodeParent.scrollHeight)           //内部元素高度，包含内边距及溢出的不可见的内容，但不包含border
console.log('scrollWidth',node.scrollWidth)           //元素的宽度，包含内边距及溢出的不可见的内容，但不包含border
console.log('scrollLeft',node.scrollLeft)           //可以读取或设置元素滚动条到元素左边的距离
console.log('scrollTop',node.scrollTop)           //元素垂直滚动的像素
console.log('nodeParent scrollTop',nodeParent.scrollTop)
```



![	](E:\project\vue-blog-ts\src\assets\note\css\scrollTop.jpeg)





#### offsetLeft 距离第一个非static布局元素的距离

```js
getBoundingClientRect {
    bottom: 180 		 // 元素下边距离页面上边的距离
	height: 150
	left: 30
	right: 180			/元素右边距离页面左边的距离
	top: 30
	width: 150
	x: 30
	y: 30
}
```

