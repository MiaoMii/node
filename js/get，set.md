```javascript
let initArgs = {
    selectedData: {
        _tables: '',			// 属性使用 _ (下划线) 私有属性
        set tables(age) {
            console.log('SET',age)
            this._tables = age; // set方法中属性赋值需要使用私有属性，不然会导致 Uncaught RangeError: Maximum call stack size exceeded
        },
        get tables() {
            console.log('GET',this._tables)
            return this._tables;
        }
    },

    // set selectedData(age) {
    //     console.log('SET',age)
    //     this._selectedData = age;
    // },
    // get selectedData() {
    //     console.log('GET',this._selectedData)
    //     return this._selectedData;
    // }
}

Object.defineProperty(initArgs.selectedData,'tables',{
    set:function(age){
        console.log('SET',age)
        this._tables = age
    },
    get:function(){
        console.log('GET',this._tables)
        return this._tables
    }
})

```
