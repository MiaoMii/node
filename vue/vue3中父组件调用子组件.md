子组件

```js
// child.vue
function setFormValues () {}

defineExpose({
  setFormValues,
});
```

父组件

```js
<template>
	<Child ref="child" />
</template>
<script>
     import {ref} from 'vue'
	const child = ref()
     child.value.setFormValues();
</script>
```

