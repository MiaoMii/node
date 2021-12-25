#### setup

新增setup生命周期函数，在beforeCreated之前执行，因此函数中不能使用this

beforeDestroy 修改为 beforeUnmount ， destroyed 修改为unmounted

#### 新增钩子函数

onBeforeMounted

onMounted

onBeforeUpdate

onUpdate

onBeforeUnmount

onErrorCaptured

onRenderTracked

onRenderTriggered

#### ref 与 toRef、toRefs

> 两者都可用于创建一个响应式数据

###### ref

> 可以将某个对象中的属性变成响应式的，<font color=red>修改响应式数据不会影响到原始数据</font>

###### toRef、toRefs

> 可以将某个对象中的属性变成响应式的，修改响应式数据会影响到原始数据

```js
import {onBeforeMount, ref, toRef, toRefs} from "vue";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      count: 0
    }
  },
  /*  接收一个响应式props
  *   不能使用解构赋值，会消除props的响应式
  *   可以使用toRefs const { title } = toRefs(props)
  */
  setup(props) {
    console.log('------------', 'setup');
    onBeforeMount(() => {
      // beforeMount代码执行
    });

    // ref
    let obj = {name: 's', age: 20}
    let newObj = ref(obj.name)

    //toref
    let torefObj = {name: 's', age: 20}
    let newTorefObj = toRef(torefObj, 'name')

    //torefs
    let torefsObj = {name: 's1', age: 20}
    let newTorefsObj = toRefs(torefsObj)

    function change() {
      // ref
      newObj.age = 10

      //toref
      newTorefObj.value = 'Tom';

      //torefs
      newTorefsObj.name.value = 'Tom';
      newTorefsObj.age.value = 18;



      console.log('-----------------obj',obj);
      console.log('-----------------newObj',newObj);
      console.log('-----------------torefObj',torefObj);
      console.log('-----------------newTorefObj',newTorefObj);
      console.log('-----------------torefsObj',torefsObj);
      console.log('-----------------newTorefsObj',newTorefsObj);
    }

    // 暴露给 template
    return {newObj, change}
  },
  beforeCreate() {
    console.log('------------', 'beforeCreate');
  },
  created() {
    console.log('------------', 'created');
  },
  beforeMount() {
    console.log('------------', 'beforeMount');
  },
  mounted() {
    this.change()
    console.log('------------', 'mounted');
  },
  beforeUpdate() {
    console.log('------------', 'beforeUpdate');
  },
  updated() {
    console.log('------------', 'updated');
  },
  beforeUnmount() {
    console.log('------------', 'beforeUnmount');
  },
  unmounted() {
    console.log('------------', 'unmounted');
  }
}
```

#### vue3中 v-for 绑定ref需要绑定在更灵活的函数上

```js
<div v-for="item in list" :ref="setItemRef"></div>

export default {
  data() {
    return {
      itemRefs: []
    }
  },
  methods: {
    setItemRef(el) {
      if (el) {
        this.itemRefs.push(el)
      }
    }
  },
  beforeUpdate() {
    this.itemRefs = []
  },
  updated() {
    console.log(this.itemRefs)
  }
}


import { onBeforeUpdate, onUpdated } from 'vue'

export default {
  setup() {
    let itemRefs = []
    const setItemRef = el => {
      if (el) {
        itemRefs.push(el)
      }
    }
    onBeforeUpdate(() => {
      itemRefs = []
    })
    onUpdated(() => {
      console.log(itemRefs)
    })
    return {
      setItemRef
    }
  }
}
```

#### attribute属性为false时会强制转换为‘false’，而不是删除该属性

#### 移除$children属性，访问子组件实例用$ref
