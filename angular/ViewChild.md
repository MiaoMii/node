#### ViewChild 属性
> 属性装饰器，用于配置视图查询。变更检测器会在视图DOM中查找能匹配该选择弃的第一个指令

在调用NgAfterViewInit回调函数之前就会设置这些视图查询



+ selector 指令类型或名字
+ read 从查询到的元素中读取另一个令牌
+ static  true时则在变更检测运行之前解析查询结果，false则在变更检测之后解析。默认为false