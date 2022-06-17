#### 响应式声明`ref`与`reactive`

##### 1.ref

> 与`reactive`一样，是用来实现响应式数据的方法
>
> 本质上还是`reactive ref(xx)  -> reactive({value: xx})`

+ `vue`是通过当前数据的 `__v_ref`为`true`来判断是否为`ref`类型的

<font color=red>注意：`vue`中使用ref的值不用通过value获取</font>

##### 2.reactive

> 创建一个响应式数据
>
> 本质上是将传入的数据包装成一个Proxy对象

<font color=red>注意：`reactive`的参数必须是一个对象或者数组</font>

##### 3.区别

+ `template`中使用`ref`类型`vue`会自动追加 `.value`,`reactive`类型不会自动添加 

#### ref与toRef

##### 1.区别

+ `ref`的本质是拷贝，修改响应式数据不会影响原始数据；`toRef`的关系是引用
+ `ref`的数据发生改变，界面会自动更新；`toRef`的不会自动更新
+ `toRef`接收两个参数一个是对象一个是对象的属性

`toRef`应用场景：

如果想让响应式数据和以前的数据关联起来，并且更新数据后不想更新`ui`则可以使用`toRef`

#### toRefs函数

可以将`reactive`创建出来的响应式对象，转成普通对象，但改对象的每个属性都是`ref`响应式数据

#### shallowReactive与shallowRef

shallowReactive： 只处理对象最外层属性的响应式

shallowReactive:  只处理基本数据类型的响应式，不进行对象的响应式