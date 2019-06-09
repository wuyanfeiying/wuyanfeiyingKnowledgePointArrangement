> ## vue路由原理
- 无刷新跳转，是单页应用的一大优势，用户体验好，加载速度快。
    + `hash`模式
        + 路由默认模式，即通过在链接后面添加#+路由名字，根据匹配这个字段的变化，触发`hashchange`事件，动态的渲染出页面，类似与a标签中的锚点。
    + `history`模式
        + 需要在定义路由的时候通过`mode`字段去配置
        + 也就是使用的浏览器的 history API，pushState 和 replaceState。通过调用 pushState 操作浏览器的 history 对象，改变当前地址，同时结合window.onpopstate 监听浏览器的返回和前进事件，同样可以实现无刷新的跳转页面。replaceState 与 pushStete 不同的就是，前者是替换一条记录，后者是添加一条记录。

> ## 路由传参的两种方式
- `/params`,表现在url上,params参数需要配置到路由定义上
- `query`以`?query=query1`

> ## vue路由的跳转
- 声明式
    + 使用`<router-link>`声明跳转，`to`属性定义跳转的参数。
- 编程式
    + 使用 `router.go()、router.push()、router.replace()`方法进行跳转，`go`方法就是与浏览器的history api 的方法相同，可以进行返回上一页等操作。

> ## 路由守卫
- vue 路由守卫分为三种，一种是全局的路由守卫，通常在实例化路由之后设置，来做一些通用的路由操作，它所有的路由跳转都会执行的操作；一种是单个路由独享的守卫，在单个路由定义的时候进行设置，所有跳转这个路由都会执行；另外一种就是组件内的守卫，只在组件内生效。

```javascript
// 全局路由守卫类型：

router.beforeEach(to, from, next)
router.afterEach(to, from, next)

// 路由独享的守卫：

beforeEnter(to, from, next)

// 组件独享的守卫:

beforeRouteEnter(to, from, next)
beforeRouteUpdate(to, from, next)  —— 动态参数路径改变时，组件实例被复用的时候调用。
beforeRouteLeave(to, from, next) —— 导航离开组件所在路由时被调用。

```
作者：下小朋友
链接：https://juejin.im/post/5cac05305188251b2261ca7b
来源：掘金