> ## angularjs和vue的区别
- AngularJS
    + 1、MVVM（Model）(View)(View-model)；
    + 2、模块化（Module）控制器（Contoller）依赖注入；
    + 3、双向数据绑定：界面的操作能实时反映到数据，数据的变更能实时展现到界面；
    + 4、指令(ng-click ng-model ng-href ng-src ng-if...)；
    + 5、服务Service($compile $filter $interval $timeout $http...)。

- Vue.js
    + 1、模块化，目前最热的方式是在项目中直接使用ES6的模块化，结合Webpack进行项目打包；
    + 2、组件化，创造单个component后缀为.vue的文件，包含template(html代码)，script(es6代码),style(css样式)；
    + 3、路由。
    
- 双向数据绑定
    + vue是一个渐进式的框架, 相当于view层, l两者都有双向数据绑定, 但是angularJS中的双向数据绑定是基于脏检查机制.
    + 当 `watch` 越来越多时会变得越来越慢，因为作用域内的每一次变化，所有 `watch` 都要重新计算。并且，如果一些 `watch` 触发另一个更新，脏检查循环（`digest cycle`）可能要运行多次。
    + vue的双向数据绑定是基于ES5的getter和setter来实现，所有的数据变化都是独立触发，除非它们之间有明确的依赖关系。

- 操纵DOM
    + `Vue`: 直接实例化对象，再将带有数据的对象挂载到相应DOM节点即可。
    + `angualrJS`: 中间多了一层controller，所有操作在相应controller的$scope中进行。


--------------------- 
作者：兵腾傲宇 
来源：CSDN 
原文：https://blog.csdn.net/qq_23334071/article/details/80504392 