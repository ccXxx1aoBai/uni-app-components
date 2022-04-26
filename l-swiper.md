* swiper 轮播图
* description 该组件一般用于导航轮播 广告展示等场景 引入即可使用
* property {Array} list 轮播图数据
* property {Boolean} showTitle 是否显示标题文字 需要配合list参数 默认false
* property {Number} current 轮播图起始页 默认0
* property {String} mode 指示器模式 默认dot 可选rect、round、number
* property {String} name list内图片属性名 默认image
* property {Boolean} indicator 是否显示指示器 默认false
* property {Number} height 轮播图组件高度 单位px 默认150
* property {Boolean} autoplay 是否自动播放 默认true
* property {Number} interval 自动轮播时间间隔 单位ms 默认3000
* property {Boolean} circular 是否衔接播放 默认false
* property {Number} border-radius 轮播图圆角值 单位px 默认8
* property {String} left 指示器距离左侧位置 默认0 单位% px
* event {Function} click 点击轮播图时触发
* example <l-swiper :list="list"></l-swiper> // 无标题
* example <l-swiper :list="list" :showTitle="true"></l-swiper> // 显示标题