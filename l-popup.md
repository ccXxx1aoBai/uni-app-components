* popup 底部弹出框
* description 该组件一般用于用户提示 互动 引入即可使用
* 可自行设置插入 dom
* content {String} 显示内容
* height {Number} 弹出框高度 默认150 单位px
* radius {Number} 圆角 默认25 单位px
* example <l-popup :height="200" :radius="15" content="你好" ref="popup"></l-popup>
* 通过$refs 调用show 和 hide 方法