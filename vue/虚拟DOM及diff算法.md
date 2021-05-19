#### 浏览器解析html的步骤

创建DOM tree –> 创建Style Rules –> 构建Render tree –>布局Layout–> 绘制Painting

每次对真是DOM进行操作时都会重头执行一遍流程，虚拟DOM就是为了解决这个浏览器性能问题才被创造出来的

> 虚拟DOM时将真是的DOM节点用js模拟出来的，将DOM变化的对比放在js层

优势：

+ 跨平台
+ 提高DOM操作效率
+ 提升渲染性能

### vue中模版转换成视图的过程

![vue中模板转换成试图的过程](E:\project\vue-blog-ts\src\assets\note\vue\vue中模板转换成试图的过程.png)



> diff算法是一种优化手段，将前后两个模块进行差异对比，修补（更新）的过程叫做patch
>
> patch：
>
> 它可以将vnode渲染成真是的DOM，这个过程时对比新旧虚拟节点之间有那些不同，然后根据对比结果找出需要更新的节点进行更新