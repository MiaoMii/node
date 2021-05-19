```javascript

let g= feature.getGeometry(); 
 
//判断是不是线
if(g instanceof LineString)
{
    console.log(g);
}
//判断是不是点
else if(g instanceof Point)
{
    console.log(g);
}
//判断是不是面
else if(g instanceof Polygon)
{
    console.log(g);
}

```

