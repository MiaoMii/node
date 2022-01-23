```js
const mixin  = {
    data() {
        return {
            message: 'hello'
        }
    }，
    created() {
    console.log('混入对象的钩子被调用')
  }
}
new Vue({
    mixins: [mixin],
    data() {
    	return {
            message: "world"
        }	
	},
    created(){
        console.log(this.$data.message) // world
    }
})
```

