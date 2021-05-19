##### 创建器

###### 1、of 单一值转为流 `of(1,2,3)`

###### 2、from 数组转为流`from([10,20,30])`

###### 3、range 范围转为流`range(1,10)`

###### 4、fromPromise Promise转为流

###### <font color=red>注意：当Promise作为参数传入时，这个Promise就已经执行了，你没有机会防止他被执行</font>

###### 5、defer 惰性创建流`defer(() => Observable.of(a,b,c))`

> 当消费方需要流时，就会调用这个函数，创建一个流并从中取数据

###### 6、timer 定时器流`timer(3000,1000)`

第一个参数是首次等待时间，第二个参数是重复间隔时间

###### 7、interval 定时器流 `interval(1000)`

和timer的唯一差别是它直接收一个参数，相当于timer(1000,1000)

##### Sunject 主体对象

> 实现了一个Observable接口的类

##### 合并创建器

###### 1、merge并联

例子：有一个列表需要每隔 5 秒钟定时刷新一次，但是一旦用户按了搜索按钮，就必须立即刷新，而不能等待 5 秒间隔。这时候就可以用一个定时器流和一个自定义的用户操作流（subject）merge 在一起。这样，无论哪个流中出现了数据，都会进行刷新。

![merge](E:\project\vue-blog-ts\src\assets\note\rxjs\imgs\merge.png)



###### 2、concat串联

例子：先通过 Web API 进行登录，然后取学生名册

###### ![concat](E:\project\vue-blog-ts\src\assets\note\rxjs\imgs\concat.png)



###### 3、zip拉链

例子：一个流中是姓名，另一个流中是成绩，还有一个流中是年龄，如果这三个流中的每个条目都有精确的对应关系，那么就可以通过 zip 把它们合并成一个由表示学生成绩的对象组成的流。

![zip](E:\project\vue-blog-ts\src\assets\note\rxjs\imgs\zip.png)

##### 操作符

###### 1、retry 失败时重试 `retry(2)`

接受一个参数用于指定最大重试次数

###### 2、repeat 成功时重试 `repeat(3)`

###### 3、delay 延迟 `delay(20)`

等价于setTimeout，接受一个毫秒数

###### 4、toArray 收集为数组 

可以看作是from的逆运算，from十八数组打散放入流中，toArray是将流中内容收集到数组中

###### 5、debounceTIme 防抖 `debounceTIme （20）`

###### 6、 switchMap 切换成另一个流

例子：流中是一些学生的 id，每过来一个 id，你要发起一个 Ajax 请求来根据这个 id 获取这个学生的详情，并且把详情放进输出流中。