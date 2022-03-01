#### tabindex

+ `tabindex="-1"`表示元素是可聚焦的，但是不能通过tab导航访问到该元素，可以通过js获取。

+ `tabindex="0"`表示元素是可聚焦的，可以通过tab导航来聚焦到该元素，若一个元素没有设置tabindex，默认为0

+ `tabinde > 0`标识该元素可聚焦，它的相对顺序按照tabindex的数值递增而滞后获焦（先获取小的），如多个元素具有相同的tabindex，则按在dom中的先后顺序决定

  > `tabindex`的最大值不应该超过32767

#### activeElement

+ 返回当前页面中获得焦点的元素，该属性是只读的
+ 页面加载中，`document.activeElement` 为 `null`
+ 页面刚刚加载完成，`document.activeElement`  为` body`元素的引用





#### tab

使用`tab`键来根据`tabindex`的定义来切换焦点



#### focus()

```js
document.getElementById("id").focus();
document.getElementById("id").focus({preventScroll:false});
```

+ `preventScroll`默认为`false`，表示当触发时，浏览器会将元素滚动到视图中
+ `preventScroll`为`true`，则不发生滚动
+ 非表单元素，须设置`tabindex="-1"`



#### autofocus

该属性会使元素在页面加载时会自动获得焦点，除非用户覆盖它

设置多个，则会将第一个拥有该属性的元素设为初始焦点

该属性只能用于表单元素



#### 判断焦点 hasFocus()

如果当前页面的活动元素获得了焦点，Document.hasFocus() 返回 true，否则为 false。

#### 取消焦点 blur()

`blur()` 会将焦点从元素中移走，并不是转移到其他特定元素上。

#### 焦点事件

```js
element.onfocus = function(){}
element.onblur = function(){}
element.onfocusin = function(){}
element.onfocusout = function(){}

element.addEventListener("focus", function(){})
element.addEventListener("blur", function(){})
element.addEventListener("focusin", function(){})
element.addEventListener("focusout", function(){})
```

- `focus` ：在元素获取焦点时触发，不支持冒泡
- `focusin` ：在元素获取焦点时触发，支持冒泡
- `blur` ：在元素失去焦点时触发，不支持冒泡
- `focusout` ：在元素失去焦点时触发，支持冒泡

