```  js
// good 
const original = {a: 1, b: 2}
const copy = {...original, c: 3}
const {a, ...noA} = copy //noA = {b: 2, c: 3}
```

