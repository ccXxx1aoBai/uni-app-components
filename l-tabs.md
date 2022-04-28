* tabs 标签
* description 标签组件 目前暂不支持左右滑动
* 可自行设置插入 dom
* tabs {Array} 标签名称
* current {Number} 当前选中tab 默认0
* @tapChange 返回点击标签序号 配合 swiper 使用时可用于切换 swiper-item
* example <l-tabs :tabs="tabs" :current="current" @tapChange="tapChange"></l-tabs>