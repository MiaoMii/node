绘制polygon坐标转换方法

```
let polygon = new ol.geom.Polygon(eval(polygonData.areaData.value))
polygon.applyTransform(ol.proj.getTransform('EPSG:4326', 'EPSG:3857'));
```