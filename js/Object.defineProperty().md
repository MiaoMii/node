#### Object.defineProperty

+ `configurable`， 为`true`该属性值可被修改同时可被删除，**默认`false`**
+ `enumerable`，该属性为`true`，才会出现在对象的枚举属性中，**默认为`false`**
+ `value`，属性的值，**默认为`undefined`**
+ `writable`，该属性为`true`时，`value`的值才能被修改，**默认为`false`**
+ `get`，属性的getter函数，当访问该属性时，会调用此函数，执行时不传入任何参数，但是会传入`this`对象，该函数的返回值会被用作属性的值，**默认为`undefined`**

+ `set`,属性的setter函数，当属性值被修改时，会调用此函数。该方法接受属性被赋予的新值，会传入赋值时的`this`对象，**默认为`undefined`**

