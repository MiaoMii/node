###  绘图

```
ol/interaction/Draw

```



### GeometryType  形状类型

| `POINT`               | 类型   | 默认            |
| --------------------- | ------ | --------------- |
| `LINE_STRING`         | string | LineString      |
| `LINEAR_RING`         | string | 线性环          |
| `POLYGON`             | string | 多边形          |
| `MULTI_POINT`         | string | 多点            |
| `MULTI_LINE_STRING`   | string | MultiLineString |
| `MULTI_POLYGON`       | string | 多多边形        |
| `GEOMETRY_COLLECTION` | string | 几何集合        |
| `CIRCLE`              | string | 圈              |

### 矢量图层取得feature

`vector.getSource().getFeatures()`

### 判断区域中是否包含点

`intersectsCoordinate`

### feature

>  绘制的要素的目标集合

### source

> 绘制的要素的目标图层源

### getGeometry 

> 获取默认几何属性

### originalEvent

默认浏览器事件

'EPSG:4326':WGS84经纬度球面坐标系，GPS坐标就是这种，如 118 32是南京。
'EPSG:3857':WGS84的墨卡托投影坐标系。