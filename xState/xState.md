##### createMachine() 状态机工厂定义函数

```js
const lightMachine = createMachine(
  {
    id: 'light',
    initial: 'green',
    states: {
      green: {
        // 通过字符串引用 action
        entry: 'alertGreen'
      }
    }
  },
  {
    actions: {
      // action 执行
      alertGreen: (context, event) => {
        alert('Green!');
      }
    },
    activities: {
      /* ... */
    },
    delays: {
      /* ... */
    },
    guards: {
      /* ... */
    },
    services: {
      /* ... */
    }
  }
);
```

+ `actions` action名称到它们执行的映射
+ `activities` activities名称与其执行的映射
+ `delays` delays名称与执行的映射
+ `guards` 转换守卫（cond），名称与其执行的映射
+ `services` 调用的服务（sec），名称与其执行的映射

##### withContext 扩展context

<font color=red>注：</font>这 *不会* 对原始 `context` 进行浅层合并，而是将原始 `context` 替换为 `.withContext(...)` 的 `context`。 你仍然可以通过引用 `machine.context` 手动“合并”上下文：

```js
const testLightMachine = lightMachine.withContext({
  // 合并原始 context
  ...lightMachine.context,
  elapsed: 1000
});
```

##### State

`State`对象实例时JSON可序列化的

+ `value` -当前状态的值
+ `context` -当前状态的context
+ `event` -触发转换到此状态的事件对象
+ `actions` -要执行的动作数组
+ `activities` -如果活动开始，则活动映射到`true`，如果活动停止，则映射false
+ `history` -上一个`State`实例
+ `meta` -在状态节点的元属性上定义的任何静态元数据
+ `done` -状态是否标识最终状态

`state.matches(parentStateValue)` 确定当前 `state.valye` 是否是给定的 `parentStateValue`的子集

```js
console.log(state.value) // {red: 'stop'}
console.log(state.matches('red')); //true
console.log(state.matches('red.stop')); //true
console.log(state.matches({ red: 'stop' })); //true
console.log(state.matches('green'));
```

`state.nextEvents`从当前事件转换到下一个事件



















##### 状态机 `.transition` 方法

`machine.transition(...)` 方法是一个纯函数 接收两个参数

+ state 要转换的状态
+ event 要转换的事件

