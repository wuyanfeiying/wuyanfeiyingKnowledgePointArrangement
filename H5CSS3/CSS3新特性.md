> CSS3新特性
1. 结构选择器
    - :nth-child :first-child :last-child ...
2. 属性选择器
    - E[attr] 属性名，不确定属性值...
3. 伪类选择器
    - :checked选择被选中的input元素（单选按钮或复选框）
    - :hover 鼠标悬停其上的元素
    - :active鼠标点击时触发的事件
    - :focus 当前获取焦点的元素
4. CSS3新增文本属性
    - color:rgba();
    - text-overflow:是否使用一个省略标记（...）标示对象内文本的溢出
        + clip： 默认值 无省略号
        + ellipsis：当对象内文本溢出时显示省略标记（...）。
        + 注意：该属性需配合over-flow:hidden属性(超出处理)还有 white-space:nowrap(禁止换行)配合使用，否则无法看到效果
    - text-align:文本的对齐方式
    - text-shadow:文本阴影
5. CSS3弹性盒模型
    - flex-direction
    - justify-content
    - align-items
    - align-content
6. 新增背景属性
    - background
7. 新增圆角
    - border-radius
8. 新增颜色渐变
    - 线性渐变：linear-gradient(起点/角度，颜色 位置，...,)
    - 径向渐变：radial-gradient(起点(圆心位置), 形状/半径/大小，颜色1，颜色2)
9. 过渡
    - transition 过渡属性
10. 媒体查询
    ```javascript
    @media (min-width: 1200px) {
    .container {
        padding-right: 15px;
        padding-left: 15px;
    }
    }

    @media (min-width: 576px) {
    .container {
        width: 540px;
        max-width: 100%;
    }
    }

    @media (min-width: 768px) {
    .container {
        width: 720px;
        max-width: 100%;
    }
    }

    ...
    ````