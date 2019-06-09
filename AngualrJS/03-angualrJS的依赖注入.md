> ## angular 的 “依赖注入”
- 依赖注入是一种软件设计模式，目的是处理代码之间的依赖关系，减少组件间的耦合。
- 原理：AngularJS 是通过构造函数的参数名字来推断依赖服务名称的，通过 toString() 来找到这个定义的 function 对应的字符串，然后用正则解析出其中的参数（依赖项），再去依赖映射中取到对应的依赖，实例化之后传入。
- 用法：
    + 数组注释法
    ```javascript
        myApp.controller('myCtrl', ['$scope','$http',function($scope, $http){
            ...
        }])
    ```