> ## 关于AngularJs中监听事件及脏循环的理解 
### 1. $watch是一个scope函数，用于监听模型变化，当你的模型部分发生变化时它会通知你。
    ```javascript
        $watch(watchExpression, listener, objectEquality);   
    ```

- watchExpression（必须）：监听的对象，它可以是一个string，将被计算为表达式 ,或函数如function(){return $scope.name}。
- listener:当watchExpression（监听对象）变化时会被调用的函数或者表达式,它接收3个参数：newValue(新值), oldValue(旧值), scope(作用域的引用)
- objectEquality：是否深度监听，如果设置为true,它告诉Angular检查所监控的对象中每一个属性的变化. 如果你希望监控数组的个别元素或者对象的属性而不是一个普通的值, 那么你应该使用它。

### 2. 脏检查
- Angular会运行一个函数$digest来检查scope模型中的数据是否发生了变化。 在$digest循环中，watchers会被触发。当一个watcher被触发时，AngularJS会检测它所监听的scope模型，如果监听对象发生了变化那么关联到该watcher的回调函数就会被调用。
- 在angular程序初始化时，会将绑定对象的属性添加为监听对象（watcher），也就是说一个$scope对象绑定了N个属性，就会添加N个watcher。 angular什么时候去脏检查呢？angular所定义的方法中都会触发$digest事件，比如：controller初始化的时候，所有以ng-开头的指令执行后，都会触发脏检查 用户与视图发生交互行为以后会触发脏检查。