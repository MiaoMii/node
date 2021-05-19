# ol/proj投影转换详解



#### EPSG:4326与EPSG:3875

区别：通常数据存储在EPSG：4326中并像是在EPSG：3857中

​	<font color=red>将地理坐标转为投影坐标：`ol.proj.transform(pos, 'EPSG:4326', 'EPSG:3857')`</font>

#### 常用方法：

`transform(coordinate, source, destination)`

> 将坐标从源投影转换为目标投影。这将返回一个新坐标

`transformExtent(extent, source, destination)`

> 将范围从源投影转换为目标投影。这将返回一个新的范围

`fromLonlat(coordinate, target_projection)`

> 将坐标从经度/纬度转换为target_projection参数指定的投影。

` toLonlat(coordinate, curr_projection="EPSG:3857")`

> 将坐标转换为经纬度

`get( projectionLike )`

> 获取当前代码的投影影像

`addProjection( projection )`

> 将投影对象添加到可由其它代码查找的受支持的投影列表中

`equivalent`

> 检查两个投影是否相同

`addEquivalentProjections(projections)`

> 注册坐标转换函数以转换