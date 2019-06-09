> ## vue组件间通信方式

1. props
2. vue的自定义事件
3. 消息订阅与发布（如： pubsub库）
4. slot
5. vuex

---
### 1. **props**
- 父组件向子组件传递数据
- 使用组件标签时：
```html
    <my-component name='tom' :age='3' :set-name='setName'></my-component>
```
- 定义 MyComponent 时
    + 在组件内声明所有的props
    + 方式一： 只指定名称
    ```javascript
        props: ['name','age','setName']
    ```
    + 方式二： 指定名称和类型
    ```javascript
        props: {
            name: String,
            age: Number,
            setName: Function
        }
    ```
    + 方式三： 指定名称/类型/必要性/默认值
    ```javascript
        props: {
            name: {type: String, required: true, default:xxx}
        }
    ```

### 2. **vue的自定义事件**
- 用户子组件向父组件传递数据
- 2.1 绑定事件监听
 + 方式一： 通过 `v-on`绑定
 ```javascript
    @delete_todo="deleteTodo"
 ```
 + 方式二： 通过`$on()`
```javascript
    this.$refs.xxx.$on('delete_todo', function (todo) {
        this.deleteTodo(todo)
    })
```
- 2.2 触发事件（只能在父组件接收）
```javascript
 this.$emit(eventName,data)
```

### 3. **消息订阅与发布(PubSubJS 库)**
- 此方法可以实现任意关系组件间的通讯
- 3.1 订阅消息
```javascript
    PubSub.subscribe('msg',function(msg,data){})
```
- 3.2 发布消息
```javascript
    PubSub.publish('msg',data)
```

- 深入理解：
+ 绑定事件监听 (订阅消息)
```
    目标: 标签元素 <button>
    事件名(类型): click/focus
    回调函数: function(event){}
```
+ 触发事件 (发布消息)
```
    DOM 事件: 用户在浏览器上对应的界面上做对应的操作
    自定义: 编码手动触发
```

### 4. **slot**
- 用于父组件向子组件传递`标签数据`
- 子组件: Child.vue
```html
<template>
    <div>
        <slot name="xxx">不确定的标签结构 1</slot>
        <div>组件确定的标签结构</div>
        <slot name="yyy">不确定的标签结构 2</slot>
    </div>
</template>
```
- 父组件: Parent.vue
```javascript
<child>
    <div slot="xxx">xxx 对应的标签结构</div>
    <div slot="yyy">yyyy 对应的标签结构</div>
</child>
```




---
> 以上参考来源：尚硅谷